# Turn on sync and shared trips

Khoroch works fully offline without any of this. These steps connect your copy to a free Firebase project, so you can sign in, use the same khatas on every device, and invite trip mates to add expenses live.

It takes about 10 minutes and needs no credit card. Firebase's free Spark plan is enough for personal and small-group use.

## 1. Create the project

1. Go to [console.firebase.google.com](https://console.firebase.google.com) and sign in with your Google account.
2. Click **Create a project**, name it `khoroch`, and continue. You can turn Google Analytics off.

## 2. Turn on sign-in

1. In the left menu, open **Build → Authentication** and click **Get started**.
2. On the **Sign-in method** tab, enable **Google** (pick your email as the support email) and **Email/Password**.
3. Open the **Settings** tab, then **Authorized domains**, and click **Add domain**. Add the address your app is hosted on, without `https://` or a path. For GitHub Pages that's `arifahamed01.github.io`.

## 3. Create the database

1. Open **Build → Firestore Database** and click **Create database**.
2. Choose a location close to you, for example `asia-south1 (Mumbai)` or `asia-southeast1 (Singapore)`. You can't change this later.
3. Start in **production mode**.
4. Open the **Rules** tab, delete what's there, paste everything from [`firestore.rules`](firestore.rules), and click **Publish**.

These rules make sure only the people on a khata can read or change it, and that an invite link can only add the person who uses it.

## 4. Connect the app

1. Click the gear icon next to **Project Overview**, then **Project settings**.
2. Under **Your apps**, click the web icon `</>`. Name the app `Khoroch` and click **Register app**. Skip Firebase Hosting.
3. Firebase shows a `firebaseConfig` block. Copy four values from it into [`firebase-config.js`](firebase-config.js) in this repository:

```js
window.KHOROCH_FIREBASE = {
  apiKey: "AIza...",
  authDomain: "khoroch-xxxx.firebaseapp.com",
  projectId: "khoroch-xxxx",
  appId: "1:1234567890:web:abc123"
};
```

On GitHub, open `firebase-config.js`, click the pencil icon, paste the values, and click **Commit changes**.

These values identify your project. They aren't secret, and it's safe to keep them in a public repository: the database rules from step 3 decide who can see what.

## 5. Try it

1. Wait a minute or two for GitHub Pages to update.
2. Open the app and refresh it twice so it picks up the new version.
3. A **Sync and share** bar appears under the globe. Tap it and sign in.

Your khatas upload to your account. Sign in on another phone or computer and they appear there too.

## Sharing a trip

1. Open the trip, tap the share icon, then **Invite people to edit**.
2. Send the link, for example in your WhatsApp group.
3. Each friend opens the link, signs in, and the trip opens for them. Everyone's expenses then appear on everyone's phone.

The people inside a trip (like "Arif & Gemi") are only names for splitting costs. Accounts are separate: anyone who joins with the link can add and edit any entry. Only the person who started the trip can create invite links or delete the trip for everyone. Others can leave it, which removes it from their devices only.

## Good to know

- **Offline:** changes save on the phone first and upload when you're back online. Two people editing the same entry at the same time: the last save wins.
- **Bill photos don't sync.** They stay on the phone that took them.
- **Signing out** removes synced khatas from that device. They stay in your account and come back when you sign in again.
- **Free plan limits** (50,000 reads and 20,000 writes a day) are far above what one person or a travel group uses.
- **Optional extra safety:** in [Google Cloud Console → Credentials](https://console.cloud.google.com/apis/credentials), open the "Browser key" Firebase created and restrict it to your site under **Website restrictions**, for example `https://arifahamed01.github.io/*`.

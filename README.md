# Khoroch

**Split trip costs with friends and track your daily spending, even with no internet.**

Khoroch (খরচ, "expense" in Bangla) is a lightweight expense app that installs on your phone from the browser. Use it to keep a shared tab on a group trip, or as a personal daily ledger with a monthly budget. Everything is stored on your device. There's no account, no server and no tracking.

<p>
  <img src="screenshots/home.png" width="200" alt="Home screen with a 3D globe and your trips and ledgers">
  <img src="screenshots/trip.png" width="200" alt="Trip overview with who pays whom and group balances">
  <img src="screenshots/add-expense.png" width="200" alt="Adding an expense with two payers and a per-person split">
  <img src="screenshots/daily-ledger.png" width="200" alt="Daily ledger with monthly budget and category breakdown">
</p>

## Features

The home screen keeps your khatas in four tabs, **Daily**, **Trips**, **Cards** and **Loans**, and opens on the one you used last. Hold a khata and drag it up or down to reorder it, or hold a tab and drag it left or right.

### Group trips
- Add each traveller, or add a couple or family as one entry with a headcount, so a group of 3 pays more than a couple.
- Split each expense **per person**, **per group** or by **custom amounts**, and include only the people it was for.
- Record **more than one payer** on a single expense, for example "SL paid 500, AG paid 80".
- **Settle up** shows the fewest payments needed to square everyone. Tap **Mark paid** when money changes hands.
- Balances show what each member paid, their fair share and the cost per person.

### Daily ledger
- Log personal spending by category: food, transport, accommodation, sightseeing, shopping, bills, health, fun and other.
- Set an optional **monthly budget** to see what's left and how much you can spend per day.
- Browse month by month, with daily totals and a category breakdown.

### Sync and shared trips (optional)
- **Sign in** with Google or email to keep your khatas on every phone and computer. Everything still saves on the device first, so the app keeps working offline and uploads when you're back online.
- **Share a trip** with an invite link. Friends who join can add and edit expenses, and everyone sees changes live.
- Runs on your own free Firebase project. Follow [SYNC_SETUP.md](SYNC_SETUP.md) to turn it on. Without it, Khoroch stays offline-only and nothing leaves the phone.

### Lending and borrowing
- A **Loans** khata records money you lend and borrow: **You lent**, **You borrowed**, **Got back** and **You paid back**, with an optional pay-back date.
- **From your daily expenses:** in a daily ledger, set **Paid with** to **Lent to someone** or **Borrowed from someone**. The entry is added to your Loans khata automatically. Money you lent leaves the daily list once it's paid back, and only the unpaid part counts toward your spending until then.
- **Pay back in installments:** choose how many, the first date and how often (monthly, every 2 weeks or weekly). Khoroch lays out the dates and amounts, and you can change any of them. Repayments are matched to installments oldest first, so each one shows as paid, due or overdue.
- See the total **owed to you** and what **you owe**, a balance for each person, and anything past its due date.
- Open a person to see their history and record a repayment in one tap, for the full balance or any part of it.

### Credit card fee waivers
Many cards waive the yearly fee after a set number of transactions, and every bank counts differently. A **Credit card** khata tracks this for each card.
- **Cards without a transaction waiver:** some cards (for example ones whose fee is waived with reward points) don't use a transaction count. Set **Annual fee waiver** to **Not by transactions** and the card skips the counting, while bills, what you owe, the limit and spending still work.
- **Each card has its own rules:** transactions needed, the date the fee year starts, an optional minimum amount, the annual fee, and which kinds of transaction count (card purchase, online, QR payment, mobile recharge, utility bill, wallet or transfer, cash withdrawal, EMI, fees).
- **Upload a monthly statement** as a PDF (password-protected ones too), a photo or a CSV. Khoroch lists the transactions, skips payments and refunds, marks anything already added, and lets you untick lines before adding them.
- **Each transaction gets a type** from its description, for example "BANGLA QR" becomes a QR payment and "GP RECHARGE" a mobile recharge. You can change the type, or mark a single transaction as counting or not counting.
- **Still to pay at a glance:** the big number on each card is what you still owe: the unpaid part of the latest bill plus anything spent since that statement. Add your **credit limit** in the card's settings to see how much is still available.
- **Pay with any card:** every expense in a trip or daily ledger has a **Paid with** dropdown: Cash, Debit card, or one of your credit cards. Pick a credit card and the expense is added to that card automatically, counts toward its fee waiver, and raises what you owe until the next bill.
- **Track each month's bill:** when you upload a statement, Khoroch reads the outstanding amount, the minimum due and the last date of payment, and shows them to you first. You type in how much you paid (or tap **Paid in full** or **Paid the minimum**). The card shows what's still to pay and warns you as the due date gets close or passes. If something was read wrong, tap **Edit**. You can also add a bill by hand.
- **See your progress:** a punch card of qualifying transactions with an even-pace marker, transactions each month (counted and not counted), spending each month, and breakdowns by type and category. Past fee years are kept.
- Statement passwords are used only to open the file and are never saved.

### Scan bills
- **Take a photo** of a bill or **upload** an image or PDF invoice when adding an expense.
- Khoroch reads the **total, date and shop name** and fills them in for you to check. If it picks the wrong total, tap the right one from the amounts it found.
- The bill photo is saved with the entry. Tap the thumbnail to view it full screen.
- Reading runs on your phone with [Tesseract.js](https://github.com/naptha/tesseract.js) (photos) and [PDF.js](https://mozilla.github.io/pdf.js/) (PDFs). The reader downloads once, about 5 MB, the first time you scan. After that it works offline.
- Works best on printed bills in English, held flat and in good light. Handwritten bills are hard to read.

### Sharing and export
- **Summary message:** totals and who pays whom, formatted for WhatsApp.
- **Trip code:** a compact code you can paste in a chat. A friend imports it into their own Khoroch with the full trip included.
- **CSV export** for Excel or Google Sheets.
- **Backup** of every book as a single code or file. Bill photos stay on the phone and aren't included.

### Design
- A clean, modern look inspired by Sylhet's tea gardens: a cool white page, deep tea-garden green for the hero and the **হালখাতা** settle-up card, jade for every button, and gold only for the coin and travel routes.
- Each khata is a soft pastel card in its own colour, so trips, daily ledgers and credit cards are easy to tell apart at a glance.
- Design rules from [UI/UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) for personal finance apps: green for money coming back, red for money owed, touch targets of at least 44 px, and text contrast of at least 4.5:1 in both light and dark mode.
- A 3D globe of travel routes that you can spin by dragging, cards that tilt, 3D bar charts and a coin flip when you save.
- Follows your phone's light or dark theme.
- Respects the system's reduced-motion setting.
- Supports ৳ BDT, ₹ INR, $ USD, € EUR, £ GBP, ฿ THB, RM MYR, रू NPR, AED and ¥ JPY.

## Install on Android

1. Open the hosted link in **Chrome**.
2. Tap **Install app** on the home screen, or use **⋮ menu → Add to Home screen**.
3. Open Khoroch from your app drawer. After the first visit it works fully offline.

Khoroch also runs in any modern browser on iPhone and desktop. On iPhone, use **Share → Add to Home Screen** in Safari.

## Host your own copy

Khoroch is plain static files with no build step. Any HTTPS static host works, and these are free:

| Host | How |
|---|---|
| **GitHub Pages** | Push this folder to a repository, then go to **Settings → Pages → Deploy from branch** and choose `main` / root. |
| **Netlify Drop** | Drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop). |
| **Cloudflare Pages** | **Workers & Pages → Create → Upload assets**, then drop the folder. |

The service worker needs HTTPS (or `localhost`) for offline mode and installation to work. To try it locally, run:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

### Shipping an update
Replace the files, then bump the cache name in `sw.js` (for example `khoroch-v1` → `khoroch-v2`) so installed copies pick up the new version.

### Play Store / APK
Once it's hosted, [PWABuilder](https://www.pwabuilder.com) can package the URL as an Android app (Trusted Web Activity) for the Google Play Store.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app: markup, styles and script in one file |
| `sw.js` | Service worker that caches the app for offline use |
| `firebase-config.js` | Your Firebase project settings for sync. Empty means offline-only |
| `firestore.rules` | Database security rules to paste into Firebase |
| `SYNC_SETUP.md` | Step-by-step guide to turn on sync and shared trips |
| `manifest.webmanifest` | Name, colours and icons used when installing |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | App icons |
| `screenshots/` | Images used in this README |

## Privacy

Without sync, your data and bill photos are saved only in your browser's storage on your own device. With sync turned on, your khatas are stored in your own Firebase project and only the accounts you invite can read them. Bill photos never leave the phone. Bills are read on the phone itself, and nothing is uploaded anywhere. Clearing the browser's site data deletes it, so use **Share → Back up everything** now and then.

## Built with

Vanilla HTML, CSS and JavaScript, with no build step. Bill scanning loads Tesseract.js and PDF.js on first use. The 3D effects are drawn with Canvas 2D and CSS transforms. The fonts are [Bricolage Grotesque](https://fonts.google.com/specimen/Bricolage+Grotesque) and [Hind Siliguri](https://fonts.google.com/specimen/Hind+Siliguri) from Google Fonts, cached for offline use after the first load.

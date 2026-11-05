# Spending

A tiny personal spending tracker for iPhone (Safari / Home Screen). Everything is in `index.html`; data stays in the browser's localStorage on your phone.

- **Auto-refresh**: save a direct link to `spending.txt` in Settings and it's fetched on every app start, when the app comes back to the foreground, and with the ↻ button (only new lines are added). The link must serve the plain file and allow cross-site fetches; Safari can't read iCloud Drive on its own. Without a link, ↻ opens the file picker
- Imports `spending.txt` (Banka Sparkasse SMS lines and `APPLE PAY;amount;merchant;dd.MM.yyyy HH:mm` lines), skipping lines already imported
- Also reads **notifications** the Shortcut appends to the same file (title and text on one line or on separate lines):
  - **mStik**: `Plačilo 10,00 EUR s kartico 5305…7168 na prodajnem mestu MERCATOR   Ljubljana   SI.` (cash withdrawals, refunds and incoming money follow the same rules as the SMS)
  - **Revolut**: `🛍 Paid 9,40 € (10,49 US$) at Amazon`; the balance line and titles are skipped, refunds lower spending, foreign-currency-only payments go to review
  - mStik payments **to Revolut are skipped** (only moving money); the Revolut notification records the real purchase
  - Notifications carry no date: put one in front (e.g. `05.11.2026 14:03 Plačilo …`, or a date on its own line before it). Without it the import time is used and shown as `~14:03`
  - The same payment seen twice (SMS / mStik / Apple Pay, or Revolut / Apple Pay) goes to Needs review as a likely duplicate
- **Scan UPN QR** (header button or "Scan UPN QR instead" when adding): point the camera at a Slovenian payment slip, or pick a photo, and the payment is added right away with recipient, amount and purpose (category guessed, Bills by default). Scanning the same slip twice asks first. Uses the bundled `jsQR.min.js`
- **STORNO** lines are refunds: the money back lowers spending in the original purchase's category
- **DVIG** lines are cash withdrawals in their own **Cash** category; you're asked what the cash was for
- Transfers to **Revolut** ask what they were spent on (Bills, Fun, Amazon or any other category)
- Unrecognized lines, incoming money and likely SMS/Apple Pay duplicates go to **Needs review**; incoming money can be added as income in one tap
- **Budget** tab: add your paycheck(s) per month, see what's left after spending and saving, and set per-category budgets deducted from it
- **Savings**: monthly savings goal, plus how much of your income you saved each month (amount and %)
- **Recurring payments** (e.g. installments): amount, category (default Bills), first month, number of months (or no end) and day; deducted automatically every month without being in the file
- Add your own categories (Settings, or "＋ New" when editing a transaction)
- Category guessing by merchant, with remembered per-merchant overrides
- Monthly overview, category chart, CSV export/restore (includes income)
- Card numbers are never stored

`jsQR.min.js` is needed for QR scanning (Safari has no built-in QR reader for web pages). `sw.js`, `manifest.webmanifest` and the icons are optional extras for offline use and a nice Home Screen icon when hosted (e.g. GitHub Pages).

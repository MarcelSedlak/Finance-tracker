# Spending

A tiny personal spending tracker for iPhone (Safari / Home Screen). Everything is in `index.html`; data stays in the browser's localStorage on your phone.

- **Auto-refresh**: save a direct link to `spending.txt` in Settings and it's fetched on every app start, when the app comes back to the foreground, and with the ↻ button (only new lines are added). The link must serve the plain file and allow cross-site fetches; Safari can't read iCloud Drive on its own. Without a link, ↻ opens the file picker
- Imports `spending.txt` (Banka Sparkasse SMS lines and `APPLE PAY;amount;merchant;dd.MM.yyyy HH:mm` lines), skipping lines already imported
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

`sw.js`, `manifest.webmanifest` and the icons are optional extras for offline use and a nice Home Screen icon when hosted (e.g. GitHub Pages).

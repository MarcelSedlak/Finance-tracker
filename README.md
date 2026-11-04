# Spending

A tiny personal spending tracker for iPhone (Safari / Home Screen). Everything is in `index.html`; data stays in the browser's localStorage on your phone.

- Imports `spending.txt` (Banka Sparkasse SMS lines and `APPLE PAY;amount;merchant;dd.MM.yyyy HH:mm` lines), skipping lines already imported
- **STORNO** lines are refunds: the money back lowers spending in the original purchase's category
- **DVIG** lines are cash withdrawals in their own **Cash** category; you're asked what the cash was for
- Transfers to **Revolut** ask what they were spent on (Bills, Fun, Amazon or any other category)
- Unrecognized lines, incoming money and likely SMS/Apple Pay duplicates go to **Needs review**; incoming money can be added as income in one tap
- **Budget** tab: add your paycheck(s) per month, see what's left after spending, and set per-category budgets deducted from it
- Add your own categories (Settings, or "＋ New" when editing a transaction)
- Category guessing by merchant, with remembered per-merchant overrides
- Monthly overview, category chart, CSV export/restore (includes income)
- Card numbers are never stored

`sw.js`, `manifest.webmanifest` and the icons are optional extras for offline use and a nice Home Screen icon when hosted (e.g. GitHub Pages).

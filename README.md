# Spending

A tiny personal spending tracker for iPhone (Safari / Home Screen). Everything is in `index.html`; data stays in the browser's localStorage on your phone.

- Imports `spending.txt` (Banka Sparkasse SMS lines and `APPLE PAY;amount;merchant;dd.MM.yyyy HH:mm` lines), skipping lines already imported
- Unrecognized lines, incoming money, refunds, cash withdrawals and likely SMS/Apple Pay duplicates go to **Needs review**
- Category guessing by merchant, with remembered per-merchant overrides
- Monthly overview, category chart, optional budgets, CSV export/restore
- Card numbers are never stored

`sw.js`, `manifest.webmanifest` and the icons are optional extras for offline use and a nice Home Screen icon when hosted (e.g. GitHub Pages).

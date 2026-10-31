# HiLo

A free, single-file browser price-guessing game with Nano at its heart. You're shown a coin, a date and its price; guess whether the next hidden card's price was higher or lower. No build step, no backend, no fees — and no live price feed, so the game never goes stale or breaks when an API changes.

## Play

- **Guess** Higher or Lower for the hidden card below the current one. Guess right and it becomes the new current card, with a fresh hidden card drawn below it — keep the chain going.
- **Daily challenge:** the same 15-card chain for everyone, new every day at 00:00 UTC. Reach the end without a wrong guess to clear the day and keep your streak.
- **Quick 60:** 60 seconds of guesses. A wrong one just resets your streak; the game carries on.
- **Survival:** a classic chain that ends on your first wrong guess. See how long you can go.
- **Skip:** not sure about the next card? Skip it once per round for a fresh one (two for supporters), free of charge to your streak.
- **Keyboard:** up arrow or H for Higher, down arrow or L for Lower, Enter or Space for Next.
- **Ranks** (by total correct guesses): Newbie, Hodler (50), Diamond Hands (150), Whale (400), Satoshi (1,000).

Everything is stored in the player's browser.

## About the data

All 51 price cards are rounded, publicly reported historical figures — mostly well-known milestones (all-time highs, bear-market lows, launch prices) across Bitcoin, Ethereum, Litecoin, Dogecoin, Monero, XRP, Cardano, Solana, BNB, Polkadot and Nano. They were checked against news and market-data sources (CoinGlass, CoinMarketCap-citing reporting, and contemporary news coverage) while this game was built, then rounded for a cleaner guessing game. They are **approximations for entertainment, not exact exchange data, live prices or financial advice**, and nothing in the game predicts future prices.

Cards live in the `DATA` array near the top of the script in `index.html`, as `[ticker, "date label", price]`. Coin names and colours are in the `COINS` object just above it. Every price in the dataset is unique, so there are no ties to worry about if you add more.

## Deploy on GitHub Pages

1. Create a new repository, for example `hilo`.
2. Upload `index.html` and `README.md` to the root of the repository.
3. Open **Settings > Pages**, set the source to **Deploy from a branch**, choose `main` and `/ (root)`, then save.
4. After a minute the game is live at `https://<your-username>.github.io/hilo/`.

## Donations

The tip card works the same way as in the other Feeless games:

- A `nano:` payment link with the chosen amount, shown as a QR code and an **Open in wallet** button.
- A **Copy address** button.
- An **I've sent it, check** button that asks public Nano nodes whether a matching payment arrived, and unlocks the supporter perks (Gold, Mint and Neon accent colours, and a second skip) on that browser.

To use a different wallet, change `NANO_ADDRESS` near the top of the script in `index.html`. If the public RPC endpoints in `RPCS` ever block browser requests, point them at your own proxy.

The supporter unlock is stored in `localStorage`, so it is a thank-you perk, not secure access control.

Add `?selftest` to the URL to expose a small `window.__hl` object for automated tests.

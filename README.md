# TrenchSwap_formFeeds

Shared Trenching call-out feed for TrenchSwap. Approved calls only.

Live feed URLs read by the TrenchSwap app:
- https://raw.githubusercontent.com/AppsthatPay/TrenchSwap_formFeeds/main/calls.json
- https://raw.githubusercontent.com/AppsthatPay/TrenchSwap_formFeeds/main/token-pages.json

## How it works

- The TrenchSwap app reads `calls.json` from this repo (raw GitHub URL). It holds NO GitHub token and never writes here from the client.
- A user submits a call in the app. The call goes to review. Jeffrey or Allen reviews it, and an approved call is committed to `calls.json` by hand. Approved calls then appear in the app's shared feed. Nothing auto-publishes.
- Shared calls are real user calls only. No seeded, invented, or example calls. The file starts empty.
- Moderation: decline spam, copied text, engagement bait, empty hype, and calls with no real take. A declined call never appears here. Abusive or scam calls are removed.
- Privacy: a call shows only what the user submitted. No wallet address, no private key, no seed, no email.

## Entry schema

Each entry in `calls`:

```json
{
  "mint": "token mint address",
  "ticker": "TICKER",
  "image_url": "https://.../token-image.png",
  "text": "Call text, max about 140 chars",
  "wallet_name": "display name shown with the call",
  "x_handle": "@handle (optional)",
  "timestamp": "2026-11-12T17:00:00Z"
}
```

Top level: `version` (number), `updated_at` (ISO timestamp), `calls` (array, newest first).

## token-pages.json

Approved "Claim a Token" pages. Same rules: claimed pages only, published by hand after review. Starts empty: `{"pages": [], ...}`. The app reads `pages` (or a bare array) and schema-validates every entry on read.

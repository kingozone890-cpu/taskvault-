# TaskVault Real MVP

A small working full-stack MVP for:
Register → Earn → Wallet → Add Bank Account → Withdraw → Admin Dashboard.

## Run locally

1. Install Node.js 20+.
2. Copy `.env.example` to `.env` and change the admin password and JWT secret.
3. Run:
   npm install
   npm start
4. Open http://localhost:3000

## Admin

POST `/api/admin/login` with the credentials from `.env`. The admin API lists withdrawals and can set them to `processing`, `paid`, or `failed`.

For a production deployment, connect the `paid` transition to a regulated Nigerian payout provider such as Paystack or Flutterwave using their server-side transfer API. Never put provider secret keys in browser JavaScript.

## Important production requirements

- Use HTTPS.
- Use a strong random JWT secret or preferably secure HTTP-only session cookies.
- Encrypt or otherwise protect bank details at rest and restrict database access.
- Add email/phone verification, rate limiting, CSRF protection, audit logs, KYC/AML controls where applicable, and fraud detection.
- Do not promise instant withdrawals unless the payout provider actually confirms them.
- Keep task rewards funded by advertiser/task revenue; do not fund user withdrawals from unverified ad-click revenue.
- For Google-served ads, follow the applicable rewarded-ad and invalid-traffic policies. Do not incentivize clicks on ordinary ads.
- Before taking deposits or operating a large payout marketplace, obtain appropriate legal, tax, consumer-protection, and payment-provider guidance for Nigeria and any other countries served.

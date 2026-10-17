# JewelBooks POS Invoice — Android prototype

This is a buildable Android Studio **source project**, not a compiled APK. The environment did not have Android SDK/Gradle to compile or run device tests.

## Build
Open the folder in Android Studio, allow Gradle sync, then Build > Build APK(s). Use a recent Android Studio with SDK 35 installed.

## What works
- Standalone offline POS preview using Android WebView
- Gold and silver category selection
- Sale and old-metal purchase calculation modes
- Gross/stone/net weight, rate, value addition, labour, discount, GST and rounded total
- Reset, local preview (Android WebView print behavior varies)

## NOT implemented
- Live admin authentication
- API write / invoice persistence / voucher numbering
- Inventory updates, ledgers, GST posting, rollback or reconciliation
- Actual PDF or WhatsApp share integration
- APK compilation or Android device testing

## Existing website findings
The supplied archive has `api/login.php`, `api/data.php`, and `api/accounting-store.php`. The `api/data.php` endpoint operates on a large shared accounting payload. Blindly writing it from the POS risks overwriting concurrent changes. Before production, implement a **new server-side atomic transaction endpoint** with admin authorization, voucher idempotency keys, stock-movement ledger, and reversal tests. Keep all credentials out of the Android package.

The existing JewelBooks site was not modified. Do not deploy this preview for real transactions.

# Gold Signal AI — PWA prototype for Android

This is a mobile-first installable web app prototype, useful when the user only has an Android phone. It is not an APK and it is not yet a production trading system.

## Run from Android
To install as an app, host the files on an HTTPS static host. You can do this from a mobile browser using a repository/site hosting service:
1. Create a repository on a Git hosting service.
2. Upload `index.html`, `manifest.json`, and `sw.js` to the repository root.
3. Enable its static Pages hosting feature.
4. Open the generated HTTPS site in Chrome on Android.
5. Chrome menu → Add to Home screen / Install app.

Some free hosting services or provider API plans may block requests or require a supported plan. API key is only held in page memory and is not saved, but browser requests still expose it to the user's browser/network and it should not be shared. A production version should use a backend proxy and secret storage.

## Market data
Uses Twelve Data REST endpoint for XAU/USD with `1min`, `5min`, and `1h`. Availability and real-time access depend on provider plan. Updates only when the user presses the button, so this is not streaming/polling live yet.

## Signal rules
- H1 and M5 bullish when last close > EMA20 > EMA200.
- H1 and M5 bearish when last close < EMA20 < EMA200.
- M1 confirmation is close relative to EMA20.
- If not aligned, `NO TRADE`.
- Support/resistance: lowest low / highest high over latest 20 M5 candles.
- SL/TP1/TP2 are simple candidate calculations; they are not validated trading instructions.

## Safety
No MT5 integration, no order execution, no HFM spread validation, no economic calendar, no backtest, no lot-based loss calculation. Always verify quotes on HFM MT5 and test on demo.

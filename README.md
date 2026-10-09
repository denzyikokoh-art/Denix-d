# DENIX D — Android + iPhone app source (early prototype)

This package prepares the existing online arena prototype for wrapping as an installable Android/iOS app using Capacitor. It is **not a finished game** and it does **not** include a compiled APK, signed iPhone app, or a deployed multiplayer server yet.

## What it includes
- The current 2D online arena game UI and client.
- The Node.js/WebSocket multiplayer server (`server.js`).
- Capacitor configuration for app ID `com.denixd.game` and app name `DENIX D`.
- A server URL setting at `public/server-config.js`.

## Required before online app testing
1. Deploy `server.js` to a Node.js host that supports long-lived WebSocket connections (for example, a correctly configured Render Web Service).
2. Copy the live HTTPS service URL into `window.DENIX_SERVER_URL` in `public/server-config.js`. The client converts HTTPS to secure WebSockets (`wss://`).
3. Test the browser game with at least two devices before packaging.

## Build Android app (Windows, macOS or Linux)
Install Node.js 20+ and Android Studio with an Android SDK.

From this folder:
```bash
npm install
npm install @capacitor/android
npx cap add android
npx cap sync android
npx cap open android
```
In Android Studio, wait for Gradle sync, choose an emulator or connected Android phone, then Run. For an APK, use **Build > Build Bundle(s) / APK(s) > Build APK(s)**. For Play Store distribution, create a signed Android App Bundle and complete Play Console requirements.

## Build iPhone app (requires a Mac)
Install Node.js 20+, Xcode, and Xcode command-line tools on a Mac.

```bash
npm install
npm install @capacitor/ios
npx cap add ios
npx cap sync ios
npx cap open ios
```
In Xcode, configure the Apple Developer signing team and bundle ID, then run on a device or archive for TestFlight/App Store review. An iOS build/signing workflow cannot be completed on a Windows PC alone; a Mac or suitable remote Mac build service is required.

## Important limitations
- This is an early 2D arena prototype, not the planned full 3D battle-royale game.
- Multiplayer server must be deployed separately and tested; this ZIP does not publish the server.
- No login/account system, payment system, matchmaking/ranked modes, voice chat, streaming, final character art, or 90+ weapon inventory is implemented yet.
- No APK or signed iOS binary is included because those need the platform SDK/build tools and, for iOS distribution, Apple signing.
- Do not publish until you have tested gameplay, security, server load, privacy, store policies, and age/content requirements.

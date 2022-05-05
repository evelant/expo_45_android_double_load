Expo SDK 45 with dev client and `jsEngine: "hermes"` loads the app bundle twice at startup in Android development mode. This causes all sorts of problems in anything beyond trivial apps.

To reproduce:

```
eas build -p android --profile development
//connect an android device
adb install ./build-123123123.apk
yarn start
//open app on device and connect to dev server
```

following these steps there will be output like

```
Android Bundling complete 23ms
loaded App.tsx
Android Bundling complete 52ms
Android Running app on SM-G965U
rendered App
loaded App.tsx
Android Running app on SM-G965U
rendered App
```

The app bundle is built twice and run twice on the device.

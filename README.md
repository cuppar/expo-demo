# Expo Building Android APK

## Environment Require

- [Node.js](https://nodejs.org/en/)
- Windows users must have WSL enabled. You can follow the installation guide [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10). 

## 1. Install Expo CLI 
```bash
$ npm install -g expo-cli
```
or
```
$ yarn global add expo-cli
``` 
## 2. Configure `app.json`

```json
{
  "expo": {
   "name": "Your App Name",
   "icon": "./path/to/your/app-icon.png",
   "version": "1.0.0",
   "slug": "your-app-slug",
   "sdkVersion": "XX.0.0",
   "ios": {
     "bundleIdentifier": "com.yourcompany.yourappname"
   },
   "android": {
     "package": "com.yourcompany.yourappname"
   }
  }
}
```
- The iOS bundleIdentifier and Android package fields use reverse DNS notation, but don't have to be related to a domain. Replace "com.yourcompany.yourappname" with whatever makes sense for your app.
- You're probably not surprised that name, icon and version are required.
- slug is the url name that your app's JavaScript is published to. For example: `expo.io/@community/native-component-list`, where community is my username and native-component-list is the slug.
- The sdkVersion tells Expo what Expo runtime version to use, which corresponds to a React Native version. Although "XX.0.0" is listed in the example, you already have an sdkVersion in your app.json and should not change it except when you want to update to a new version of Expo.

## 3. Start the build
Run
```
expo build:android
```
If you don't already have a packager running for this project, expo will start one for you.
#### You can choose to build
- APK
```
expo build:android -t apk
```
- Android App Bundle (publish to Google Play)
```
expo build:android -t app-bundle
```
 App bundles are recommended, but you have to make sure the [Google Play App Signing](https://docs.expo.io/versions/v34.0.0/distribution/app-signing/) is enabled for your project, you can read more about it [here](https://developer.android.com/guide/app-bundle)

## 4. Wait for it to finish building
When one of expo's building machines will be free, it'll start building your app. You can check how long you'll wait on [Turtle status](https://expo.io/turtle-status) site. We'll print a url you can visit (such as `expo.io/builds/some-unique-id`) to watch your build logs. Alternatively, you can check up on it by running `expo build:status`. When it's done, you'll see the url of a .apk (Android) or .ipa (iOS) file -- this is your app. Copy and paste the link into your browser to download the file.

## 5. Test it on your device or simulator
- To run it on your Android device
- You can drag and drop the .apk into your Android emulator. 

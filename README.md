# Expo ImagePicker Android Crash: Inconsistent TypeError

This repository demonstrates a bug in the Expo ImagePicker library on Android.  The app intermittently crashes after selecting an image, throwing a `TypeError: undefined is not an object (evaluating 'response.assets[0].uri')` error.  This is likely due to an asynchronous race condition where the response object is accessed before its assets are fully populated.

## Steps to Reproduce

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on an Android device or emulator.
4. Select an image using the ImagePicker.
5. The app may crash, or it may work correctly. Repeat step 4 until a crash occurs.

## Solution

A solution is implemented in `bugSolution.js` that addresses this issue by using promises to check if the data has arrived before trying to access it. This ensures that we are always accessing `response.assets` after the data is completely available, thus preventing the crash.
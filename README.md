# React Native Project Setup Guide

## Table of Contents

- [Create a New React Native Project](#1-create-a-new-react-native-project)
- [Run the Project](#2-run-the-project)
- [Setup Splash Screen](#3-setup-splash-screen-using-react-native-bootsplash)
- [Update Navigation](#5-update-navigation)
- [Copy and Setup Assets](#5-copy-and-setup-assets)
- [Setup Redux Toolkit](#6-setup-redux-toolkit)
- [Copy Utils & Theme Folders](#7-copy-utils-theme-folders)

## 1. Create a New React Native Project

1. Open the terminal and navigate to the desired project folder.
2. Run the following command to create a new React Native project:
   ```sh
   npx react-native init ProjectName --version <react-native-version> 
   ```
   - This command initializes a new React Native project with TypeScript support.
3. Navigate into the project directory:
   ```sh
   cd ProjectName
   ```
4. If using iOS, install CocoaPods dependencies:
   ```sh
   cd ios && pod install && cd ..
   ```

## 2. Run the Project

1. Start Metro Bundler to manage JavaScript bundling:
   ```sh
   npx react-native start
   ```
2. Run the application on an emulator or physical device:
   ```sh
   npx react-native run-android
   ```
   or
   ```sh
   npx react-native run-ios
   ```
   - Ensure you have an emulator or device connected for testing.

## 3. Setup Splash Screen Using react-native-bootsplash

1. Install the required package to handle splash screens:
   ```sh
   yarn add react-native-bootsplash
   ```
2. Link the package if using React Native < 0.71:
   ```sh
   npx react-native-setup-init
   ```
3. Generate the splash screen images:
   ```sh
   npx react-native-bootsplash generate --platforms android,ios --background-color "#FFFFFF" --logo-path path/to/logo.png
   ```
   - Please reter to [React Native BootSplash setup](https://www.npmjs.com/package/react-native-bootsplash) for full configurations.
   - Ensure you replace `path/to/logo.png` with the actual path to your splash screen logo image.
4. Modify `App.tsx` to hide the splash screen once the app is loaded:
   ```tsx
   import { useEffect } from 'react';
   import RNBootSplash from "react-native-bootsplash";

   useEffect(() => {
       setTimeout(() => {
           RNBootSplash.hide();
       }, 1000);
   }, []);
   ```
5. Run the project to verify the splash screen setup:
   ```sh
   npx react-native run-android
   ```
   or
   ```sh
   npx react-native run-ios
   ```

## 4. Update Navigation

1. Install React Navigation if it is not already installed:
   ```sh
   yarn add @react-navigation/native
   yarn add react-native-screens react-native-safe-area-context react-native-gesture-handler react-native-reanimated react-native-vector-icons
   ```
2. Set up navigation same as Master project.

## 5. Copy and Setup Assets

1. Copy assets folder from the Master project as per requirement.
2. Ensure assets are correctly linked in `react-native.config.js`:
   ```js
   module.exports = {
     assets: ['./assets/fonts', './assets/images'],
   };
   ```
3. Run the following command to link assets if needed.
   ```sh
   npx react-native-asset
   ```

## 6. Setup Redux Toolkit

1. Install Redux Toolkit and React Redux:
   ```sh
   yarn add @reduxjs/toolkit react-redux
   ```
2. Refer `store` folder from the Master project and copy as per requirement.
3. Ensure the store is configured in `App.tsx`. Refer the master project if needed:
   ```tsx
   import { Provider } from 'react-redux';
   import store from './src/store';

   function App() {
       return (
           <Provider store={store}>
               {/* Rest of the app */}
           </Provider>
       );
   }

   export default App;
   ```

## 7. Copy Utils & Theme Folders

1. Copy `utils` folder from the Master project.
2. Copy `theme` folder from the Master project.



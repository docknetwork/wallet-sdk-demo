# Installation steps used to generate this example app

```bash
npx react-native init WalletSDKDemo
yarn add patch-package
yarn add rn-nodeify
yarn add jetifier 
```

```bash
yarn add @react-native-async-storage/async-storage
yarn add realm
yarn add @docknetwork/wallet-sdk-core   
yarn add @docknetwork/wallet-sdk-react-native
yarn add native-base
```

create scripts on package.json
```json
{
    "postinstall": "./node_modules/.bin/rn-nodeify --install --hack --yarn && patch-package && jetifier && yarn create-assets-dir && yarn copy-assets",
    "create-assets-dir": "mkdir -p android/app/src/main/assets/app-html && mkdir -p assets/app-html",
    "copy-assets": "node node_modules/@docknetwork/wallet-sdk-react-native/bundler/copy-rn-assets.js"
}
```

install the UI library of your choise
```bash
yarn add native-base
```

Disable hemres on android (for react-native 0.70)

```
android/app/build.gradle
project.ext.react = [
    enableHermes: false,  // clean and rebuild if changing
]
```
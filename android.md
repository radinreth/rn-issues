1.
Task :app:bundleReleaseJsAndAssets FAILED
* What went wrong:
Execution failed for task ':app:bundleReleaseJsAndAssets'.
> Could not list contents of '/Users/radin/workspaces/projects/mobiles/eoc/eoc-mobile/node_modules/@babel/plugin-proposal-decorators/node_modules/@babel/template/node_modules/.bin/parser'. Couldn't follow symbolic link.

#solution: 

```
$ find . -type l -exec test ! -e {} \; -delete
```

2.
unable to load script from assets index.android.bundle

#solution:

```
- mkdir android/app/src/main/assets
- react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
- react-native run-android
```

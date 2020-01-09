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

3. 
Once a component is connected, 
```
connect(mapStateToProps, mapDispatchToProps)(MyComponent);
```
when createRef, need to forward it, become:
```
this.ref.current.call();

connect(mapStateToProps, mapDispatchToProps, null, {forwardRef: true})(MyComponent);
```

Note: if it is wrapped in HOC, {withNavigation}
we no need to forwardRef anymore
```
connect(mapStateToProps, mapDispatchToProps)(withNavigation(MyComponent));

this.ref.call()

<MyComponent onRef={ele=>(this.ref=ele)}/>
```

# Upgrading Expo 54 to 55

Before starting the upgrade, I confirmed that the following commands build and run as expected:

```sh
yarn android
yarn ios
yarn web
```

Starting from the current canary build: `55.0.0-canary-20251031-b135dff`. I'll update `package.json` to point to that directly and then run:

```sh
yarn # update deps
npx expo install --fix # fix Expo dependencies, although we're skipping worklets right now - should consider not doing so.
```

Here's the output of that:

```sh
igniteexpo54to55 git:(feat/upgrade-to-expo-55) ✗ npx expo install --fix               
Skipped fixing dependencies: react-native-worklets. These dependencies are listed in expo.install.exclude in package.json. Learn more
Dependency validation might be unreliable when using canary SDK versions
The following packages should be updated for best compatibility with the installed expo version:
  @expo/metro-runtime@6.1.2 - expected version: 6.2.0-canary-20251031-b135dff
  expo-application@7.0.7 - expected version: 7.0.8-canary-20251031-b135dff
  expo-build-properties@1.0.9 - expected version: 1.0.10-canary-20251031-b135dff
  expo-dev-client@6.0.17 - expected version: 6.0.17-canary-20251031-b135dff
  expo-font@14.0.9 - expected version: 14.0.10-canary-20251031-b135dff
  expo-linking@8.0.8 - expected version: 8.0.9-canary-20251031-b135dff
  expo-localization@17.0.7 - expected version: 17.0.8-canary-20251031-b135dff
  expo-splash-screen@31.0.10 - expected version: 31.0.11-canary-20251031-b135dff
  expo-system-ui@6.0.8 - expected version: 6.0.9-canary-20251031-b135dff
  react@19.1.0 - expected version: 19.1.1
  react-dom@19.1.0 - expected version: 19.1.1
  react-native@0.81.5 - expected version: 0.82.1
  eslint-config-expo@10.0.0 - expected version: 10.0.1-canary-20251031-b135dff
  jest-expo@54.0.13 - expected version: 55.0.0-canary-20251031-b135dff
Your project may not work correctly until you install the expected versions of the packages.
› Installing 14 SDK 55.0.0 compatible native modules using yarn
> yarn add @expo/metro-runtime@6.2.0-canary-20251031-b135dff expo-application@7.0.8-canary-20251031-b135dff expo-build-properties@1.0.10-canary-20251031-b135dff expo-dev-client@6.0.17-canary-20251031-b135dff expo-font@14.0.10-canary-20251031-b135dff expo-linking@8.0.9-canary-20251031-b135dff expo-localization@17.0.8-canary-20251031-b135dff expo-splash-screen@31.0.11-canary-20251031-b135dff expo-system-ui@6.0.9-canary-20251031-b135dff react@19.1.1 react-dom@19.1.1 react-native@0.82.1
yarn add v1.22.22
(node:18359) [DEP0169] DeprecationWarning: `url.parse()` behavior is not standardized and prone to errors that have security implications. Use the WHATWG URL API instead. CVEs are not issued for `url.parse()` vulnerabilities.
(Use `node --trace-deprecation ...` to show where the warning was created)
[1/5] 🔍  Validating package.json...
[2/5] 🔍  Resolving packages...
[3/5] 🚚  Fetching packages...
[4/5] 🔗  Linking dependencies...
warning "expo > @expo/log-box@0.0.13-canary-20251031-b135dff" has unmet peer dependency "@expo/dom-webview@0.2.8-canary-20251031-b135dff".
warning "expo > @expo/cli > @expo/router-server@0.1.1-canary-20251031-b135dff" has unmet peer dependency "expo-router@7.0.0-canary-20251031-b135dff".
warning "jest-expo > react-server-dom-webpack@19.0.0" has unmet peer dependency "webpack@^5.59.0".
[5/5] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 20 new dependencies.
info Direct dependencies
├─ @expo/metro-runtime@6.2.0-canary-20251031-b135dff
├─ expo-application@7.0.8-canary-20251031-b135dff
├─ expo-build-properties@1.0.10-canary-20251031-b135dff
├─ expo-dev-client@6.0.17-canary-20251031-b135dff
├─ expo-linking@8.0.9-canary-20251031-b135dff
├─ expo-localization@17.0.8-canary-20251031-b135dff
├─ expo-splash-screen@31.0.11-canary-20251031-b135dff
├─ expo-system-ui@6.0.9-canary-20251031-b135dff
├─ react-dom@19.1.1
├─ react-native@0.82.1
└─ react@19.1.1
info All dependencies
├─ @expo/metro-runtime@6.2.0-canary-20251031-b135dff
├─ @react-native/assets-registry@0.82.1
├─ @react-native/community-cli-plugin@0.82.1
├─ @react-native/gradle-plugin@0.82.1
├─ @react-native/js-polyfills@0.82.1
├─ @react-native/virtualized-lists@0.82.1
├─ expo-application@7.0.8-canary-20251031-b135dff
├─ expo-build-properties@1.0.10-canary-20251031-b135dff
├─ expo-dev-client@6.0.17-canary-20251031-b135dff
├─ expo-dev-launcher@6.1.0-canary-20251031-b135dff
├─ expo-json-utils@0.15.1-canary-20251031-b135dff
├─ expo-linking@8.0.9-canary-20251031-b135dff
├─ expo-localization@17.0.8-canary-20251031-b135dff
├─ expo-splash-screen@31.0.11-canary-20251031-b135dff
├─ expo-system-ui@6.0.9-canary-20251031-b135dff
├─ expo-updates-interface@2.0.1-canary-20251031-b135dff
├─ hermes-compiler@0.0.0
├─ react-dom@19.1.1
├─ react-native@0.82.1
└─ react@19.1.1
✨  Done in 8.39s.
> yarn add --dev eslint-config-expo@10.0.1-canary-20251031-b135dff jest-expo@55.0.0-canary-20251031-b135dff
yarn add v1.22.22
(node:18412) [DEP0169] DeprecationWarning: `url.parse()` behavior is not standardized and prone to errors that have security implications. Use the WHATWG URL API instead. CVEs are not issued for `url.parse()` vulnerabilities.
(Use `node --trace-deprecation ...` to show where the warning was created)
[1/5] 🔍  Validating package.json...
[2/5] 🔍  Resolving packages...
[3/5] 🚚  Fetching packages...
[4/5] 🔗  Linking dependencies...
warning "@expo/metro-runtime > @expo/log-box@0.0.13-canary-20251031-b135dff" has unmet peer dependency "@expo/dom-webview@0.2.8-canary-20251031-b135dff".
warning "expo > @expo/cli > @expo/router-server@0.1.1-canary-20251031-b135dff" has unmet peer dependency "expo-router@7.0.0-canary-20251031-b135dff".
warning "jest-expo > react-server-dom-webpack@19.0.0" has unmet peer dependency "webpack@^5.59.0".
[5/5] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 3 new dependencies.
info Direct dependencies
├─ eslint-config-expo@10.0.1-canary-20251031-b135dff
└─ jest-expo@55.0.0-canary-20251031-b135dff
info All dependencies
├─ eslint-config-expo@10.0.1-canary-20251031-b135dff
├─ eslint-plugin-expo@1.0.1-canary-20251031-b135dff
└─ jest-expo@55.0.0-canary-20251031-b135dff
✨  Done in 2.89s.
```

Now I'll run:

```sh
yarn prebuild:clean # Run Expo CNG
yarn android # Works and runs, but does not seem to persist favorites.
yarn ios # Fails to build
```

## iOS build failures

```sh
 igniteexpo54to55 git:(feat/upgrade-to-expo-55) ✗ yarn ios    
yarn run v1.22.22
$ expo run:ios
› Planning build
› Executing react-native Pods/ReactNativeDependencies » [CP-User] [RNDeps] Replace React Native Dependencies for the right configuration, if needed
› Executing react-native Pods/hermes-engine » [CP-User] [Hermes] Replace Hermes for the right configuration, if needed
› Preparing expo-constants Pods/EXConstants-EXConstants » ResourceBundle-EXConstants-EXConstants-Info.plist
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/ExpoFileSystem/ExpoFileSystem_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/expo-file-system/ios/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/ExpoSystemUI/ExpoSystemUI_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/expo-system-ui/ios/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/EXConstants/ExpoConstants_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/expo-constants/ios/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/React-Core/React-Core_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/react-native/React/Resources/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/React-cxxreact/React-cxxreact_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/react-native/ReactCommon/cxxreact/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/EXApplication/ExpoApplication_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/expo-application/ios/PrivacyInfo.xcprivacy
› Copying   ../Library/Developer/Xcode/DerivedData/igniteexpo54to55-drfabdxozkuqbidjemewwmpgaogq/Build/Products/Debug-iphonesimulator/ExpoLocalization/ExpoLocalization_privacy.bundle/PrivacyInfo.xcprivacy ➜ node_modules/expo-localization/ios/PrivacyInfo.xcprivacy
› Preparing Pods/EXConstants-ExpoConstants_privacy » ResourceBundle-ExpoConstants_privacy-EXConstants-Info.plist
› Preparing Pods/React-cxxreact-React-cxxreact_privacy » ResourceBundle-React-cxxreact_privacy-React-cxxreact-Info.plist
› Preparing Pods/ExpoLocalization-ExpoLocalization_privacy » ResourceBundle-ExpoLocalization_privacy-ExpoLocalization-Info.plist
› Preparing Pods/React-Core-React-Core_privacy » ResourceBundle-React-Core_privacy-React-Core-Info.plist
› Preparing Pods/ExpoSystemUI-ExpoSystemUI_privacy » ResourceBundle-ExpoSystemUI_privacy-ExpoSystemUI-Info.plist
› Preparing Pods/ExpoFileSystem-ExpoFileSystem_privacy » ResourceBundle-ExpoFileSystem_privacy-ExpoFileSystem-Info.plist
› Preparing Pods/EXApplication-ExpoApplication_privacy » ResourceBundle-ExpoApplication_privacy-EXApplication-Info.plist
› Executing react-native Pods/ReactNativeDependencies » [CP] Copy XCFrameworks
› Executing react-native Pods/hermes-engine » [CP] Copy XCFrameworks
› Executing react-native Pods/React-Core-prebuilt » [CP-User] [RNDeps] Replace React Native Core for the right configuration, if needed
› Compiling expo-json-utils Pods/EXJSONUtils » NSDictionary+EXJSONUtils.m
› Compiling expo-json-utils Pods/EXJSONUtils » EXJSONUtils-dummy.m
› Executing react-native Pods/React-Core-prebuilt » [CP] Copy XCFrameworks
› Packaging expo-json-utils Pods/EXJSONUtils » libEXJSONUtils.a
› Compiling expo-dev-menu-interface Pods/expo-dev-menu-interface » expo-dev-menu-interface-dummy.m
› Packaging expo-dev-menu-interface Pods/expo-dev-menu-interface » libexpo-dev-menu-interface.a
› Executing expo-dev-menu-interface Pods/expo-dev-menu-interface » Copy generated compatibility header
› Preparing Pods/expo-dev-launcher-EXDevLauncher » ResourceBundle-EXDevLauncher-expo-dev-launcher-Info.plist
› Executing react-native Pods/React-RCTFBReactNativeSpec » [CP-User] [RN]Check FBReactNativeSpec
› Compiling @expo/log-box Pods/ExpoLogBox » ExpoRedBoxSwap.mm
› Executing igniteexpo-54-to-55 Pods/ReactCodegen » [CP-User] Generate Specs
› Compiling @expo/log-box Pods/ExpoLogBox » ExpoLogBox-dummy.m
› Packaging @expo/log-box Pods/ExpoLogBox » libExpoLogBox.a
› Executing @expo/log-box Pods/ExpoLogBox » Copy generated compatibility header
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ComponentDescriptors.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ComponentDescriptors.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » EventEmitters.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » EventEmitters.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » EventEmitters.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » EventEmitters.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ComponentDescriptors.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » Props.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » Props.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » Props.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » Props.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RCTThirdPartyComponentsProvider.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RCTModulesConformingToProtocolsProvider.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RCTModuleProviders.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » States.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » safeareacontextJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » safeareacontext-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnworkletsJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnworklets-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnscreensJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnscreens-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnreanimatedJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rnreanimated-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rngesturehandler_codegenJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » rngesturehandler_codegen-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » reactnativekeyboardcontrollerJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » reactnativekeyboardcontroller-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » States.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » States.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » States.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ShadowNodes.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ShadowNodes.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ShadowNodes.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ShadowNodes.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ReactCodegen-dummy.m
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RNMmkvSpecJSI-generated.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RNMmkvSpec-generated.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » RCTUnstableModulesRequiringMainQueueSetupProvider.mm
› Compiling igniteexpo-54-to-55 Pods/ReactCodegen » ComponentDescriptors.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » AESCrypt.cpp
› Compiling igniteexpo-54-to-55 Pods/ReactAppDependencyProvider » RCTAppDependencyProvider.mm
› Compiling react-native-worklets Pods/RNWorklets » AnimationFrameBatchinator.cpp
› Compiling react-native-screens Pods/RNScreens » NSString+RNSUtility.mm
› Compiling react-native-reanimated Pods/RNReanimated » algorithms.cpp

❌  (node_modules/expo-modules-core/ios/ReactDelegates/ExpoReactDelegate.swift:42:39)

  40 |     return self.handlers.lazy
  41 |       .compactMap { $0.createRootViewController() }
> 42 |       .first(where: { _ in true }) ?? UIViewController()
     |                                       ^ call to main actor-isolated initializer 'init' in a synchronous nonisolated context
  43 |   }
  44 | }
  45 | 


❌  (node_modules/expo-modules-core/ios/Core/Logging/PersistentFileLog.swift:77:54)

  75 |       do {
  76 |         let contents = try self.readFileSync()
> 77 |         let newcontents = contents.filter { entry in filter(entry) }
     |                                                      ^ capture of 'filter' with non-sendable type 'PersistentFileLogFilter' -> Bool') in an isolated closure
  78 |         try self.writeFileSync(newcontents)
  79 |         completionHandler(nil)
  80 |       } catch {


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift:45:89)

  43 |    A hosting view that renders a SwiftUI view inside the UIKit view hierarchy.
  44 |    */
> 45 |   public final class HostingView<Props: ViewProps, ContentView: View<Props>>: ExpoView, @MainActor AnyExpoSwiftUIHostingView {
     |                                                                                         ^ unknown attribute 'MainActor'
  46 |     /**
  47 |      Props object that stores all the props for this particular view.
  48 |      It's an environment object that is observed by the content view.


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift:114:26)

  112 |      Updates the environment object with props, based on the given dictionary with raw props.
  113 |      */
> 114 |     public override func updateProps(_ rawProps: [String: Any]) {
      |                          ^ main actor-isolated instance method 'updateProps' cannot be used to satisfy nonisolated requirement from protocol 'AnyExpoSwiftUIHostingView'
  115 |       guard let appContext else {
  116 |         log.error("AppContext is not available, view props cannot be updated for \(ContentView.self)")
  117 |         return


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift:129:17)

  127 |      Returns inner SwiftUI view.
  128 |      */
> 129 |     public func getContentView() -> any ExpoSwiftUI.View {
      |                 ^ main actor-isolated instance method 'getContentView' cannot be used to satisfy nonisolated requirement from protocol 'AnyExpoSwiftUIHostingView'
  130 |       return contentView
  131 |     }
  132 | 


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift:136:17)

  134 |      Returns the view's props
  135 |      */
> 136 |     public func getProps() -> ExpoSwiftUI.ViewProps {
      |                 ^ main actor-isolated instance method 'getProps' cannot be used to satisfy nonisolated requirement from protocol 'AnyExpoSwiftUIHostingView'
  137 |       return props
  138 |     }
  139 | 


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIViewFrameObserver.swift:29:38)

  27 |         // Update layout metrics of the `Child` view. The `origin` needs to be frame's origin,
  28 |         // as `bounds` refers to coordinates relative to view's own space (instead of the parent's space).
> 29 |         callback(CGRect(origin: view.frame.origin, size: newValue.size))
     |                                      ^ main actor-isolated property 'frame' can not be referenced from a Sendable closure
  30 |       }
  31 |     }
  32 |   }


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:74:17)

  72 |      */
  73 |     override func updateProps(_ rawProps: [String: Any]) {
> 74 |       guard let appContext else {
     |                 ^ main actor-isolated property 'appContext' can not be referenced from a nonisolated context
  75 |         log.error("AppContext is not available, view props cannot be updated for \(self)")
  76 |         return
  77 |       }


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:79:13)

  77 |       }
  78 |       do {
> 79 |         try props.updateRawProps(rawProps, appContext: appContext)
     |             ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  80 |       } catch let error {
  81 |         log.error("Updating props for \(self) has failed: \(error.localizedDescription)")
  82 |       }


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:121:22)

  119 |      */
  120 |     override func mountChildComponentView(_ childComponentView: UIView, index: Int) {
> 121 |       var children = props.children ?? []
      |                      ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  122 |       let child: any AnyChild
  123 |       if let view = childComponentView as AnyObject as? (any ExpoSwiftUI.View) {
  124 |         child = view


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:130:7)

  128 |       children.insert(child, at: index)
  129 | 
> 130 |       props.children = children
      |       ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  131 |       props.objectWillChange.send()
  132 |     }
  133 | 


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:131:7)

  129 | 
  130 |       props.children = children
> 131 |       props.objectWillChange.send()
      |       ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  132 |     }
  133 | 
  134 |     /**


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:139:26)

  137 |     override func unmountChildComponentView(_ childComponentView: UIView, index: Int) {
  138 |       // Make sure the view has no superview, React Native asserts against this.
> 139 |       childComponentView.removeFromSuperview()
      |                          ^ call to main actor-isolated instance method 'removeFromSuperview' in a synchronous nonisolated context
  140 | 
  141 |       let childViewId: ObjectIdentifier
  142 |       if let child = childComponentView as AnyObject as? (any AnyChild) {


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:143:29)

  141 |       let childViewId: ObjectIdentifier
  142 |       if let child = childComponentView as AnyObject as? (any AnyChild) {
> 143 |         childViewId = child.id
      |                             ^ main actor-isolated property 'id' can not be referenced from a nonisolated context
  144 |       } else {
  145 |         childViewId = ObjectIdentifier(childComponentView)
  146 |       }


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:148:25)

  146 |       }
  147 | 
> 148 |       if let children = props.children {
      |                         ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  149 |         props.children = children.filter({ $0.id != childViewId })
  150 |         #if DEBUG
  151 |         assert(props.children?.count == children.count - 1, "Failed to remove child view")


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:149:9)

  147 | 
  148 |       if let children = props.children {
> 149 |         props.children = children.filter({ $0.id != childViewId })
      |         ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  150 |         #if DEBUG
  151 |         assert(props.children?.count == children.count - 1, "Failed to remove child view")
  152 |         #endif


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:149:47)

  147 | 
  148 |       if let children = props.children {
> 149 |         props.children = children.filter({ $0.id != childViewId })
      |                                               ^ main actor-isolated property 'id' can not be referenced from a nonisolated context
  150 |         #if DEBUG
  151 |         assert(props.children?.count == children.count - 1, "Failed to remove child view")
  152 |         #endif


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:151:16)

  149 |         props.children = children.filter({ $0.id != childViewId })
  150 |         #if DEBUG
> 151 |         assert(props.children?.count == children.count - 1, "Failed to remove child view")
      |                ^ main actor-isolated property 'props' can not be referenced from a nonisolated autoclosure
  152 |         #endif
  153 |         props.objectWillChange.send()
  154 |       }


❌  (node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIVirtualView.swift:153:9)

  151 |         assert(props.children?.count == children.count - 1, "Failed to remove child view")
  152 |         #endif
> 153 |         props.objectWillChange.send()
      |         ^ main actor-isolated property 'props' can not be referenced from a nonisolated context
  154 |       }
  155 |     }
  156 | 


❌  (node_modules/expo-modules-core/ios/DevTools/URLAuthenticationChallengeForwardSender.swift:7:7)

   5 |  */
   6 | internal final class URLAuthenticationChallengeForwardSender: NSObject, URLAuthenticationChallengeSender {
>  7 |   let completionHandler: (URLSession.AuthChallengeDisposition, URLCredential?) -> Void
     |       ^ stored property 'completionHandler' of 'Sendable'-conforming class 'URLAuthenticationChallengeForwardSender' has non-sendable type '-> Void'
   8 | 
   9 |   init(completionHandler: @escaping (URLSession.AuthChallengeDisposition, URLCredential?) -> Void) {
  10 |     self.completionHandler = completionHandler


❌  (node_modules/expo-modules-core/ios/DevTools/URLSessionSessionDelegateProxy.swift:8:15)

   6 | public final class URLSessionSessionDelegateProxy: NSObject, URLSessionDataDelegate {
   7 |   private let dispatchQueue: DispatchQueue
>  8 |   private var delegateMap: [AnyHashable: URLSessionDataDelegate] = [:]
     |               ^ stored property 'delegateMap' of 'Sendable'-conforming class 'URLSessionSessionDelegateProxy' is mutable
   9 | 
  10 |   public init(dispatchQueue: DispatchQueue) {
  11 |     self.dispatchQueue = dispatchQueue


❌  (node_modules/expo-modules-core/ios/Core/Views/ViewDefinition.swift:124:19)

  122 | }
  123 | 
> 124 | extension UIView: @MainActor AnyArgument {
      |                   ^ unknown attribute 'MainActor'
  125 |   public static func getDynamicType() -> AnyDynamicType {
  126 |     return DynamicViewType(innerType: Self.self)
  127 |   }

› Compiling react-native-screens Pods/RNScreens » UIWindow+RNScreens.mm
› Compiling react-native-screens Pods/RNScreens » UIViewController+RNScreens.mm
› Compiling react-native-screens Pods/RNScreens » UIView+RNSUtility.mm
› Compiling react-native-screens Pods/RNScreens » UIScrollView+RNScreens.mm
› Compiling react-native-screens Pods/RNScreens » UINavigationBar+RNSUtility.mm
› Compiling react-native-screens Pods/RNScreens » RNScreensTurboModule.cpp
› Compiling react-native-screens Pods/RNScreens » RNSViewControllerInvalidator.mm
› Compiling react-native-worklets Pods/RNWorklets » WorkletsVersion.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletsModuleProxy.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletsModule.mm
› Compiling react-native-worklets Pods/RNWorklets » WorkletsMessageThread.mm
› Compiling react-native-mmkv Pods/react-native-mmkv » openssl_md5_one.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » openssl_md5_dgst.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » openssl_cfb128.cpp
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCOnInsetsChangeEvent.m
› Compiling react-native-mmkv Pods/react-native-mmkv » openssl_aes_core.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » crc32_armv8.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » crc32.cpp
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCSafeAreaViewComponentView.mm
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCSafeAreaViewState.cpp
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCSafeAreaViewShadowNode.cpp
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCSafeAreaProviderComponentView.mm
› Compiling react-native-safe-area-context Pods/react-native-safe-area-context » RNCSafeAreaContext.mm
› Compiling react-native-mmkv Pods/react-native-mmkv » ThreadLock_Win32.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » ThreadLock.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » PBUtility.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » NativeMmkvModule.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MmkvPlatformContextModule.mm
› Compiling react-native-mmkv Pods/react-native-mmkv » MmkvOnLoad.mm
› Compiling react-native-mmkv Pods/react-native-mmkv » MmkvHostObject.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MiniPBCoder_OSX.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MiniPBCoder.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MemoryFile_Win32.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MemoryFile_OSX.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MemoryFile_Linux.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MemoryFile_Android.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MemoryFile.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKV_OSX.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKV_IO.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKV_Android.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKVLog_Android.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKVLog.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMKV.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » MMBuffer.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » KeyValueHolder.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » InterProcessLock_Win32.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » InterProcessLock_Android.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » InterProcessLock.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » CodedOutputData.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » CodedInputData_OSX.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » CodedInputDataCrypt_OSX.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » CodedInputDataCrypt.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » CodedInputData.cpp
› Compiling react-native-mmkv Pods/react-native-mmkv » AppleLogger.mm
› Compiling react-native-worklets Pods/RNWorklets » WorkletsJSIUtils.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletRuntimeRegistry.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletRuntimeDecorator.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletRuntime.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletHermesRuntime.cpp
› Compiling react-native-worklets Pods/RNWorklets » WorkletEventHandler.cpp
› Compiling react-native-worklets Pods/RNWorklets » VersionUtils.cpp
› Compiling react-native-worklets Pods/RNWorklets » ValueUnpacker.cpp
› Compiling react-native-worklets Pods/RNWorklets » UIScheduler.cpp
› Compiling react-native-worklets Pods/RNWorklets » UIRuntimeDecorator.cpp
› Compiling react-native-worklets Pods/RNWorklets » SynchronizableUnpacker.cpp
› Compiling react-native-worklets Pods/RNWorklets » SynchronizableAccess.cpp
› Compiling react-native-worklets Pods/RNWorklets » Synchronizable.cpp
› Compiling react-native-worklets Pods/RNWorklets » SlowAnimations.mm
› Compiling react-native-worklets Pods/RNWorklets » Serializable.cpp
› Compiling react-native-worklets Pods/RNWorklets » RuntimeManager.cpp
› Compiling react-native-worklets Pods/RNWorklets » RuntimeData.cpp
› Compiling react-native-worklets Pods/RNWorklets » RNRuntimeWorkletDecorator.cpp
› Compiling react-native-worklets Pods/RNWorklets » PlatformLogger.mm
› Compiling react-native-worklets Pods/RNWorklets » JSScheduler.cpp
› Compiling react-native-worklets Pods/RNWorklets » JSLogger.cpp
› Compiling react-native-worklets Pods/RNWorklets » JSIWorkletsModuleProxy.cpp
› Compiling react-native-worklets Pods/RNWorklets » JSISerializer.cpp
› Compiling react-native-worklets Pods/RNWorklets » IOSUIScheduler.mm
› Compiling react-native-worklets Pods/RNWorklets » FeatureFlags.cpp
› Compiling react-native-worklets Pods/RNWorklets » EventLoop.cpp
› Compiling react-native-worklets Pods/RNWorklets » EventHandlerRegistry.cpp
› Compiling react-native-worklets Pods/RNWorklets » AsyncQueueImpl.cpp
› Compiling react-native-worklets Pods/RNWorklets » AnimationFrameQueue.mm
› Compiling react-native-screens Pods/RNScreens » RNSTabsScreenViewController.mm
› Compiling react-native-screens Pods/RNScreens » RNSTabBarControllerDelegate.mm
› Compiling react-native-screens Pods/RNScreens » RNSTabBarController.mm
› Compiling react-native-screens Pods/RNScreens » RNSTabBarAppearanceCoordinator.mm
› Compiling react-native-screens Pods/RNScreens » RNSSplitViewScreenShadowNode.cpp
› Compiling react-native-screens Pods/RNScreens » RNSSearchBar.mm
› Compiling react-native-screens Pods/RNScreens » RNSScrollViewHelper.mm
› Compiling react-native-screens Pods/RNScreens » RNSScrollViewFinder.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenWindowTraits.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenViewEvent.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenState.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderSubviewState.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderSubviewShadowNode.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderSubview.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderConfigState.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderConfigShadowNode.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackHeaderConfig.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenStackAnimator.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenStack.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenShadowNode.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenRemovalListener.cpp
› Compiling react-native-screens Pods/RNScreens » RNSScreenNavigationContainer.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenFooter.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenContentWrapper.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreenContainer.mm
› Compiling react-native-screens Pods/RNScreens » RNSScreen.mm
› Compiling react-native-screens Pods/RNScreens » RNSReactBaseView.mm
› Compiling react-native-screens Pods/RNScreens » RNSPercentDrivenInteractiveTransition.mm
› Compiling react-native-screens Pods/RNScreens » RNSModule.mm
› Compiling react-native-screens Pods/RNScreens » RNSModalScreenShadowNode.cpp
› Compiling react-native-screens Pods/RNScreens » RNSModalScreen.mm
› Compiling react-native-screens Pods/RNScreens » RNSInvalidatedComponentsRegistry.mm
› Compiling react-native-screens Pods/RNScreens » RNSHeaderHeightChangeEvent.mm
› Compiling react-native-screens Pods/RNScreens » RNSGammaStubs.mm
› Compiling react-native-screens Pods/RNScreens » RNSFullWindowOverlayShadowNode.cpp
    Run script build phase '[CP-User] [Hermes] Replace Hermes for the right configuration, if needed' will be run during every build because it does not specify any outputs. To address this issue, either add output dependencies to the script phase, or configure it to run in every build by unchecking "Based on dependency analysis" in the script phase. (in target 'hermes-engine' from project 'Pods')

› 22 error(s), and 1 warning(s)

CommandError: Failed to build iOS project. "xcodebuild" exited with error code 65.
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
➜  igniteexpo54to55 git:(feat/upgrade-to-expo-55) ✗ 
```

Ok, so let's open in Xcode and see if it has any auto suggestions.

No auto suggestions, but Claude suggested I change Swift strict concurrency in Podfile:

```rb
    # Disable Swift strict concurrency to fix Expo 55 canary build errors
    installer.pods_project.targets.each do |target|
      target.build_configurations.each do |config|
        config.build_settings['SWIFT_STRICT_CONCURRENCY'] = 'minimal'
      end
    end
```

But that didn't fix it. Still got the same output. Oh right, I need to pod install.

```sh
cd ios
pod install
cd ..
yarn ios
```

But same errors: `› 22 error(s), and 1 warning(s)`

Ok, so I was able to downgrade swift and patch Expo UI to not use `@MainActor`, but that feels wrong. Here's the code diff that worked:

```patch
# Expo 55 Canary iOS Build Fix for Xcode 16.4
# This patch fixes Swift 6 concurrency errors when building with Xcode 16.4
#
# Apply this patch after upgrading to Expo 55 canary
# The Swift file patches need to be reapplied after yarn install

diff --git a/ios/Podfile b/ios/Podfile
index 1234567..abcdefg 100644
--- a/ios/Podfile
+++ b/ios/Podfile
@@ -50,6 +50,23 @@ target 'igniteexpo54to55' do
   )

   post_install do |installer|
     react_native_post_install(
       installer,
       config[:reactNativePath],
       :mac_catalyst_enabled => false,
       :ccache_enabled => ccache_enabled?(podfile_properties),
     )
+
+    # Disable Swift 6 concurrency checking (Xcode 16+) to fix Expo 55 canary build errors
+    # The ExpoModulesCore podspec sets swift_version = '6.0', we need to override it
+    installer.pods_project.targets.each do |target|
+      target.build_configurations.each do |config|
+        # Override Swift 6 from podspec, use 5.10 which supports @MainActor
+        config.build_settings['SWIFT_VERSION'] = '5.10'
+        # Explicitly disable strict concurrency
+        config.build_settings.delete('SWIFT_STRICT_CONCURRENCY')
+        # Add flags to disable concurrency warnings/errors
+        other_swift_flags = config.build_settings['OTHER_SWIFT_FLAGS'] ||= ['$(inherited)']
+        # Remove any existing concurrency flags
+        other_swift_flags.delete_if { |flag| flag.to_s.include?('concurrency') }
+      end
+    end
+
+    # Also update the pods project-level settings
+    installer.pods_project.build_configurations.each do |config|
+      config.build_settings['SWIFT_VERSION'] = '5.10'
+      config.build_settings.delete('SWIFT_STRICT_CONCURRENCY')
+    end
   end
 end

diff --git a/node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift b/node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift
index 1234567..abcdefg 100644
--- a/node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift
+++ b/node_modules/expo-modules-core/ios/Core/Views/SwiftUI/SwiftUIHostingView.swift
@@ -42,7 +42,7 @@ extension ExpoSwiftUI {
   /**
    A hosting view that renders a SwiftUI view inside the UIKit view hierarchy.
    */
-  public final class HostingView<Props: ViewProps, ContentView: View<Props>>: ExpoView, @MainActor AnyExpoSwiftUIHostingView {
+  public final class HostingView<Props: ViewProps, ContentView: View<Props>>: ExpoView, AnyExpoSwiftUIHostingView {
     /**
      Props object that stores all the props for this particular view.
      It's an environment object that is observed by the content view.

diff --git a/node_modules/expo-modules-core/ios/Core/Views/ViewDefinition.swift b/node_modules/expo-modules-core/ios/Core/Views/ViewDefinition.swift
index 2345678..bcdefgh 100644
--- a/node_modules/expo-modules-core/ios/Core/Views/ViewDefinition.swift
+++ b/node_modules/expo-modules-core/ios/Core/Views/ViewDefinition.swift
@@ -121,7 +121,7 @@ extension ConcurrentFunctionDefinition: ViewDefinitionFunctionElement {
   public typealias ViewType = FirstArgType
 }

-extension UIView: @MainActor AnyArgument {
+extension UIView: AnyArgument {
   public static func getDynamicType() -> AnyDynamicType {
     return DynamicViewType(innerType: Self.self)
   }
```

I'll spin up an Expo project specifically and try to reproduce. But for now, iOS builds. I'm seeing the same problem with favorites not persisting here as well.

Now let's try web:

```sh
yarn web
```

Web built, and also does not persist favorites, but other functionality is working. I'll have to dig into that a bit more.

## iOS build errors

Maybe we need xcode 26 to build this correctly? I'll try that instead. Here's what I'll do:

1. Install Xcode 26
2. `rm -rf node_modules android ios`
3. `yarn`
4. `yarn prebuild:clean`
5. Make Xcode 26.1 my active Xcode
6. Try building iOS again

It built on the command line, although I'm having weird simulator stuff going on - just a black screen, but it opened the iPhone 18.6 simulator and I think I need iOS 26, so I'll do this from Xcode directly.

Nice, that worked! Still not seeing favorites persist.

## Removing the patch with the Expo beta release

When I upgraded to Expo@55.0.0-preview.5, I was able to remove the patch and build to Xcode 16.4 and 26.10 without issue.
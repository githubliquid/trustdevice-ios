

# install xcode

then
```
xcode-select --install # Install Command Line Tools if you haven't already.
sudo xcode-select --switch /Library/Developer/CommandLineTools # Enable command line tools
# Change the path if you installed Xcode somewhere else.
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

# modify 2 pbxproj files:
Example/TrustDecision.xcodeproj/project.pbxproj
Example/Pods/Pods.xcodeproj/project.pbxproj

`IPHONEOS_DEPLOYMENT_TARGET = 16.1`

# build command:
```
xcodebuild -workspace Example/TrustDecision.xcworkspace -scheme TrustDecision-Example -sdk iphonesimulator ONLY_ACTIVE_ARCH=NO
```


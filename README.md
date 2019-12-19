fastlane documentation
================
# Installation

Make sure you have the latest version of the Xcode command line tools installed:

```
xcode-select --install
```

Install _fastlane_ using
```
[sudo] gem install fastlane -NV
```
or alternatively using 
```
brew cask install fastlane
```
### cocoapods工程加入fastlane

#### Required

cocoapods: ~>1.6.1

Init
```
cd [project_dir]
git submodule add http://code.xingshulin.com/fastlane/fastlane-pod fastlane
```
Update
```
git submodule update --remote
```

# Available Actions
### release_pod
```
fastlane release_pod version:[version] msg:[commit message]
```

### pod_lint
```
fastlane pod_lint
```

### test
```
fastlane test
```

### push
```
fastlane push
```


----

This README.md is auto-generated and will be re-generated every time [fastlane](https://fastlane.tools) is run.
More information about fastlane can be found on [fastlane.tools](https://fastlane.tools).
The documentation of fastlane can be found on [docs.fastlane.tools](https://docs.fastlane.tools).

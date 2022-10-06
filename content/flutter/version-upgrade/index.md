---
emoji: 
title: flutter 버전 업그레이드 후기(2.10.4 -> 3.3.4)
date: "2022-10-07T00:00:00.000Z"
author: uzzam
description: 
tags: 
categories: flutter
---

## 버전 업그레이드

자세한 사항을 보려면 [Upgrading Flutter(공식문서)](https://docs.flutter.dev/development/tools/sdk/upgrading)   

버전 업그레이드 자체는 되게 간단했다.  

```bash
flutter upgrade
```

한줄이면 스테이블 버전으로 업그레이드 된다.  

```bash
Upgrading Flutter to 3.3.4 from 2.10.4 ...
```

![3.3.4](/images/334.png)  

너무 쉽네 하고 앱을 빌드해보았더니 역시 에러가 났다.  
간단한 앱인데도 쉽게쉽게 안되는구나,,  
하나씩 해결해보자

---

## 에러 해결법

---

### deployment target 에러

`The iOS Simulator deployment target 'IPHONEOS_DEPLOYMENT_TARGET' is set to 9.0, but the range of supported deployment target versions is 11.0 to 16.0.99. (in target 'GoogleUtilities' from project 'Pods')`  
가장 많은 줄을 차지하고 있던 에러, Pods의 target들의 deployment target을 12.0 으로 올려서 해결하였다.  podfile을 수정해주면 된다.

```ruby
post_install do |installer|
  installer.pods_project.targets.each do |target|
    flutter_additional_ios_build_settings(target)
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '12.0'
    end
  end
end
```
전체적인 해결과정은 [이 글](https://www.wafrat.com/fixing-the-ios-simulator-deployment-target-iphoneos_deployment_target-is-set-to-8-0-but-the-range-of-supported-deployment-target-versions-is-9-0/)을 참고하면 된다.  
[stackoverflow](https://stackoverflow.com/questions/63973136/the-ios-deployment-target-iphoneos-deployment-target-is-set-to-8-0-in-flutter)에서는 podfile 수정하는 법을 알려준다.

---

### pod update, pod install 안될 때

에러 해결 과정이 너무 어지러워서 깔끔하게 정리가 안된다.
다만 pod update를 통해 다양한 문제를 해결할 수 있는데, pod update 시 에러가 나는 경우가 있다.  
이 때 해결법은 아래와 같다.

```bash
sudo arch -x86_64 gem install ffi
arch -x86_64 pod update
arch -x86_64 pod install
```

---

### Couldn't find constructor 'VelocityTracker'.

혹시 modal_bottom_sheet을 사용한다면 pubspec.yaml에서 버전을 수정해주자 ([출처](https://stackoverflow.com/questions/72254922/getting-error-when-i-run-flutter-app-in-android-studio))

```yaml
modal_bottom_sheet: ^2.0.1 
```

---

### CocoaPods did not set the base configuration of your project because your project already has a custom config set

https://github.com/flutter/flutter/issues/66222

---

### 이상한 에러
아주 요상한 에러.. 아래 무적기를 써보자 (안될 수도 있음)
```bash
2022-10-07 03:06:57.213 xcodebuild[50526:356450] warning:  The file reference for "GoogleAppMeasurement-xcframeworks.sh" is a member of multiple groups ("Support Files" and "Support Files"); this indicates a malformed project.  Only the membership in one of the groups will be preserved (but membership in targets will be unaffected).  If you want a reference to the same file in more than one group, please add another reference to the same path.
2022-10-07 03:06:57.213 xcodebuild[50526:356450] warning:  The file reference for "GoogleAppMeasurement.debug.xcconfig" is a member of multiple groups ("Support Files" and "Support Files"); this indicates a malformed project.  Only the membership in one of the groups will be preserved (but membership in targets will be unaffected).  If you want a reference to the same file in more than one group, please add another reference to the same path.
2022-10-07 03:06:57.213 xcodebuild[50526:356450] warning:  The file reference for "GoogleAppMeasurement.release.xcconfig" is a member of multiple groups ("Support Files" and "Support Files"); this indicates a malformed project.  Only the membership in one of the groups will be preserved (but membership in targets will be unaffected).  If you want a reference to the same file in more than one group, please add another reference to the same path.
```

---

## 무적기
flutter 오류 해결하려고 구글링 하면 제일 많이 보이는 것,,  
실제로 많은 에러에서 효과가 있는 듯 하다.  
사용하기 전에 [[Cocoapods] pod install? pod update? 제대로 알고 쓰자
](https://onelife2live.tistory.com/30)를 읽어보면 좋다.  

ios/Podfile.lock 삭제  
flutter clean  
flutter pub get  
arch -x86_64 pod repo update (ios 폴더에서)  
arch -x86_64 pod update (ios 폴더에서)  

## 후기
버전 업그레이드가 잘됐다. 담부턴 미리미리 해야겠다.

```toc
```
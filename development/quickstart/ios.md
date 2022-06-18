# iOS 연동하기

## 1. 사전 준비

* [FlareLane 콘솔](https://console.flarelane.com) 에서 회원가입 후 프로젝트 생성
* APNS 인증 정보 설정 (아래 페이지 참고)

{% content-ref url="../advanced/channel/apns-setting.md" %}
[apns-setting.md](../advanced/channel/apns-setting.md)
{% endcontent-ref %}

## 2. CocoaPods을 사용하여 SDK 연동

1. 내 Xcode 프로젝트에 CocoaPods 설치가 되어있는지 확인합니다. 처음일 경우 여기를 참고하세요.
2. `Podfile` 파일의 상단에 `platform :ios, '11.0'` 혹은 11버전 이상을 입력합니다.
3. `Podfile`에 다음 코드를 추가합니다.

{% tabs %}
{% tab title="Podfile" %}
```swift
target 'YOUR_PROJECT_NAME' do

  // 아래 줄 추가
  pod 'FlareLane'
  
end
```
{% endtab %}
{% endtabs %}

4\. 터미널에서 `pod install` 을 통해 설치 완료합니다.

5\. `<YOUR_PROJECT_NAME>.xcworkspace` 파일을 열어 Xcode 프로젝트를 실행합니다.

## 3. Capability 추가

1\. 대상 PROJECT의 `Deployment Target` 을 11.0 혹은 그 이상으로 입력합니다.

2\. 대상 TARGET의 `Deployment Info` 를 11.0 혹은 그 이상으로 입력합니다.

3\. 앱푸시 발송 권한을 추가합니다. Target 의 "Signing & Capabilites" 탭으로 들어와 좌상단의 "+ Capability" 를 클릭합니다.

4\. "Push Notifications" 를 선택하여 추가합니다

{% hint style="info" %}
[Apple Developer Program](https://developer.apple.com/programs/whats-included/)에 가입된 Apple 계정만 Push Notifications Capability를 추가할 수 있습니다
{% endhint %}

![](<../../.gitbook/assets/스크린샷 2021-10-05 오후 5.55.43.png>)

## 4. 초기화 코드 작성

### Optional. SwiftUI 프로젝트에서 AppDelegate.swift 생성

{% hint style="danger" %}
SwiftUI 프로젝트의 경우 초기에 AppDelegate.swift 파일이 존재하지 않습니다. 따라서 신규 AppDelegate 파일을 우선 만들어주셔야 합니다.&#x20;
{% endhint %}

`AppDelegate.swift` 파일을 새로 만들고 `<YOUR_PROJECT_NAME>App.swift` 파일을 일부 수정합니다.

{% tabs %}
{% tab title="(추가) AppDelegate.swift" %}
```swift
import UIKit

class AppDelegate: NSObject, UIApplicationDelegate {
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey : Any]? = nil) -> Bool {
    return true
  }
}

```
{% endtab %}

{% tab title="(기존) <YOUR_PROJECT_NAME>App.swift" %}
```swift
struct <YOUR_PROJECT_NAME>App: App {
    // 아래 코드 추가
    @UIApplicationDelegateAdaptor(AppDelegate.self) var appDelegate
}
```
{% endtab %}
{% endtabs %}

### 1. AppDelegate 내부 연동 코드 작성

AppDelegate 파일에 다음과 같은 초기화 코드를 입력합니다. 프로젝트 ID는 콘솔의 \[프로젝트] 페이지에서 확인할 수 있습니다.

{% tabs %}
{% tab title="Swift" %}
{% code title="AppDelegate.swift" %}
```swift

// 1. SDK 사용을 위해 import 코드 추가
import FlareLane

class AppDelegate: UIResponder, UIApplicationDelegate {
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {    

    // 2. 아래 init 코드 추가
    FlareLane.initWithLaunchOptions(launchOptions, projectId: "<INPUT_YOUR_PROJECT_ID>")
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code title="AppDelegate.m" %}
```objectivec
// 1. SDK 사용을 위해 import 코드 추가
@import FlareLane

@implementation AppDelegate
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

     // 2. 아래 init 코드 추가
     [FlareLane initWithLaunchOptions:launchOptions projectId:@"INPUT_YOUR_PROJECT_ID"];
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
프로젝트 ID는 콘솔의 프로젝트 화면에서 확인할 수 있습니다.
{% endhint %}

## 5. 방금 등록한 기기 확인

{% hint style="info" %}
iOS 시뮬레이터는 푸시 지원이 되지 않으니 실제 기기를 통해 확인하셔야 합니다.
{% endhint %}

앱 실행을 한 뒤, 콘솔 내 \[전체 기기] 페이지를 클릭하여 기기가 추가된 것을 확인해보세요!

![](<../../.gitbook/assets/스크린샷 2021-12-15 오후 11.19.00.png>)

## 함께 보기

#### iOS 앱의 이미지 등 미디어 첨부를 위해서는 아래 가이드를 참고하세요.&#x20;

{% content-ref url="../advanced/ios-rich-notification.md" %}
[ios-rich-notification.md](../advanced/ios-rich-notification.md)
{% endcontent-ref %}


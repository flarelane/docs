# iOS: Rich Notification

{% hint style="info" %}
지원되는 SDK 버전을 반드시 확인하세요

Native iOS: 1.0.6 이후

React Native: 1.0.11 이후

Flutter: 1.0.4 이후
{% endhint %}

iOS에서는 이미지 등 미디어 첨부를 위해 `Notification Service Extension` 생성이 필요합니다.

플레어레인을 사용하면 본 과정 또한 매우 쉽게 가능합니다.

## 1. Notification Service Extension 생성 <a href="#adding-a-notification-service-extension" id="adding-a-notification-service-extension"></a>

Xcode 에서 File > New > Target 에서 `Notification Service Extension` 을 선택합니다.

![](<../../.gitbook/assets/스크린샷 2022-04-14 오후 4.44.40.png>)

Product Name에 적절한 이름을 입력합니다. 본 가이드에서는 `FlareLaneNotificationServiceExtension` 으로 정의하겠습니다.

{% hint style="info" %}
Language 는 가능하면 Swift 를 권장합니다.
{% endhint %}

![](<../../.gitbook/assets/스크린샷 2022-04-14 오후 4.47.42.png>)

TARGETS 에서 생성된 Extension의 Deployment Info를 정식 앱과 동일한 버전으로 설정합니다.

![](<../../.gitbook/assets/스크린샷 2022-04-14 오후 5.21.46.png>)

## 2. Extension에 SDK 연동

Xcode 종료 후 `Podfile` 에 다음 코드를 추가합니다.

```swift
// 파일 최상단에 아래 줄을 추가하여 Dynamic Framework를 활성화합니다.
use_frameworks!

// 아래 줄을 추가하여 생성한 Extension 을 타겟으로 SDK를 연동합니다.
// 앞서 입력한 Extension의 Product Name 이 target 입니다.
// 본 가이드에서는 FlareLaneNotificationServiceExtension 입니다.
target 'FlareLaneNotificationServiceExtension' do
  pod 'FlareLane'
end
```

`pod install` 를 실행하여 SDK 설치를 완료합니다.

## 3. Extension 코드 수정

다시 Xcode를 실행하여 생성한 Extension 파일을 수정합니다. 자동으로 채워진 코드들을 지우고 플레어레인이 제공하는 클래스를 상속하기만 하면 모든 연동이 완료됩니다.

{% tabs %}
{% tab title="Swift" %}
{% code title="NotificationService.swift" %}
```swift
import FlareLane

class NotificationService: FlareLaneNotificationServiceExtension {
}
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code title="NotificationService.h/.m" %}
```objectivec
// NotificationService.h
@import FlareLane;

@interface NotificationService : FLNNotificationServiceExtension
@end

// NotificationService.m
#import "NotificationService.h"

@implementation NotificationService
@end

```
{% endcode %}
{% endtab %}
{% endtabs %}




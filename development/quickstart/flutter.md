# Flutter 연동하기

## 1. 사전 준비

* [FlareLane 콘솔](https://console.flarelane.com) 에서 회원가입 후 프로젝트 생성
* FCM, APNS 인증 정보 설정 (아래 페이지 참고)

{% content-ref url="../advanced/channel/fcm-setting.md" %}
[fcm-setting.md](../advanced/channel/fcm-setting.md)
{% endcontent-ref %}

{% content-ref url="../advanced/channel/apns-setting.md" %}
[apns-setting.md](../advanced/channel/apns-setting.md)
{% endcontent-ref %}

## 2. SDK 설치

터미널에서 프로젝트 루트 디렉토리로 이동한 뒤, 다음 명령어를 입력합니다

```
$ flutter pub add flarelane_flutter
```

## 3. iOS 프로젝트 설정

1\. 터미널에서 `cd ios` 를 입력하여 ios 디렉토리로 이동합니다.

2\. `Podfile` 파일의 상단에 `platform :ios, '11.0'` 혹은 11.0 버전 이상을 입력합니다.

3\. `pod install` 을 입력하여 CocoaPods 설치를 완료합니다.

4\. `<YOUR_PROJECT_NAME>.xcworkspace` 파일을 열어 Xcode 프로젝트를 실행합니다.

5\. 대상 PROJECT의 `Deployment Target` 을 11.0 혹은 그 이상으로 입력합니다.

6\. 대상 TARGET의 `Deployment Info` 를 11.0 혹은 그 이상으로 입력합니다.

7\. 앱푸시 발송 권한을 추가합니다. Target 의 "Signing & Capabilites" 탭으로 들어와 좌상단의 "+ Capability" 를 클릭합니다.

8\. "Push Notifications" 를 선택하여 추가합니다

![](<../../.gitbook/assets/스크린샷 2021-10-05 오후 5.55.43.png>)

## 4. 초기화 코드 작성

main.dart 파일에서 다음 초기화 코드를 입력합니다. 프로젝트 ID는 콘솔의 \[프로젝트] 페이지에서 확인할 수 있습니다.

{% tabs %}
{% tab title="main.dart" %}
```dart
// 1. 파일 최상단에 아래 줄 추가하여 import
import 'package:flarelane_flutter/flarelane_flutter.dart';

// 2. 시작 함수 내부에서 아래 줄 추가하여 초기화 코드 작성
FlareLane.shared.initialize("INPUT_YOUR_PROJECT_ID");
```
{% endtab %}
{% endtabs %}

## 5. 방금 등록한 기기 확인

앱 실행을 한 뒤, 콘솔 내 \[전체 기기] 페이지를 클릭하여 기기가 추가된 것을 확인해보세요!

![](<../../.gitbook/assets/스크린샷 2021-12-15 오후 11.19.00.png>)

## 함께보기

#### Android 앱의 알림 아이콘 설정이 필요하다면 아래 가이드를 참고하세요.

{% content-ref url="../advanced/android-notification-icon.md" %}
[android-notification-icon.md](../advanced/android-notification-icon.md)
{% endcontent-ref %}

#### iOS 앱의 이미지 등 미디어 첨부를 위해서는 아래 가이드를 참고하세요.&#x20;

{% content-ref url="../advanced/ios-rich-notification.md" %}
[ios-rich-notification.md](../advanced/ios-rich-notification.md)
{% endcontent-ref %}


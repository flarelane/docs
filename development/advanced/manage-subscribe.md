# 수신가능 여부의 자동 관리

기기는 특정한 상황(앱삭제, 유효하지 않은 토큰 등)에서 앱푸시 수신이 불가능할 수 있습니다. 기기 관리의 용이성을 위해 아래와 같은 상황에서는 플레어레인이 자동으로 수신가능(isSubscribed) 값을 조정합니다.

### 앱푸시 발송 결과에 따른 수신가능 여부 자동 비활성화

**푸시 발송 후 수신되는 응답을 통해 자동으로 개별 기기의 수신가능 여부를 비활성화(false)합니다.** 구체적인 수신 응답 기준은 각 발송 서버(FCM, APNS)로부터 받는 응답을 기준으로 아래와 같습니다.

FCM ([docs](https://firebase.google.com/docs/cloud-messaging/http-server-ref#error-codes))

* InvalidRegistration
* NotRegistered

APNS ([docs](https://developer.apple.com/documentation/usernotifications/setting\_up\_a\_remote\_notification\_server/handling\_notification\_responses\_from\_apns))

* BadDeviceToken
* Unregistered (Apple 정책에 따르면 앱삭제 반영은 며칠 걸릴 수 있습니다)

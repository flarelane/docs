# SDK Reference

## Initialize

#### SDK 초기화 및 프로젝트 ID 설정

Android: `FlareLane.initWithContext(Context context, String projectId)`

iOS: `FlareLane.initWithLaunchOptions(_ launchOptions: [UIApplication.LaunchOptionsKey: Any]?, projectId: String)`

ReactNative: `FlareLane.initialize(projectId: string)`

Flutter: `FlareLane.shared.initialize(String: projectId)`

## Set Log Level

#### 로그 출력 기준 설정 (현재 none, verbose 및 error 레벨에 대해서만 허용)

Android: `FlareLane.setLogLevel(int logLevel)`

iOS: `FlareLane.setLogLevel(level: LogLevel)`

ReactNative: `FlareLane.setLogLevel(logLevel: LogLevel)`

Flutter: `FlareLane.shared.setLogLevel(LogLevel: logLevel)`

## Set Notification Converted Handler

**알림 반응(클릭)시 수행할 콜백 동작 지정**

Android: `FlareLane.setNotificationConvertedHandler(NotificationConvertedHandler notificationConvertedHandler)`

iOS: `FlareLane.setNotificationConvertedHandler(callback: @escaping (FlareLaneNotification) -> Void)`

ReactNative: `FlareLane.setNotificationConvertedHandler(callback: NotificationHandlerCallback)`

Flutter: `FlareLane.shared.setNotificationConvertedHandler(NotificationConvertedHandler handler)`

## Set IsSubscribed

**알림 수신 여부 설정**

Android:  `FlareLane.setIsSubscribed(Context context, boolean isSubscribed)`

iOS: `FlareLane.setIsSubscribed(isSubscribed: Bool)`

ReactNative: `FlareLane.setIsSubscribed(isSubscribed: boolean)`

Flutter: `FlareLane.shared.setIsSubscribed(bool isSubscribed)`

## Set User ID

**유저 ID 지정 (null 입력 시 삭제)**

Android: `FlareLane.setUserId(Context context, String userId)`

iOS: `FlareLane.setUserId(userId: String?)`

ReactNative: `FlareLane.setUserId(userId: string | null)`

FlareLane: `FlareLane.shared.setUserId(String? userId)`

## Set Tags

**태그 추가 및 수정**

Android: `FlareLane.setTags(Context context, JSONObject tags)`

iOS: `FlareLane.setTags(tags: [String: Any])`

ReactNative: `FlareLane.setTags(tags: Tags)`

Flutter: `FlareLane.shared.setTags(Map<String, Object> tags)`

## Delete Tags

**태그 삭제 (key 문자열 배열 입력)**

Android: `FlareLane.deleteTags(Context context, ArrayList<String> keys)`

iOS: `FlareLane.deleteTags(keys: [String])`

ReactNative: `FlareLane.deleteTags(keys: string[])`

Flutter: `FlareLane.shared.deleteTags(List<String> tags)`


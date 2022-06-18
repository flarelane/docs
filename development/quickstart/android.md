# Android 연동하기

## 1. 사전 준비

* [FlareLane 콘솔](https://console.flarelane.com) 에서 회원가입 후 프로젝트 생성
* FCM 인증 정보 설정 (아래 페이지 참고)

{% content-ref url="../advanced/channel/fcm-setting.md" %}
[fcm-setting.md](../advanced/channel/fcm-setting.md)
{% endcontent-ref %}

## 2. Gradle을 사용하여 SDK 연동

1\. Gradle 리포지토리를 추가합니다. project 수준의 `build.gradle` (`<project>/build.gradle`) 에 다음 항목들을 입력합니다.

{% hint style="info" %}
최신 Android Studio 를 통해 생성된 프로젝트의 경우 build.gradle의 allprojects 항목이 없습니다. 따라서 settings.gradle 파일에 추가해야합니다. 아래 예시 코드 중 settings.gradle 탭을 참고하세요.
{% endhint %}

{% tabs %}
{% tab title="build.gradle" %}
```java
// allprojects 가 없는 경우 settings.gradle 탭을 참고합니다.

allprojects {
  repositories {
    // 아래 코드 추가
    maven { url 'https://jitpack.io' }
  }
}
```
{% endtab %}

{% tab title="settings.gradle" %}
```java
// 최신 Android Studio를 통해 생성된 프로젝트의 경우 다음 가이드를 따릅니다.

dependencyResolutionManagement {
  repositories {
     // 아래 코드 추가
     maven { url 'https://jitpack.io' }
   }
}
```
{% endtab %}
{% endtabs %}

2\. app 수준의 `build.gradle` (`<project>/<app>/build.gradle`) 에 다음 항목들을 입력합니다

{% tabs %}
{% tab title="build.gradle" %}
```java
dependencies {
  // 아래 코드 추가
  implementation 'com.github.flarelane:FlareLane-Android-SDK:1.0.13'
}
```
{% endtab %}
{% endtabs %}

3\. Sync Now 를 클릭하여 Gradle을  최신화합니다

## 3. 초기화 코드 추가

{% hint style="info" %}
초기화 코드는 Application Class (Activity가 아님) 의 onCreate 에 추가합니다. 따라서 Application Class 를 먼저 만드는 것부터 시작하며, 이미 Application Class 가 있는 경우 해당 과정은 넘어가셔도 좋습니다.
{% endhint %}

1. `AndroidManifest.xml` 파일에서 `android.name=".MainApplication"` 을 입력하고 에디터 도우미를 통해 `MainApplication` 클래스 파일을 생성합니다. 직접 클래스 파일을 만드셔도 상관 없습니다.

![](../../.gitbook/assets/스크린샷\_2021-07-27\_오후\_12.11.47.png)

2\. `onCreate` 함수에서 `FlareLane.initWithContext` 함수를 추가합니다. 프로젝트 ID는 콘솔의 \[프로젝트] 페이지에서 확인할 수 있습니다.

{% tabs %}
{% tab title="Java" %}
{% code title="MainApplication.java" %}
```java
import com.flarelane.FlareLane;

public class MainApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        
        // 아래 코드 추가
        FlareLane.initWithContext(this, "INPUT_YOUR_PROJECT_ID");
    }
}
```
{% endcode %}
{% endtab %}

{% tab title="Kotlin" %}
{% code title="MainApplication.kt" %}
```kotlin
import com.flarelane.FlareLane

class MainApplication : Application() {
    override fun onCreate() {
        super.onCreate()
        
        // 아래 코드 추가
        FlareLane.initWithContext(this, "INPUT_YOUR_PROJECT_ID")
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

## 4. 방금 등록한 기기 확인

앱 실행을 한 뒤, 콘솔 내 \[전체 기기] 페이지를 클릭하여 기기가 추가된 것을 확인해보세요!

![](<../../.gitbook/assets/스크린샷 2021-12-15 오후 11.19.00.png>)

## 함께보기

#### Android 앱의 알림 아이콘 설정이 필요하다면 아래 가이드를 참고하세요.

{% content-ref url="../advanced/android-notification-icon.md" %}
[android-notification-icon.md](../advanced/android-notification-icon.md)
{% endcontent-ref %}




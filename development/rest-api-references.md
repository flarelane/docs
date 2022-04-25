# REST API Reference

{% hint style="danger" %}
무료 플랜(스타터)의 경우 분당 100회까지의 API 요청 제한이 있습니다. 유료 플랜 전환 시 무제한 사용이 가능합니다.
{% endhint %}

{% hint style="info" %}
API 종류는 계속 추가될 예정입니다.
{% endhint %}

{% swagger baseUrl="https://api.flarelane.com" path="/v1/projects/<project-id>/notifications" method="post" summary="메시지 발송하기" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="targetType" type="string" required="true" %}
발송 대상 유형 (segment, device, userId)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="targetIds" type="string[]" required="true" %}
발송 대상의 id 배열\
\* targetType별 최대 개수

&#x20; \- segment: 5

&#x20; \- device: 100

&#x20; \- userId: 1
{% endswagger-parameter %}

{% swagger-parameter in="body" name="templateId" type="string" %}
템플릿 id. 템플릿 사용시 다른 파라미터가 함께 있어도 템플릿의 내용으로 대체됩니다.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="title" type="string" %}
메시지 제목
{% endswagger-parameter %}

{% swagger-parameter in="body" name="body" type="string" required="false" %}
메시지 내용. templateId 와 body 중 하나는 반드시 존재해야 합니다.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="url" type="string" %}
메시지 URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="imageUrl" type="string" %}
첨부할 이미지 URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="object" %}
{key:value} 형태의 추가 변수 제공
{% endswagger-parameter %}

{% swagger-parameter in="path" name="project-id" type="string" %}
프로젝트 ID
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
발급받은 REST API Bearer 토큰 

\


ex) Bearer <bearer-token>
{% endswagger-parameter %}

{% swagger-response status="200" description="Success" %}

{% endswagger-response %}

{% swagger-response status="404" description="Fail" %}

{% endswagger-response %}
{% endswagger %}

---
product: campaign
title: IMS 문제 해결
description: IMS 문제 해결
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# IMS 문제 해결{#ims-troubleshooting}

![](../../assets/common.svg)

다음 문제 해결 팁이 도움이 됩니다 **온-프레미스** 고객은 IMS 통합을 사용할 때 발생하는 가장 일반적인 문제를 해결합니다. 대상 **호스팅** 고객이 Adobe에게 문의하십시오.

**외부 계정**

단지 **하나** 다음 설정을 사용하는 외부 계정:

* **내부 이름**: Adobe_Marketing_Cloud
* **유형**: Adobe Marketing Cloud

동일한 설정이 있는 중복 외부 계정을 삭제합니다.

**제품 컨텍스트**

외부 계정에 **제품 컨텍스트** 필드에서 해당 값이 **dma_campaign_classic**

제품 컨텍스트가 Campaign 및 Experience Cloud에 대해 동일한지 확인합니다.

예를 들어 **제품 컨텍스트** 이 표시되지 않으면 기본 제품 컨텍스트가 **dma_campaign** ( Campaign과 Experience Cloud 모두에 있습니다.) 만약 **제품 컨텍스트** 필드가 나타나면 기본 제품 컨텍스트가 **dma_campaign_classic** ( Campaign과 Experience Cloud 모두에 있습니다.)

**[!UICONTROL IMS Server URL]**

캠페인에서 **Adobe Marketing Cloud** 외부 계정을 확인하고 **[!UICONTROL IMS Server URL]** 다음 중 하나입니다. `adobeid-na1.services.adobe.com` 또는 `ims-na1.adobelogin.com`. 스테이지 및 프로덕션 인스턴스가 모두 동일한 IMS 프로덕션 종료 지점을 가리키는지 확인합니다.

**연결 마스크**

* 로그인하려는 사용자가 Enterprise Dashboard에서 운영자 그룹의 일부인지 확인합니다.
* 다음을 확인하십시오. **[!UICONTROL Association Mask]** 는 Enterprise Dashboard에서 사용자의 운영자 그룹 이름의 접두사입니다.
* 공백과 철자 오류가 없는지 확인하십시오.
* Campaign의 운영자 그룹 이름이 변경되지 않았는지 확인하고 다음 구문을 준수하십시오.

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**범위**

Campaign 외부 계정에 정의된 범위는 IMS에서 제공한 범위의 하위 집합이어야 합니다.

**콜백 URL**

다음 **콜백 URL** 를에 추가하고 허용 목록에 추가하다 &quot;https://&quot;으로 시작해야 합니다. 다음을 확인하십시오. **콜백 URL** 가 해당 인스턴스에 연결됩니다. 예를 들어 프로덕션 인스턴스는 프로덕션 URL로 리디렉션해야 합니다.

**클라이언트 ID 및 암호**

클라이언트 ID는 Campaign 외부 계정과 IMS에서 제공한 계정 간에 일치합니다.

입력한 클라이언트 암호가 올바른지 확인합니다.

**서버 다시 시작**

Campaign 외부 계정에서 위의 설정을 변경한 경우 서버를 다시 시작합니다

**일반적인 유형의 오류 및 가능한 솔루션**

* 사용자가 adobe.com 페이지로 리디렉션됩니다.

   문제에 문제가 있습니다 **[!UICONTROL Callback URL]**. 이전 단계를 참조하여 을(를) 확인합니다. **[!UICONTROL Callback URL]** 구성.

* 메시지 &quot;로그인에 표현식과 일치하는 권한이 없습니다.&quot;:

   이전 단계를 참조하여 을(를) 확인합니다. **[!UICONTROL Association Mask]** 및 연산자 그룹 구성을 참조하십시오.

* 사용자가 Adobe ID 로그인 페이지에 액세스할 수 없습니다.

   범위 구성을 확인하려면 이전 단계를 참조하십시오.

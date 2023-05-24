---
product: campaign
title: IMS 문제 해결
description: IMS 문제 해결
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# IMS 문제 해결{#ims-troubleshooting}



다음 문제 해결 팁이 도움이 됩니다 **온-프레미스** 고객은 IMS 통합을 사용할 때 발생하는 가장 일반적인 문제를 해결합니다. 대상 **호스트됨** 고객님, Adobe에게 문의해 주십시오.

**외부 계정**

다음과 같은 항목만 있어야 합니다. **1** 다음 설정을 사용하는 외부 계정:

* **내부 이름**: Adobe_마케팅_클라우드
* **유형**: ADOBE MARKETING CLOUD

설정이 동일한 중복 외부 계정을 삭제합니다.

**제품 컨텍스트**

외부 계정에 **제품 컨텍스트** 필드에서 값이 다음으로 설정되어 있는지 확인합니다. **dma_campaign_클래식**

제품 컨텍스트가 Campaign과 Experience Cloud에 대해 동일한지 확인합니다.

예를 들어 **제품 컨텍스트** 표시되지 않습니다. 기본 제품 컨텍스트는 다음과 같아야 합니다. **dma_campaign** Campaign과 Experience Cloud 모두에서. 다음과 같은 경우 **제품 컨텍스트** 필드가 나타나면 기본 제품 컨텍스트는 다음과 같아야 합니다. **dma_campaign_클래식** Campaign과 Experience Cloud 모두에서.

**[!UICONTROL IMS Server URL]**

캠페인에서 **Adobe Marketing Cloud** 외부 계정에서 다음을 확인합니다. **[!UICONTROL IMS Server URL]** 다음 중 하나 `adobeid-na1.services.adobe.com` 또는 `ims-na1.adobelogin.com`. 스테이지 및 프로덕션 인스턴스가 동일한 IMS 프로덕션 끝점을 가리켜야 합니다.

**연결 마스크**

* 로그인하려는 사용자가 Enterprise Dashboard에서 연산자 그룹의 일부인지 확인합니다.
* 다음을 확인하십시오. **[!UICONTROL Association Mask]** 는 Enterprise Dashboard에 있는 사용자의 연산자 그룹 이름의 접두사입니다.
* 공백과 철자 오류가 없는지 확인하십시오.
* Campaign의 연산자 그룹 이름이 변경되지 않았는지 확인하고 다음 구문을 준수합니다.

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**범위**

Campaign 외부 계정에 정의된 범위는 IMS에서 프로비저닝한 범위의 하위 집합이어야 합니다.

**콜백 URL**

다음 **콜백 URL** 허용 목록에 추가하다에 추가하고 &quot;https://&quot;로 시작해야 합니다. 다음을 확인하십시오. **콜백 URL** 가 해당 인스턴스에 연결됩니다. 예를 들어 프로덕션 인스턴스는 프로덕션 URL로 리디렉션되어야 합니다.

**클라이언트 ID 및 암호**

클라이언트 ID는 Campaign 외부 계정과 IMS에서 프로비저닝한 계정 간에 일치합니다.

입력한 클라이언트 암호가 올바른지 확인하십시오.

**서버 다시 시작**

Campaign 외부 계정의 위의 설정이 변경되면 서버를 다시 시작합니다

**일반적인 오류 유형 및 가능한 해결 방법**

* 사용자가 adobe.com 페이지로 리디렉션됩니다.

   에 문제가 있습니다. **[!UICONTROL Callback URL]**. 이전 단계를 참조하여 다음을 확인하십시오. **[!UICONTROL Callback URL]** 구성.

* &quot;로그인에 표현식과 일치하는 권한이 없습니다.&quot; 메시지:

   이전 단계를 참조하여 다음을 확인하십시오. **[!UICONTROL Association Mask]** 및 연산자 그룹 구성.

* Adobe ID 로그인 페이지에 액세스할 수 없습니다.

   범위 구성을 확인하려면 이전 단계를 참조하십시오.

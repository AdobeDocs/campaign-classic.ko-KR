---
product: campaign
title: IMS 문제 해결
description: IMS 문제 해결
feature: Configuration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# IMS 문제 해결{#ims-troubleshooting}


다음 문제 해결 팁은 **온-프레미스** 및 **하이브리드** 고객이 IMS 통합을 사용할 때 발생하는 가장 일반적인 문제를 해결하는 데 도움이 됩니다. **호스팅** 고객의 경우 Adobe에 문의하십시오.

**외부 계정**

다음 설정을 사용하는 외부 계정 **one**&#x200B;만 있어야 합니다.

* **내부 이름**: Adobe_Marketing_Cloud
* **유형**: Adobe Marketing Cloud

설정이 동일한 중복 외부 계정을 삭제합니다.

**제품 컨텍스트**

외부 계정에 **제품 컨텍스트** 필드가 있는 경우 해당 값이 **dma_campaign_classic**(으)로 설정되어 있는지 확인하십시오.

제품 컨텍스트가 Campaign과 Experience Cloud에 대해 동일한지 확인합니다.

예를 들어 **제품 컨텍스트**&#x200B;가 나타나지 않으면 기본 제품 컨텍스트는 Campaign과 Experience Cloud 모두에서 **dma_campaign**&#x200B;이어야 합니다. **제품 컨텍스트** 필드가 나타나면 Campaign과 Experience Cloud 모두에서 기본 제품 컨텍스트는 **dma_campaign_classic**&#x200B;이어야 합니다.

**[!UICONTROL IMS Server URL]**

Campaign **Adobe Marketing Cloud** 외부 계정에서 **[!UICONTROL IMS Server URL]**&#x200B;이(가) `adobeid-na1.services.adobe.com` 또는 `ims-na1.adobelogin.com`인지 확인하십시오. 스테이지 및 프로덕션 인스턴스가 동일한 IMS 프로덕션 끝점을 가리켜야 합니다.

**연결 마스크**

* 로그인하려는 사용자가 Enterprise Dashboard에서 연산자 그룹의 일부인지 확인합니다.
* **[!UICONTROL Association Mask]**&#x200B;이(가) Enterprise Dashboard에서 사용자 연산자 그룹 이름의 접두사인지 확인합니다.
* 공백과 철자 오류가 없는지 확인하십시오.
* Campaign의 연산자 그룹 이름이 변경되지 않았는지 확인하고 다음 구문을 준수합니다.

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**범위**

Campaign 외부 계정에 정의된 범위는 IMS에서 프로비저닝한 범위의 하위 집합이어야 합니다.

**콜백 URL**

**콜백 URL**&#x200B;을(를) 허용 목록에 추가하다에 추가하고 &quot;https://&quot;로 시작해야 합니다. **콜백 URL**&#x200B;이(가) 해당 인스턴스에 연결되어 있는지 확인하십시오. 예를 들어 프로덕션 인스턴스는 프로덕션 URL로 리디렉션되어야 합니다.

**클라이언트 ID 및 암호**

클라이언트 ID는 Campaign 외부 계정과 IMS에서 프로비저닝한 계정 간에 일치합니다.

입력한 클라이언트 암호가 올바른지 확인하십시오.

**서버 다시 시작**

Campaign 외부 계정의 위의 설정이 변경되면 서버를 다시 시작합니다

**일반적인 오류 유형 및 가능한 해결 방법**

* 사용자가 adobe.com 페이지로 리디렉션됩니다.

  **[!UICONTROL Callback URL]**&#x200B;에 문제가 있습니다. **[!UICONTROL Callback URL]** 구성을 확인하려면 이전 단계를 참조하세요.

* &quot;로그인에 표현식과 일치하는 권한이 없습니다.&quot; 메시지:

  **[!UICONTROL Association Mask]** 및 연산자 그룹 구성을 확인하려면 이전 단계를 참조하세요.

* Adobe ID 로그인 페이지에 액세스할 수 없습니다.

  범위 구성을 확인하려면 이전 단계를 참조하십시오.

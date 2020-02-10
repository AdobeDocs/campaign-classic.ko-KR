---
title: IMS 문제 해결
seo-title: IMS 문제 해결
description: IMS 문제 해결
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# IMS 문제 해결{#ims-troubleshooting}

다음 문제 해결 팁은 **온-프레미스** 고객이 IMS 통합을 사용할 때 발생하는 가장 일반적인 문제를 해결하는 데 도움이 됩니다. 호스팅 **** 고객의 경우 Adobe에 문의하십시오.

**외부 계정**

다음 설정을 사용하는 **외부 계정은 하나만** 있어야 합니다.

* **내부 이름**:Adobe_Marketing_Cloud
* **유형**:Adobe Marketing Cloud

동일한 설정을 갖는 중복 외부 계정을 삭제합니다.

**제품 컨텍스트**

외부 계정에 제품 **컨텍스트** 필드가 있는 경우 해당 값이 다음과 같이 설정되어 있는지 확인하십시오. **dma_campaign_classic**

제품 컨텍스트가 Campaign 및 Experience Cloud와 동일한지 확인하십시오.

예를 들어 제품 **컨텍스트가** 나타나지 않는 경우 기본 제품 컨텍스트는 Campaign과 Experience Cloud 모두에서 **dma_campaign** 이어야 합니다. 제품 **컨텍스트** 필드가 나타나면 기본 제품 컨텍스트는 Campaign 및 Experience Cloud에서 **dma_campaign_classic** 이어야 합니다.

**[!UICONTROL IMS Server URL]**

Campaign Adobe **Marketing Cloud** 외부 계정에서 **[!UICONTROL IMS Server URL]** 해당 계정이 [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) 또는 [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/)인지 확인하십시오. 스테이지와 프로덕션 인스턴스가 모두 동일한 IMS 프로덕션 끝점을 가리키는지 확인합니다.

**연결 마스크**

* 로그인하려는 사용자가 Enterprise Dashboard에서 운영자 그룹에 속하는지 확인합니다.
* Enterprise Dashboard **[!UICONTROL Association Mask]** 에서 사용자의 연산자 그룹 이름의 접두사인지 확인합니다.
* 공백과 철자 오류가 없는지 확인합니다.
* Campaign의 연산자 그룹 이름이 변경되지 않았는지 확인하고 다음 구문을 준수합니다.

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**범위**

Campaign 외부 계정에 정의된 범위는 IMS에서 제공하는 범위 중 일부여야 합니다.

**콜백 URL**

콜백 **URL은** 허용 목록에 포함되어야 하며 &quot;https://&quot;로 시작해야 합니다. 콜백 URL **이** 해당 인스턴스에 연결되어 있는지 확인합니다. 예를 들어 프로덕션 인스턴스는 프로덕션 URL로 리디렉션해야 합니다.

**클라이언트 ID 및 암호**

클라이언트 ID 파섹

입력한 클라이언트 암호가 올바른지 확인하십시오.

**서버 다시 시작**

Campaign 외부 계정의 위 설정을 변경하면 서버를 다시 시작합니다

**일반적인 유형의 오류 및 가능한 솔루션**

* 사용자가 adobe.com 페이지로 리디렉션됩니다.

   문제가 **[!UICONTROL Callback URL]**&#x200B;있습니다. 구성을 확인하려면 이전 단계를 **[!UICONTROL Callback URL]** 참조하십시오.

* &quot;로그인에 표현식과 일치하는 권한이 없습니다.&quot; 메시지:

   및 연산자 그룹 구성을 확인하려면 이전 단계를 **[!UICONTROL Association Mask]** 참조하십시오.

* 사용자가 Adobe ID 로그인 페이지에 액세스할 수 없습니다.

   범위 구성을 확인하려면 이전 단계를 참조하십시오.


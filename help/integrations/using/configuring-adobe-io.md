---
product: campaign
title: Adobe Experience Cloud Triggers에 대한 Adobe I/O 구성
description: Adobe Experience Cloud Triggers용 Adobe I/O을 구성하는 방법 알아보기
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 514f390b5615a504f3805de68f882af54e0c3949
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---

# Adobe Experience Cloud Triggers에 대한 Adobe I/O 구성 {#configuring-adobe-io}

>[!CAUTION]
>
>oAuth 인증을 통해 이전 버전의 트리거 통합을 사용하는 경우 **아래 설명에 따라 Adobe I/O으로 이동해야 합니다.**.
>이 이동 중에 [!DNL Adobe I/O]일부 들어오는 트리거가 손실될 수 있습니다.
>
>Campaign의 레거시 oAuth 인증 모드가 사용 중지됨 **2021년 10월 20일**. 호스팅된 환경은 다음 기한까지 확장 혜택을 받을 수 있습니다. **2022년 5월 25일**. 온-프레미스 또는 하이브리드 고객은 Adobe 고객 지원 센터에 연락하여 지원 대상을 확장합니다. **2022년 5월**. 다음을 수행해야 합니다. [oaUth 애플리케이션의 AppID 제공](../../integrations/using/configuring-pipeline.md#step-optional) Adobe.

## 필수 구성 요소 {#adobe-io-prerequisites}

이 통합은 시작에만 적용됩니다. **Campaign Classic 20.2.4 이상, 19.1.8 및 Gold Standard 11 릴리스**.

이 구현을 시작하기 전에 다음을 확인하십시오.

* 유효한 **조직 식별자**: 조직 ID는 Adobe Experience Cloud 내의 고유 식별자로서, 예를 들어 방문자 ID 서비스 및 IMS SSO(Single Sign-On)에 사용됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko)
* a **개발자 액세스** (으)로 가져왔습니다. 조직의 시스템 관리자는 **단일 제품 프로필에 개발자 추가** 프로시저 세부 정보 [이 페이지에서](https://helpx.adobe.com/enterprise/using/manage-developers.html) 개발자에게 다음에 대한 액세스 권한을 제공하려면 `Analytics - {tenantID}` 트리거와 연결된 Adobe Analytics 제품의 제품 프로필 .

## 1단계: Adobe I/O 프로젝트 만들기/업데이트 {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> 서비스 계정(JWT) 자격 증명은 Adobe에서 더 이상 사용되지 않으며, Adobe 솔루션 및 앱과 Campaign 통합은 이제 OAuth 서버 간 자격 증명을 사용해야 합니다. </br>
>
> * Campaign과 인바운드 통합을 구현하면에 자세히 설명된 대로 기술 계정을 마이그레이션해야 합니다. [이 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 기존 서비스 계정(JWT) 자격 증명은 2025년 1월 27일까지 계속 작동합니다. 또한 2024년 6월 3일부터 개발자 콘솔에서 새 서비스 계정(JWT) 자격 증명을 더 이상 만들 수 없습니다. 이 날짜 이후에는 새 서비스 계정(JWT) 자격 증명을 만들거나 프로젝트에 추가할 수 없습니다. </br>
>
> * Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일까지 계속 작동합니다. 그러나 해당 날짜 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 oAuth로 마이그레이션해야 합니다. 2024년 6월 3일부터 개발자 콘솔에서 새 서비스 계정(JWT) 자격 증명을 만들 수 없으므로 이 날짜 이후에는 JWT를 사용하는 새 아웃바운드 통합을 만들 수 없습니다

1. 액세스 [!DNL Adobe I/O] 조직의 개발자 액세스 권한으로 로그인합니다. 올바른 조직 포털에 로그인했는지 확인하십시오.

1. 인스턴스 구성 파일 ims/authIMSTAClientId에서 기존 통합 클라이언트 식별자(클라이언트 ID)를 추출합니다. 존재하지 않거나 비어 있는 속성은 클라이언트 식별자가 구성되지 않았음을 나타냅니다.

   >[!NOTE]
   >
   >클라이언트 식별자가 비어 있으면 직접 **[!UICONTROL Create a New project]** Adobe I/O.

1. 추출된 클라이언트 식별자를 사용하여 기존 프로젝트를 식별합니다. 이전 단계에서 추출한 것과 동일한 클라이언트 식별자가 있는 기존 프로젝트를 찾습니다.

   ![](assets/do-not-localize/adobe_io_8.png)

1. 선택 **[!UICONTROL + Add to Project]** 및 선택 **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. 다음에서 **[!UICONTROL Add an API]** 창, 선택 **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 선택 **[!UICONTROL Service Account (JWT)]** 를 인증 유형으로 사용하십시오.

   ![](assets/do-not-localize/adobe_io_3.png)

1. 클라이언트 ID가 비어 있으면 다음을 선택합니다. **[!UICONTROL Generate a key pair]** 공용 및 개인 키 쌍을 만듭니다.

   그러면 기본 만료 날짜가 365일인 키가 자동으로 다운로드됩니다. 만료되면 새 키 쌍을 만들고 구성 파일에서 통합을 업데이트해야 합니다. 옵션 2를 사용하여 을(를) 수동으로 만들고 업로드하도록 선택할 수 있습니다 **[!UICONTROL Public key]** 만료일이 더 긴 경우

   만료되는 인증서 키 쌍을 바꾸는 방법에 대한 단계별 안내서는 을 참조하십시오. [이 페이지](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >다시 다운로드할 수 없으므로 다운로드 프롬프트가 나타나면 config.zip 파일을 저장해야 합니다.

   ![](assets/do-not-localize/adobe_io_4.png)

1. **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/adobe_io_5.png)

1. 기존 항목 선택 **[!UICONTROL Product profile]** 또는 필요한 경우 새 템플릿을 만듭니다. 이에 대한 권한은 필요하지 않습니다. **[!UICONTROL Product profile]**. 에 대한 자세한 내용 [!DNL Analytics] **[!UICONTROL Product Profiles]**, 참조 [Adobe Analytics 설명서](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   그런 다음 을 클릭합니다. **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 프로젝트에서 을 선택합니다. **[!UICONTROL Adobe Analytics]** 다음 정보를 복사합니다. **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O 인증서는 12개월 후에 만료됩니다. 매년 새 키 쌍을 생성해야 합니다.

## 2단계: Adobe Campaign에서 프로젝트 자격 증명 추가 {#add-credentials-campaign}

>[!NOTE]
>
>에서 클라이언트 식별자가 비어 있지 않은 경우 이 단계는 필요하지 않습니다. [1단계: Adobe I/O 프로젝트 만들기/업데이트](#creating-adobe-io-project).

개인 키는 base64 UTF-8 형식으로 인코딩해야 합니다. 방법은 다음과 같습니다.

1. 에서 생성된 개인 키 사용 [1단계: Adobe I/O 프로젝트 섹션 만들기/업데이트](#creating-adobe-io-project). 개인 키는 통합을 만드는 데 사용되는 키와 동일해야 합니다.

1. 다음 명령을 사용하여 개인 키를 인코딩합니다. `base64 ./private.key > private.key.base64`. 이렇게 하면 base64 컨텐츠가 새 파일에 저장됩니다 `private.key.base64`.

   >[!NOTE]
   >
   >개인 키를 복사/붙여넣을 때 추가 줄을 자동으로 추가할 수도 있습니다. 개인 키를 인코딩하기 전에 제거해야 합니다.

1. 파일에서 내용 복사 `private.key.base64`.

1. SSH를 통해 Adobe Campaign 인스턴스가 설치된 각 컨테이너에 로그인하고 다음 명령을 실행하여 Adobe Campaign에서 프로젝트 자격 증명을 추가합니다. `neolane` 사용자. 이렇게 하면 **[!UICONTROL Technical Account]** 인스턴스 구성 파일의 자격 증명입니다.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 3단계: 파이프라인된 태그 업데이트 {#update-pipelined-tag}

>[!NOTE]
>
>에서 클라이언트 식별자가 비어 있지 않은 경우 이 단계는 필요하지 않습니다. [1단계: Adobe I/O 프로젝트 만들기/업데이트](#creating-adobe-io-project).

업데이트하려면 [!DNL pipelined] 태그: 구성 파일에서 인증 유형을 Adobe I/O 프로젝트로 업데이트해야 합니다 **config-&lt; instance-name >.xml** 다음과 같이:

```
<pipelined ... authType="imsJwtToken"  ... />
```

그런 다음 를 실행합니다. `config -reload` 및 의 다시 시작 [!DNL pipelined] 를 참조하십시오.

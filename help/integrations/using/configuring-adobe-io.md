---
product: campaign
title: Adobe Experience Cloud 트리거에 대한 Adobe I/O 구성
description: Adobe Experience Cloud Triggers에 대한 Adobe I/O 구성 방법 알아보기
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 4%

---

# Adobe Experience Cloud 트리거에 대한 Adobe I/O 구성 {#configuring-adobe-io}

>[!CAUTION]
>
>oAuth 인증을 통해 이전 버전의 트리거 통합을 사용하는 경우 **아래에 설명된 대로 Adobe I/O으로 이동해야 합니다**. Campaign이 있는 Campaign이 있는 이전 oAuth 인증 모드는 2021년 11월 30일에 사용이 중단됩니다. [자세히 알아보기](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>이 이동 중에 [!DNL Adobe I/O](으)로 이동하면 일부 수신 트리거가 손실될 수 있습니다.

## 사전 요구 사항 {#adobe-io-prerequisites}

이 통합은 **Campaign Classic 20.3, 20.2.4, 19.1.8 및 [!DNL Gold Standard] 11 릴리스**&#x200B;만 적용됩니다.

이 구현을 시작하기 전에 다음 내용이 있는지 확인하십시오.

* 유효한 **조직 식별자**:ims(Identity Management 시스템) 조직 식별자는 Adobe Experience Cloud 내의 고유 식별자로, 방문자 ID 서비스 및 IMS SSO(Single-Sign On)와 같이 사용됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* 조직에 대한 **개발자 액세스**  IMS 조직에 대한 시스템 관리자 권한을 요청해야 하는 경우 이 페이지](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)에 자세히 설명된 절차를 따라 모든 제품 프로필에 대해 이 액세스 권한을 제공합니다.[

## 1단계:Adobe I/O 프로젝트 {#creating-adobe-io-project} 만들기/업데이트

1. [!DNL Adobe I/O]에 액세스하여 IMS 조직의 시스템 관리자 권한으로 로그인합니다.

   >[!NOTE]
   >
   > 올바른 조직 포털에 로그인되어 있는지 확인하십시오.

1. 인스턴스 구성 파일 ims/authIMSTAClientId에서 기존 통합 클라이언트 식별자(클라이언트 ID)를 추출합니다. 존재하지 않거나 빈 속성은 클라이언트 식별자가 구성되지 않았음을 나타냅니다.

   >[!NOTE]
   >
   >클라이언트 식별자가 비어 있는 경우 Adobe I/O에서 직접 **[!UICONTROL Create a New project]**&#x200B;을 수행할 수 있습니다.

1. 추출된 클라이언트 식별자를 사용하여 기존 프로젝트를 식별합니다. 이전 단계에서 추출된 것과 동일한 클라이언트 식별자를 사용하는 기존 프로젝트를 찾습니다.

   ![](assets/do-not-localize/adobe_io_8.png)

1. **[!UICONTROL + Add to Project]** 을 선택하고 **[!UICONTROL API]** 을 선택합니다.

   ![](assets/do-not-localize/adobe_io_1.png)

1. **[!UICONTROL Add an API]** 창에서 **[!UICONTROL Adobe Analytics]** 을 선택합니다.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 인증 유형으로 **[!UICONTROL Service Account (JWT)]**&#x200B;을(를) 선택합니다.

   ![](assets/do-not-localize/adobe_io_3.png)

1. 클라이언트 ID가 비어 있는 경우 **[!UICONTROL Generate a key pair]** 을 선택하여 공개 및 개인 키 쌍을 만듭니다.

   그러면 기본 만료 날짜인 365일로 키가 자동으로 다운로드됩니다. 만료되면 새 키 쌍을 만들고 구성 파일에서 통합을 업데이트해야 합니다. 옵션 2를 사용하여 더 긴 만료 날짜가 있는 **[!UICONTROL Public key]**&#x200B;을 수동으로 만들고 업로드하도록 선택할 수 있습니다.

   ![](assets/do-not-localize/adobe_io_4.png)

1. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/do-not-localize/adobe_io_5.png)

1. 기존 **[!UICONTROL Product profile]**&#x200B;을 선택하거나 필요한 경우 새 항목을 만드십시오. 이 **[!UICONTROL Product profile]**&#x200B;에 대한 권한이 필요하지 않습니다. [!DNL Analytics] **[!UICONTROL Product Profiles]**&#x200B;에 대한 자세한 내용은 [Adobe Analytics 설명서](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)를 참조하십시오.

   그런 다음 **[!UICONTROL Save configured API]** 을 클릭합니다.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 프로젝트에서 **[!UICONTROL Adobe Analytics]** 을 선택하고 **[!UICONTROL Service Account (JWT)]** 아래에 다음 정보를 복사합니다.

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O 인증서는 12개월 후에 만료됩니다. 매년 새 키 쌍을 만들어야 합니다.

## 2단계:Adobe Campaign {#add-credentials-campaign}에 프로젝트 자격 증명을 추가합니다.

Adobe Campaign에 프로젝트 자격 증명을 추가하려면 Adobe Campaign 인스턴스의 모든 컨테이너에서 &#39;neolane&#39; 사용자로 다음 명령을 실행하여 인스턴스 구성 파일에 **[!UICONTROL Technical Account]** 자격 증명을 삽입합니다.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

개인 키는 base64 UTF-8 형식으로 인코딩해야 합니다. 방법은 다음과 같습니다.

1. [1단계에서 생성된 개인 키를 사용하십시오.Adobe I/O 프로젝트 섹션](#creating-adobe-io-project) 만들기/업데이트. 개인 키는 통합을 만드는 데 사용되는 키와 같아야 합니다.

1. 다음 명령을 사용하여 개인 키를 인코딩합니다.```base64 ./private.key```

   >[!NOTE]
   >
   >개인 키를 복사/붙여넣을 때 추가 줄이 자동으로 추가되는 경우가 있습니다. 개인 키를 인코딩하기 전에 제거해야 합니다.

1. 위에서 자세히 설명한 명령을 실행하려면 새로 생성된 개인 키를 base64 UTF-8 형식으로 인코딩합니다.

## 3단계:파이프라인 태그 {#update-pipelined-tag} 업데이트

[!DNL pipelined] 태그를 업데이트하려면 다음과 같이 구성 파일 **config-&lt; instance-name >.xml**&#x200B;에서 인증 유형을 Adobe I/O 프로젝트로 업데이트해야 합니다.

```
<pipelined ... authType="imsJwtToken"  ... />
```

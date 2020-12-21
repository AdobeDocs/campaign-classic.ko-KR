---
solution: Campaign Classic
product: campaign
title: Adobe Experience Cloud 트리거에 대한 Adobe I/O 구성
description: Adobe Experience Cloud 트리거에 대한 Adobe I/O 구성 방법 알아보기
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 4%

---


# Adobe Experience Cloud 트리거에 대한 Adobe I/O 구성 {#configuring-adobe-io}

>[!CAUTION]
>
>Auth 인증을 통해 이전 버전의 트리거 통합을 사용하는 경우 **아래 설명에 따라 Adobe I/O으로 이동해야 합니다.** 레거시 Auth 인증 모드는 2021년 4월 30일에 종료됩니다. [자세히 알아보기](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## 사전 요구 사항 {#adobe-io-prerequisites}

이 통합은 **Campaign Classic 20.3 및 Gold Standard 11 릴리스**&#x200B;부터 적용됩니다.

이 구현을 시작하기 전에 다음을 확인하십시오.

* 유효한 IMSOrgID:IMS(Identity Management 시스템) 조직 식별자는 Adobe Experience Cloud 내의 고유 식별자이며, VisitorID 서비스 및 IMS SSO(Single-Sign On),
* IMS 조직에 대한 개발자 액세스.

>[!NOTE]
>
>IMS 조직에 대한 시스템 관리자 권한을 요청해야 하는 경우 이 페이지](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html)에 자세한 [ 절차를 따라 모든 제품 프로필에 대한 이 액세스 권한을 제공합니다.


## 1단계:Adobe I/O 프로젝트 {#creating-adobe-io-project} 만들기/업데이트

1. Adobe I/O에 액세스하여 IMSorg의 시스템 관리자 권한으로 로그인합니다.

   >[!NOTE]
   >
   > 올바른 IMSorg 포털에 로그인되어 있는지 확인하십시오.

1. 인스턴스 구성 파일 ims/authIMSTAClientId에서 기존 통합 클라이언트 ID를 추출합니다. 존재하지 않거나 빈 속성은 클라이언트 ID가 구성되지 않았음을 나타냅니다.

   >[!NOTE]
   >
   >클라이언트 ID가 비어 있는 경우 Adobe I/O에서 바로 **[!UICONTROL Create a New project]**&#x200B;을(를) 사용할 수 있습니다.

1. 추출된 클라이언트 ID를 사용하여 기존 프로젝트를 식별합니다. 이전 단계에서 추출된 프로젝트와 클라이언트 ID가 동일한 기존 프로젝트를 찾습니다.

   ![](assets/do-not-localize/adobe_io_8.png)

1. **[!UICONTROL + Add to Project]**&#x200B;을 선택하고 **[!UICONTROL API]**&#x200B;을 선택합니다.

   ![](assets/do-not-localize/adobe_io_1.png)

1. **[!UICONTROL Add an API]** 창에서 **[!UICONTROL Adobe Analytics]**&#x200B;을 선택합니다.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 인증 유형으로 **[!UICONTROL Service Account (JWT)]**&#x200B;을 선택합니다.

   ![](assets/do-not-localize/adobe_io_3.png)

1. 클라이언트 ID가 비어 있는 경우 **[!UICONTROL Generate a key pair]**&#x200B;을 선택하여 공개 및 개인 키 쌍을 만듭니다.

   ![](assets/do-not-localize/adobe_io_4.png)

1. 공개 키를 업로드하고 **[!UICONTROL Next]**&#x200B;을 클릭합니다.

   ![](assets/do-not-localize/adobe_io_5.png)

1. **Analytics-&lt; 조직 이름 >**&#x200B;이라는 제품 프로필을 선택하고 **[!UICONTROL Save configured API]**&#x200B;를 클릭합니다.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 프로젝트에서 **[!UICONTROL Service Account (JWT)]**&#x200B;을 선택하고 다음 정보를 복사합니다.
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## 2단계:Adobe Campaign {#add-credentials-campaign}에 프로젝트 자격 증명 추가

Adobe Campaign에서 프로젝트 자격 증명을 추가하려면 Adobe Campaign 인스턴스의 모든 컨테이너에 &#39;neolane&#39; 사용자로 다음 명령을 실행하여 인스턴스 구성 파일에 **[!UICONTROL Technical Account]** 자격 증명을 삽입합니다.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>개인 키는 base64 UTF-8 형식으로 인코딩해야 합니다. 개인 키를 제외하고 인코딩 전에 키에서 새 행을 제거해야 합니다. 비공개 키는 통합을 만드는 데 사용한 키와 동일해야 합니다.

## 3단계:파이프라인 태그 {#update-pipelined-tag} 업데이트

[!DNL pipelined] 태그를 업데이트하려면 다음과 같이 구성 파일 **config-&lt; instance-name >.xml**&#x200B;에서 인증 유형을 Adobe I/O 프로젝트로 업데이트해야 합니다.

```
<pipelined ... authType="imsJwtToken"  ... />
```

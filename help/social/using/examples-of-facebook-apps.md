---
solution: Campaign Classic
product: campaign
title: Facebook 앱의 예
description: Facebook 앱의 예
audience: social
content-type: reference
topic-tags: annexes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---


# Facebook 앱의 예{#examples-of-facebook-apps}

사용자가 Facebook 애플리케이션의 탭을 클릭하면 폭이 810픽셀인 공간에 표시됩니다. Adobe Campaign은 Facebook 유형 웹 애플리케이션을 사용하여 Facebook 애플리케이션에 표시되는 컨텐츠를 정의하고 개인화할 수 있으므로 프로필을 쉽게 획득할 수 있습니다.

>[!NOTE]
>
>또한 파트너가 개발한 Facebook 애플리케이션에 Adobe Campaign을 통합할 수도 있습니다. 이 경우 Adobe Campaign 웹 애플리케이션을 사용하여 Facebook 프로필을 가져올 필요가 없습니다. 자세한 내용은 외부 계정 [구성을 참조하십시오](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Facebook 애플리케이션 만들기에 설명된 [구성 단계를 따르십시오](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>이 섹션에서는 Facebook 유형 웹 애플리케이션에 연결된 요소에 대해 자세히 설명합니다. 표준 웹 애플리케이션과 공유되는 모든 요소는 [이 섹션에 자세히 설명되어 있습니다](../../web/using/about-web-applications.md).

Facebook 유형 웹 애플리케이션의 예는 다음과 같습니다.

* 7단계에서 Facebook 애플리케이션을 만드는 방법입니다. 빠른 [시작을 참조하십시오.7단계로 Facebook 애플리케이션 만들기를 참조하십시오](#quick-start--creating-a-facebook-application-in-7-steps).
* Facebook 애플리케이션에 설정을 전달하는 방법. Facebook 애플리케이션에 [설정을 전달하는 방법을 참조하십시오](#how-to-forward-settings-to-a-facebook-application-).
* 팬 데이터를 얻는 방법 팬 데이터 [를 얻는 방법을 참조하십시오](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>이러한 간단한 사용 사례는 Facebook 유형 웹 애플리케이션의 기능을 설명하기 위한 예로 제공됩니다.

## 추천 {#recommendations}

다음 제한 사항은 Facebook에 직접 연결됩니다.

* 모든 웹 응용 프로그램을 HTTPS로 빌드해야 합니다.
* 탭을 통해 표시되는 Facebook 애플리케이션의 너비는 810픽셀입니다.

## 빠른 시작:7단계로 Facebook 애플리케이션 만들기 {#quick-start--creating-a-facebook-application-in-7-steps}

이 예에서는 Facebook에서 Adobe Campaign 내장 애플리케이션을 표시하는 방법에 대한 단계별 프로세스를 제공합니다. 이 경우 사용자가 응용 프로그램 탭( **App01** )을 클릭할 때&#x200B;**환영**&#x200B;메시지를 표시할 수 있는 응용 프로그램을 만들어야 합니다.

이 응용 프로그램을 만들려면 다음 단계를 적용합니다.

1. Facebook에서 애플리케이션을 [만듭니다( https://developers.facebook.com/apps](https://developers.facebook.com/apps)). 자세한 내용은 다음을 참조하십시오. [Facebook 애플리케이션 만들기를 참조하십시오](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. 외부 계정 **[!UICONTROL Facebook Connect]** 유형을 만들고 Facebook 애플리케이션의 매개 변수를 입력합니다. 자세한 내용은 다음을 참조하십시오. [외부 계정](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)구성

   ![](assets/social_quick_start_2.png)

1. Facebook 권한 요청 화면에 표시할 **[!UICONTROL Terms of service]** 및 **[!UICONTROL Privacy policy]** 링크를 입력합니다. 자세한 내용은 다음을 참조하십시오. [서비스 약관 및 개인 정보 보호 정책 링크를 입력합니다](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Adobe Campaign에서 Facebook 유형 웹 애플리케이션을 만듭니다. 자세한 내용은 다음을 참조하십시오. [Facebook 유형 웹 애플리케이션](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)만들기를 참조하십시오.

   ![](assets/social_webapp_005.png)

1. 웹 애플리케이션을 편집합니다. 이 예에서는 활동을 추가하고 **[!UICONTROL Page]** 활동의 제목을 정의했습니다.

   ![](assets/social_quick_start_4.png)

1. 애플리케이션을 배포합니다.

   ![](assets/social_webapp_004.png)

1. Facebook 페이지에서 탭으로 표시되도록 Facebook 애플리케이션을 구성합니다. 자세한 내용은 다음을 참조하십시오. [Facebook 탭](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs)구성

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

App01 **** 애플리케이션의 탭이 Facebook 페이지에 표시되는지 확인하십시오. 이 단추를 클릭하면 **환영** 메시지가 표시됩니다.

![](assets/social_webapp_042.png)

## Facebook 애플리케이션에 설정을 전달하는 방법? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Facebook 애플리케이션 만들기에 설명된 [구성 단계를 따릅니다](../../social/using/creating-a-facebook-application.md).

예 1에서는 **[!UICONTROL Fan of the page]** 필드 값에 따라 Facebook 페이지 표시를 개인화했습니다. 또한 **[!UICONTROL Application settings]** 필드를 처리할 수도 있습니다. 이 필드를 사용하면 Facebook을 통해 Adobe Campaign에서 생성한 링크에 포함된 데이터를 복구할 수 있습니다.

이메일 캠페인을 보내는 회사의 예를 들어보겠습니다. 배달에서 링크는 Facebook 애플리케이션을 가리킵니다. 이 링크는 URL 끝에 추가된 매개 변수 **[!UICONTROL app_data]** 로 개인화됩니다. 이 매개 변수의 값은 고객 중요성을 반영하는 지표일 수 있습니다. 이 예에서는 매개 변수 **[!UICONTROL app_data]** 값 **[!UICONTROL big]** (중요한 고객)과 **[!UICONTROL small]** (덜 중요한 고객)이 있습니다.

개인화된 URL은 다음과 같습니다.

* `http://<path of the Facebook application>&app_data=big` (중요한 고객의 경우)
* `http://<path of the Facebook application>&app_data=small` (덜 중요한 고객의 경우)

Facebook에서 Adobe Campaign으로 전달된 익명 데이터 중 필드 값이 수집되므로 Adobe Campaign은 이 매개 변수를 기반으로 애플리케이션 표시를 개인화할 수 있습니다. **[!UICONTROL Application parameters]**

사용자가 중요한 고객인 경우(매개 변수의 값 **[!UICONTROL app_data]** 이 **[!UICONTROL big]**&#x200B;해당) 다음 이미지가 표시됩니다.

![](assets/social_webapp_017.png)

사용자가 덜 중요한 고객인 경우(매개 변수의 값 **[!UICONTROL app_data]** 이 **[!UICONTROL small]**&#x200B;해당) 다음 이미지가 표시됩니다.

![](assets/social_webapp_016.png)

이 사용 사례를 다시 만들기 위해 다음 요소로 구성된 웹 응용 프로그램을 만들었습니다.

* 필드를 **[!UICONTROL Test]** 기반으로 하는 **[!UICONTROL Application parameter]** 활동.
* 필드 값에 따라 표시할 이미지가 포함된 두 **[!UICONTROL Application parameter]** 페이지.

![](assets/social_webapp_018.png)

## 팬 데이터를 얻는 방법 {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>Facebook 애플리케이션 만들기에 설명된 [구성 단계를 따릅니다](../../social/using/creating-a-facebook-application.md).

이 예에서는 Facebook 사용자와 연락하고 프로필 정보를 공유할 수 있도록 오퍼를 제공하는 방법을 보여 줍니다. 예를 들어 잠재 고객을 확보하고 자신의 페이스북 페이지에 경쟁사를 조직하여 이들의 참여를 유도할 수 있는 회사의 예를 보자.

사용자가 **[!UICONTROL App03]** 탭을 클릭할 때마다 해당 사용자가 대회에 참가할지 여부를 묻습니다.

![](assets/social_webapp_fb_000.png)

그들이 그 대회에 참가하기로 결정한다면, 우리는 그들이 그들의 프로필 정보를 공유할 것을 제안합니다.

![](assets/social_webapp_021.png)

정보 공유에 동의하는 경우 다음 화면이 표시됩니다.

![](assets/social_webapp_022.png)

이 사용 사례를 만들기 위해 다음 요소를 포함하는 웹 응용 프로그램을 만들었습니다.

* **[!UICONTROL Test]** 활동
* 세 페이지
* an **[!UICONTROL Access control]** activity
* **[!UICONTROL Pre-loading]** 활동
* **[!UICONTROL Save]** 활동
* an **[!UICONTROL End]** activity

![](assets/social_webapp_019.png)

### 활동 테스트 {#test-activity}

이 **[!UICONTROL Test]** 활동은 **[!UICONTROL ID]** 및 **[!UICONTROL Application parameters]** 필드를 기반으로 합니다.

![](assets/social_webapp_023.png)

그것은 세 개의 가지들로 구성되어 있습니다.

* **[!UICONTROL identifier (UID) is empty]** :식별자는 사용자가 이미 정보를 공유하기로 동의한 경우에만 Facebook에서 전달됩니다. 활동의 첫 번째 분기를 사용하면 **[!UICONTROL Test]** 입력한 적이 없는 사용자(예: 빈 ID가 있는 사용자)만 경쟁을 사용할 수 있도록 만들 수 있습니다.
* **[!UICONTROL application parameter equals 'thanks']** :Facebook에 연결된 표시 오류를 방지하려면 웹 애플리케이션 종료 페이지가 Facebook 애플리케이션의 URL을 가리키며, 이 값 **[!UICONTROL app_data]** 을 사용하여 매개 변수가 추가되는 **[!UICONTROL thanks]** 경우 다음을 참조하십시오. [종료 활동](#end-activity)). 두 번째 분기를 사용하면 사용자가 첫 번째 분기의 **[!UICONTROL End]** 활동에서 왔는지(그리고 방금 경쟁업체에 들어온) 확인하여 감사 메시지를 표시할 수 있습니다. 추가 URL 매개 변수 사용에 대한 자세한 내용은 다음을 참조하십시오. [Facebook 애플리케이션에 설정을 전달하는 방법](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** :사용자가 이전 날짜(응용 프로그램 매개 변수와 다름)에 이미 경쟁 제품(ID가 이미 입력됨)에 입장한 경우 이미 입력되어 있다는 **[!UICONTROL thanks]**&#x200B;페이지가 표시됩니다.

### 대회 페이지 {#competition-page}

Facebook에 연결된 표시 오류를 피하려면 대회 페이지의 필드 **[!UICONTROL Parent window]** 에서 또 **[!UICONTROL In the top window]** 는 **[!UICONTROL Window]** 선택해야 합니다.

![](assets/social_webapp_028.png)

### 액세스 제어 활동 {#access-control-activity}

이 **[!UICONTROL Access control]** 활동에서는 사용자가 경쟁에 들어갈 때 Facebook 권한 요청 페이지를 표시할 수 있습니다. 정보를 공유하기로 동의하면 사전 로드 중에 복구됩니다. For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

웹 애플리케이션을 만들 때 이전에 외부 계정을 입력한 경우(Facebook [유형 웹 애플리케이션](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)만들기 참조) 활동을 편집할 필요가 없습니다. 그렇지 않은 경우 **[!UICONTROL Application]** 필드로 이동하여 Facebook 애플리케이션에 연결된 외부 계정을 선택합니다.

![](assets/social_webapp_024.png)

### 사전 로드 활동 {#pre-loading-activity}

사전 로딩에 사용할 데이터 소스를 선택합니다.

* **[!UICONTROL Marketing database]** :이 옵션을 사용하면 Adobe Campaign 데이터베이스를 통해 데이터를 미리 로드할 수 있습니다.
* **[!UICONTROL Facebook]** :이 옵션을 사용하면 Facebook을 사용하여 데이터를 미리 로드할 수 있습니다.

![](assets/social_webapp_029.png)

**마케팅 데이터베이스**

이 옵션을 사용하면 방문자 테이블에 존재하는 프로필의 데이터를 복구할 수 있습니다. 사용자가 Facebook 애플리케이션 탭을 클릭할 때 복구된 외부 Facebook ID를 기반으로 확인이 수행됩니다. 활동 후에 양식을 추가하는 경우 데이터베이스에 정보가 들어 있는 필드가 미리 로드됩니다. **[!UICONTROL Pre-loading]**

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Adobe Campaign 데이터베이스를 통해 데이터를 미리 로드하는 방법에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

이 옵션을 사용하면 사용자가 공유하기로 합의한 Facebook 프로필 정보를 저장하는 과정에서 수집할 Facebook 프로필 정보를 정의할 수 있습니다.

![](assets/social_webapp_025.png)

이 **[!UICONTROL Database information]** 옵션을 사용하면 다음 데이터를 수집할 수 있습니다.

* **[!UICONTROL External ID]**:사용자 ID
* **[!UICONTROL Gender]**:사용자의 성별
* **[!UICONTROL Verified]** :이 필드는 사용자가 확인된 Facebook 계정을 가지고 있는지 여부를 지정합니다.
* **[!UICONTROL Full name]**:사용자의 전체 이름
* **[!UICONTROL First name]**:사용자 이름
* **[!UICONTROL Last name]**:사용자의 성
* **[!UICONTROL Language]**:사용자 언어

해당 상자를 체크하여 프로필 사진, 친구 목록, 이메일 주소, 생년월일, 관심사 및 위치를 수집할 수도 있습니다.

클릭하기 **[!UICONTROL Ok]**&#x200B;전에 **[!UICONTROL I agree to comply with Facebook conditions of use]** 상자를 선택합니다.

>[!NOTE]
>
>섹션에서 하나 이상의 상자를 선택하면 **[!UICONTROL Private information]** Facebook 권한 요청 화면에 해당 데이터에 대한 액세스 요청이 자동으로 표시됩니다.
>
>사용자가 선택한 정보를 수집하려면 사용자가 정보를 공유하기로 동의해야 합니다.
>
>두 가지 유형의 사전 로드(Adobe Campaign을 통해, Facebook을 통해)를 원하는 경우 각각 두 개의 사전 로드 상자를 추가합니다.

### 활동 저장 {#save-activity}

이 **[!UICONTROL Save]** 활동을 통해 이전 단계 동안 수집된 정보를 방문자 테이블에 저장할 수 있습니다.

프로필이 방문자 테이블에 이미 존재하는 경우 데이터가 수집된 새 데이터로 업데이트됩니다.

데이터베이스에 프로필이 없고 Facebook 사용자의 이메일 주소가 수집된 경우 방문자 테이블에 방문자가 만들어집니다.

![](assets/social_webapp_026.png)

1. 필드에서 **[!UICONTROL Visitor creation folder]** 프로파일을 만들 폴더를 선택합니다. Facebook 유형 웹 애플리케이션의 경우 기본 생성 폴더는 입니다 **[!UICONTROL Visitors]**.
1. 필드에서 **[!UICONTROL Reconciliation mode]** 사용할 조정 모드를 선택합니다.

   * **[!UICONTROL Automatic]** :화해는 이메일, 성, 이름, 생년월일을 기준으로 한다.
   * **[!UICONTROL Manual]** :조정 키를 하나 이상 선택하십시오.
   * **[!UICONTROL None]** :화해할 수 없다.

1. 필드에서 **[!UICONTROL Mapping]** 조정을 수행할 스키마를 선택합니다.

   >[!IMPORTANT]
   >
   >배달 매핑에서 **[!UICONTROL Social networks]** 탭의 필드가 올바르게 입력되었는지 확인합니다. 배달 매핑은 노드를 통해 **[!UICONTROL Administration > Campaign management > Target mappings]** 액세스합니다.

1. 조정을 위해 검색 폴더를 선택하고 새 프로파일을 만들기 폴더를 선택할 수 있습니다. 필드가 비어 있으면, 프로필은 검색 후 매핑 스키마의 기본 폴더에 만들어집니다.

### 종료 활동 {#end-activity}

Facebook에 연결된 표시 오류를 피하려면 **[!UICONTROL Use an external URL]** 상자를 선택하고 Facebook 애플리케이션의 URL을 입력한 다음 매개 변수와 값을 **[!UICONTROL app_data]** 입력해야 합니다. 이 값은 사용자가 경쟁업체에 막 입장했는지 여부를 감지하고 해당되는 경우 감사 메시지를 표시하는 데 사용됩니다. **[!UICONTROL Test]** For more on this, refer to: [Test activity](#test-activity).

이 예에서 사용된 값은 **감사합니다**.

![](assets/social_webapp_027.png)

### 방문자의 세부 사항 화면 {#details-screen-of-a-visitor}

Twitter 팔로워의 경우처럼 [운영 원칙](../../social/using/publishing-on-twitter.md#operating-principle)) 복구된 Facebook 프로필은 방문자 표에 저장됩니다. 방문자 목록을 표시하려면 **[!UICONTROL Profiles and Targets > Visitors]** 노드로 이동합니다.

프로필 정보를 공유하기로 동의하는 각 Facebook 잠재 고객이 방문자 목록에 추가됩니다. 이 **[!UICONTROL Friends]** 상자가 활동 **[!UICONTROL Pre-load]** 에서 선택된 경우( [사전 로딩 활동](#pre-loading-activity)) 친구도 추가됩니다.

![](assets/social_webapp_037.png)

방문자 세부 사항 창 **[!UICONTROL Summary]** 의 섹션에는 표시기에 대해 두 가지 가능한 상태가 **[!UICONTROL New Contact]** 있습니다.

![](assets/social_webapp_038.png)

녹색 확인 표시가 표시되면 방문자가 수신자와 화해하지 않은 것입니다. 이 경우 수신자 목록에 새 프로필이 만들어집니다.

![](assets/social_webapp_039.png)

적십자란 방문자가 수신자와 화해했음을 의미합니다. 필드 오른쪽의 돋보기를 클릭하여 일치하는 수신자를 표시할 수 **[!UICONTROL Recipient]** 있습니다.

![](assets/social_webapp_040.png)

해당하는 경우 수신자의 세부 정보 창으로 이동하여 일치하는 방문자를 표시합니다. 탭을 **[!UICONTROL Others]** 선택한 다음 섹션에서 방문자 이름을 두 번 **[!UICONTROL Web identities]** 클릭합니다.

![](assets/social_webapp_041.png)

방문자 세부 사항 페이지의 **[!UICONTROL Activities]** 화면에는 다음 정보가 포함됩니다.

* &quot;Open Graph&quot; 유형 팬 활동:설치된 응용 프로그램(Deezer, Spotify, Dailymotion, Yahoo News 등)의 음악 재생, 비디오, 아티클 읽기 및 정보

   ![](assets/social_facebook_activities.png)

* &quot;좋아요&quot; 및 팬이 Adobe Campaign이 보낸 배달 후 추가한 의견
* 팬의 페이지
* 팬의 체크 인

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Adobe Campaign이 팬의 체크인을 수집하려면 서비스 구성 화면에서 **[!UICONTROL Subscribe]** 버튼을 클릭해야 합니다. 자세한 내용은 외부 계정 [구성을 참조하십시오](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Facebook 프로필 데이터를 사용하여 양식 필드를 미리 로드하는 방법 {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

또한 이 **[!UICONTROL Social Marketing]** 애플리케이션을 사용하면 Facebook 프로필 정보를 사용하여 미리 로드 필드에 대한 단추를 양식에 추가할 수도 있습니다. 모든 웹 애플리케이션 템플릿(유형 활동)에서 사용할 수 있는 이 옵션&#x200B;**[!UICONTROL Page]** 은 [이 섹션에 자세히 설명되어 있습니다](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>이 함수 사용을 시작하기 전에 Facebook 애플리케이션 및 **[!UICONTROL Facebook Connect]** 유형 외부 계정을 만들어야 합니다. 자세한 내용은 외부 계정 [구성을 참조하십시오](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).


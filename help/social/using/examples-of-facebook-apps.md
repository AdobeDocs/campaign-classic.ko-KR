---
product: campaign
title: Facebook 앱의 예
description: Facebook 앱의 예
audience: social
content-type: reference
topic-tags: annexes
exl-id: 3b8c7db4-9c55-42f6-8e09-e5ab781efe8f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2222'
ht-degree: 1%

---

# Facebook 앱의 예{#examples-of-facebook-apps}

![](../../assets/v7-only.svg)

사용자가 Facebook 애플리케이션의 탭을 클릭하면 폭이 810픽셀인 공간에 표시됩니다. Adobe Campaign은 Facebook 유형 웹 애플리케이션을 사용하여 Facebook 애플리케이션에 표시되는 컨텐츠를 정의하고 개인화할 수 있으므로 프로필을 보다 쉽게 획득할 수 있습니다.

>[!NOTE]
>
>또한 파트너가 개발한 Facebook 애플리케이션과 Adobe Campaign을 통합할 수 있습니다. 이 경우 Adobe Campaign 웹 애플리케이션을 사용하여 Facebook 프로필을 획득할 필요가 없습니다. 자세한 내용은 [외부 계정 구성](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>에 설명된 구성 단계를 따르십시오. [facebook 애플리케이션 만들기](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>이 섹션에서는 Facebook 유형 웹 애플리케이션에 연결된 요소에 대해 자세히 설명합니다. 표준 웹 애플리케이션과 공유되는 모든 요소는 [이 섹션](../../web/using/about-web-applications.md).

여기에 자세히 설명된 Facebook 유형 웹 애플리케이션의 예는 다음과 같습니다.

* 7단계로 Facebook 애플리케이션을 만드는 방법입니다. 을(를) 참조하십시오. [빠른 시작: 7단계로 Facebook 애플리케이션 만들기](#quick-start--creating-a-facebook-application-in-7-steps).
* facebook 애플리케이션에 설정을 전달하는 방법 을(를) 참조하십시오. [facebook 애플리케이션에 설정을 전달하는 방법](#how-to-forward-settings-to-a-facebook-application-).
* 팬 데이터를 얻는 방법 을(를) 참조하십시오. [팬 데이터를 얻는 방법](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>이러한 간단한 사용 사례는 Facebook 유형 웹 애플리케이션의 기능을 보여주는 예로서 제공됩니다.

## 추천 {#recommendations}

다음 제한 사항은 Facebook에 직접 연결됩니다.

* HTTPS로 모든 웹 애플리케이션을 빌드해야 합니다.
* 탭을 통해 표시되는 Facebook 애플리케이션의 너비는 810픽셀입니다.

## 빠른 시작: 7단계로 Facebook 애플리케이션 만들기 {#quick-start--creating-a-facebook-application-in-7-steps}

이 예제는 Facebook에서 Adobe Campaign 기본 제공 애플리케이션을 표시하는 방법에 대한 단계별 프로세스를 제공합니다. 이 경우 **시작** 사용자가 애플리케이션 탭을 클릭하면 표시되는 메시지(**App01**).

이 응용 프로그램을 만들려면 다음 단계를 수행합니다.

1. facebook에서 애플리케이션 만들기( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). 자세한 내용은 다음을 참조하십시오. [facebook 애플리케이션 만들기](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. 만들기 **[!UICONTROL Facebook Connect]** 외부 계정을 입력하고 Facebook 애플리케이션의 매개 변수를 입력합니다. 자세한 내용은 다음을 참조하십시오. [외부 계정 구성](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. 을(를) 입력합니다. **[!UICONTROL Terms of service]** 및 **[!UICONTROL Privacy policy]** facebook 권한 요청 화면에 표시되는 링크입니다. 자세한 내용은 다음을 참조하십시오. [서비스 약관 및 개인 정보 보호 정책 링크 입력](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Adobe Campaign에서 Facebook 유형 웹 애플리케이션을 만듭니다. 자세한 내용은 다음을 참조하십시오. [facebook 유형 웹 애플리케이션 만들기](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_005.png)

1. 웹 애플리케이션을 편집합니다. 이 예에서는 **[!UICONTROL Page]** 활동을 정의하고 제목을 정의합니다.

   ![](assets/social_quick_start_4.png)

1. 애플리케이션을 배포합니다.

   ![](assets/social_webapp_004.png)

1. facebook 페이지에서 Facebook 애플리케이션이 탭으로 표시되도록 구성합니다. 자세한 내용은 다음을 참조하십시오. [facebook 탭 구성](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

의 탭을 확인합니다. **App01** 애플리케이션이 Facebook 페이지에 표시됩니다. 이 링크를 클릭하면 **시작** 메시지를 표시합니다.

![](assets/social_webapp_042.png)

## facebook 애플리케이션에 설정을 전달하는 방법 {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>에 자세히 설명된 구성 단계를 따르십시오 [facebook 애플리케이션 만들기](../../social/using/creating-a-facebook-application.md).

예제 1에서는 의 값에 따라 Facebook 페이지의 표시를 개인화했습니다 **[!UICONTROL Fan of the page]** 필드. 또한 를 처리할 수도 있습니다 **[!UICONTROL Application settings]** 필드. 이 필드를 사용하면 Facebook을 통해 Adobe Campaign에서 생성한 링크에 포함된 데이터를 복구할 수 있습니다.

이메일 캠페인을 보내기로 결정하는 회사의 예를 들어보겠습니다. 게재에서 링크가 Facebook 애플리케이션을 가리킵니다. 이 링크는 **[!UICONTROL app_data]** 매개 변수가 URL 끝에 추가되었습니다. 이 매개 변수의 값은 고객 중요성을 반영하는 지표일 수 있습니다. 이 예제에서는 **[!UICONTROL app_data]** 매개 변수 **[!UICONTROL big]** (중요한 고객) 및 **[!UICONTROL small]** (덜 중요한 고객)

개인화된 URL은 다음과 같습니다.

* `http://<path of the Facebook application>&app_data=big` (중요한 고객의 경우)
* `http://<path of the Facebook application>&app_data=small` (덜 중요한 고객의 경우)

facebook이 Adobe Campaign에 보내는 익명 데이터 중 다음 값 **[!UICONTROL Application parameters]** 필드가 수집되므로 Adobe Campaign에서 이 매개 변수를 기반으로 애플리케이션 표시를 개인화할 수 있습니다.

사용자가 상당한 고객인 경우(이)의 **[!UICONTROL app_data]** 매개 변수: **[!UICONTROL big]**) 위에 표시된다면 다음 이미지가 표시됩니다.

![](assets/social_webapp_017.png)

사용자가 덜 중요한 고객인 경우( **[!UICONTROL app_data]** 매개 변수: **[!UICONTROL small]**) 위에 표시된다면 다음 이미지가 표시됩니다.

![](assets/social_webapp_016.png)

이 사용 사례를 다시 만들기 위해 다음 요소로 구성된 웹 애플리케이션을 만들었습니다.

* A **[!UICONTROL Test]** 활동을 기반으로 합니다 **[!UICONTROL Application parameter]** 필드.
* 의 값에 따라 표시할 이미지가 들어 있는 두 페이지 **[!UICONTROL Application parameter]** 필드.

![](assets/social_webapp_018.png)

## 팬 데이터를 얻는 방법 {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>에 자세히 설명된 구성 단계를 따르십시오 [facebook 애플리케이션 만들기](../../social/using/creating-a-facebook-application.md).

이 예는 Facebook 사용자에게 연락하여 해당 사용자가 프로필 정보를 공유할 수 있도록 제공하는 방법을 보여줍니다. 한 예로 Facebook에서 잠재 고객을 확보하고 경쟁을 펼치고자 하는 회사의 경우를 보자.

사용자가 를 클릭할 때마다 **[!UICONTROL App03]** 우리는 그들에게 그들이 그 대회에 참가하기를 원하는지 물어본다.

![](assets/social_webapp_fb_000.png)

만약 그들이 그 대회에 참가하기로 결정한다면, 우리는 그들이 그들의 프로필 정보를 공유하도록 제안합니다.

![](assets/social_webapp_021.png)

정보 공유에 동의하는 경우 다음 화면이 표시됩니다.

![](assets/social_webapp_022.png)

이 사용 사례를 빌드하기 위해 다음 요소를 포함하는 웹 애플리케이션을 만들었습니다.

* **[!UICONTROL Test]** 활동
* 세 페이지
* an **[!UICONTROL Access control]** 활동
* **[!UICONTROL Pre-loading]** 활동
* **[!UICONTROL Save]** 활동
* an **[!UICONTROL End]** 활동

![](assets/social_webapp_019.png)

### 활동 테스트 {#test-activity}

다음 **[!UICONTROL Test]** 활동은 **[!UICONTROL ID]** 및 **[!UICONTROL Application parameters]** 필드.

![](assets/social_webapp_023.png)

그것은 세 개의 지기로 구성되어 있습니다.

* **[!UICONTROL identifier (UID) is empty]** : 사용자가 이미 정보를 공유하기로 동의한 경우에만 식별자가 Facebook에 의해 전달됩니다. 의 첫 번째 분기 **[!UICONTROL Test]** 활동을 사용하면 입장한 적이 없는 사용자(예: 빈 ID가 있는 사용자)에게만 경쟁을 사용할 수 있도록 할 수 있습니다.
* **[!UICONTROL application parameter equals 'thanks']** : facebook에 연결된 표시 오류를 사이드 스텝(siststep)하려면, 웹 애플리케이션 종료 페이지가 Facebook 애플리케이션의 URL을 가리키는 **[!UICONTROL app_data]** 를 사용하여에 매개 변수가 추가됩니다. **[!UICONTROL thanks]** 값(자세한 내용은 다음을 참조하십시오.) [종료 활동](#end-activity)). 두 번째 분기를 사용하면 사용자가 **[!UICONTROL End]** 첫 번째 분기(및 방금 경쟁에 참가함)의 활동으로 감사 메시지를 표시합니다. 추가 URL 매개 변수 사용에 대한 자세한 내용은 다음을 참조하십시오. [facebook 애플리케이션에 설정을 전달하는 방법](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : 사용자가 이전 날짜(애플리케이션 매개 변수와 다른 애플리케이션 매개 변수)에 이미 경쟁 제품(ID)에 입력한 경우 **[!UICONTROL thanks]**)이면 이미 입력되었음을 나타내는 페이지가 표시됩니다.

### 경쟁 페이지 {#competition-page}

facebook에 연결된 표시 오류를 사이드 단계로 전환하려면 을(를) 선택해야 합니다 **[!UICONTROL Parent window]** 또는 **[!UICONTROL In the top window]** 에서 **[!UICONTROL Window]** 경쟁업체 페이지의 필드입니다.

![](assets/social_webapp_028.png)

### 액세스 제어 활동 {#access-control-activity}

다음 **[!UICONTROL Access control]** 활동을 사용하면 사용자가 경쟁에 들어갈 때 Facebook 권한 요청 페이지를 표시할 수 있습니다. 이들이 자신의 정보를 공유하는 데 동의하면 사전 로드 중에 복구됩니다. 자세한 내용은 다음을 참조하십시오. [사전 로드 활동](#pre-loading-activity).

웹 애플리케이션을 만들 때 이전에 외부 계정을 입력한 경우 [facebook 유형 웹 애플리케이션 만들기](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)) 활동을 편집할 필요가 없습니다. 없는 경우 로 이동합니다. **[!UICONTROL Application]** 필드를 작성하고 Facebook 애플리케이션에 연결된 외부 계정을 선택합니다.

![](assets/social_webapp_024.png)

### 사전 로드 활동 {#pre-loading-activity}

미리 로드하는 데 사용할 데이터 소스를 선택합니다.

* **[!UICONTROL Marketing database]** : 이 옵션을 사용하면 Adobe Campaign 데이터베이스를 통해 데이터를 미리 로드할 수 있습니다.
* **[!UICONTROL Facebook]** : 이 옵션을 사용하면 Facebook을 사용하여 데이터를 미리 로드할 수 있습니다.

![](assets/social_webapp_029.png)

**마케팅 데이터베이스**

이 옵션을 사용하면 방문자 표에 있는 프로필의 데이터를 복구할 수 있습니다. 사용자가 Facebook 애플리케이션 탭을 클릭할 때 복구된 외부 Facebook ID를 기반으로 유효성 검사가 수행됩니다. 다음에 양식을 추가하는 경우 **[!UICONTROL Pre-loading]** 활동. 데이터베이스에 정보가 들어 있는 필드가 미리 로드됩니다.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Adobe Campaign 데이터베이스를 통해 데이터를 미리 로드하는 방법에 대한 자세한 내용은 [이 섹션](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

이 옵션을 사용하면 사용자가 공유하기로 동의한 프로필 정보 중에서 저장할 Facebook 프로필 정보를 정의할 수 있습니다.

![](assets/social_webapp_025.png)

다음 **[!UICONTROL Database information]** 옵션을 사용하면 다음 데이터를 수집할 수 있습니다.

* **[!UICONTROL External ID]**: 사용자 ID
* **[!UICONTROL Gender]**: 사용자의 성별
* **[!UICONTROL Verified]** : 이 필드는 사용자에게 확인된 Facebook 계정이 있는지 여부를 지정합니다.
* **[!UICONTROL Full name]**: 사용자의 전체 이름
* **[!UICONTROL First name]**: 사용자 이름
* **[!UICONTROL Last name]**: 사용자의 성
* **[!UICONTROL Language]**: 사용자 언어

해당 상자를 선택하여 프로필 사진, 친구 목록, 이메일 주소, 생년월일, 관심사 및 위치를 수집하도록 결정할 수도 있습니다.

클릭하기 전에 **[!UICONTROL Ok]**&#x200B;에서 을(를) 확인합니다. **[!UICONTROL I agree to comply with Facebook conditions of use]** 상자.

>[!NOTE]
>
>에서 하나 이상의 상자를 선택하는 경우 **[!UICONTROL Private information]** 섹션에서 Facebook 권한 요청 화면에 이 데이터에 대한 액세스 요청이 자동으로 표시됩니다.
>
>선택한 정보를 수집하려면 사용자가 해당 정보를 공유하는 것에 동의해야 합니다.
>
>(Adobe Campaign을 통해 및 Facebook을 통해) 두 유형의 사전 로드를 원하는 경우 두 개의 사전 로드 상자를 하나씩 추가합니다.

### 활동 저장 {#save-activity}

다음 **[!UICONTROL Save]** 활동을 사용하면 이전 단계 동안 수집된 정보를 방문자 테이블에 저장할 수 있습니다.

프로필이 이미 방문자 표에 있는 경우 해당 데이터가 수집된 새 데이터로 업데이트됩니다.

프로필이 데이터베이스에 없고 Facebook 사용자의 이메일 주소가 수집된 경우 방문자 표에 방문자가 만들어집니다.

![](assets/social_webapp_026.png)

1. 에서 **[!UICONTROL Visitor creation folder]** 필드에서 프로필을 만들 폴더를 선택합니다. facebook 유형 웹 애플리케이션의 경우 기본 만들기 폴더는 다음과 같습니다 **[!UICONTROL Visitors]**.
1. 에서 **[!UICONTROL Reconciliation mode]** 필드에서 사용할 조정 모드를 선택합니다.

   * **[!UICONTROL Automatic]** : 조정은 이메일, 성, 이름 및 생년월일에 따라 수행됩니다.
   * **[!UICONTROL Manual]** : 조정 키를 하나 이상 선택하십시오.
   * **[!UICONTROL None]** : 어떠한 화해도 일어나지 않을 것이다.

1. 에서 **[!UICONTROL Mapping]** 필드에서 조정을 수행할 스키마를 선택합니다.

   >[!IMPORTANT]
   >
   >의 필드를 확인합니다 **[!UICONTROL Social networks]** 탭이 게재 매핑에 올바르게 입력됩니다. 게재 매핑은 **[!UICONTROL Administration > Campaign management > Target mappings]** 노드 아래에 있어야 합니다.

1. 조정을 위한 검색 폴더 및 새 프로필에 대한 만들기 폴더를 선택할 수 있습니다. 필드가 비어 있으면 프로필이 검색 및 매핑 스키마의 기본 폴더에서 만들어집니다.

### 종료 활동 {#end-activity}

facebook에 연결된 표시 오류를 사이드 단계로 전환하려면 다음을 확인해야 합니다 **[!UICONTROL Use an external URL]** 상자에 Facebook 애플리케이션의 URL을 입력하고 다음에 를 입력합니다 **[!UICONTROL app_data]** 매개 변수와 값을 사용하여 값을 지정할 수 있습니다. 이 값은 **[!UICONTROL Test]** 활동을 통해 사용자가 경쟁사에 참가했는지 여부를 감지하고 해당하는 경우 감사 메시지를 표시할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [활동 테스트](#test-activity).

이 예제에서 사용된 값은 **감사**.

![](assets/social_webapp_027.png)

### 방문자의 세부 사항 화면 {#details-screen-of-a-visitor}

twitter 팔로워의 경우처럼 다음을 참조하십시오. [운영 원칙](../../social/using/publishing-on-twitter.md#operating-principle)). 복구된 Facebook 프로필은 방문자 표에 저장됩니다. 방문자 목록을 표시하려면 **[!UICONTROL Profiles and Targets > Visitors]** 노드 아래에 있어야 합니다.

프로필 정보를 공유하는 데 동의한 각 Facebook 잠재 고객이 방문자 목록에 추가됩니다. 만약 **[!UICONTROL Friends]** 확인란이 선택되어 있습니다. **[!UICONTROL Pre-load]** 활동(참조: [사전 로드 활동](#pre-loading-activity)), 친구도 추가됩니다.

![](assets/social_webapp_037.png)

에서 **[!UICONTROL Summary]** 방문자 세부 사항 창의 섹션에는 두 가지 가능한 상태가 있습니다 **[!UICONTROL New Contact]** 표시기:

![](assets/social_webapp_038.png)

녹색 확인 표시가 표시되면 방문자가 수신자와 조정되지 않은 것입니다. 이 경우 수신자 목록에 새 프로필이 만들어집니다.

![](assets/social_webapp_039.png)

빨간색 십자는 방문자가 수신자와 조정되었음을 의미합니다. 오른쪽 돋보기를 클릭할 수 있습니다 **[!UICONTROL Recipient]** 일치하는 수신자를 표시하는 필드입니다.

![](assets/social_webapp_040.png)

해당하는 경우 수신자의 세부 사항 창으로 이동하여 일치하는 방문자를 표시합니다. 을(를) 선택합니다 **[!UICONTROL Others]** 탭을 클릭한 다음, **[!UICONTROL Web identities]** 섹션을 참조하십시오.

![](assets/social_webapp_041.png)

다음 **[!UICONTROL Activities]** 방문자 세부 사항 페이지의 화면에는 다음 정보가 포함됩니다.

* &quot;Open Graph&quot; 유형 팬 활동: 음악 재생, 비디오 시청, 문서 읽기 및 설치된 애플리케이션(Deezer, Spotify, Dailymotion, Yahoo News 등)

   ![](assets/social_facebook_activities.png)

* Adobe Campaign에서 보낸 게재 후 팬이 추가한 &quot;좋아요&quot; 및 주석
* 팬이 좋아하는 페이지
* 팬에서 체크 인

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Adobe Campaign에서 팬의 체크 인을 수집하려면 **[!UICONTROL Subscribe]** 단추를 클릭합니다. 자세한 내용은 [외부 계정 구성](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## facebook 프로필 데이터를 사용하여 양식을 미리 로드하는 방법 {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

다음 **[!UICONTROL Social Marketing]** 또한 Facebook 프로필 정보를 사용하여 필드를 미리 로드할 수 있도록 양식에 단추를 추가할 수도 있습니다. 이 옵션은 모든 웹 응용 프로그램 템플릿에서 사용할 수 있습니다(**[!UICONTROL Page]** 유형 활동)에 대해서는 [이 섹션](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>이 기능을 사용하기 전에 Facebook 애플리케이션 및 **[!UICONTROL Facebook Connect]** 외부 계정을 입력합니다. 자세한 내용은 [외부 계정 구성](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

**facebook 프로필에서 가져온 데이터로 양식 필드를 미리 로드합니다**

웹 양식을 만들고 사용자가 양식 페이지에 상호 작용이 없는 요소를 포함합니다. 이미지, HTML 컨텐츠, 가로 막대 또는 하이퍼텍스트 링크와 같은 정적 요소입니다. 웹 양식의 정적 요소에 대해 자세히 알아보기 [이 페이지](../../web/using/static-elements-in-a-web-form.md).

정적 요소를 삽입할 때 **[!UICONTROL Preload with Facebook]** 옵션을 사용하면 Facebook 프로필 정보를 사용하여 필드를 미리 로드하기 위해 양식에 단추를 삽입할 수 있습니다.

![](assets/web_social_webapp_037.png)

사용자가 를 클릭할 때 **[!UICONTROL Fill in automatically]** 버튼을 클릭하면 Facebook 권한 요청 창이 열립니다.

![](assets/web_social_webapp_029.png)

>[!NOTE]
>
>외부 계정을 구성할 때 확장 권한 목록을 변경할 수 있습니다. 확장 권한이 구성되지 않은 경우 Facebook은 기본적으로 기본 프로필 정보를 전달합니다.\
>확장 권한 목록 및 해당 구문을 보려면, [facebook 설명서 을 참조하십시오](https://developers.facebook.com/docs/reference/api/permissions).

사용자가 정보를 공유하기로 동의하면 양식의 필드가 미리 로드됩니다.

![](assets/web_social_webapp_030.png)

이 사용 사례에서는 다음 요소로 구성된 웹 애플리케이션을 만들었습니다.

* 양식이 포함된 페이지
* **[!UICONTROL Record]** 활동
* an **[!UICONTROL End]** 활동

![](assets/social_webapp_031.png)

미리 로드 단추를 추가하려면 다음 단계를 수행합니다.

1. 양식을 만듭니다.

   ![](assets/social_webapp_032.png)

1. 양식의 필드와 동일한 수준으로 이동하여 링크를 추가합니다.

   ![](assets/social_webapp_033.png)

1. 레이블을 입력하고 **[!UICONTROL Button]** 유형.

   ![](assets/social_webapp_034.png)

1. 로 이동합니다. **[!UICONTROL Action]** 필드 및 선택 **[!UICONTROL Preload with Facebook]**.

   ![](assets/social_webapp_035.png)

1. 로 이동합니다. **[!UICONTROL Application]** 필드를 선택하고 **[!UICONTROL Facebook Connect]** 이전에 만든 외부 계정을 입력합니다. 자세한 정보는 이 [페이지](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)를 참조하십시오.

   ![](assets/social_webapp_036.png)


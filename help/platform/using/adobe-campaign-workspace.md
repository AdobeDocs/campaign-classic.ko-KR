---
solution: Campaign Classic
product: campaign
title: Adobe Campaign 작업 영역
description: 캠페인 작업 영역을 사용하고 사용자 지정하는 방법 학습
feature: 개요
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 4%

---

# Adobe Campaign 작업 영역{#adobe-campaign-workspace}

## Adobe Campaign 인터페이스 탐색 {#about-adobe-campaign-interface}

데이터베이스에 연결되면 대시보드인 Adobe Campaign 홈 페이지에 액세스합니다.이 단축키는 설치 및 일반 플랫폼 구성에 따라 기능에 액세스할 수 있는 링크와 단축키로 구성되어 있습니다.

홈 페이지의 중앙 섹션에서 링크를 사용하여 Campaign 온라인 문서 포털, 포럼 및 지원 웹 사이트에 액세스할 수 있습니다.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ 비디오에서 캠페인 작업 영역 살펴보기](#video)

>[!NOTE]
>
>인스턴스에서 사용할 수 있는 Adobe Campaign 기능은 설치된 모듈 및 추가 기능에 따라 다릅니다. 사용 권한 및 특정 구성에 따라 일부 옵션을 사용할 수도 없습니다.
>
>모듈 또는 Add-On을 설치하기 전에 사용권 계약을 확인하거나 Adobe 계정 담당자에게 문의하십시오.

### 콘솔 및 웹 액세스 {#console-and-web-access}

Adobe Campaign 플랫폼은 콘솔 또는 인터넷 브라우저를 통해 액세스할 수 있습니다.

웹 액세스는 콘솔과 비슷하지만 기능 세트가 줄어든 인터페이스를 제공합니다.

예를 들어, 지정된 연산자에 대해 캠페인은 콘솔에 다음 옵션이 표시됩니다.

![](assets/operation_from_console.png)

웹 액세스가 가능한 반면 이 옵션은 주로 보기를 활성화합니다.

![](assets/operation_from_web.png)

### 언어 {#languages}

Adobe Campaign Classic 인스턴스를 설치할 때 해당 언어가 선택됩니다.

![](assets/language.png)

5개 언어 중에서 선택할 수 있습니다.

* 영어(영국)
* 영어(미국)
* 프랑스어
* 독일어
* 일본어

Adobe Campaign Classic 인스턴스에 대해 선택한 언어는 날짜 및 시간 형식에 영향을 줄 수 있습니다. 자세한 정보는 이 [섹션](../../platform/using/adobe-campaign-workspace.md#date-and-time)을 참조하십시오.

인스턴스를 만드는 방법에 대한 자세한 내용은 이 [page](../../installation/using/creating-an-instance-and-logging-on.md)을 참조하십시오.

>[!CAUTION]
>
>인스턴스를 만든 후에는 언어를 변경할 수 없습니다.

## 탐색 기본 사항 {#navigation-basics}

### 검색 페이지 {#browsing-pages}

플랫폼의 다양한 기능이 핵심 기능으로 분류됩니다.인터페이스의 상단 섹션에 있는 링크를 사용하여 액세스할 수 있습니다.

![](assets/overview_home.png)

액세스할 수 있는 핵심 기능 목록은 설치된 패키지 및 추가 기능과 액세스 권한에 따라 다릅니다.

각 기능에는 작업 관련 요구 사항 및 사용 컨텍스트에 따라 일련의 기능이 포함되어 있습니다. 예를 들어 **[!UICONTROL Profiles and targets]** 링크는 수신자 목록, 구독 서비스, 기존 타깃팅 워크플로우 및 이러한 요소를 만드는 단축키로 연결됩니다.

목록은 **[!UICONTROL Profiles and Targets]** 인터페이스의 왼쪽 섹션에 있는 **[!UICONTROL Lists]** 링크를 통해 사용할 수 있습니다.

![](assets/recipient_list_overview.png)

### 탭 {#using-tabs} 사용

* 핵심 기능 또는 링크를 클릭하면 관련 페이지가 현재 페이지로 바뀝니다. 이전 페이지로 돌아가려면 도구 모음에서 **[!UICONTROL Back]** 단추를 클릭합니다. 홈 페이지로 돌아가려면 **[!UICONTROL Home]** 단추를 클릭합니다.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 메뉴 또는 표시 화면 단축키(웹 애플리케이션, 프로그램, 전달, 보고서 등)의 경우 일치하는 페이지가 다른 탭에 표시됩니다. 탭을 사용하여 한 페이지에서 다른 페이지로 이동할 수 있습니다.

   ![](assets/d_ncs_user_interface_tabs.png)

### {#creating-an-element} 요소 만들기

각 핵심 기능 섹션에서 사용 가능한 요소 간을 탐색할 수 있습니다. 이렇게 하려면 **[!UICONTROL Browsing]** 섹션의 단축키를 사용합니다. **[!UICONTROL Other choices]** 링크를 사용하면 환경에 상관없이 다른 모든 페이지에 액세스할 수 있습니다.

새 요소(전달, 웹 애플리케이션, 워크플로우 등)를 만들 수 있습니다. 화면 왼쪽의 **[!UICONTROL Create]** 섹션에 있는 단축키를 사용합니다. 목록 위의 **[!UICONTROL Create]** 단추를 사용하여 목록에 새 요소를 추가합니다.

예를 들어 배달 페이지에서 **[!UICONTROL Create]** 단추를 사용하여 새 배달을 만듭니다.

![](assets/d_ncs_user_interface_tab_add_del.png)


## 형식 및 단위 {#formats-and-units}

### 날짜 및 시간 {#date-and-time}

Adobe Campaign Classic 인스턴스의 언어는 날짜 및 시간 형식에 영향을 줍니다.

Campaign을 설치할 때 언어가 선택되고 이후에는 변경할 수 없습니다. 다음을 선택할 수 있습니다.영어(미국), 영어(EN), 프랑스어, 독일어 또는 일본어 자세한 정보는 이 [페이지](../../installation/using/creating-an-instance-and-logging-on.md)를 참조하십시오.

미국 영어와 영국 영어의 주요 차이점은 다음과 같습니다.

<table> 
 <thead> 
  <tr> 
   <th> 형식<br /> </th> 
   <th> 영어(미국)<br /> </th> 
   <th> 영어(EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 날짜<br /> </td> 
   <td> 주 시작 날짜<br /> </td> 
   <td> 주 시작 날짜<br /> </td> 
  </tr> 
  <tr> 
   <td> 짧은 날짜<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>예:09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>예:25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> <br /> 시간이 있는 짧은 날짜 </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>예:09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>예:25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 열거형 {#add-values-in-an-enumeration}에 값 추가

드롭다운 목록이 있는 입력 필드를 사용하여 드롭다운 목록에 옵션으로 제공되는 열거형 값을 입력할 수 있습니다. 열거형 값은 저장된 후 드롭다운 목록에서 사용할 수 있습니다. 예를 들어 수신자 프로필의 **[!UICONTROL General]** 탭의 **[!UICONTROL City]** 필드에서 London을 입력할 수 있습니다. Enter 키를 눌러 이 값을 확인하면 필드와 연관된 열거형에 이 값을 저장할 것인지 묻는 메시지가 표시됩니다.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

**[!UICONTROL Yes]**&#x200B;을 클릭하면 관련 필드의 콤보 상자에서 이 값을 사용할 수 있습니다(이 경우:**[!UICONTROL London]**).

>[!NOTE]
>
>열거형(&#39;항목별 목록&#39;이라고도 함)은 관리자가 **[!UICONTROL Administration > Platform > Enumerations]** 섹션을 통해 관리합니다. 자세한 내용은 [열거형 관리](../../platform/using/managing-enumerations.md)를 참조하십시오.

### 기본 단위 {#default-units}

기간을 설명하는 필드(예: 배달 리소스의 유효성 기간, 작업의 승인 기한 등)에서 이 값은 다음 **units**&#x200B;으로 표시될 수 있습니다.

* **[!UICONTROL s]** 몇 초 동안
* **[!UICONTROL mn]** 몇 분 동안
* **[!UICONTROL h]** 몇 시간 동안
* **[!UICONTROL d]** 을 참조하십시오.

![](assets/enter_unit_sample.png)

## 자습서 비디오 {#video}

이 비디오는 Campaign Classic 작업 영역을 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.

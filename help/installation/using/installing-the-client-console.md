---
solution: Campaign Classic
product: campaign
title: 클라이언트 콘솔 설치
description: 클라이언트 콘솔 설치 방법 알아보기
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 6%

---


# 캠페인 클라이언트 콘솔 설치{#installing-the-client-console}

캠페인 클라이언트 콘솔은 캠페인 응용 프로그램 서버에 연결할 수 있는 리치 클라이언트입니다.

시작하기 전에 캠페인 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 확인하고 캠페인 서버 URL과 사용자 자격 증명을 가져와야 합니다.

>[!CAUTION]
>
>캠페인 클라이언트 콘솔 및 캠페인 애플리케이션 서버는 동일한 제품 버전에서 실행되어야 합니다. Adobe에서는 동일한 제품 빌드를 사용하는 것이 좋습니다.

![](assets/do-not-localize/how-to-video.png) 비디오에서 Adobe Campaign 클라이언트를 설치하고 설정하는 방법을  [알아봅니다.](#video)

## 콘솔 {#download-the-client-console} 다운로드

Adobe Campaign 클라이언트 콘솔을 다운로드하여 설치하려면 아래 단계를 수행하십시오.

1. 웹 브라우저를 열고 다음 주소에서 콘솔을 다운로드합니다.

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. ID 창에서 로그인 및 암호를 입력합니다.

   ![](assets/s_ncs_install_setup_download01.png)

   필요한 경우 인스턴스를 만드는 동안 정의된 내부 계정의 자격 증명을 사용합니다.

1. 설치 페이지에서 **[!UICONTROL Download]** 링크를 클릭합니다.
1. 클라이언트 설정 파일을 다운로드하고 저장합니다.
1. Windows의 컴퓨터에서 다운로드한 파일을 실행합니다.설치가 시작됩니다. 클라이언트 콘솔의 기본 설치 경로는 Adobe Campaign 버전에 따라 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX 클라이언트**&#x200B;입니다. 여기서 &#39;X&#39;는 &#39;6&#39; 또는 &#39;7&#39;입니다.

>[!NOTE]
>
>Windows의 경우 Windows 서버의 `[INSTALL]/bin` 디렉토리에서 직접 **nlclient.exe** 파일을 시작할 수 있습니다. 여기서 `[INSTALL]`은 Adobe Campaign 설치 폴더의 액세스 경로입니다.

## 연결 만들기{#create-the-connection}

클라이언트 콘솔이 설치되면 아래 절차에 따라 응용 프로그램 서버에 연결을 만듭니다.

1. **Adobe Campaign** 프로그램 그룹의 Windows **[!UICONTROL Start]** 메뉴에서 콘솔을 시작합니다.

1. 자격 증명 필드의 오른쪽 상단에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

   ![](assets/s_ncs_install_define_connection_01.png)

1. **[!UICONTROL Add > Connection]**&#x200B;을 클릭하고 Adobe Campaign 응용 프로그램 서버의 레이블과 URL을 입력합니다.

   ![](assets/s_ncs_install_define_connection_02.png)

1. URL을 통해 Adobe Campaign 응용 프로그램 서버에 대한 연결을 지정합니다. 컴퓨터의 DNS 또는 별칭 또는 IP 주소를 사용합니다.

   예를 들어 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 유형 URL을 사용할 수 있습니다.

1. Adobe IMS가 조직에 맞게 구성된 경우 **[!UICONTROL Connect with an Adobe ID]** 옵션을 선택합니다.

1. 설정을 저장하려면 **[!UICONTROL Ok]**&#x200B;을 클릭합니다.

예를 들어 테스트, 스테이지 및 프로덕션 환경에 연결하는 데 필요한 만큼 연결을 추가할 수 있습니다.

>[!NOTE]
>
>**[!UICONTROL Add]** 단추를 사용하면 **[!UICONTROL folders]**&#x200B;을(를) 만들어 모든 연결을 구성할 수 있습니다. 각 연결을 하나의 폴더로 드래그하여 놓으면 됩니다.

## Adobe Campaign에 로그온

기존 인스턴스에 로그온하려면 아래 단계를 수행하십시오.

1. **Adobe Campaign** 프로그램 그룹의 Windows **[!UICONTROL Start]** 메뉴에서 콘솔을 시작합니다.

1. 자격 증명 필드의 오른쪽 상단에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

1. 로그인해야 하는 캠페인 인스턴스를 선택합니다.

1. 클릭 **[!UICONTROL Ok]**

1. 사용자 로그인 자격 증명을 입력하고 **[!UICONTROL Log in]**

**관련 항목**

* [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).
* [호환성 매트릭스](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## 자습서 비디오

이 비디오에서는 Adobe Campaign 클라이언트를 설치하고 설정하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.

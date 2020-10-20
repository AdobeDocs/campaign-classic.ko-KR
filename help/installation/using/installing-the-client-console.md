---
title: 클라이언트 콘솔 설치
description: 클라이언트 콘솔 설치 방법 살펴보기
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: bdc09e1b6e037e1b21573b8624a947e30f8ad1fc
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 5%

---


# 캠페인 클라이언트 콘솔 설치{#installing-the-client-console}

캠페인 클라이언트 콘솔은 캠페인 응용 프로그램 서버에 연결할 수 있는 리치 클라이언트입니다.

시작하기 전에 캠페인 [호환성 매트릭스를](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)확인하고 캠페인 서버 URL과 사용자 자격 증명을 구해야 합니다.

>[!CAUTION]
>
>캠페인 클라이언트 콘솔 및 캠페인 애플리케이션 서버는 동일한 제품 버전에서 실행해야 합니다. Adobe은 동일한 제품 빌드를 사용하는 것도 좋습니다.

## 콘솔 다운로드{#download-the-client-console}

Adobe Campaign 클라이언트 콘솔을 다운로드하여 설치하려면 아래 단계를 수행하십시오.

1. 웹 브라우저를 열고 다음 주소에서 콘솔을 다운로드합니다.

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. 식별 창에서 로그인 및 암호를 입력합니다.

   ![](assets/s_ncs_install_setup_download01.png)

   필요한 경우 인스턴스 생성 중에 정의된 내부 계정의 자격 증명을 사용합니다.

1. 설치 페이지에서 **[!UICONTROL Download]** 링크를 클릭합니다.
1. 클라이언트 설치 파일을 다운로드하고 저장합니다.
1. Windows의 컴퓨터에서 다운로드한 파일을 실행합니다.설치가 시작됩니다. 클라이언트 콘솔의 기본 설치 경로는 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX 클라이언트**(여기서 &#39;X&#39;는 &#39;6&#39; 또는 &#39;7&#39;입니다.

>[!NOTE]
>
>Windows에서는 Windows 서버의 **디렉토리에서 직접** nlclient.exe `[INSTALL]/bin` 파일을 `[INSTALL]` 시작할 수 있습니다. 여기서는 Adobe Campaign 설치 폴더의 액세스 경로입니다.

## 연결 만들기{#create-the-connection}

클라이언트 콘솔이 설치되면 아래 절차에 따라 응용 프로그램 서버에 연결을 만듭니다.

1. Windows 메뉴의 **[!UICONTROL Start]** Adobe Campaign **** 프로그램 그룹에서 콘솔을 시작합니다.

1. 자격 증명 필드의 오른쪽 상단에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

   ![](assets/s_ncs_install_define_connection_01.png)

1. 을 **[!UICONTROL Add > Connection]** 클릭하고 Adobe Campaign 응용 프로그램 서버의 레이블과 URL을 입력합니다.

   ![](assets/s_ncs_install_define_connection_02.png)

1. URL을 통해 Adobe Campaign 응용 프로그램 서버에 대한 연결을 지정합니다. 시스템의 DNS 또는 별칭 또는 IP 주소를 사용합니다.

   예를 들어 유형 URL을 사용할 수 [`https://<machine>.<domain>.com`](https://machine) 있습니다.

1. 조직에 대해 Adobe IMS가 구성된 경우 옵션을 선택하십시오 **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

예를 들어 테스트, 스테이지 및 프로덕션 환경에 연결하는 데 필요한 만큼 연결을 추가할 수 있습니다.

>[!NOTE]
>
>이 **[!UICONTROL Add]** 단추를 사용하면 모든 연결을 구성할 **[!UICONTROL folders]** 수 있습니다. 각 연결을 하나의 폴더로 드래그하여 놓으면 됩니다.


## Adobe Campaign에 로그온

기존 인스턴스에 로그인하려면 아래 단계를 수행하십시오.

1. Windows 메뉴의 **[!UICONTROL Start]** Adobe Campaign **** 프로그램 그룹에서 콘솔을 시작합니다.

1. 자격 증명 필드의 오른쪽 상단에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

1. 로그인해야 하는 캠페인 인스턴스를 선택합니다.

1. 클릭 **[!UICONTROL Ok]**

1. 사용자 로그인 자격 증명을 입력하고 **[!UICONTROL Log in]**

**관련 항목**

* [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).
* [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)
* [Adobe Campaign 클라이언트](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) 설치 및 설정(비디오)

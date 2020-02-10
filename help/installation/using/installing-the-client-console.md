---
title: 클라이언트 콘솔 설치
seo-title: 클라이언트 콘솔 설치
description: 클라이언트 콘솔 설치
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 클라이언트 콘솔 설치{#installing-the-client-console}

Adobe Campaign 콘솔 설치 절차는 아래에 자세히 설명되어 있습니다.

Adobe Campaign 콘솔을 설치하기 전에 호환성 매트릭스에 나열된 사전 요구 사항을 [확인하십시오](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Adobe Campaign 콘솔을 설치하려면 다음 단계를 수행하십시오.

1. 웹 브라우저를 열고 다음 주소에서 콘솔을 다운로드합니다.

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. ID 창에서 로그인 및 암호를 입력합니다.

   ![](assets/s_ncs_install_setup_download01.png)

   필요한 경우 인스턴스 생성 중에 정의된 내부 계정의 자격 증명을 사용합니다.

1. 설치 페이지에서 **[!UICONTROL Download]** 링크를 클릭합니다.
1. 클라이언트 설정 파일을 다운로드하고 저장합니다.
1. Windows의 컴퓨터에서 다운로드한 파일을 실행합니다.설치가 시작됩니다. 클라이언트 콘솔의 기본 설치 경로는 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client이며**, 여기서 &#39;X&#39;는 &#39;6&#39; 또는 &#39;7&#39;입니다.
1. 설치 프로그램이 완료되면 Windows **[!UICONTROL Start]** 메뉴(Adobe Campaign **프로그램 그룹의** )에서 콘솔을 시작합니다.

>[!NOTE]
>
>Windows에서는 Windows 서버의 **디렉토리에서 직접 nlclient.exe** 파일을 시작할 수 있습니다. 여기서 `[INSTALL]/bin` `[INSTALL]` nlclient.exe 파일은 Adobe Campaign 설치 폴더의 액세스 경로입니다.\
>새 연결을 만들려면 인스턴스 [만들기 및 로그인을](../../installation/using/creating-an-instance-and-logging-on.md)참조하십시오.


---
product: campaign
title: 클라이언트 콘솔 설치
description: 클라이언트 콘솔을 설치하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 3%

---

# Campaign 클라이언트 콘솔 설치 및 업데이트{#installing-the-client-console}



Campaign 클라이언트 콘솔은 Campaign 애플리케이션 서버에 연결할 수 있는 리치 클라이언트입니다.

클라이언트 콘솔 설치를 시작하기 전에 다음을 수행해야 합니다.

* 에서 Adobe Campaign과의 시스템 및 도구 호환성 확인 [호환성 매트릭스](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Campaign 서버 URL 가져오기
* 사용자 자격 증명 가져오기
* 시스템에 Microsoft Edge Webview2 런타임이 설치되어 있습니다(Campaign Classic 7.3 빌드 버전). [자세히 알아보기](#webview)

클라이언트 콘솔을 설치하거나 업데이트하는 프로세스는 Adobe Campaign Classic 구현에 따라 다릅니다.
구현에 필요한 사항을 이해하려면 아래 세부 사항을 검토하십시오.

![](assets/do-not-localize/how-to-video.png) 에서 Adobe Campaign 클라이언트를 설치하고 설정하는 방법을 알아봅니다. [비디오](#video)

>[!CAUTION]
>
>Campaign 클라이언트 콘솔 및 Campaign 애플리케이션 서버를 실행해야 합니다. **동일한 제품 버전**. Adobe은 또한 **동일한 제품 빌드**. 에서 Campaign 클라이언트 및 서버 버전을 확인하는 방법을 알아봅니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Microsoft Edge Webview2 런타임 설치 {#webview}

Campaign Classic 7.3 빌드 버전에서 모든 콘솔 설치에 Microsoft Edge Webview 2 런타임을 설치해야 합니다.

Web View는 기본적으로 Windows 11 운영 체제의 일부로 설치됩니다. 시스템에 아직 없으면 Campaign Classic 콘솔 설치 관리자에서 다운로드할 것인지 묻는 메시지가 표시됩니다. [Microsoft 개발자 웹 사이트](http://www.adobe.com/go/acc-ms-webview2-runtime-download_kr). Microsoft에서 해당 지원이 더 이상 사용되지 않으므로 다운로드 링크가 Internet Explorer 11 브라우저에서 작동하지 않습니다. 다른 브라우저를 사용하여 링크에 액세스해야 합니다.

## Adobe 호스팅 구현 {#hosted-customers}

호스팅된 고객은 클라이언트 콘솔을 설치하거나 업데이트하는 두 가지 옵션이 있습니다.

1. Adobe은 직접 배포할 수 있습니다. 콘솔이 업데이트되면 팝업 창에서 최신 클라이언트 콘솔 버전을 다운로드하라는 메시지가 표시됩니다.

1. 에서 클라이언트 콘솔로 다운로드할 수 있습니다. [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)

   **업데이트를 완료하려면 관리자 액세스 권한이 필요합니다. 사용자에게 관리자 권한이 없는 경우 시스템 관리자가 모든 클라이언트 콘솔에 배포해야 합니다**

## 하이브리드 및 온-프레미스 구현 {#hybrid-onprem-customers}

Adobe Campaign 사용자가 생성 및 구성한 인스턴스에 로그온할 수 있으려면 클라이언트 콘솔을 사용해야 합니다.

### 사용자가 콘솔을 사용할 수 있도록 설정 {#make-console-available}

Adobe Campaign 애플리케이션 서버(nlserver 웹)를 시작하는 데 사용되는 컴퓨터가 클라이언트 콘솔에서 사용자 연결을 받으면 HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트의 설치 프로그램을 사용할 수 있도록 구성할 수 있습니다. 새 버전의 클라이언트 콘솔을 사용할 수 있을 때마다 사용자는 클라이언트 콘솔을 시작할 때 클라이언트 콘솔을 다운로드하도록 초대됩니다.

이렇게 하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 선택합니다.

   이 파일을 setup-client-7.X.XXXX.exe(v7의 경우) 또는 setup-client-6.X.XXXX.exe(v6.1의 경우)라고 합니다. 여기서 X는 Adobe Campaign의 하위 버전이고 XXXX는 빌드 번호입니다.

1. 이 패키지를 복사하여 /datakit/nl/eng/jsp 아래의 Adobe Campaign 설치 폴더(하이브리드 설치용 마케팅 서버)에 붙여넣습니다.

1. Adobe Campaign 서버를 시작합니다.


### 더 이상 이 질문을 하지 않음 옵션

Adobe은 이 옵션을 종료하는 것을 권장합니다. **[!UICONTROL No longer ask this question]** 새 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 알림 메시지가 표시되게 하려면 선택을 취소합니다.  이 옵션을 선택하면 사용 가능한 새 버전이 표시되지 않습니다.

If **[!UICONTROL No longer ask this question]**  이(가) 선택되었으므로 이 프롬프트를 재설정할 수 있습니다. Windows 레지스트리를 편집하는 데 익숙한 시스템 관리자만 다음과 같이 변경해야 합니다.

1. 다음을 사용하여 레지스트리 편집기 열기 **regedit** 다음에서 명령 **[!UICONTROL Start > Run]** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 삭제 **confAdvisedUpgrade** 레지스트리 편집기를 시작하고 닫습니다.

>[!NOTE]
>
>기존 구현에 업데이트된 콘솔을 적용하는 경우 사용자는 클라이언트 콘솔을 업데이트하라는 메시지를 자동으로 수신하게 됩니다. Campaign을 처음 구현하는 경우 사용자가 콘솔을 다운로드해야 합니다. 두 옵션에 대한 자세한 내용은 아래를 참조하십시오

### 기존 구현을 위한 콘솔 업데이트{#update-the-client-console}

Campaign 서버 폴더에서 콘솔을 사용할 수 있게 되면 팝업 창에서 최신 클라이언트 콘솔 버전을 다운로드하라는 메시지가 표시됩니다.

**업데이트를 완료하려면 관리자 액세스 권한이 필요합니다. 사용자에게 관리자 권한이 없는 경우 시스템 관리자가 모든 클라이언트 콘솔에 배포해야 합니다**


### 새 구현을 위해 콘솔 다운로드{#download-the-client-console}

사용자는 이제 아래 단계에 따라 콘솔을 다운로드하여 설치해야 합니다.

1. 웹 브라우저를 열고 다음 주소에서 콘솔을 다운로드합니다.

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. ID 창에서 로그인 및 암호를 입력합니다.

   ![](assets/s_ncs_install_setup_download01.png)

   필요한 경우 인스턴스를 만드는 동안 정의된 내부 계정의 자격 증명을 사용합니다.

1. 다음을 클릭합니다. **[!UICONTROL Download]** 설치 페이지의 링크입니다.
1. 클라이언트 설치 파일을 다운로드하여 저장합니다.
1. Windows의 컴퓨터에서 다운로드한 파일을 실행합니다. 설치가 시작됩니다. 클라이언트 콘솔의 기본 설치 경로는 다음과 같습니다. **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX 클라이언트**, 여기서 &#39;X&#39;는 Adobe Campaign 버전에 따라 &#39;6&#39; 또는 &#39;7&#39;입니다.

### 연결 만들기 - 처음 사용자만 해당{#create-the-connection}

클라이언트 콘솔이 설치되면 아래 단계에 따라 애플리케이션 서버에 대한 연결을 만듭니다.

1. Windows에서 콘솔 시작 **[!UICONTROL Start]** 메뉴, **Adobe Campaign** 프로그램 그룹.

1. 자격 증명 필드의 오른쪽 상단 모서리에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

   ![](assets/s_ncs_install_define_connection_01.png)

1. 클릭 **[!UICONTROL Add > Connection]** 및 Adobe Campaign 애플리케이션 서버의 레이블과 URL을 입력합니다.

   ![](assets/s_ncs_install_define_connection_02.png)

1. URL을 통해 Adobe Campaign 애플리케이션 서버에 대한 연결을 지정합니다. 컴퓨터의 DNS, 별칭 또는 IP 주소를 사용합니다.

   예를 들어 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) url을 입력합니다.

1. Adobe IMS가 조직에 대해 구성된 경우 옵션을 선택합니다 **[!UICONTROL Connect with an Adobe ID]**

1. 클릭 **[!UICONTROL Ok]** 설정을 저장합니다.

예를 들어 테스트, 스테이지 및 프로덕션 환경에 연결하는 데 필요한 만큼 연결을 추가할 수 있습니다.

>[!NOTE]
>
>다음 **[!UICONTROL Add]** 버튼을 사용하여 다음을 만들 수 있습니다. **[!UICONTROL folders]** 모든 연결을 구성합니다. 각 연결을 폴더로 끌어다 놓기만 하면 됩니다.

### Adobe Campaign에 로그온

기존 인스턴스에 로그온하려면 아래 단계를 수행합니다.

1. Windows에서 콘솔 시작 **[!UICONTROL Start]** 메뉴, **Adobe Campaign** 프로그램 그룹.

1. 자격 증명 필드의 오른쪽 상단 모서리에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다.

1. 로그인해야 하는 Campaign 인스턴스를 선택합니다.

1. 클릭 **[!UICONTROL Ok]**

1. 사용자 로그인 자격 증명을 입력하고 **[!UICONTROL Log in]**

>[!NOTE]
>
>Campaign classic 7.3 빌드 버전의 경우 Adobe Campaign 클라이언트 콘솔은 프록시 인증 중에 두 번 프록시 자격 증명을 요청할 수 있습니다. 이는 Microsoft Edge Webview2가 Internet Explorer와 달리 캐시/암호 저장소에 프록시 자격 증명을 저장하지 않기 때문입니다.

**관련 항목**

* [인스턴스 만들기 및 로그온](../../installation/using/creating-an-instance-and-logging-on.md).
* [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)

## 튜토리얼 비디오

이 비디오는 Adobe Campaign 클라이언트를 설치하고 설정하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).

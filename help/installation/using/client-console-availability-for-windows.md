---
title: Windows용 클라이언트 콘솔 가용성
seo-title: Windows용 클라이언트 콘솔 가용성
description: Windows용 클라이언트 콘솔 가용성
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Windows용 클라이언트 콘솔 가용성{#client-console-availability-for-windows}

Adobe Campaign 사용자가 만들고 구성한 인스턴스에 로그온하려면 클라이언트 콘솔을 사용해야 합니다.

Adobe Campaign 응용 프로그램 서버(**nlserver 웹**)를 시작하는 데 사용된 컴퓨터가 클라이언트 콘솔에서 사용자 연결을 받으면 HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트에 대한 설정 프로그램을 사용할 수 있도록 구성할 수 있습니다.

이렇게 하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 복구합니다.

   이 파일은 v7 `setup-client-7.X.XXXX.exe` 또는 v6.1 `setup-client-6.X.XXXX.exe` 에 대해 호출됩니다. 여기서 `X` 은 Adobe Campaign의 하위 버전이며 빌드 `XXXX` 번호입니다.

1. 이 패키지를 복사하여 /datakit/nl/eng/jsp 아래의 **Adobe Campaign 설치 폴더에 붙여 넣습니다**.
1. Adobe Campaign 서버를 시작합니다.

최종 사용자는 다음 URL 덕분에 웹 브라우저를 통해 콘솔 설치 프로그램을 다운로드할 수 있습니다.

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

이 페이지에는 응용 프로그램에 정의된 로그인 및 암호가 필요합니다.

콘솔을 다운로드하고 설치하려면 클라이언트 콘솔 [설치를 참조하십시오](../../installation/using/installing-the-client-console.md).

클라이언트 콘솔의 새 버전을 사용할 수 있을 때마다 다운로드하도록 초대됩니다.

>[!NOTE]
>
>표시되는 프롬프트에서 옵션을 선택하지 **[!UICONTROL No longer ask this question]** 않은 상태로 두면 새로운 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 경고가 표시되는지 확인할 수 있습니다.\
>이 옵션을 선택하고 최신 버전을 다운로드하지 않도록 선택하면 사용 가능한 새 버전에 대해 다른 사용자에게 통보되지 않습니다.

이 프롬프트를 재설정하려면 아래 절차를 따르십시오(레지스트리를 편집하는 데 익숙한 시스템 관리자만 이러한 변경을 수행해야 함).

1. **** **[!UICONTROL Start > Run]** 메뉴에서 regedit 명령을 사용하여 레지스트리 편집기를 엽니다.
1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. confAdvisedUpgrade **항목을** 삭제하고 레지스트리 편집기를 닫습니다.


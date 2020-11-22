---
solution: Campaign Classic
product: campaign
title: Windows용 클라이언트 콘솔 가용성
description: Windows용 클라이언트 콘솔 가용성
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# Windows용 클라이언트 콘솔 가용성{#client-console-availability-for-windows}

Adobe Campaign 사용자가 만들고 구성한 인스턴스에 로그온하려면 클라이언트 콘솔을 사용해야 합니다.

Adobe Campaign 응용 프로그램 서버를 시작하는 데 사용된 컴퓨터(**nlserver 웹**)가 클라이언트 콘솔에서 사용자 연결을 수신하는 경우, HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트에 대한 설정 프로그램을 사용할 수 있도록 구성할 수 있습니다.

이렇게 하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 복구합니다.

   이 파일 `setup-client-7.X.XXXX.exe` 은 v7 또는 v6.1 `setup-client-6.X.XXXX.exe` 에 대해 호출됩니다. 여기서 `X` 는 Adobe Campaign의 하위 버전이며 빌드 번호 `XXXX` 입니다.

1. 이 패키지를 복사하여 Adobe Campaign 설치 폴더의 /datakit/nl/eng/jsp **에 붙여 넣습니다**.
1. Adobe Campaign 서버를 시작합니다.

최종 사용자는 다음 URL 덕분에 웹 브라우저를 통해 콘솔 설치 프로그램을 다운로드할 수 있습니다.

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

이 페이지에는 응용 프로그램에 정의된 로그인 및 암호가 필요합니다.

콘솔을 다운로드 및 설치하려면 클라이언트 콘솔 [설치를 참조하십시오](../../installation/using/installing-the-client-console.md).

클라이언트 콘솔의 새 버전을 사용할 수 있을 때마다 다운로드하도록 초대됩니다.

>[!NOTE]
>
>표시되는 프롬프트에서 옵션을 선택하지 않은 상태로 두면 새로운 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 경고가 표시되는지 확인할 **[!UICONTROL No longer ask this question]** 것을 권장합니다.\
>이 옵션을 선택하고 최신 버전을 다운로드하지 않도록 선택하면 사용 가능한 새 버전에 대해 다른 사용자에게 통보되지 않습니다.

이 메시지를 재설정하려면 아래 단계를 따르십시오(레지스트리를 편집하기 쉬운 시스템 관리자만 이러한 변경 작업을 수행해야 함).

1. 메뉴에서 **regedit** 명령을 사용하여 레지스트리 편집기를 **[!UICONTROL Start > Run]** 엽니다.
1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. confAdortedUpgrade **항목을** 삭제하고 레지스트리 편집기를 닫습니다.


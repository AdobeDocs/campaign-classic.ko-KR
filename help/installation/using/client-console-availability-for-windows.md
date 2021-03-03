---
solution: Campaign Classic
product: campaign
title: Windows용 클라이언트 콘솔 가용성
description: Windows용 클라이언트 콘솔 가용성
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---


# Windows용 클라이언트 콘솔 가용성{#client-console-availability-for-windows}

Adobe Campaign 사용자가 만들고 구성한 인스턴스에 로그온하려면 클라이언트 콘솔을 사용해야 합니다.

## 클라이언트 콘솔을 사용 가능하게 만들기

Adobe Campaign 응용 프로그램 서버를 시작하는 데 사용된 컴퓨터(**nlserver 웹**)가 클라이언트 콘솔에서 사용자 연결을 받는 경우, HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트에 대한 설정 프로그램을 사용할 수 있도록 구성할 수 있습니다. 클라이언트 콘솔의 새 버전을 사용할 수 있을 때마다 사용자는 클라이언트 콘솔을 시작할 때 클라이언트 콘솔을 다운로드하도록 초대받습니다.

이렇게 하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 선택합니다.

   이 파일은 v7의 경우 `setup-client-7.X.XXXX.exe`, v6.1의 경우 `setup-client-6.X.XXXX.exe` 입니다. 여기서 `X`는 Adobe Campaign의 하위 버전이고 `XXXX`은 빌드 번호입니다.

1. 이 패키지를 복사하여 **/datakit/nl/eng/jsp** 아래의 Adobe Campaign 설치 폴더(하이브리드 설치의 경우 마케팅 서버)에 붙여 넣습니다.
1. Adobe Campaign 서버를 시작합니다.

그러면 캠페인 사용자는 다음 URL 덕분에 웹 브라우저를 통해 콘솔 설치 프로그램을 다운로드할 수 있습니다.

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

이 페이지에는 응용 프로그램에 정의된 로그인 및 암호가 필요합니다.

이 섹션](../../installation/using/installing-the-client-console.md)에서 콘솔 [을(를) 설치하는 방법을 알아봅니다.

## 최종 사용자에게 클라이언트 콘솔 업그레이드 제안

Campaign 서버 폴더에서 콘솔을 사용할 수 있게 되면 전용 프롬프트 창에서 최신 클라이언트 콘솔 버전을 다운로드하도록 사용자에게 초대됩니다. Adobe에서는 **[!UICONTROL No longer ask this question]** 옵션을 선택하지 않은 상태에서 새로운 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 경고가 표시되는지 확인할 것을 권장합니다.

이 옵션을 선택하고 최신 버전을 다운로드하지 않도록 선택하면 사용 가능한 새 버전에 대해 다른 사용자에게 통보되지 않습니다.

이 옵션을 선택한 경우 이 프롬프트를 재설정할 수 있습니다. Windows 레지스트리 편집에 익숙한 시스템 관리자만 다음 사항을 변경해야 합니다.

1. **[!UICONTROL Start > Run]** 메뉴에서 **regedit** 명령을 사용하여 레지스트리 편집기를 엽니다.
1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. **confAdortedUpgrade** 항목을 삭제하고 레지스트리 편집기를 닫습니다.


---
product: campaign
title: Windows용 클라이언트 콘솔 가용성
description: Windows용 클라이언트 콘솔 가용성
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Windows용 클라이언트 콘솔 가용성{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

Adobe Campaign 사용자가 만들고 구성한 인스턴스에 로그온할 수 있으려면 클라이언트 콘솔을 사용해야 합니다.

## 클라이언트 콘솔을 사용할 수 있도록 설정

Adobe Campaign 응용 프로그램 서버를 시작하는 데 사용된 컴퓨터(**nlserver web**)가 클라이언트 콘솔에서 사용자 연결을 받으면 HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트에 대한 설정 프로그램을 사용하도록 구성할 수 있습니다. 클라이언트 콘솔의 새 버전을 사용할 수 있을 때마다 클라이언트 콘솔을 시작할 때 다운로드하도록 사용자에게 초대됩니다.

이를 수행하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 선택합니다.

   이 파일을 v7의 경우 `setup-client-7.X.XXXX.exe`, v6.1의 경우 `setup-client-6.X.XXXX.exe` 이라고 합니다. 여기서 `X`는 Adobe Campaign의 하위 버전이고 `XXXX`은 빌드 번호입니다.

1. 이 패키지를 복사하여 **/datakit/nl/eng/jsp** 아래의 Adobe Campaign 설치 폴더(하이브리드 설치에 대한 마케팅 서버)에 붙여넣습니다.
1. Adobe Campaign 서버를 시작합니다.

Campaign 사용자는 다음 URL 덕분에 웹 브라우저를 통해 콘솔 설치 프로그램을 다운로드할 수 있습니다.

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

이 페이지에는 응용 프로그램에 정의된 로그인과 암호가 필요합니다.

이 섹션](../../installation/using/installing-the-client-console.md)에서 콘솔 [을 설치하는 방법을 알아봅니다.

## 최종 사용자에게 클라이언트 콘솔 업그레이드를 제안

Campaign 서버 폴더에서 콘솔을 사용할 수 있게 되면 전용 프롬프트 창에서 최신 클라이언트 콘솔 버전을 다운로드하도록 사용자에게 초대됩니다. Adobe은 새 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 경고하도록 **[!UICONTROL No longer ask this question]** 선택 취소 옵션을 그대로 둘 것을 권장합니다.

이 옵션을 선택하고 최신 버전을 다운로드하지 않도록 선택하면 다른 사용자에게 사용 가능한 새 버전에 대한 정보가 표시되지 않습니다.

옵션을 선택한 경우 이 메시지를 재설정할 수 있습니다. Windows 레지스트리 편집에 익숙한 시스템 관리자만 다음 내용을 변경해야 합니다.

1. **[!UICONTROL Start > Run]** 메뉴에서 **regedit** 명령을 사용하여 레지스트리 편집기를 엽니다.
1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. **confAdoredUpgrade** 항목을 삭제하고 레지스트리 편집기를 닫습니다.

---
product: campaign
title: Windows용 클라이언트 콘솔 가용성
description: Windows용 클라이언트 콘솔 가용성
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 4%

---

# Windows용 클라이언트 콘솔 가용성{#client-console-availability-for-windows}



Adobe Campaign 사용자가 생성 및 구성한 인스턴스에 로그온할 수 있으려면 클라이언트 콘솔을 사용해야 합니다.

## 클라이언트 콘솔을 사용할 수 있도록 설정

컴퓨터가 Adobe Campaign 애플리케이션 서버를 시작하는 데 사용되는 경우(**nlserver 웹**)는 클라이언트 콘솔에서 사용자 연결을 수신하므로, HTML 인터페이스를 통해 Adobe Campaign 리치 클라이언트의 설정 프로그램을 사용할 수 있도록 구성할 수 있습니다. 새 버전의 클라이언트 콘솔을 사용할 수 있을 때마다 사용자는 클라이언트 콘솔을 시작할 때 클라이언트 콘솔을 다운로드하도록 초대됩니다.

이렇게 하려면 다음을 수행해야 합니다.

1. 콘솔 설치 프로그램이 포함된 패키지를 선택합니다.

   이 파일은 라고 합니다. `setup-client-7.X.XXXX.exe`, 여기서 `X` 는 Adobe Campaign의 하위 버전이며 `XXXX` 는 빌드 번호입니다.

1. 이 패키지를 복사하여 Adobe Campaign 설치 폴더(하이브리드 설치용 마케팅 서버의)에 붙여넣습니다. **/datakit/nl/eng/jsp**.
1. Adobe Campaign 서버를 시작합니다.

그런 다음 Campaign 사용자는 다음 URL 덕분에 웹 브라우저를 통해 콘솔 설치 프로그램을 다운로드할 수 있습니다.

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

이 페이지에는 응용 프로그램에 정의된 로그인 및 암호가 필요합니다.

콘솔 설치 방법 알아보기 [이 섹션에서](../../installation/using/installing-the-client-console.md).

## 최종 사용자에게 클라이언트 콘솔 업그레이드 제안

Campaign 서버 폴더에서 콘솔을 사용할 수 있게 되면 전용 프롬프트 창에서 최신 클라이언트 콘솔 버전을 다운로드할 수 있도록 사용자가 초대됩니다. Adobe은 이 옵션을 종료하는 것을 권장합니다. **[!UICONTROL No longer ask this question]** 새 버전의 콘솔을 사용할 수 있을 때 모든 사용자에게 알림 메시지가 표시되게 하려면 선택을 취소합니다.

이 옵션을 선택하고 최신 버전을 다운로드하지 않도록 선택하면 다른 사용자에게 사용 가능한 새 버전에 대한 알림이 전송되지 않습니다.

옵션을 선택한 경우 이 프롬프트를 재설정할 수 있습니다. Windows 레지스트리를 편집하는 데 익숙한 시스템 관리자만 다음과 같이 변경해야 합니다.

1. 다음을 사용하여 레지스트리 편집기 열기 **regedit** 다음에서 명령 **[!UICONTROL Start > Run]** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 노드를 검색하고 확장합니다.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 삭제 **confAdvisedUpgrade** 레지스트리 편집기를 시작하고 닫습니다.

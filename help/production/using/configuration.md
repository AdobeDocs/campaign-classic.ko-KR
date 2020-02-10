---
title: 구성
seo-title: 구성
description: 구성
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 구성{#configuration}

## syslogd 의견 수렴 포트 변경 {#changing-the-syslogd-listening-port}

기본적으로 **syslogd** 의견 수렴 포트는 666(udp)입니다. 필요한 경우 환경 변수를 사용하여 변경할 수 있습니다.

구성이 완료되면 이 변수는 모든 Adobe Campaign 모듈에서 고려됩니다.

### Linux {#in-linux}

customer.sh **** 파일을 편집하고 다음 줄을 추가합니다.

```
export TRACE_ADDR=localhost:<listening port>
```

### Windows {#in-windows}

TRACE_ADDR **** 환경 변수를 **localhost** 값으로 만들어야 합니다. **`<listening port="" />`** Adobe

>[!CAUTION]
>
>이 환경 변수를 만든 후 플랫폼이 작동하는지 확인하려면 몇 가지 테스트를 실행하는 것이 좋습니다.

## 보안 영역 구성 {#configuring-security-zones}

각 연산자를 인스턴스에 로그온하려면 영역에 연결해야 하며 연산자 IP가 보안 영역에 정의된 주소 또는 주소 세트에 포함되어야 합니다. 기술 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다. 콘솔( **[!UICONTROL Administration > Access management > Operators]** 노드)에서 연산자의 보안 영역에 대한 연결을 정의해야 합니다.

>[!NOTE]
>
>보안 영역 구성에 대한 자세한 내용은 [이 섹션을](../../installation/using/configuring-campaign-server.md#defining-security-zones)참조하십시오.


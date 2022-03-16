---
product: campaign
title: 추가 구성
description: 구성
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# 구성{#configuration}

![](../../assets/v7-only.svg)

## syslogd 수신 포트 변경 {#changing-the-syslogd-listening-port}

기본적으로 **sylogd** 수신 포트는 666(udp)입니다. 필요한 경우 환경 변수를 사용하여 변경할 수 있습니다.

구성이 완료되면 이 변수는 모든 Adobe Campaign 모듈에서 고려합니다.

### Linux에서 {#in-linux}

편집 **customer.sh** 파일을 추가하고 다음 줄을 추가합니다.

```
export TRACE_ADDR=localhost:<listening port>
```

### Windows에서 {#in-windows}

을(를) 만들어야 합니다 **TRACE_ADDR** 환경 변수와 **localhost** 값: **`<listening port="" />`**.

>[!IMPORTANT]
>
>이 환경 변수를 만든 후 플랫폼이 작동하는지 확인하려면 몇 가지 테스트를 실행하는 것이 좋습니다.

## 보안 영역 구성 {#configuring-security-zones}

각 연산자는 인스턴스에 로그온하기 위해 영역에 연결해야 하며 운영자 IP는 보안 영역에 정의된 주소 또는 주소 세트에 포함해야 합니다. 기술 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다. 연산자와 보안 영역 간의 연결은 콘솔에서 정의해야 합니다( **[!UICONTROL Administration > Access management > Operators]** 노드)에 속해 있어야 합니다.

>[!NOTE]
>
>보안 영역 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/security-zones.md).

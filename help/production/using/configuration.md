---
product: campaign
title: 추가 구성
description: 구성
feature: Monitoring, Configuration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# 구성{#configuration}



## syslogd 수신 포트 변경 {#changing-the-syslogd-listening-port}

기본적으로 **syslogd** 수신 포트는 666(udp)입니다. 필요한 경우 환경 변수를 사용하여 변경할 수 있습니다.

구성하고 나면 모든 Adobe Campaign 모듈에서 이 변수를 고려합니다.

### Linux에서 {#in-linux}

**customer.sh** 파일을 편집하고 다음 줄을 추가합니다.

```sql
export TRACE_ADDR=localhost:<listening port>
```

### Windows {#in-windows}

**localhost** 값으로 **TRACE_ADDR** 환경 변수를 만들어야 합니다. **`<listening port="" />`**.

>[!IMPORTANT]
>
>이 환경 변수를 만든 후 플랫폼이 작동하는지 확인하려면 몇 가지 테스트를 실행하는 것이 좋습니다.

## 보안 영역 구성 {#configuring-security-zones}

각 연산자는 영역에 연결되어 인스턴스에 로그온해야 하며 연산자 IP는 보안 영역에 정의된 주소 또는 주소 집합에 포함되어야 합니다. 기술 영역 구성은 Adobe Campaign 서버의 구성 파일에서 수행됩니다. 연산자와 보안 영역 간의 연결을 콘솔(**[!UICONTROL Administration > Access management > Operators]** 노드)에서 정의해야 합니다.

>[!NOTE]
>
>보안 영역 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/security-zones.md)을 참조하세요.

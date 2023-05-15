---
product: campaign
title: Campaign On-premise, Hybrid 및 Hosted 기능 매트릭스
description: 호스팅된 배포와 온-프레미스 배포 간의 주요 차이점 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 28%

---

# 모델별 기능 매트릭스{#capability-matrix-per-model}



Adobe Campaign Classic에는 모듈 및 옵션 세트가 포함되어 있습니다. 이러한 모듈 및 모듈의 사용 가능 여부는 설치 배포 유형에 따라 달라질 수 있습니다. 이 문서에서는 전체 호스팅(Managed Services)과 온-프레미스 배포 간의 특정 기능에 대한 주요 차이점에 대한 세부 사항을 공유합니다.

이 페이지에는 호스팅된(Managed Services) 배포와 온-프레미스 배포 간의 주요 차이점이 표시됩니다. 하이브리드 배포 지정은 Adobe에서 호스팅하고 온-프레미스에서 호스팅되는 요소에 따라 다릅니다.

다양한 호스팅 모델이 도입되었습니다 [이 섹션](../../installation/using/hosting-models.md).

## 배포 모델당 가용성 {#capability-matrix}

| 기능 | 호스팅 | 하이브리드 | 온프레미스 | 세부 정보 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 캠페인 서버 구성 | 온디맨드 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../installation/using/the-server-configuration-file.md) |
| 이메일 BCC | 온디맨드 | 온디맨드 | 사용 가능 | [자세히 알아보기](../../installation/using/email-archiving.md) |
| 메시지 센터 실행 인스턴스 관리 | 온디맨드 | 온디맨드 | 사용 가능 | [자세히 알아보기](../../message-center/using/about-transactional-messaging.md) |
| 중간 소싱 플랫폼 관리 | 온디맨드 | 온디맨드 | 사용 가능 | [자세히 알아보기](../../installation/using/mid-sourcing-server.md) |
| Litmus를 통한 받은 편지함 렌더링 | 온디맨드 | 온디맨드 | 사용 가능 | [자세히 알아보기](../../delivery/using/inbox-rendering.md) |
| IMS와 통합(Adobe ID) | 온디맨드 | 온디맨드 | 온디맨드 | [자세히 알아보기](../../integrations/using/about-adobe-id.md) |
| 파일 전송을 위한 데이터 암호화/암호 해독 | 온디맨드 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../platform/using/unzip-decrypt.md) |
| 파일 압축/압축 해제 | 온디맨드 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../platform/using/unzip-decrypt.md) |
| 도메인 이름 위임 | 온디맨드 | 온디맨드 | 사용 불가 | [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=ko) |
| SpamAssassin 설치 | 온디맨드 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../delivery/using/spamassassin.md) |
| 게재 기능 보고서 액세스 | 사용 가능 | 온디맨드 | 사용 가능 | [자세히 알아보기](../../delivery/using/monitoring-deliverability.md) |
| LDAP 인증 구성 | 사용할 수 없음 | 사용 가능 | 사용 가능 | [자세히 알아보기](../../installation/using/connecting-through-ldap.md) |


## FDA(Federated Data Access){#fda}

Adobe Campaign은 다음을 제공합니다 **페더레이션 데이터 액세스** (FDA) 옵션을 사용하여 하나 이상의 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. Adobe Campaign 데이터의 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다. [자세히 알아보기](../../installation/using/about-fda.md)

>[!CAUTION]
>
>호환되는 외부 데이터베이스 시스템은 호스팅 모델에 따라 다릅니다. 추가 정보 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md).

**참조 항목**

* [호환성 매트릭스](../../rn/using/compatibility-matrix.md)
* [릴리스 정보](../../rn/using/latest-release.md)
* [Campaign Classic 업그레이드](../../rn/using/rn-overview.md)
* [사용이 중단되거나 제거된 기능](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 릴리스](../../rn/using/gold-standard.md)

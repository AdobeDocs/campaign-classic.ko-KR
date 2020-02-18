---
title: 외부 데이터베이스 액세스
seo-title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# 통합 데이터 액세스 정보 {#about-federated-data-access}

Adobe Campaign은 하나 이상의 **외부 데이터베이스에 저장된** 정보를 처리하기 위해 Federated Data Access(FDA) 옵션을 제공합니다.adobe Campaign 데이터 구조를 변경하지 않고 외부 데이터에 액세스할 수 있습니다.

>[!CAUTION]
>
>FDA를 통해 외부 데이터베이스에 액세스하는 것은 Snowflake 커넥터를 제외하고 온-프레미스 또는 하이브리드 설치에서만 가능합니다. 자세한 내용은 이 [페이지를](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)참조하십시오.

## 운영 원칙 {#operating-principle}

FDA 옵션을 사용하면 데이터 모델을 서드파티 데이터베이스로 확장할 수 있습니다. 타깃팅된 테이블의 구조를 자동으로 감지하고 SQL 소스의 데이터를 사용합니다.


이 기능을 사용하려면 다음을 수행해야 합니다.

1. Adobe Campaign FDA 모듈과 호환되는 외부 데이터베이스가 있어야 합니다. 데이터베이스 시스템 및 호환 버전 목록은 [호환성 매트릭스에](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)자세히 설명되어 있습니다. 또한 사용자는 Adobe Campaign 및 외부 데이터베이스에서 [필요한 권한을](#remote-database-access-rights) 가져야 합니다.
1. [Adobe Campaign 서버에 데이터베이스에 해당하는 드라이버를](#specific-configurations-by-database-type) 설치합니다.
1. [Adobe Campaign과 외부 데이터베이스 간의 연결을 설정할 수 있는 외부 계정을](#connecting-to-the-database) 만들고 구성합니다. 사용 가능한 외부 계정에 대한 자세한 내용은 이 [페이지를](../../platform/using/external-accounts.md)참조하십시오.
1. [Adobe Campaign에서 외부 데이터베이스의 스키마를](#creating-the-data-schema) 만듭니다. 이를 통해 외부 데이터베이스의 데이터 구조를 인식할 수 있습니다.
1. 마지막으로 [전달의 수신자가 외부 데이터베이스에서 오는 경우 이전에 생성된 스키마에서 새 대상 매핑을](#defining-data-mapping) 만듭니다. 이것은 특히 납품을 개인화하는 것과 관련하여 특정한 제한 사항을 나타낸다.

데이터 스키마가 만들어지면 Adobe Campaign 워크플로우에서 데이터를 처리할 수 있습니다. For more on this, refer to [this section](../../workflow/using/executing-a-workflow.md#architecture).

## 모범 사례 및 추천 {#best-practices-and-recommendations}

워크플로우에서 일괄 처리 모드에서 외부 데이터베이스의 데이터를 조작하기 위해 FDA 옵션이 제공됩니다. FDA를 다른 맥락에서 사용하는 경우, 예를 들면, 군 작전의 경우, 예방 조치(개인화, 상호 작용, 실시간 전달 등)를 수행해야 합니다.

Adobe Campaign과 외부 데이터베이스를 최대한 모두 사용해야 하는 작업을 방지합니다. 이렇게 하려면 다음을 수행할 수 있습니다.

* 결과를 Adobe Campaign으로 다시 가져오기 전에 Adobe Campaign 데이터베이스를 외부 데이터베이스로 내보내고 외부 데이터베이스에서만 작업을 실행합니다.
* 외부 Adobe Campaign 데이터베이스에서 데이터를 수집하고 작업을 로컬로 실행합니다.

외부 데이터베이스의 데이터를 사용하여 게재에서 개인화를 수행하려는 경우 워크플로우에서 사용할 데이터를 수집하여 임시 테이블에서 사용할 수 있도록 합니다. 그런 다음 임시 테이블의 데이터를 사용하여 배달을 개인화합니다.

## 제한 사항 {#limitations}

FDA 옵션은 사용자가 사용하는 외부 데이터베이스 시스템의 소프트 사용에 따릅니다.

성능상의 이유로, Adobe는 이 기능을 사용하여 단일 작업(전달 개인화, 상호 작용 모듈, 실시간)을 수행하는 것을 권장하지 않습니다.

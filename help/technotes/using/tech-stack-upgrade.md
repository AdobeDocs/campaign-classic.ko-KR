---
product: campaign
title: 기술 노트 - Adobe Campaign 시스템 업그레이드
description: Adobe Campaign 시스템 업그레이드
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 9%

---

# Adobe Campaign 2023 환경 업그레이드 {#ac-system-upgrade}

Campaign 인프라는 최신 버전 및 수정 사항으로 정기적으로 업데이트해야 하는 서드파티 시스템을 사용합니다. 이러한 업데이트는 서비스의 연속성을 보장하고 보안 위험으로부터 Campaign 환경을 보호하기 위해 필수입니다. 또한 서드파티 시스템 변경 사항과의 호환성을 보장하려면 Campaign을 업그레이드해야 합니다.

로서의 **호스팅 또는 관리 Cloud Services 고객**, Adobe은 이러한 업그레이드가 필요할 때 사용자에게 알려 줍니다. 규정 준수를 보장하기 위해 권장 사항에 따라 환경을 업그레이드해야 합니다.

(으)로 **온-프레미스 또는 하이브리드 고객**, Adobe은 동일한 달력에 따라 시스템 및 Campaign 버전을 업그레이드할 것을 강력히 권장합니다.

보안상의 이유로 다음을 수행해야 합니다 [최신 Campaign 빌드 설치](#ac-upgrade)을 클릭한 다음 을(를) 업그레이드하십시오 [운영 체제](#os-upgrade) 및/또는 사용자 [RDBMS(관계 데이터베이스 관리 시스템)](#pg-upgrade).

>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오. 다음 항목도 참조하십시오. [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md).
>

## Campaign 빌드 업그레이드 {#ac-upgrade}

**영향을 받습니까?**

의 영향을 받는 경우 [운영 체제 업그레이드](#os-upgrade) 및/또는 [데이터베이스 시스템 업그레이드](#pg-upgrade) 아래에 자세히 설명되어 있습니다. Campaign 환경을 다음으로 업그레이드해야 합니다. [최신 7.3.2 버전](../../rn/using/latest-release.md#release-7-3-2): 이러한 시스템과 호환됩니다.

**업데이트 방법**

* 호스팅 또는 관리 Cloud Services 고객인 Adobe은 귀하에게 연락하여 Campaign 버전을 업그레이드합니다.
* 하이브리드 고객은 Adobe이 중간 소싱 환경에 대해 예약된 빌드 업그레이드 날짜를 알려줍니다. 또한 마케팅 환경을 동일한 버전으로 업그레이드해야 합니다.
* 온-프레미스 고객은 Campaign 환경을 최신 7.3.2 빌드로 업그레이드해야 합니다.


## 운영 체제 업그레이드 {#os-upgrade}

**영향을 받습니까?**

데비안 운영 체제에서 Campaign을 실행하는 경우 최신 데비안 보안 업데이트의 혜택을 받으려면 Campaign 인프라를 다음으로 이동해야 합니다. **데비안**. Debian 9에 대한 보안 지원은 2023년 6월 30일까지 제공됩니다.

**업데이트 방법**

* 호스팅 또는 관리 Cloud Services 고객인 Adobe은 귀하에게 연락하여 환경을 업그레이드합니다.
* 하이브리드 고객은 Adobe에서 중간 소싱 환경에 대해 예약된 업그레이드 날짜를 알려줍니다. 마케팅 환경도 Debian에서 실행 중인 경우 Debian 11로 업그레이드해야 합니다.
* 온프레미스 고객은 환경을 Debian 11로 업그레이드해야 합니다.

## 데이터베이스 시스템 업그레이드 {#pg-upgrade}

**영향을 받습니까?**

Campaign용 데이터베이스 시스템이 PostgreSQL인 경우 최신 PostgreSQL 혁신 및 보안 업데이트의 혜택을 받으려면 다음을 업그레이드해야 합니다. **PostgreSQL 14**. PostgreSQL 11은 2023년 11월 9일에 사용이 종료됩니다.

**업데이트 방법**

* 호스팅 또는 관리 Cloud Services 고객인 Adobe은 사용자에게 연락하여 데이터베이스 시스템을 PostgreSQL 11에서 PostgreSQL 14로 업그레이드합니다.
* 하이브리드 고객인 경우 마케팅 데이터베이스 시스템이 PostgreSQL인 경우 PostgreSQL 14로 업그레이드해야 합니다.
* 온-프레미스 고객은 데이터베이스 시스템을 PostgreSQL 14로 업그레이드해야 합니다.


## 유용한 링크

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [최신 Campaign Classic 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)
* [사용자가 새 클라이언트 콘솔을 사용할 수 있도록 설정](../../installation/using/client-console-availability-for-windows.md)

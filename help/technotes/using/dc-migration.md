---
product: campaign
title: 공개 클라우드로 마이그레이션
description: Public Cloud로 Campaign Classic 마이그레이션에 대해 자세히 알아보기
feature: Overview
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 2%

---

# 개요{#dc-ovv}

![](../../assets/v7-only.svg)

## 컨텍스트

Adobe는 Adobe Campaign Classic 고객에게 최상의 경험과 가치를 제공하기 위해 노력하고 있습니다. 수년 동안 Adobe는 클라우드에서 고객을 호스팅하는 데 대한 가치와 신뢰성을 실현했습니다.  Adobe의 일부로 [연간 업그레이드 이니셔티브](../../rn/using/rn-overview.md#yearly-upgrade), Adobe는 모든 고객을 Adobe Managed Services(AWS의 Public Cloud)로 이동하여 보다 안전하고 안정적인 서비스를 제공하고 있습니다.

이 프로그램에는 세 가지 주요 목표가 있습니다.

* 보안 및 최신 환경으로 인프라를 이동함으로써 식별된 보안 취약점 해결(AWS).
* 번거로울 수 있는 확장 프로세스를 제거하고 [향상된 MTA](../../delivery/using//sending-with-enhanced-mta.md) 모든 유지 관리 서비스 수준을 향상시킬 수 있습니다.
* 리소스를 많거나 시간이 많이 필요하지 않은 보다 자동화된 일반 업그레이드를 포함하여 Adobe Campaign Classic의 향후 인스턴스에 대해 준비를 하십시오.

### 용어집

* **빌드 업그레이드** - Adobe Campaign Classic 소프트웨어가 최신 보안 빌드 번호로 업데이트되지만 동일한 주요/부 빌드 수준에서 유지됩니다. 예: Campaign v7 20.2.3 빌드 9182에서 Campaign v7 21.2.5 빌드 9188로 이동합니다. [자세히 알아보기](../../platform/using/faq-build-upgrade.md)
* **MID/RT** - Adobe Cloud에 호스팅되는 메시지 실행 서버(배치 캠페인의 경우 MID, 실시간 단일 메시지의 경우 RT)
* **연간 업그레이드 프로그램** - 이 프로그램은 향상된 보안, 향상된 지원, 유지 관리 및 안정성을 제공합니다. 또한 향후 업그레이드를 보다 쉽게 할 수 있고 Campaign의 새로운 기능에 액세스할 수 있습니다.  [자세히 알아보기](../../rn/using/rn-overview.md#yearly-upgrade)
* **AWS** - Amazon Web Services(Amazon Public Cloud)
* **SFTP** - 보안 파일 전송 프로토콜. [자세히 알아보기](../../platform/using/sftp-server-usage.md)


>[!NOTE]
>Public Cloud로의 v7 마이그레이션은 **Adobe Managed Services** 전용.


## 이점

**보안**

* 최신 보안 수정 사항
* 데이터 암호화 작동 중지
* 향상된 인증(IMS)

**인프라**

* 민첩한 하드웨어 확장성
* 신속한 복원
* 향상된 안정성 및 안정성
* 통합 운영 절차

**공연**

* 향상된 이메일 용량
* 대규모 데이터베이스
* 수정된 Campaign 버전

**Adobe Campaign Classic 고객을 위한 강력하고 안정적인 솔루션**

1. 운영 절차가 개선되어 신뢰성이 향상되고 문제가 발생할 경우 재활동이 빨라지며 중요한 사고 발생 시 복구 속도가 빨라집니다.
1. 높은 이메일 전송 용량. 새로운 데이터 센터에서 호스팅되는 인스턴스는 이메일 전달을 위한 전문 인프라를 통해 이점을 얻을 수 있습니다. 이를 통해 이메일 전송 속도가 빨라지거나 IP 전송 사용량이 줄어들 수 있습니다.
1. 향상된 하드웨어 확장성 하드웨어 리소스를 늘리는 것이 훨씬 더 빠릅니다. 기술적으로, 그것은 며칠 대신 1시간의 진도에 있을 것입니다.

**연간 업그레이드로 향후 업그레이드가 보다 쉬워집니다.**

1. 조직에서 업그레이드를 대기하는 시간이 길수록 업그레이드가 더 복잡해지고 취약점에 직면할 가능성이 높습니다(특히 이전 버전에서 이동할 때).
1. Campaign 연간 업그레이드 (Gold Standard 이니셔티브)를 사용하면 인스턴스가 현대화되며 수동 개입이 적고 리소스를 덜 활용하여 보다 자동화된 정기 업데이트를 받을 수 있습니다.

![](assets/GSMigrations.png)

## 마이그레이션 기본 정보

영향을 받는 계정의 경우 Adobe Managed Services(Public Cloud)2020/2021으로 마이그레이션됩니다. Adobe은 이 여정을 통해 조직을 이끌고 안내합니다.

이러한 작업을 시작하기 위해 이 마이그레이션을 필요로 하는 계정은 타임라인과 설명서에 대한 액세스를 제공하는 Adobe에서 이메일 커뮤니케이션을 받습니다. 계정이 마이그레이션되도록 예약되었다는 알림이 표시됩니다.

마이그레이션은 [새 고객 지원 지원 티켓 열기](https://experienceleague.adobe.com/?support-solution=Campaign#support). 제목란 &quot;AWS으로 마이그레이션&quot;을 사용합니다.

### 이 마이그레이션은 필수 사항입니까?

Cloud로의 마이그레이션은 **첫 번째 단계 [연간 업그레이드 프로그램](../../rn/using/rn-overview.md#yearly-upgrade)** Adobe Campaign 인스턴스 중 하나를 생성할 수 있습니다. Public Cloud(AWS)이 아닌 데이터 센터에서 호스팅되는 경우 이 마이그레이션은 필수입니다.

Adobe Managed Services 클라우드는 현대적이고 안전한 최적화된 환경인 Amazon Web Services(AWS)에서 호스팅됩니다. [AWS에 대해 자세히 알아보기](https://aws.amazon.com/application-hosting/benefits/).

Adobe은 기존 데이터 센터를 해제할 계획이며, 여기서 실행 중인 Adobe Campaign 인스턴스는 새 참조 데이터 센터 AWS으로 전송되어야 합니다.

현재 위치가 **보안 및 성능 취약점**.

또한 이 마이그레이션은 **향후 빌드 업그레이드에 대한 사전 요구 사항** Adobe Campaign의 기존 데이터 센터에서 빌드 업그레이드를 수행할 수 없습니다.

Adobe은 데이터를 보호하고 Adobe Campaign의 향후 계획을 추적하는 데 최선을 다하고 있습니다. 공동 성공을 위해서는 여러분의 파트너십이 필요합니다!


**우리는 팀을 조직했다** 전담 고객 지원 담당자, 고객 성공 관리자, 제품 관리자, 엔지니어, TechOps 전문가 및 제품 컨설턴트를 통해 원활한 경험을 제공하고 보장합니다. Adobe는 귀하에게 관련 프로젝트 및 연락처 정보를 제공하기 위해 최선을 다하고 있습니다.

Dell은 이러한 마이그레이션을 신속하고 원활하게 수행할 수 있는 기술 개발에 많은 노력을 투자했습니다.

### 제한

* 마이그레이션은 불가피한 플랫폼 다운타임과 함께 제공됩니다. 이 계획의 목적은 이 다운타임을 최소화하는 방법을 안내하는 것입니다.
* 데이터 통합을 위한 IP 변경 사항.
* 새로운 전송 IP의 게재 기능 램프-업. 그러나, 이 계획은 go-live 동안 수행되는 초기 램프 업과 달리 사업을 위해 이 작업을 투명하게 만드는 것입니다.

다음으로 Campaign 마이그레이션의 자세한 내용 [Public Cloud FAQ](dc-migration-faq.md).


## Public Cloud로의 마이그레이션 경로

Adobe은 대부분의 작업을 처리합니다. 확인 및 승인을 위해 사용자가 필요합니다.

![](assets/MigrationPath.png)

## 마이그레이션 지침

### 글로벌 접근 방식

**데이터베이스**

데이터베이스는 기존 데이터 센터에서 덤프되고 Public Cloud (AWS)에서 복원됩니다. 새 데이터 센터에서 다시 시작하면 애플리케이션이 종료 전 정확한 상태에서 다시 시작됩니다. 일부 예약된 작업이 지연되는 경우를 제외하고는 사용자에게 아무런 차이가 없습니다.

**이메일 전송 IP**

마이그레이션이 완료되면 Campaign 인스턴스에는 전송 IP가 완전히 다르게 생성됩니다. 원활한 전환을 위해 Adobe은 이전 IP에서 새 IP로 트래픽을 예시적으로 전환하여 새로운 전송 IP를 램프 업(ramp-up)으로 구현합니다.

**데이터 통합 IP**

클라이언트측의 데이터 통합은 데이터 통합을 위한 IP가 변경되어 영향을 받을 수 있습니다. 변경 사항은 Campaign이 서버나 클라이언트로 작동하는지 여부에 따라 양방향으로 모두 영향을 줄 수 있습니다.
일반적인 사례:

* SFTP, 양방향일 수 있음
* HTTP, 양방향으로
* SMPP(SMS 공급자에 연결), Campaign as a client, 소스 IP 변경

일반적으로, 이는 클라이언트가 방화벽에 설정된 가능한 IP 제한 사항을 확인하고 그에 따라 조정해야 함을 의미합니다.*

**Campaign 서버**

기존 Campaign 서버(실제로 컨테이너)는 &quot;이동 및 이동&quot; 방식으로 Public Cloud(AWS)으로 이동됩니다. 즉 새 서버를 설치할 필요가 없지만 전체 서버가 새 데이터 센터로 전송됩니다. 이 작업은 낮은 수준의 기술 재구성 이상의 작업이 필요하지 않습니다.

**서버 이름**

마케팅 통신에 사용되는 하위 도메인 아래에서 다음을 수행합니다. 는 동일하게 유지됩니다. 그러나 구현에 따라 클라이언트 측에서 작업이 필요할 수 있습니다.

* 하위 도메인을 위임하는 경우(일반 경우) Adobe은 모든 변경 사항을 관리하고 원활한 전환을 보장합니다
* CNAME 설정(예외)의 경우 클라이언트가 변경 사항을 구현하도록 요청합니다. Adobe과의 조정이 필요합니다.

사용자 액세스 및 데이터 통합의 경우 neolane.net 아래의 이름은 변경되지 않습니다.

즉, 서버 이름을 하드 코딩된 IP로 대체하지 않은 경우 사용자가 변경되고 데이터 통합 구현이 투명하게 변경됩니다.

### 준비

**이메일 전송 IP**

먼저 Adobe 게재 능력을 통해 플랫폼의 게재 능력을 평가하고 새 IP로 전환할 계획을 추천합니다.

Adobe은 새 데이터 센터에 동일한 수의 IP를 프로비저닝합니다.

새 IP가 프로비저닝되는 즉시 새 IP의 램프 업을 시작할 수 있습니다.

**애플리케이션 정리**
데이터 센터 간의 데이터 전송은 다운타임의 중요한 경로에 있습니다.

데이터는 다음 두 가지 방법으로 저장됩니다.

1. 가장 중요한 것은 데이터베이스
1. 애플리케이션 서버의 파일(데이터 가져오기 및 내보내기)

데이터베이스 크기를 줄이는 것이 데이터 전송 속도를 높이는 데 가장 중요합니다.

제안 사항:

* 이전 데이터(게재 로그, 추적 로그 등)의 보존 기간을 줄입니다
* 다른 테이블(게재, 수신자, 사용자 지정 테이블)에서 불필요한 레코드 삭제

### 실행

**실행 일시 중지**

애플리케이션이 레거시 데이터 센터에서 종료되기 바로 전에 모든 실행을 중단하고 일시 중지하는 것이 좋습니다. 게재 및 워크플로우. 프로세스에 &quot;부드럽게&quot;를 일시 중지하고 진행 중인 실행 상태를 저장할 시간이 부여되므로 이를 통해 Public Cloud(AWS)에서 다시 시작됩니다.

**마이그레이션 중**

마이그레이션이 진행되는 동안 하나의 서비스만 계속 작동합니다. 이메일 링크 리디렉션. 즉, 수신자는 이메일을 클릭하면 랜딩 페이지에 도달하게 됩니다. 이러한 클릭은 기록되지 않으므로 마이그레이션 바로 전에 시작된 게재의 클릭 비율은 정상보다 낮습니다.

**다시 시작**

새 환경으로 마이그레이션되면 애플리케이션이 점진적으로 다시 시작됩니다.

* 첫 번째 콘솔 액세스. 사용자는 아직 실행 중이 아닌 상태에서 상태를 확인할 수 있습니다
* 그런 다음 워크플로우 및 게재

### 마이그레이션 후

**기존 데이터 센터에서 인스턴스 삭제**

애플리케이션 마이그레이션이 완료되면 기존 데이터 센터에서 프로세스를 다시 실행할 계획이 없습니다. 예약된 백업 프로세스가 Public Cloud(AWS)에서 실행될 때까지 임시 백업을 제외한 레거시 데이터 센터의 모든 데이터를 지울 수 있습니다.

**DNS 위임**

일반적으로 Campaign에서 전자 메일을 보내는 데 사용되는 도메인(오류 주소에서 @ 기호 오른쪽에 있음)이 Adobe에 위임되었습니다. 위임은 AWS DNS 서버에 대해 변경하고 구현할 수 있습니다.


## 지원 및 기타 유용한 링크{#support}

* [Adobe Managed Services(Public Cloud)로 마이그레이션 FAQ](dc-migration-faq.md)
* [캠페인 연간 업그레이드](../../rn/using/rn-overview.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)

---
title: 캠페인 운영자를 IMS(Identity Management System) Adobe으로 마이그레이션
description: Campaign 연산자를 IMS(Identity Management System) Adobe으로 마이그레이션하는 방법에 대해 알아봅니다.
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 2%

---

# 캠페인 운영자를 IMS(Identity Management System) Adobe으로 마이그레이션 {#migrate-users-to-ims}

보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로, Adobe Campaign은 최종 사용자 인증 모드를 로그인/암호 기본 인증에서 Adobe Identity Management 시스템(IMS)으로 마이그레이션할 것을 강력히 권장합니다. 모든 연산자가 Campaign에 연결하려면 [IMS(Adobe Identity Management 시스템)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}을(를) 구현해야 합니다.

[이 페이지](ac-ims.md)에서 이 마이그레이션에 대해 자세히 알아보세요.

## 변경 사항 {#move-to-ims-changes}

Campaign Classic을 사용하면 모든 일반 사용자가 이미 Adobe Identity Management System(IMS)을 통해 Adobe ID을 사용하여 Adobe Campaign 클라이언트 콘솔에 연결할 수 있습니다. 그러나 사용자/암호 연결은 계속 사용할 수 있습니다. Campaign v8에서는 더 이상 허용되지 않습니다.

또한 보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로 이제 Adobe Campaign 클라이언트 애플리케이션이 IMS 기술 계정 토큰을 사용하여 Campaign API를 직접 호출합니다. 기술 운영자에 대한 마이그레이션은 전용 문서에 자세히 설명되어 있습니다. [이 페이지](ims-migration.md)에서 확인할 수 있습니다.

이 변경 사항은 이미 Campaign Classic v7에 적용되며 Campaign v8로 이동하려면 **필수**&#x200B;가 됩니다.

Adobe은 이러한 마이그레이션 노력에서 여러분을 지원합니다. 아래 문서에서 자세한 컨텍스트와 단계별 지침을 찾을 수 있습니다.

## 영향을 받습니까?{#migrate-ims-impacts}

이 절차는 Adobe ID으로 Campaign에 아직 연결하지 않은 모든 Campaign 사용자에게 적용됩니다.

조직의 운영자가 로그인/암호(예: )를 사용하여 Campaign 클라이언트 콘솔에 연결하는 경우 기본 인증)을 사용하면 영향을 받게 되며 아래에 자세히 설명된 대로 이러한 연산자를 Adobe IMS로 마이그레이션해야 합니다.

[IMS(Adobe Identity Management System)로 마이그레이션](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}은(는) 다른 대부분의 Adobe Experience Cloud 솔루션과 앱이 이미 IMS에 있으므로 환경을 안전하고 표준화해야 하는 보안 필수 요소입니다.

이 변경 사항은 Campaign Classic v7.4.1(및 최신 [IMS 마이그레이션 호환 버전](ac-ims.md#ims-versions))부터 적용할 수 있으며 Adobe Campaign v8로 이동하려면 **필수**&#x200B;입니다.


## 호스팅 및 Managed Services 환경을 마이그레이션하는 방법 {#ims-migration-procedure}

### 필수 구성 요소 {#ims-migration-prerequisites}

마이그레이션 프로세스를 시작하기 전에 Adobe 기술 팀이 기존 운영자 Adobe 및 IMS(Identity Management System) Adobe에 대한 명명된 권한을 마이그레이션할 수 있도록 Adobe 전환 관리자(Managed Services 고객용) 또는 고객 지원 센터(다른 호스팅 고객용)에 연락해야 합니다.

### 주요 단계 {#ims-migration-steps}

이 마이그레이션에 대한 주요 단계는 아래에 나와 있습니다.

1. Adobe이 환경을 Campaign v7.4.1(또는 [IMS 마이그레이션 호환 버전](ac-ims.md#ims-versions))로 업그레이드합니다.
1. 업그레이드 후에도 기본 사용자 또는 IMS와 같은 두 가지 방법을 사용하여 새 사용자를 만들 수 있습니다.
1. 내부 Campaign 관리자는 Campaign 클라이언트 콘솔의 모든 기본 사용자에게 고유한 이메일을 추가하고, 작업이 완료되면 Adobe 담당자/고객 지원 센터에 확인해야 합니다.  이 단계는 [이 섹션](#ims-migration-id)에 자세히 설명되어 있습니다.
1. Adobe 담당자/고객 지원 팀과 협력하여 기술 전문가가 아닌 사용자(운영자) 및 제품 프로필에 대해 자동 마이그레이션을 실행할 Adobe 날짜를 확보하십시오. 이 단계에는 서비스에 대한 다운타임 없이 1시간 동안의 시간이 필요합니다.
1. 내부 Campaign 관리자가 이러한 변경 사항을 확인하고 승인을 제공합니다. 이 마이그레이션 후에는 더 이상 이 로그인 및 암호로 인증하는 연산자를 만들지 않아야 합니다.

[이 기술 문서](ims-migration.md)에 설명된 대로 기술 연산자를 Adobe Developer Console으로 마이그레이션할 수도 있습니다.

이 마이그레이션이 완료되면 Adobe 전환 관리자 (Managed Services 사용자용) 또는 고객 지원 Adobe (호스팅된 고객용)에 문의하십시오. 그런 다음 Adobe은 마이그레이션을 완료된 것으로 표시합니다. 그런 다음 환경을 보호하고 표준화합니다.


## 하이브리드 및 온-프레미스 환경을 마이그레이션하는 방법 {#ims-migration-procedure-on-prem}

이 마이그레이션에 대한 주요 단계는 아래에 나와 있습니다.

1. 환경을 Campaign v7.4.1(또는 [IMS 마이그레이션 호환 버전](#ims-versions))로 업그레이드하십시오.
1. 업그레이드 후에도 기본 사용자 또는 IMS와 같은 두 가지 방법을 사용하여 새 사용자를 만들 수 있습니다.
1. 내부 Campaign 관리자는 [이 섹션](../../integrations/using/configuring-ims.md)에 자세히 설명된 대로 Adobe IMS를 구성해야 합니다.
1. 그런 다음 Campaign 클라이언트 콘솔의 모든 기본 사용자에게 고유한 이메일을 추가합니다. 이 단계는 [이 섹션](#ims-migration-id)에 자세히 설명되어 있습니다.
1. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=ko){target="_blank"}에 자세히 설명된 대로 Adobe Admin Console에서 사용자 및 제품 프로필을 만듭니다.
1. 모든 연산자에 대해 **Adobe ID과 연결** 옵션을 사용하도록 설정하십시오.
1. [이 페이지](../../integrations/using/implementing-ims.md)에 자세히 설명된 대로 연결에 Adobe IMS를 구현합니다.

[이 기술 문서](ims-migration.md)에 설명된 대로 기술 연산자를 Adobe Developer Console으로 마이그레이션할 수도 있습니다.


## FAQ(자주 묻는 질문) {#ims-migration-faq}

### 마이그레이션 후 사용자를 만드는 방법 {#ims-migration-native}

Adobe은 Campaign Classic v7.4.1(또는 [IMS 마이그레이션 호환 버전](#ims-versions))로 업그레이드한 후 IMS 사용자만 만들 것을 권장합니다.
Campaign v7.4.1을 시작하면 [이 페이지](impact-ims-migration.md)에 설명된 대로 인스턴스 구성을 업데이트하여 기본 연산자 생성을 방지할 수 있습니다.

Campaign 관리자는 Adobe Admin Console 및 Campaign 클라이언트 콘솔을 통해 조직의 사용자에게 권한을 부여할 수 있습니다. 사용자가 Adobe ID으로 Adobe Campaign에 로그온합니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=ko){target="_blank"}에서 IMS를 사용하여 권한을 설정하는 방법을 알아봅니다.

### 현재 기본 사용자의 이메일을 추가하는 방법 {#ims-migration-id}

Campaign 관리자는 클라이언트 콘솔에서 모든 기본 사용자에게 이메일 ID를 추가해야 합니다. 이렇게 하려면 아래 단계를 수행합니다.

1. 클라이언트 콘솔에 연결하고 **관리 > 액세스 관리 > 연산자**&#x200B;로 이동합니다.
1. 연산자 목록에서 업데이트할 연산자를 선택합니다.
1. 연산자 양식의 **연락처** 섹션에 연산자의 전자 메일을 입력합니다.
1. 변경 내용을 저장합니다.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### IMS를 통해 Campaign에 로그인하는 방법 {#ims-migration-log}

[이 섹션](../../integrations/using/implementing-ims.md)에서 Adobe ID을 사용하여 Campaign에 연결하는 방법을 알아봅니다.

### 이 마이그레이션 도중 중단 시간이 발생합니까? {#ims-migration-downtime}

호스팅 및 Managed Services 고객의 경우 마이그레이션을 완료하려면(사용자 및 제품 프로필 마이그레이션) Adobe에 인스턴스(워크플로 등)에 대한 다운타임 없이 1시간 정도의 시간이 필요합니다.

이 기간 동안 IMS로의 마이그레이션이 완료되면 모든 Campaign 사용자는 로그오프한 후 Adobe ID으로 다시 로그인해야 합니다.

Adobe은 마이그레이션 기간 동안 모든 사용자를 로그오프할 것을 강력히 권장합니다.

### 조직의 사용자가 이미 IMS를 사용하고 있습니다. IMS 마이그레이션을 수행해야 합니까?{#ims-migration-needed}

이 마이그레이션에는 최종 사용자 마이그레이션(및 제품 프로필 포함)과 기술 사용자 마이그레이션(사용자 지정 코드의 API에 사용됨)의 두 가지 측면이 있습니다.

모든 사용자(캠페인 운영자)가 IMS에 있는 경우에도 Adobe 담당자/고객 지원 센터에 문의하여 제품 프로필 마이그레이션을 계획해야 합니다. 사용자 지정 코드에서 사용했을 수 있는 기술 사용자를 마이그레이션해야 합니다. [이 페이지](ims-migration.md)에서 자세히 알아보십시오.

### 운영자의 인증 유형을 보는 방법

Campaign에서 연산자의 인증 유형을 보는 방법을 알아봅니다.

1. **탐색기**&#x200B;에서 **관리** `>` **액세스 관리** `>` **연산자**&#x200B;에 액세스합니다.

1. 머리글 행을 마우스 오른쪽 단추로 클릭하고 **목록 구성** 메뉴를 선택합니다.

   ![](assets/ims_2.png)

1. **계정 사용 안 함** 및 **인증 유형**&#x200B;을(를) **출력 열**(으)로 추가하십시오.

   ![](assets/ims_1.png)

이제 **연산자** 목록과 해당 **인증 유형**&#x200B;을 볼 수 있습니다.

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [기술 사용자를 Adobe Developer 콘솔로 마이그레이션](ims-migration.md)
>* [Adobe Campaign Classic v7 릴리스 노트](../../rn/using/latest-release.md)
>* [IMS(Identity Management System) Adobe은 무엇입니까](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}

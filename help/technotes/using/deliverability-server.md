---
product: campaign
title: 새 게재 기능 서버로 업데이트
description: 새로운 Campaign 게재 기능 서버로 업데이트하는 방법 알아보기
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 1%

---

# 새 게재 기능 서버로 업데이트 {#acc-deliverability}

시작 [v7.2.2 릴리스](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign은 고가용성을 제공하고 보안 규정 준수 문제를 해결하는 새로운 전달성 서버를 사용합니다. 이제 Campaign Classic이 게재 가능성 규칙, 브로드로그 및 제외 주소를 새 게재 가능성 서버에서 및 새 게재 가능성 서버로 동기화합니다. 이전 게재 기능 서버는 2022년 8월 31일에 서비스 해제됩니다.

Campaign Classic 고객은 새 게재 기능 서버를 구현해야 합니다 **2022년 8월 31일 이전**.

>[!NOTE]
>
>이러한 변경 사항에 대한 자세한 내용은 [FAQ](#faq), 또는 연락처 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## 변경 사항{#acc-deliverability-changes}

Adobe이 보안 규정 준수를 이유로 이전 데이터 센터를 폐기하고 있습니다. Adobe Campaign Classic 클라이언트는 Amazon 웹 서비스(AWS)에서 호스팅되는 새로운 게재 기능 서비스로 마이그레이션해야 합니다.

이 새 서버는 고가용성(99.9)을 보장하고&#x200B;, Campaign 서버가 필요한 데이터를 가져올 수 있도록 안전하고 인증된 끝점을 제공합니다. 즉, 모든 요청에 대해 데이터베이스에 연결하는 대신 새 전달성 서버가 데이터를 캐시하여 가능한 한 요청을 제공합니다. 이 메커니즘은 응답 시간을 향상시킵니다&#x200B;.

## 영향을 받습니까?{#acc-deliverability-impacts}

모든 고객은 영향을 받으며 로 업그레이드해야 합니다. [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (또는 그 이상) 새로운 전달성 서버의 이점을 활용하도록 환경을 구현합니다.

## 업데이트 방법{#acc-deliverability-update}

로서의 **호스팅된 고객**, Adobe이 사용자와 함께 작동하여 인스턴스를 최신 버전으로 업그레이드하고 Adobe Developer 콘솔에서 프로젝트를 만듭니다.

(으)로 **온-프레미스/하이브리드 고객**&#x200B;로 업그레이드해야 합니다. [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (또는 그 이상) 새로운 전달성 서버를 활용할 수 있습니다. 모든 인스턴스가 업그레이드되면 다음을 수행해야 합니다 [새 통합 구현](#implementation-steps) 전달성 서버 Adobe 및 원활한 전환을 보장합니다.

## 구현 단계 {#implementation-steps}

>[!WARNING]
>
>이러한 단계는 하이브리드 및 온프레미스 구현에 대해서만 수행해야 합니다.

새 게재율 서버 통합의 일부로, Campaign은 IMS(Identity Management Service) 기반 인증을 통해 Adobe Shared Services와 통신해야 합니다. 선호하는 방법은 Adobe Developer 기반 게이트웨이 토큰(기술 계정 토큰 또는 Adobe IO JWT라고도 함)을 사용하는 것입니다.

>[!AVAILABILITY]
>
> 서비스 계정(JWT) 자격 증명은 Adobe에서 더 이상 사용되지 않으며, Adobe 솔루션 및 앱과 Campaign 통합은 이제 OAuth 서버 간 자격 증명을 사용해야 합니다. </br>
>
> * Campaign과 인바운드 통합을 구현하면에 자세히 설명된 대로 기술 계정을 마이그레이션해야 합니다. [이 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 기존 서비스 계정(JWT) 자격 증명은 2025년 1월 27일까지 계속 작동합니다. </br>
>
> * Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일까지 계속 작동합니다. 그러나 해당 날짜 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 oAuth로 마이그레이션해야 합니다.

### 필수 구성 요소{#prerequisites}

구현을 시작하기 전에 인스턴스 구성을 확인하십시오.

1. Campaign 클라이언트 콘솔을 열고 Adobe Campaign에 관리자로 로그온합니다.
1. 다음으로 이동 **관리 > 플랫폼 > 옵션**.
1. 다음을 확인하십시오. `DmRendering_cuid` 옵션 값이 입력되었습니다.

   * 옵션이 채워지면 구현을 시작할 수 있습니다.
   * 값을 채우지 않은 경우 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} CUID를 가져옵니다.

   이 옵션은 모든 Campaign 인스턴스(MKT, MID, RT, EXEC)에 올바른 값으로 채워야 합니다. 하이브리드 고객은 Adobe에게 연락하여 MID, RT 및 EXEC 인스턴스에 옵션을 설정합니다.

온-프레미스 고객은 캠페인도 확인해야 합니다 **[!UICONTROL Product profile]** 는 조직에서 사용할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다.

1. 관리자로서 다음 위치에 연결합니다. [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. 액세스 **제품 및 서비스** 섹션 및 확인 **Adobe Campaign** 이 나열됩니다.
표시되지 않는 경우 **Adobe Campaign** 연락처 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 추가.
1. 클릭 **Adobe Campaign** 조직을 선택합니다.
   **주의**: 둘 이상의 조직이 있는 경우 올바른 조직을 선택해야 합니다. 조직에 대해 자세히 알아보기 [이 페이지에서](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. 다음 확인: **[!UICONTROL Product profile]** 존재함. 그렇지 않으면 만듭니다. 이에 대한 권한은 필요하지 않습니다. **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>온프레미스 고객은 방화벽이 사용자 쪽에 구현된 경우 이 URL을 추가해야 합니다 `https://deliverability-service.adobe.io` 허용 목록에 추가하다에 [자세히 알아보기](../../installation/using/url-permissions.md).


### 1단계: Adobe Developer 프로젝트 만들기/업데이트 {#adobe-io-project}

Adobe Analytics 커넥터 구성을 계속하려면 Adobe Developer 콘솔에 액세스하고 OAuth 서버 간 프로젝트를 만듭니다.

을(를) 참조하십시오 [이 페이지](../../integrations/using/oauth-technical-account.md#oauth-service) 을 참조하십시오.

### 2단계: Adobe Campaign에서 프로젝트 자격 증명 추가 {#add-credentials-campaign}

다음에 자세히 설명된 단계 수행 [이 페이지](../../integrations/using/oauth-technical-account.md#add-credentials) Adobe Campaign에서 OAuth 프로젝트 자격 증명을 추가할 수 있습니다.

### 3단계: 구성 유효성 검사

통합이 성공했는지 확인하려면 아래 단계를 수행합니다.

1. 클라이언트 콘솔을 열고 Adobe Campaign에 로그온합니다.
1. 다음으로 이동 **관리 > 프로덕션 > 기술 워크플로우**.
1. 다시 시작 **게재 가능성을 위해 새로 고침** (게재 가능성 업데이트) 워크플로우입니다. 모든 Campaign 인스턴스(MKT, MID, RT, EXEC)에서 이 작업을 수행해야 합니다. 하이브리드 고객은 Adobe에게 연락하여 MID, RT 및 EXEC 인스턴스에서 워크플로우를 다시 시작하도록 합니다.
1. 로그 확인: 워크플로우가 오류 없이 실행되어야 합니다.

>[!CAUTION]
>
>업데이트 후 **받은 편지함 렌더링에 대한 시드 네트워크 업데이트(updateRenderingSeeds)** 워크플로우가 더 이상 적용되지 않고 실패하므로 중지해야 합니다.

## FAQ(자주 묻는 질문) {#faq}

### 업데이트의 타임라인은 어떻게 됩니까?

이러한 향상된 기능을 추가하고 보안을 강화하는 새 전달성 서버로 전환하는 작업은 호스팅된 고객(Campaign Managed Services)을 위해 2022년 7월부터 시작됩니다. 호스팅된 모든 고객은 8월 말까지 업데이트됩니다.

온-프레미스 및 하이브리드 고객은 동일한 기간 동안 전환해야 합니다.

### 환경을 업그레이드하지 않으면 어떻게 됩니까?

8월 31일까지 업그레이드되지 않은 모든 Campaign 인스턴스는 더 이상 Campaign Deliverability 서버에 연결할 수 없습니다. 그 결과 **게재 가능성을 위해 새로 고침** (게재 가능성 업데이트) 워크플로우가 실패하고 게재 가능성에 영향을 미칩니다.

환경을 업그레이드하지 않으면 이메일 설정 동기화가 중지됩니다(MX 관리 규칙, 인바운드 이메일 규칙, 도메인 관리 규칙 및 반송 자격 규칙). 이는 시간이 지남에 따라 게재 가능성에 영향을 줄 수 있습니다. 이러한 규칙에 중요한 변경이 이루어진 경우 이 시점부터 수동으로 적용해야 합니다.

MKT 인스턴스의 경우에만 [전역 제외 목록](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) 영향을 받습니다.

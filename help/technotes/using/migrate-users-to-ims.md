---
title: 캠페인 운영자를 Adobe Identity Management System(IMS)으로 마이그레이션
description: Campaign 연산자를 Adobe Identity Management System(IMS)으로 마이그레이션하는 방법에 대해 알아봅니다.
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%
---
# 캠페인 운영자를 Adobe Identity Management System(IMS)으로 마이그레이션 {#migrate-users-to-ims}

보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로, Adobe Campaign은 최종 사용자 인증 모드를 로그인/암호 기본 인증에서 Adobe Identity Management System(IMS)으로 마이그레이션할 것을 강력히 권장합니다. 모든 연산자가 Campaign에 연결하려면 [Adobe IMS(Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}를 구현해야 합니다.

[이 페이지](ac-ims.md)에서 이 마이그레이션에 대해 자세히 알아보세요.

## 변경 사항 {#move-to-ims-changes}

Campaign Classic을 사용하면 모든 일반 사용자가 이미 Adobe IMS(Identity Management System)를 통해 Adobe ID을 사용하여 Adobe Campaign 클라이언트 콘솔에 연결할 수 있습니다. 그러나 사용자/암호 연결은 계속 사용할 수 있습니다. Campaign v8에서는 더 이상 허용되지 않습니다.

또한 보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로 이제 Adobe Campaign 클라이언트 애플리케이션이 IMS 기술 계정 토큰을 사용하여 Campaign API를 직접 호출합니다. 기술 운영자에 대한 마이그레이션은 전용 문서에 자세히 설명되어 있습니다. [이 페이지](ims-migration.md)에서 확인할 수 있습니다.

이 변경 사항은 이미 Campaign Classic v7에 적용되며 Campaign v8로 이동하려면 **필수**&#x200B;가 됩니다.

Adobe은 이러한 마이그레이션 작업을 지원합니다. 아래 문서에서 자세한 컨텍스트와 단계별 지침을 찾을 수 있습니다.

## 영향을 받습니까?{#migrate-ims-impacts}

이 절차는 Adobe ID으로 Campaign에 아직 연결하지 않은 모든 Campaign 사용자에게 적용됩니다.

조직의 운영자가 로그인/암호(예: )를 사용하여 Campaign 클라이언트 콘솔에 연결하는 경우 기본 인증)을 사용하면 영향을 받게 되며 아래에 자세히 설명된 대로 이러한 연산자를 Adobe IMS로 마이그레이션해야 합니다.

[IMS(Adobe Identity Management System)로 마이그레이션](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}은(는) 다른 Adobe Experience Cloud 솔루션 및 앱의 대부분이 이미 IMS에 있으므로 환경을 안전하고 표준화하도록 하는 데 필수적인 보안입니다.

이 변경 사항은 Campaign Classic v7.4.1(및 최신 [IMS 마이그레이션 호환 버전](ac-ims.md#ims-versions))부터 적용할 수 있으며 Adobe Campaign v8로 이동하려면 **필수**&#x200B;입니다.

>[!IMPORTANT]
>
>**Campaign 컨트롤 패널 액세스 영향**
>
>사용자를 IMS로 마이그레이션한 후에는 Adobe Admin Console의 제품 프로필에 이름에 &quot;admin&quot;이라는 단어가 포함되어 있는지 확인하십시오(예: &quot;Administrators&quot;, &quot;admin&quot;, &quot;admins&quot;, &quot;approval admin&quot; 등). 는 Campaign Campaign 컨트롤 패널에 대한 액세스 권한을 자동으로 부여합니다. Campaign 컨트롤 패널은 Campaign 인스턴스를 크게 변경할 수 있는 셀프서비스 도구입니다.
>
>제품 프로필 이름 지정 규칙을 주의 깊게 검토하여 승인된 사용자만 Campaign 컨트롤 패널에 액세스할 수 있도록 합니다. [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko){target="_blank"}에서 Campaign 컨트롤 패널 권한 관리에 대해 자세히 알아보세요.


## 하이브리드 및 온-프레미스 환경을 마이그레이션하는 방법 {#ims-migration-procedure-on-prem}

이 마이그레이션에 대한 주요 단계는 아래에 나와 있습니다.

1. 환경을 Campaign v7.4.1(또는 [IMS 마이그레이션 호환 버전](#ims-versions))로 업그레이드하십시오.
1. 업그레이드 후에도 기본 사용자 또는 IMS와 같은 두 가지 방법을 사용하여 새 사용자를 만들 수 있습니다.
1. 내부 Campaign 관리자는 [이 섹션](../../integrations/using/configuring-ims.md)에 자세히 설명된 대로 Adobe IMS를 구성해야 합니다.
1. 그런 다음 Campaign 클라이언트 콘솔의 모든 기본 사용자에게 고유한 이메일을 추가합니다. 이 단계는 [이 섹션](https://experienceleague.adobe.com/ko/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"}에 자세히 설명되어 있습니다(Campaign v8 설명서).
1. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=ko){target="_blank"}에 자세히 설명된 대로 Adobe Admin Console에서 사용자 및 제품 프로필을 만듭니다.
1. 모든 연산자에 대해 **Adobe ID과 연결** 옵션을 사용하도록 설정하십시오.
1. [이 페이지](../../integrations/using/implementing-ims.md)에 자세히 설명된 대로 연결에 Adobe IMS를 구현합니다.

[이 기술 문서](ims-migration.md)에 설명된 대로 기술 연산자를 Adobe Developer Console으로 마이그레이션할 수도 있습니다.

## 자주 묻는 질문 {#ims-migration-faq}

마이그레이션에 대한 일반적인 질문(마이그레이션 후 사용자 만들기, 기본 사용자를 위한 이메일 추가, IMS를 통해 로그인, 가동 중지, 이미 IMS를 사용하는 조직, 운영자의 인증 유형 보기)에 대한 답변은 [Campaign v8 기술 정보](https://experienceleague.adobe.com/ko/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank}(Campaign v8 설명서)를 참조하십시오.

>[!MORELIKETHIS]
>
>* [기술 사용자를 Adobe Developer 콘솔로 마이그레이션](ims-migration.md)
>* [Adobe Campaign Classic v7 릴리스 노트](../../rn/using/latest-release.md)
>* [IMS(Adobe Identity Management System)란 무엇입니까](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}

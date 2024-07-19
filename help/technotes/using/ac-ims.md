---
title: Adobe Identity Management 시스템(IMS)으로 마이그레이션
description: 인증 프로세스를 IMS(Identity Management System) Adobe으로 마이그레이션하는 방법에 대해 알아봅니다
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# Adobe Identity Management 시스템(IMS)으로 마이그레이션 {#migrate-to-ims}

보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로 Adobe Campaign은 최종 사용자 인증 모드를 로그인/암호 기본 인증에서 [IMS(Identity Management 시스템) Adobe](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}(으)로 마이그레이션할 것을 강력히 권장합니다.

또한 Adobe Campaign 클라이언트 애플리케이션은 이제 IMS 기술 계정 토큰을 사용하여 Campaign API를 직접 호출합니다. 기술 연산자를 Adobe Developer Console으로 마이그레이션해야 합니다.

>[!CAUTION]
>
>이 변경 사항은 이미 Campaign Classic v7에 적용되며 Campaign v8로 이동하려면 **필수**&#x200B;가 됩니다. Campaign v8에서는 기본 사용자/암호 인증이 허용되지 않습니다. **Adobe은 Campaign v7.3.5부터 이 마이그레이션을 수행하여 Campaign v8로 원활하게 마이그레이션할 것을 권장합니다.**
>

## 마이그레이션 단계 {#ims-steps}

[IMS(Adobe Identity Management System)로 마이그레이션](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}은(는) 다른 대부분의 Adobe Experience Cloud 솔루션과 앱이 이미 IMS에 있으므로 환경을 안전하고 표준화해야 하는 보안 필수 요소입니다.

Adobe은 이러한 마이그레이션 노력에서 여러분을 지원합니다. 자세한 컨텍스트와 단계별 지침은 아래 문서에서 확인할 수 있습니다.

* 최종 사용자 인증에 대한 마이그레이션은 [이 페이지](migrate-users-to-ims.md)에 자세히 설명되어 있습니다.
* 기술 운영자 인증을 위한 마이그레이션은 [이 페이지](ims-migration.md)에 자세히 설명되어 있습니다.
* Campaign v7.4.1부터 사용자 인터페이스 및 API 제한을 활성화하여 [이 페이지](impact-ims-migration.md)에 설명된 대로 기본 인증과 관련된 옵션과 기능을 제거합니다.


## IMS 마이그레이션 호환 버전 {#ims-versions}

이 마이그레이션의 전제 조건은 환경을 다음 제품 버전 중 하나로 업그레이드하는 것입니다.

* Campaign v7.4.1 (권장)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

이러한 Campaign 버전은 [릴리스 정보](../../rn/using/latest-release.md)에 자세히 설명되어 있습니다.

## FAQ(자주 묻는 질문) {#ims-migration-faq}

### 언제 마이그레이션을 시작할 수 있습니까? {#ims-migration-start}

[IMS(Adobe Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}(으)로 마이그레이션하기 위한 권장 사항은 환경을 Campaign Classic v7.4.1(또는 [IMS 마이그레이션 호환 버전](#ims-versions))로 업그레이드하는 것입니다.

스테이징 환경에서 IMS 마이그레이션을 시작하고 최신 버전으로 업그레이드한 후 프로덕션 환경에 대한 계획을 수립할 수 있습니다.

### Campaign Classic v7.4.1로 빌드 업그레이드 후 어떻게 됩니까? {#ims-migration-after-upgrade}

환경이 Campaign Classic v7.4.1(또는 [IMS 마이그레이션 호환 버전](#ims-versions))로 업그레이드되면 [IMS(Identity Management 시스템) Adobe](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}(으)로 전환을 시작할 수 있습니다.

### 마이그레이션이 언제 완료됩니까? {#ims-migration-end}

IMS(Adobe Identity Management System)로 최종 사용자 마이그레이션 및 기술 운영자를 마이그레이션한 후 환경을 업데이트하여 기본 인증과 관련이 있고 IMS 인증에는 더 이상 적용할 수 없는 옵션을 제거해야 합니다. 이 업데이트는 Campaign v7.4.1부터 사용할 수 있습니다. [자세히 알아보기](impact-ims-migration.md)



## 유용한 링크 {#ims-useful-links}

* [최종 사용자를 IMS로 마이그레이션](migrate-users-to-ims.md)
* [기술 운영자를 Adobe Developer 콘솔로 마이그레이션](ims-migration.md)
* [Adobe Campaign Classic v7 최신 릴리스 노트](../../rn/using/latest-release.md)
* [IMS(Identity Management System) Adobe은 무엇입니까](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}

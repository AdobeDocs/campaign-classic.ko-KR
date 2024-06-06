---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: ht
source-wordcount: '352'
ht-degree: 100%

---

# 최신 릴리스{#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.3.5 - 빌드 9368 {#release-7-3-5}

[!BADGE 일반 공급]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}


_2023년 12월 5일 수요일_


### 보안 기능 개선 {#release-7-3-5-security}


* Campaign Classic v7.3.5를 통해 인증 프로세스가 개선되고 안전해졌습니다. 이제 기술 운영자는 Adobe IMS(Identity Management System)를 사용하여 Campaign에 연결해야 합니다. [이 기술 노트](../../technotes/using/ims-migration.md)에서 기존 기술 계정을 마이그레이션하는 방법을 알아봅니다.

* 또한 보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로 Adobe Campaign은 최종 사용자 인증 모드를 로그인/암호 기본 인증에서 Adobe IMS(Identity Management System)로 마이그레이션할 것을 강력히 권장합니다. [이 기술 노트](../../technotes/using/migrate-users-to-ims.md)에서 운영자를 마이그레이션하는 방법을 알아봅니다.

* 이제 웹 양식이 **게시 보류 중** 상태인 경우 자동으로 게시되지 않습니다. 보안 문제를 방지하려면 **온라인**&#x200B;이 되기 전에 게시해야 하며 웹 브라우저에서 웹 양식 URL을 통해 액세스할 수 있어야 합니다. [자세히 보기](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### 패치 {#release-7-3-5-patches}

* Google Big Query 데이터베이스의 데이터를 사용하고 Oracle 데이터베이스의 데이터를 업데이트할 때 워크플로우 임시 테이블의 모든 키가 `0`(으)로 설정되는 문제를 해결했습니다. (NEO-65091)
* Google Big Query 데이터베이스의 두 쿼리가 **합집합** 워크플로우 활동으로 결합되어 있을 때 워크플로우 실행에 실패하는 문제를 해결했습니다. (NEO-63705)
* Campaign 보고서의 `Back` 버튼을 클릭할 때 사용자에게 다시 인증하라는 요청이 표시되는 문제를 해결했습니다. (NEO-65087)
* 게재 증명 전에 게재를 삭제할 때 발생하는 데이터베이스 정리 워크플로우의 오류를 해결했습니다. (NEO-48114)
* TLS 인증에 대한 최근 업데이트로 인해 클라이언트 콘솔에 연결할 때 연결 오류가 발생하는 문제를 해결했습니다. (NEO-50488)
* Campaign을 7.3.1로 업그레이드한 후 HTTP 프록시 인증 시 Campaign 워크플로우의 HTTP 요청이 실패하며 `error 407 – proxy auth required is returned`라는 오류 메시지가 표시되는 문제를 해결했습니다. (NEO-49624)
* **스크립트** 워크플로우 활동에서 GPG 암호 해독이 간헐적으로 실패하는 오류를 해결했습니다. 관련 오류 메시지는 다음과 같습니다. `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->


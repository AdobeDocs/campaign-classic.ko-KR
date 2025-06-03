---
product: campaign
title: 사용 권한 시작
description: Campaign 기능에 대한 액세스 권한을 부여하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 6%

---

# 사용 권한 시작{#access-management}


>[!CAUTION]
>
>Campaign Classic v7.3.1부터 모든 연산자는 [Adobe IMS(Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}를 사용하여 Campaign에 연결해야 합니다.
>
>보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로, Adobe Campaign은 모든 기존 운영자 인증 모드를 로그인/암호 기본 인증에서 Adobe Identity Management System(IMS)으로 마이그레이션할 것을 강력히 권장합니다. [이 페이지](../../technotes/using/migrate-users-to-ims.md)에서 연산자를 마이그레이션하는 방법에 대해 알아보세요.
> 
>이 마이그레이션 후에는 다음 섹션이 더 이상 적용되지 않습니다.  [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=ko){target="_blank"}에서 Adobe IMS를 사용하여 권한을 설정하는 방법에 대해 알아봅니다.


Adobe Campaign을 사용하면 다양한 연산자에 할당된 권한을 정의하고 관리할 수 있습니다. 다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* (명명된 권한을 통해) 특정 기능에 액세스
* 특정 레코드에 대한 액세스,
* 레코드(작업, 연락처, 캠페인, 그룹 등)의 생성, 수정 및/또는 삭제.

권한은 운영자 프로필 또는 운영자 그룹에 적용됩니다.

운영자의 Adobe Campaign 연결 모드에 연결된 안전 매개 변수에 의해 완료됩니다. [이 페이지](../../installation/using/security-zones.md)의 보안 영역에 대한 자세한 정보.

사용자에게 부여할 수 있는 권한은 두 가지 유형이 있습니다.

* 권한을 지정할 연산자 그룹을 정의한 다음 연산자를 하나 이상의 그룹과 연결할 수 있습니다. 이렇게 하면 권한을 재사용하고 운영자 프로필을 보다 일관되게 만들 수 있습니다. 또한 프로필 관리 및 유지 관리를 용이하게 합니다. 그룹 생성 및 관리가 [이 섹션](access-management-groups.md)에 표시됩니다.

* 명명된 권한을 사용자에게 직접 지정할 수 있으며, 경우에 따라 그룹을 통해 할당된 권한을 오버로드할 수 있습니다. 이러한 권한은 [이 페이지](access-management-named-rights.md)에 표시됩니다.

>[!NOTE]
>
> * Adobe 사용 권한 정의를 시작하기 전에 [보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)을 읽는 것이 좋습니다.
> * 권한에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}의 자세한 설명을 참조하십시오.

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->
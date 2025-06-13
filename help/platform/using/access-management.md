---
product: campaign
title: 사용 권한 시작
description: Campaign 기능에 대한 액세스 권한을 부여하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: b27b85b126e002c0ea8b5d71da1ed60e1e817980
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 9%

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

>[!BEGINTABS]

>[!TAB 사용 권한 설명서]

Adobe Campaign의 권한에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}

>[!TAB 폴더 액세스 관리]

폴더 액세스 및 관리 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/folder-permissions?lang=en#_blank){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)] ([![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}){target=_blank}

>[!ENDTABS]

<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/kr/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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
---
product: campaign
title: 사용 권한 시작
description: Campaign 기능에 대한 액세스 권한을 부여하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
TQID: https://experienceleague.adobe.com/03hVUeg0dRIFz0J20RfxH4EdSmAhe9h2c9BfKB-qJUs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 315
ht-degree: 21%

---

# 사용 권한 시작{#access-management}


>[!CAUTION]
>
>Campaign Classic v7.3.1부터 모든 연산자는 [Adobe IMS(Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}를 사용하여 Campaign에 연결해야 합니다.
>
>보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로, Adobe Campaign은 모든 기존 운영자 인증 모드를 로그인/암호 기본 인증에서 Adobe Identity Management System(IMS)으로 마이그레이션할 것을 강력히 권장합니다. [이 페이지](../../technotes/using/migrate-users-to-ims.md)에서 연산자를 마이그레이션하는 방법에 대해 알아보세요.
> 
>이 마이그레이션 후에는 다음 섹션이 더 이상 적용되지 않습니다.  [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=ko){target="_blank"}에서 Adobe IMS를 사용하여 권한을 설정하는 방법에 대해 알아봅니다.


Adobe Campaign을 사용하면 다양한 운영자에 할당된 권한을 정의하고 관리할 수 있습니다. 다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* (명명된 권한을 통해) 특정 기능에 액세스
* 특정 레코드에 대한 액세스,
* 레코드(작업, 연락처, 캠페인, 그룹 등)의 생성, 수정 및/또는 삭제.

>[!BEGINTABS]

>[!TAB 사용 권한 설명서]

**Adobe Campaign의 권한**&#x200B;에 대한 자세한 내용은 **[Campaign v8(콘솔) 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}**&#x200B;를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}


>[!TAB 폴더에 대한 권한 관리]

**폴더에 대한 권한**&#x200B;을 정의하는 방법은 **[Campaign v8(콘솔) 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**&#x200B;를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB 기본 인증]

로그인/암호를 사용하는 기본 인증은 Campaign v7에서 계속 사용할 수 있지만, 보안 및 인증 프로세스를 강화하기 위해 Adobe Campaign에서는 기본 인증에서 Adobe Identity Management System(IMS)으로 [최종 사용자 인증 모드를 마이그레이션](../../technotes/using/ac-ims.md)할 것을 강력히 권장합니다. Campaign v8에서는 기본 인증과의 연결이 허용되지 않습니다.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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
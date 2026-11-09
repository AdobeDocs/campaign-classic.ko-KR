---
product: campaign
title: 사용 권한 시작
description: Campaign 기능에 대한 액세스 권한을 부여하는 방법 알아보기
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
TQID: 'https://experienceleague.adobe.com/03hVUeg0dRIFz0J20RfxH4EdSmAhe9h2c9BfKB-qJUs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 9%
---
# 사용 권한 시작{#access-management}

Adobe Campaign을 사용하면 다양한 운영자에 할당된 권한을 정의하고 관리할 수 있습니다. 다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* (명명된 권한을 통해) 특정 기능에 액세스
* 특정 레코드에 대한 액세스,
* 레코드(작업, 연락처, 캠페인, 그룹 등)의 생성, 수정 및/또는 삭제.

>[!NOTE]
>
>Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 권한 및 폴더에 대한 권한을 정의하는 방법에 대한 자세한 내용은 Campaign v8 설명서를 참조하십시오.
>
>* [사용 권한 시작](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}
>* [폴더에 권한 추가](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/folder-permissions){target="_blank"}
>
>[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}

## 인증 모드 {#authentication-mode}

>[!CAUTION]
>
>Campaign Classic v7.3.1부터 모든 연산자는 [Adobe IMS(Identity Management System)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}를 사용하여 Campaign에 연결해야 합니다.
>
>로그인/암호를 사용하는 기본 인증은 Campaign v7에서 계속 사용할 수 있습니다. 그러나 보안 및 인증 프로세스를 강화하려면 기존 연산자를 모두 기본 인증에서 Adobe IMS로 마이그레이션하는 것이 좋습니다. Campaign v8에서는 기본 인증과의 연결이 허용되지 않습니다.

* 연산자를 마이그레이션하려면 [사용자를 IMS로 마이그레이션](../../technotes/using/migrate-users-to-ims.md)을 참조하세요.
* 최종 사용자의 인증 모드를 마이그레이션하려면 [최종 사용자 인증 모드 마이그레이션](../../technotes/using/ac-ims.md)을 참조하세요.

이 마이그레이션 후에는 권한이 Adobe IMS로 관리됩니다. 설정 방법은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}를 참조하세요.


<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation)

* [Manage Campaign folder access](access-management.md)

* [Access rights matrix](assets/access-rights-matrix.pdf)


See also:

* [Manage permissions for workflows](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/advanced-management/managing-rights){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for distributed marketing](https://experienceleague.adobe.com/en/docs/campaign/automation/distributed-marketing/about-distributed-marketing#operators-and-entities){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for the interaction module](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/offers/interaction-settings/interaction-operators){target="_blank"} (Campaign v8 documentation)
* [Filter access to schemas](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/filter-schema){target="_blank"} (Campaign v8 documentation)
* [Restricting PI view](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/restrict-pi-view){target="_blank"} (Campaign v8 documentation)
-->
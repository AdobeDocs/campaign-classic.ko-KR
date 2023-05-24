---
product: campaign
title: 사용 권한 시작
description: Campaign 기능에 대한 액세스 권한을 부여하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---

# 사용 권한 시작{#access-management}



Adobe Campaign을 사용하면 다양한 연산자에 할당된 권한을 정의하고 관리할 수 있습니다. 다음은 권한을 부여하거나 거부한 권한 및 제한 세트입니다.

* (명명된 권한을 통해) 특정 기능에 액세스
* 특정 레코드에 대한 액세스,
* 레코드(작업, 연락처, 캠페인, 그룹 등)의 생성, 수정 및/또는 삭제.

권한은 운영자 프로필 또는 운영자 그룹에 적용됩니다.

운영자의 Adobe Campaign 연결 모드에 연결된 안전 매개 변수에 의해 완료됩니다. 의 보안 영역에 대한 자세한 정보 [이 페이지](../../installation/using/security-zones.md).

사용자에게 부여할 수 있는 권한은 두 가지 유형이 있습니다.

* 권한을 지정할 연산자 그룹을 정의한 다음 연산자를 하나 이상의 그룹과 연결할 수 있습니다. 이렇게 하면 권한을 재사용하고 운영자 프로필을 보다 일관되게 만들 수 있습니다. 또한 프로필 관리 및 유지 관리를 용이하게 합니다. 그룹 생성 및 관리는에 나와 있습니다. [이 섹션](access-management-groups.md).

* 명명된 권한을 사용자에게 직접 지정할 수 있으며, 경우에 따라 그룹을 통해 할당된 권한을 오버로드할 수 있습니다. 이러한 권한은에 제공됩니다. [이 페이지](access-management-named-rights.md).

>[!NOTE]
>
>권한 정의를 시작하기 전에 Adobe은 [보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html).

액세스 권한 부여 및 권한 설정 방법은 다음 섹션에서 알아봅니다.

* [운영자 만들기](access-management-operators.md)

* [그룹 정의](access-management-groups.md)

* [명명된 권한 추가](access-management-named-rights.md)

* [Campaign 폴더 액세스 관리](access-management-folders.md)

* [액세스 권한 지표](access-management-named-rights.md#access-rights-matrix)


참조 항목:

* [워크플로우에 대한 권한 관리](../../workflow/using/managing-rights.md)
* [분산 마케팅에 대한 권한 관리](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [상호 작용 모듈에 대한 권한 관리](../../interaction/using/operator-profiles.md)
* [스키마에 대한 액세스 필터링](../../configuration/using/filtering-schemas.md)
* [PI 보기 제한](../../configuration/using/restricting-pii-view.md)

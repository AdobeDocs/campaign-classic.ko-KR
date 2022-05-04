---
product: campaign
title: 개인 정보 보호 요청 관리
description: 개인 정보 보호 요청에 대해 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: ht
source-wordcount: '489'
ht-degree: 100%

---

# 개인 정보 보호 요청 정보 {#privacy-requests}

![](../../assets/v7-only.svg)

개인 정보 관리에 대한 일반 프레젠테이션은 [이 섹션](privacy-management.md)을 참조하십시오.

이 정보는 GDPR, CPA, PDPA 및 LGPD에 적용됩니다. 이러한 규정에 대한 자세한 내용은 [이 섹션](privacy-management.md#privacy-management-regulations)을 참조하십시오.

>[!NOTE]
>
>CPA에만 해당되는 개인 정보 판매 옵트아웃은 [이 섹션](#sale-of-personal-information-ccpa)에 설명되어 있습니다.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Adobe Campaign을 사용하면 개인 정보 보호 준비를 용이하게 하기 위해 액세스 및 삭제 요청을 처리할 수 있습니다. **액세스 권한** 및 **잊혀질 권리(삭제 요청)**&#x200B;는 [이 섹션](privacy-management.md#right-access-forgotten)에 설명되어 있습니다.

Adobe Campaign은 데이터 컨트롤러에게 개인 정보 보호 액세스 및 삭제 요청을 수행하는 두 가지 방법을 제공합니다.

* **Adobe Campaign 인터페이스를 통해** 각 개인 정보 보호 요청을 하는 경우 데이터 컨트롤러는 Adobe Campaign에서 새로운 개인 정보 보호 요청을 생성합니다. [이 섹션](privacy-requests-ui.md)을 참조하십시오.
*  **API**&#x200B;를 통해 Adobe Campaign은 SOAP를 사용한 개인 정보 보호 요청 자동 프로세스를 허용하는 API를 제공합니다. [이 섹션](privacy-requests-api.md)을 참조하십시오.

>[!NOTE]
>
>개인 데이터 및 데이터를 관리하는 다른 엔터티(데이터 컨트롤러, 데이터 프로세서 및 데이터 주체)에 대한 자세한 내용은 [개인 데이터 및 가상 사용자](privacy-and-recommendations.md#personal-data)를 참조하십시오.

## 필수 구성 요소 {#prerequesites}

Adobe Campaign은 저장된 데이터에 대한 개인 정보 요청을 만들고 처리할 수 있는 데이터 컨트롤러 도구를 제공합니다. 하지만 데이터 주체(이메일, 고객 지원 센터 또는 웹 포털)와의 관계를 처리하는 것은 데이터 컨트롤러의 책임입니다.

따라서 요청을 하는 데이터 주체의 ID를 확인하고 요청자에게 반환되는 데이터가 데이터 주체의 정보임을 확인하는 것은 데이터 컨트롤러로서의 책임입니다.

## 개인 정보 보호 패키지 설치 {#install-privacy-package}

이 기능을 사용하려면 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**&#x200B;메뉴를 통해&#x200B;**[!UICONTROL Privacy Data Protection Regulation]** 패키지를 설치해야 합니다. 패키지 설치 방법에 대한 자세한 내용은 [자세한 설명서](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

[개인 정보]에만 해당하는 2개의 새 폴더가 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** 아래에 만들어집니다.

* **[!UICONTROL Privacy Requests]**: 여기에서 개인 정보 보호 요청을 만들고 진행 상황을 추적할 수 있습니다.
* **[!UICONTROL Namespaces]**: 여기에서 Adobe Campaign 데이터베이스의 데이터 주체를 식별하는 데 사용될 필드를 정의할 수 있습니다.

![](assets/privacy-folders.png)

**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;에서 개인 정보 보호 요청을 처리하기 위해 매일 3개의 기술 워크플로우가 실행됩니다.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: 이 워크플로우는 Adobe Campaign에 저장된 수신자의 데이터를 생성하여 개인 정보 보호 요청의 화면에서 다운로드할 수 있도록 합니다.
* **[!UICONTROL Delete privacy requests data]**: 이 워크플로우에서는 Adobe Campaign에 저장된 수신자 데이터를 삭제합니다.
* **[!UICONTROL Privacy request cleanup]**: 이 워크플로우에서는 90일 이전의 액세스 요청 파일을 삭제합니다.

**[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**&#x200B;의 **[!UICONTROL Privacy Data Right]** 명명된 권한이 추가되었습니다. 데이터 컨트롤러가 개인 정보 보호 도구를 사용하려면 이 명명된 권한이 필요합니다. 이를 통해 새로운 요청을 만들고 진행 상황을 추적하며 API를 사용하는 등의 작업을 할 수 있습니다.

![](assets/privacy-right.png)

## 네임스페이스 {#namesspaces}

개인 정보 보호 요청을 만들기 전에 사용할 네임스페이스를 정의해야 합니다. 이 필드는 Adobe Campaign 데이터베이스의 데이터 주체를 식별하는 데 사용됩니다.

기본적으로 제공되는 네임스페이스 3개(이메일, 전화 및 휴대폰)가 있습니다. 다른 네임스페이스(예: 수신자 사용자 정의 필드)가 필요한 경우 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**&#x200B;에서 새 네임스페이스를 만들 수 있습니다.

>[!NOTE]
>
>최적의 성능을 위해서는 바로 사용할 수 있는 네임스페이스를 사용하는 것이 좋습니다.

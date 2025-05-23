---
product: campaign
title: Adobe ID을 사용하여 Adobe Campaign에 연결
description: Adobe Campaign의 Adobe IMS 구현에 대해 자세히 알아보기
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 15%

---

# Adobe ID 정보 {#about-adobe-id}

IMS(Identity Management System) Adobe은 관리자가 애플리케이션 및 서비스에 대한 사용자의 액세스 권한을 만들고 관리할 수 있도록 도와줍니다. 다양한 유형의 Adobe ID에 대한 자세한 내용은 [이 페이지](https://helpx.adobe.com/kr/enterprise/using/identity.html)를 참조하세요.

Campaign 사용자는 [기본 사용자/암호 인증](../../platform/using/access-management-operators.md) 대신 Adobe ID을 사용하여 Adobe Campaign 콘솔에 연결할 수 있습니다. 이 구현은 다음과 같은 이점을 제공합니다.

* 모든 Experience Cloud 솔루션에 동일한 ID를 사용할 수 있습니다.
* 서로 다른 통합으로 Adobe Campaign을 사용하는 경우 연결이 유지됩니다.
* 기본 로그인/암호보다 안전한 암호 관리 정책.
* 페더레이션 ID 계정 사용(외부 ID 공급자).

>[!IMPORTANT]
>
> Campaign v8에서는 사용자/암호(즉, 기본 인증)로 연결할 수 없습니다. **Adobe은 Campaign v7.3.5부터 이 마이그레이션을 수행하여 Campaign v8로 원활하게 마이그레이션할 것을 권장합니다.**
>
>[이 섹션](../../technotes/using/ac-ims.md)에서 Adobe IMS로 마이그레이션하는 방법을 알아보세요.
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## 추가 리소스

| 유용한 페이지 | 추가 자료 |
|---|---|
| [IMS 구성](../../integrations/using/configuring-ims.md) | [Experience Cloud FAQ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=ko) |
| [IMS 구현](../../integrations/using/implementing-ims.md) | [액세스 관리](../../platform/using/access-management.md) |
| [IMS 문제 해결](../../integrations/using/ims-troubleshooting.md) | [Campaign 패키지 설치](../../installation/using/installing-campaign-standard-packages.md) |

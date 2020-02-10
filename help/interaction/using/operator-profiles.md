---
title: 연산자 프로필
seo-title: 연산자 프로필
description: 연산자 프로필
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 연산자 프로필{#operator-profiles}

상호 작용을 사용하는 연산자는 두 가지 유형이 있습니다.오퍼 관리자 및 배달 관리자 이들은 특정 권리를 가지며 특정 트리 부분과 플랫폼의 일부에만 액세스할 수 있습니다.

* **[!UICONTROL Offer manager]** :오퍼를 만들고 유지
* **[!UICONTROL Delivery manager]** :오퍼 승인 및 사용

상호 작용에만 적용되는 연산자를 만드는 단계는 플랫폼에서 다른 모든 연산자를 만드는 데 사용되는 연산자와 동일합니다. For more on this, refer to [this section](../../platform/using/access-management.md#creating-an-operator). 운영자를 만드는 동안 권한이 구성됩니다.

## 오퍼 관리자 {#offer-manager}

1. 새 연산자를 만듭니다.
1. 창으로 **[!UICONTROL Groups and named rights]** 이동하여 **[!UICONTROL Add]** 을 클릭하고 **[!UICONTROL Offer manager]** 그룹을 선택합니다.

   ![](assets/offer_operators_create_001.png)

오퍼 관리자에 지정된 권한을 통해 사용자는 다음 작업을 수행할 수 있습니다.

* 환경을 **[!UICONTROL Design]** 수정합니다.
* 환경 **[!UICONTROL Live]** 보기
* 관리 함수(사전 정의된 공간 및 필터)를 구성합니다.
* 카테고리 만들기 및 변경
* 오퍼를 만듭니다.
* 오퍼 자격 조건을 구성합니다.
* 오퍼를 승인합니다.

   >[!NOTE]
   >
   >오퍼 관리자는 두 가지 경우에 한하여 오퍼를 승인할 수 있습니다. 첫 번째는 특정 검토자가 지정되지 않은 경우이고, 두 번째는 템플릿 생성(검토자를 할당할 수 있는 권한 사용)을 담당하는 운영자가 오퍼가 기반이 되는 오퍼 템플릿의 검토자로 지정했는지 여부입니다.

## 배달 관리자 {#delivery-manager}

1. 새 연산자를 만듭니다.
1. 창으로 **[!UICONTROL Groups and named rights]** 이동하여 **[!UICONTROL Add]** 을 클릭하고 **[!UICONTROL Delivery manager]** 그룹을 선택합니다.

   ![](assets/offer_operators_create_002.png)

배달 관리자에게 할당된 권한은 다음 작업을 수행할 수 있도록 하거나 활성화합니다.

* 디스플레이 **[!UICONTROL Live]** 환경
* 오퍼 카테고리를 표시하고 수정합니다.
* 오퍼가 검토자 중 하나로 지정된 경우 오퍼를 승인합니다.

   >[!NOTE]
   >
   >제공 관리자는 오퍼 구성 중에 검토자로 정의된 경우에만 오퍼를 승인할 수 있습니다.

## 작업자에 따른 권한 요약 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>오퍼 관리자(편집)</strong><br /> </td> 
   <td> <strong>오퍼 관리자(라이브)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>트리 구조 수준</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 편집 중인/라이브 오퍼<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 수신자 - 환경<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 관리<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 공백<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 사전 정의된 오퍼 필터<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형 규칙<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 카탈로그<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 카테고리<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>배달 관리자(편집)</strong><br /> </td> 
   <td> <strong>배달 관리자(라이브)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>트리 구조 수준</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 편집 중인/라이브 오퍼<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 수신자 - 환경<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 관리<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공백<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사전 정의된 오퍼 필터<br /> </td> 
   <td> 읽기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형<br /> </td> 
   <td> 읽기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형 규칙<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 카탈로그<br /> </td> 
   <td> 읽기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 카테고리<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
 </tbody> 
</table>


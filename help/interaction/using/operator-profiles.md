---
product: campaign
title: 운영자 프로필
description: 운영자 프로필
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 5%

---

# 운영자 프로필{#operator-profiles}

![](../../assets/v7-only.svg)

상호 작용을 사용하는 연산자는 두 가지 유형이 있습니다. 오퍼 관리자 및 게재 관리자 이들은 트리와 플랫폼의 일부 부분에만 액세스할 수 있는 특정 권한을 갖습니다.

* **[!UICONTROL Offer manager]** : 오퍼를 만들고 유지 관리합니다. 오퍼가 워크플로우에서 사용되는 경우 연산자는 **[!UICONTROL Administrator]** 또는 **[!UICONTROL Offer managers]** 작업 흐름을 실행할 연산자 그룹입니다.
* **[!UICONTROL Delivery manager]** : 오퍼 승인 및 사용

상호 작용에 대한 연산자를 만드는 단계는 플랫폼에서 다른 모든 연산자를 만드는 데 사용되는 연산자와 동일합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/access-management.md)을 참조하십시오. 연산자를 만드는 동안 권한이 구성됩니다.

## 오퍼 관리자 {#offer-manager}

1. 새 연산자를 만듭니다.
1. 로 이동합니다. **[!UICONTROL Groups and named rights]** 창 **[!UICONTROL Add]** 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL Offer manager]** 그룹에 속해 있어야 합니다.

   ![](assets/offer_operators_create_001.png)

오퍼 관리자에 할당된 권한을 사용하여 다음 작업을 수행할 수 있습니다.

* 수정 **[!UICONTROL Design]** 환경.
* 보기 **[!UICONTROL Live]** 환경.
* 관리 함수(사전 정의된 공간 및 필터)를 구성합니다.
* 카테고리를 만들고 변경합니다.
* 오퍼를 만듭니다.
* 오퍼 자격 을 구성합니다.
* 오퍼를 승인합니다.

   >[!NOTE]
   >
   >오퍼 관리자는 특정 두 가지 경우에만 오퍼를 승인할 수 있습니다. 첫 번째 경우는 특히 아무도 검토자로 지정되지 않은 경우이고, 두 번째 경우는 템플릿을 만드는 운영자(검토자를 할당할 수 있는 권한 포함)가 오퍼를 기반으로 한 오퍼 템플릿의 검토자로 지정했는지 여부입니다.

## 게재 관리자 {#delivery-manager}

1. 새 연산자를 만듭니다.
1. 로 이동합니다. **[!UICONTROL Groups and named rights]** 창 **[!UICONTROL Add]** 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL Delivery manager]** 그룹에 속해 있어야 합니다.

   ![](assets/offer_operators_create_002.png)

게재 관리자에게 할당된 권한을 통해 다음 작업을 수행할 수 있습니다.

* 표시 **[!UICONTROL Live]** 환경.
* 오퍼 카테고리를 표시하고 수정합니다.
* 이 게재 관리자가 해당 검토자 중 하나로 지정된 경우 오퍼를 승인합니다.

   >[!NOTE]
   >
   >게재 관리자는 오퍼 구성 중에 오퍼가 검토자로 정의된 경우에만 오퍼를 승인할 수 있습니다.

## 연산자에 따른 권한 모음 {#recap-of-rights-according-to-operator}

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
   <td> 편집 중인 오퍼/라이브 오퍼<br /> </td> 
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
   <td> Spaces<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 사전 정의된 오퍼 필터<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형화<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형화 규칙<br /> </td> 
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
   <td> <strong>게재 관리자(편집)</strong><br /> </td> 
   <td> <strong>게재 관리자(라이브)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>트리 구조 수준</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 편집 중인 오퍼/라이브 오퍼<br /> </td> 
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
   <td> Spaces<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사전 정의된 오퍼 필터<br /> </td> 
   <td> 읽기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형화<br /> </td> 
   <td> 읽기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 유형화 규칙<br /> </td> 
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

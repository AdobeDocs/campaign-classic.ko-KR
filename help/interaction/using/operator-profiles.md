---
product: campaign
title: 운영자 프로필
description: 운영자 프로필
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---

# 운영자 프로필{#operator-profiles}



상호 작용을 사용하는 운영자에는 오퍼 관리자와 게재 관리자의 두 가지 유형이 있습니다. 각 사용자에게 트리의 일부 및 플랫폼에 대한 액세스 권한만 부여하는 특정 권한이 있습니다.

* **[!UICONTROL Offer manager]** : 오퍼를 만들고 유지 관리합니다. 오퍼가 워크플로에서 사용되는 경우 연산자는 **[!UICONTROL Administrator]** 또는 **[!UICONTROL Offer managers]** 연산자 그룹에 있어야 워크플로를 실행할 수 있습니다.
* **[!UICONTROL Delivery manager]** : 오퍼를 승인하고 사용합니다.

상호 작용과 관련된 연산자를 만드는 단계는 플랫폼에서 다른 모든 연산자를 만드는 데 사용되는 단계와 동일합니다. 자세한 정보는 [이 섹션](../../platform/using/access-management.md)을 참조하세요. 권한은 연산자 생성 중에 구성됩니다.

## 오퍼 관리자 {#offer-manager}

1. 새 연산자를 만듭니다.
1. **[!UICONTROL Groups and named rights]** 창으로 이동하여 **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 **[!UICONTROL Offer manager]** 그룹을 선택합니다.

   ![](assets/offer_operators_create_001.png)

오퍼 관리자에게 할당된 권한을 통해 다음 작업을 수행할 수 있습니다.

* **[!UICONTROL Design]** 환경을 수정합니다.
* **[!UICONTROL Live]** 환경을 봅니다.
* 관리 기능(사전 정의된 스페이스 및 필터)을 구성합니다.
* 범주를 만들고 변경합니다.
* 오퍼를 만듭니다.
* 오퍼 자격 조건을 구성합니다.
* 오퍼를 승인합니다.

  >[!NOTE]
  >
  >오퍼 관리자는 두 가지 특정 경우에만 오퍼를 승인할 수 있습니다. 첫 번째는 특별히 검토자로 지정된 사람이 없는 경우이고, 두 번째는 템플릿을 만드는 작업을 담당하는 운영자(검토자를 할당할 권한이 있음)가 오퍼의 기반이 되는 오퍼 템플릿에서 검토자로 지정한 경우입니다.

## 게재 관리자 {#delivery-manager}

1. 새 연산자를 만듭니다.
1. **[!UICONTROL Groups and named rights]** 창으로 이동하여 **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 **[!UICONTROL Delivery manager]** 그룹을 선택합니다.

   ![](assets/offer_operators_create_002.png)

게재 관리자에게 할당된 권한을 통해 다음과 같은 작업을 수행할 수 있습니다.

* **[!UICONTROL Live]** 환경을 표시합니다.
* 오퍼 범주를 표시하고 수정합니다.
* 이 게재 관리자가 검토자 중 하나로 지정된 경우 오퍼를 승인합니다.

  >[!NOTE]
  >
  >게재 관리자는 오퍼 구성 중에 검토자로 정의된 경우에만 오퍼를 승인할 수 있습니다.

## 연산자에 따른 권한 요약 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>오퍼 관리자(편집 중)</strong><br /> </td> 
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
   <td> 받는 사람 - 환경<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 관리<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 공간<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 미리 정의된 오퍼 필터<br /> </td> 
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
   <td> 오퍼 범주<br /> </td> 
   <td> 읽기/쓰기<br /> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>게재 관리자(편집 중)</strong><br /> </td> 
   <td> <strong>게재 관리자(live)</strong><br /> </td> 
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
   <td> 받는 사람 - 환경<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
  <tr> 
   <td> 관리<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공간<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 미리 정의된 오퍼 필터<br /> </td> 
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
   <td> 오퍼 범주<br /> </td> 
   <td> </td> 
   <td> 읽기<br /> </td> 
  </tr> 
 </tbody> 
</table>

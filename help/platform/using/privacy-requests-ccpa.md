---
product: campaign
title: 개인 정보 판매 옵트아웃
description: 개인 데이터 판매 옵트아웃에 대해 알아보기
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---

# 개인 정보 판매 옵트아웃(CCPA) {#sale-of-personal-information-ccpa}

![](../../assets/common.svg)

**CCPA**(California Consumer Privacy Act)는 캘리포니아 거주자들에게 개인 정보에 대한 새로운 권리를 제공하고 캘리포니아에서 비즈니스를 수행하는 특정 엔터티에 데이터 보호 책임을 부과합니다.

액세스 및 삭제 요청의 구성 및 사용은 GDPR과 CCPA와 공통됩니다. 이 섹션에서는 CCPA에만 해당되는 개인 데이터 판매에 대한 옵트아웃을 제공합니다.

Adobe Campaign이 제공하는 [동의 관리](privacy-management.md#consent-management) 도구 외에도 소비자가 개인 정보 판매를 옵트아웃했는지 여부를 추적할 수 있습니다.

연락처 주인은 시스템을 통해 자신의 개인 정보를 서드파티에 판매하는 것을 허용하지 않기로 결정할 수 있습니다. Adobe Campaign에서 이 정보를 저장하고 추적할 수 있습니다.

이 작업을 수행하려면 프로필 테이블을 확장하고 **[!UICONTROL Opt-Out for CCPA]** 필드를 추가해야 합니다.

>[!IMPORTANT]
>
>데이터 주체의 요청을 받고 CCPA에 대한 요청 날짜를 추적하는 것은 데이터 컨트롤러로서의 책임입니다. 기술 제공업체에서는 수신 거부 방법만 제공합니다. 데이터 컨트롤러로서의 역할에 대한 자세한 내용은 [개인 데이터 및 가상 사용자를 참조하십시오](privacy-and-recommendations.md#personal-data).

## 사전 요구 사항 {#ccpa-prerequisite}

이 정보를 활용하려면 Adobe Campaign Classic에서 이 필드를 만들어야 합니다. 이 경우 부울 필드를 **[!UICONTROL Recipient]** 테이블에 추가합니다. 새 필드를 만들면 Campaign API에서 자동으로 지원됩니다.

사용자 지정 수신자 테이블을 사용하는 경우 이 작업도 수행해야 합니다.

새 필드를 만드는 방법에 대한 자세한 내용은 [스키마 버전 설명서](../../configuration/using/about-schema-edition.md)를 참조하십시오.

>[!IMPORTANT]
>
>스키마 수정은 전문가만 수행해야 하는 중요한 작업입니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**(으)로 이동한 다음 **[!UICONTROL Document type]**&#x200B;로 **[!UICONTROL Recipients]**&#x200B;를 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다. 테이블에 필드를 추가하는 방법에 대한 자세한 내용은 [이 섹션](../../configuration/using/new-field-wizard.md)을 참조하십시오.

   ![](assets/privacy-ccpa-1.png)

1. **[!UICONTROL Field type]**&#x200B;에는 **[!UICONTROL SQL field]**&#x200B;을(를) 선택합니다. 레이블에는 **[!UICONTROL Opt-Out for CCPA]**&#x200B;을(를) 사용합니다. **[!UICONTROL 8-bit integer (boolean)]** 유형을 선택하고 다음의 고유한 **[!UICONTROL Relative path]**&#x200B;을(를) 정의합니다. @OPTOUTCCPA. **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

   ![](assets/privacy-ccpa-2.png)

   이렇게 하면 **[!UICONTROL Recipient (cus)]** 스키마가 확장되거나 생성됩니다. 필드를 클릭하여 필드가 올바르게 추가되었는지 확인합니다.

   ![](assets/privacy-ccpa-3.png)

1. 탐색기의 **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** 노드를 클릭합니다. **[!UICONTROL Recipient (nms)]**&#x200B;의 &quot;일반 패키지&quot;에서 `<input>` 요소를 추가하고 2단계에서 정의된 상대 경로인 xpath 값에 사용합니다. 양식 식별에 대한 자세한 내용은 [이 섹션](../../configuration/using/identifying-a-form.md)을 참조하십시오.

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. 연결을 끊고 다시 연결합니다. 다음 섹션에서 설명하는 단계에 따라 필드를 수신자의 세부 정보에서 사용할 수 있는지 확인합니다.

## 사용 {#usage}

필드의 값을 채우고 데이터 판매에 관한 CCPA 지침 및 규칙을 따르는 것은 데이터 컨트롤러의 책임입니다.

값을 채우려면 다음과 같은 몇 가지 방법을 사용할 수 있습니다.

* 수신자의 세부 정보를 편집하여 Campaign의 인터페이스 사용
* API 사용
* 데이터 가져오기 작업 과정을 통해

그런 다음 옵트아웃한 프로필의 개인 정보를 제3자에게 판매해서는 안 됩니다.

1. 옵트아웃 상태를 변경하려면 **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]**(으)로 이동하여 수신자를 선택합니다. **[!UICONTROL General]** 탭에서는 이전 섹션에 구성된 필드가 표시됩니다.

   ![](assets/privacy-ccpa-5.png)

1. 옵트아웃 열이 표시되도록 수신자 목록을 구성합니다. 목록을 구성하는 방법을 알아보려면 [자세한 설명서](../../platform/using/adobe-campaign-workspace.md#configuring-lists)를 참조하십시오.

   ![](assets/privacy-ccpa-6.png)

1. 이 열을 클릭하여 옵트아웃 정보에 따라 수신자를 정렬할 수 있습니다. 옵트아웃한 수신자만 표시하는 필터를 만들 수도 있습니다. 필터를 만드는 방법에 대한 자세한 내용은 [이 섹션](../../platform/using/creating-filters.md)을 참조하십시오.

   ![](assets/privacy-ccpa-7.png)

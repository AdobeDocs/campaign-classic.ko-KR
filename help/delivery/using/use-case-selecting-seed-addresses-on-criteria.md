---
product: campaign
title: "사용 사례: 기준 시드 주소 선택"
description: "사용 사례: 기준 시드 주소 선택"
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# 활용 사례: 기준 시드 주소 선택{#use-case-selecting-seed-addresses-on-criteria}


게재 또는 캠페인의 프레임워크에서 **[!UICONTROL Edit the dynamic condition...]** 링크를 사용하면 특정 선택 기준에 따라 시드 주소를 선택할 수 있습니다.

이 사용 사례에서는 사이트가 **내 온라인 라이브러리** 고객의 문학적인 취향에 따라 뉴스레터를 개인화하고 싶습니다.

구매부서와 연계해 배달을 담당하는 이용자가 경찰소설을 구입한 구독자를 위한 뉴스레터를 만들었다.

최종 협업 결과를 공유하기 위해 배송 관리자는 구매 부서의 동료를 시드 주소로 배송에 추가하기로 합니다. 동적 조건을 사용하면 주소 구성 및 업데이트 시간을 절약할 수 있습니다.

동적 조건을 사용하려면 다음 조건을 충족해야 합니다.

* 게재를 보낼 준비가 되었습니다.
* 공통 값이 있는 시드 주소입니다. 이 값은 Adobe Campaign에 이미 존재하는 필드일 수 있습니다. 이 예에서 시드 주소는 기본적으로 애플리케이션에 존재하지 않는 &quot;부서&quot; 필드의 &quot;구매&quot; 값을 공유합니다.

## 1단계 - 게재 만들기 {#step-1---creating-a-delivery}

게재를 만드는 단계는 [이메일 게재 만들기](creating-an-email-delivery.md) 섹션.

이 예에서 게재 관리자는 뉴스레터를 생성하고 수신자를 선택했습니다.

![](assets/dlv_seeds_usecase_01.png)

## 2단계 - 공통 값 만들기 {#step-2---creating-a-common-value}

예제(구매 부서)의 값과 같은 공통 값을 생성하려면 먼저 를 확장해야 합니다. **데이터 스키마** 시드 주소 및 관련 입력 양식 편집

### 데이터 스키마 확장 {#extending-the-data-schema}

스키마 확장에 대한 자세한 내용은 [이 섹션](../../configuration/using/data-schemas.md).

1. 다음에서 **[!UICONTROL Administration > Configuration > Data schemas]** 노드를 클릭하고 **[!UICONTROL New]** 아이콘.
1. 다음에서 **[!UICONTROL Creation of a data schema]** 창에서 **[!UICONTROL Extension of a schema]** 옵션 및 클릭 **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. 다음 항목 선택 **[!UICONTROL Seed addresses]** 소스 스키마, 입력 **문서** (으)로 **[!UICONTROL Namespace]** 및 클릭 **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.
1. 스키마 편집 창에서 아래 줄을 복사하여 스크린샷에 표시된 영역에 붙여넣습니다.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   그런 다음 다음 다음 줄을 복사하여 아래에 붙여넣습니다. **[!UICONTROL Seed to insert in the export files]** 요소를 생성하지 않습니다.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   이 경우 이름이 인 새 열거형이 **[!UICONTROL Department]** 이(가) 시드 주소 테이블에 만들어졌으며 표준을 기반으로 합니다 **[!UICONTROL @company]** 열거형 템플릿(이름 아래에 레이블 지정됨) **회사** ( 시드 주소 양식)을 참조하십시오.

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.
1. 다음에서 **[!UICONTROL Tools > Advanced]** 메뉴에서 **[!UICONTROL Update database structure]** 옵션을 선택합니다.

   ![](assets/dlv_seeds_usecase_12.png)

1. 업데이트 마법사가 표시되면 **[!UICONTROL Next]** [테이블 편집] 창에 액세스하기 위한 단추: 시드 주소 데이터 스키마에서 변경을 수행하려면 구조를 갱신해야 합니다.

   ![](assets/dlv_seeds_usecase_13.png)

1. 업데이트를 실행할 페이지로 이동할 때까지 마법사를 따릅니다. **[!UICONTROL Start]** 버튼을 클릭합니다.

   ![](assets/dlv_seeds_usecase_14.png)

   업데이트가 완료되면 마법사를 닫을 수 있습니다.

1. 연결을 끊고 Adobe Campaign에 다시 연결합니다. 시드 주소 데이터 스키마에서 변경한 사항이 이제 적용됩니다. 시드 주소 화면에서 이를 보려면 관련 항목을 업데이트해야 합니다 **[!UICONTROL Input form]**. 다음을 참조하십시오. [입력 양식 업데이트](#updating-the-input-form) 섹션.

#### 연결된 테이블에서 데이터 스키마 확장 {#extending-the-data-schema-from-a-linked-table}

시드 주소 데이터 스키마는 수신자 데이터 스키마 - 수신자 (nms)에 연결된 테이블의 값을 사용할 수 있습니다.

예를 들어, 사용자는 **[!UICONTROL Internet Extension]** 다음에서 찾음: **[!UICONTROL Country]** 수신자 스키마에 연결된 테이블입니다.

![](assets/dlv_seeds_usecase_06.png)

따라서 섹션에 자세히 설명된 대로 시드 주소 데이터 스키마를 확장해야 합니다. 단, 통합할 코드 행은 **4단계** 은 다음과 같습니다.

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

다음 사항을 나타냅니다.

* 을 추가하여 라는 새 요소를 **[!UICONTROL Internet Extension]**,
* 이 요소는 **[!UICONTROL Country]** 테이블.

>[!CAUTION]
>
>연결된 테이블 이름에서 **xpath-dst** 연결된 테이블의
>
>다음에서 찾을 수 있습니다. **[!UICONTROL Country]** 요소를 추가합니다.

![](assets/dlv_seeds_usecase_07.png)

사용자는 다음 위치에서 팔로우할 수 있습니다. **5단계** 섹션에 있는 마지막 항목이 **[!UICONTROL Input form]** 시드 주소.

다음을 참조하십시오. [입력 양식 업데이트](#updating-the-input-form) 섹션.

#### 입력 양식 업데이트 {#updating-the-input-form}

1. 다음에서 **[!UICONTROL Administration > Configuration > Input forms]** 노드에서 시드 주소 입력 양식을 찾습니다.

   ![](assets/dlv_seeds_usecase_19.png)

1. 양식을 편집하고에 다음 줄을 삽입합니다. **[!UICONTROL Recipient]** 컨테이너.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 변경 내용을 저장합니다.
1. 시드 주소를 엽니다. 다음 **[!UICONTROL Department]** 필드에 다음이 표시됩니다. **[!UICONTROL Recipient]** 테이블.

   ![](assets/dlv_seeds_usecase_22.png)

1. 게재에 사용할 시드 주소를 편집하고 입력합니다 **구매** 을 의 값으로 **[!UICONTROL Department]** 필드.

## 3단계 - 조건 정의 {#step-3---defining-the-condition}

이제 게재에 대한 시드 주소의 동적 조건을 지정할 수 있습니다. 방법은 다음과 같습니다.

1. 게재를 엽니다.

   ![](assets/dlv_seeds_usecase_01.png)

1. 다음을 클릭합니다. **[!UICONTROL To]** 링크를 클릭한 다음 **[!UICONTROL Seed addresses]** 탭을 사용하여 액세스 **[!UICONTROL Edit the dynamic condition...]** 링크를 클릭합니다.

   ![](assets/dlv_seeds_usecase_02.png)

1. 원하는 시드 주소를 선택할 수 있는 표현식을 선택합니다. 여기에서 사용자는 **[!UICONTROL Department (@workField)]** 표현식.

   ![](assets/dlv_seeds_usecase_03.png)

1. 원하는 값을 선택합니다. 이 예에서 사용자는 **구매** 부서(값 드롭다운 목록)

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >이전에 만든 스키마 확장은 **수신자** 스키마. 위의 화면에 표시되는 값은 **수신자** 스키마.

1. **[!UICONTROL Ok]**&#x200B;를 클릭합니다.

   쿼리가 **[!UICONTROL Select target]** 창.

   ![](assets/dlv_seeds_usecase_04.png)

1. 클릭 **[!UICONTROL Ok]** 쿼리를 승인합니다.
1. 게재를 분석한 다음 **[!UICONTROL Delivery]** 탭으로 이동하여 게재 로그에 액세스합니다.

   구매 부서의 시드 주소는 수신자 또는 다른 시드 주소의 시드 주소와 마찬가지로 게재 보류 중으로 표시됩니다.

   ![](assets/dlv_seeds_usecase_05.png)

1. 다음을 클릭합니다. **[!UICONTROL Send]** 버튼을 클릭하여 게재를 시작합니다.

   구매 부서의 구성원은 이메일 받은 편지함에 게재를 받을 시드 주소의 일부를 구성합니다.

   ![](assets/dlv_seeds_usecase_18.png)

---
product: campaign
title: '"사용 사례: 기준 시드 주소 선택"'
description: '"사용 사례: 기준 시드 주소 선택"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---

# 사용 사례: 기준 시드 주소 선택{#use-case-selecting-seed-addresses-on-criteria}

게재 또는 캠페인의 프레임워크에서 **[!UICONTROL Edit the dynamic condition...]** 링크를 사용하면 특정 선택 기준에 따라 시드 주소를 선택할 수 있습니다.

이 사용 사례에서 사이트 **내 온라인 라이브러리**&#x200B;는 고객의 문학적 취미에 따라 Newsletter를 개인화하려는 것입니다.

구매 부서와 함께 배달을 담당하는 사용자는 경찰 소설을 구입한 구독자를 위한 뉴스레터를 만들었습니다.

게재 관리자는 이들의 공동 작업의 최종 결과를 공유하기 위해 구매 부서의 동료를 게재에 시드 주소로 추가하기로 합니다. 동적 조건을 사용하면 주소 구성 및 업데이트 시간을 절약할 수 있습니다.

동적 조건을 사용하려면 다음을 수행해야 합니다.

* 배송을 준비하고
* 공통 값을 갖는 시드 주소. 이 값은 Adobe Campaign에 이미 존재하는 필드일 수 있습니다. 이 예에서 시드 주소는 기본적으로 애플리케이션에 존재하지 않는 &quot;부서&quot; 필드에 &quot;구매&quot; 값을 공유합니다.

## 1단계 - 게재 만들기 {#step-1---creating-a-delivery}

게재를 만드는 단계는 [이메일 게재 만들기](creating-an-email-delivery.md) 섹션에 자세히 설명되어 있습니다.

이 예에서는 게재 관리자가 뉴스레터를 만들고 수신자를 선택했습니다.

![](assets/dlv_seeds_usecase_01.png)

## 2단계 - 공통 값 만들기 {#step-2---creating-a-common-value}

예제(구매 부서)의 공통 값과 같은 공통 값을 만들려면 먼저 시드 주소의 **데이터 스키마**&#x200B;를 확장하고 관련 입력 양식을 편집해야 합니다.

### 데이터 스키마 확장 {#extending-the-data-schema}

스키마 확장에 대한 자세한 내용은 [구성 안내서](../../configuration/using/data-schemas.md)를 참조하십시오.

1. **[!UICONTROL Administration > Configuration > Data schemas]** 노드에서 **[!UICONTROL New]** 아이콘을 클릭합니다.
1. **[!UICONTROL Creation of a data schema]** 창에서 **[!UICONTROL Extension of a schema]** 옵션을 선택하고 **[!UICONTROL Next]** 를 클릭합니다.

   ![](assets/dlv_seeds_usecase_09.png)

1. **[!UICONTROL Seed addresses]** 소스 스키마를 선택하고 **doc**&#x200B;를 **[!UICONTROL Namespace]** 로 입력하고 **[!UICONTROL Ok]**&#x200B;를 클릭합니다.

   ![](assets/dlv_seeds_usecase_10.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
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

   그런 다음 다음 다음 줄을 복사하여 **[!UICONTROL Seed to insert in the export files]** 요소 아래에 붙여넣습니다.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   이 경우, **[!UICONTROL Department]**&#x200B;이라는 새 열거형이 시드 주소 테이블에 만들어졌는지, 표준 **[!UICONTROL @company]** 열거형 템플릿(시드 주소 양식의 **Company** 이름 아래에 레이블 지정)을 기반으로 한다고 지정합니다.

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Tools > Advanced]** 메뉴에서 **[!UICONTROL Update database structure]** 옵션을 선택합니다.

   ![](assets/dlv_seeds_usecase_12.png)

1. 업데이트 마법사가 표시되면 **[!UICONTROL Next]** 버튼을 클릭하여 테이블 편집 창에 액세스합니다.시드 주소 데이터 스키마에서 수행되는 변경 사항은 구조 업데이트가 필요합니다.

   ![](assets/dlv_seeds_usecase_13.png)

1. 업데이트를 실행하기 위해 페이지가 나타날 때까지 마법사를 따릅니다. **[!UICONTROL Start]** 버튼을 클릭합니다.

   ![](assets/dlv_seeds_usecase_14.png)

   업데이트가 완료되면 마법사를 닫을 수 있습니다.

1. 연결을 끊은 다음 Adobe Campaign에 다시 연결합니다. 이제 시드 주소 데이터 스키마에서 변경된 사항이 적용됩니다. 시드 주소 화면에서 표시되도록 하려면 연결된 **[!UICONTROL Input form]**&#x200B;을 업데이트해야 합니다. [입력 양식 업데이트](#updating-the-input-form) 섹션을 참조하십시오.

#### 연결된 테이블에서 데이터 스키마 확장 {#extending-the-data-schema-from-a-linked-table}

시드 주소 데이터 스키마는 수신자 데이터 스키마 - 수신자(nms)에 연결된 테이블의 값을 사용할 수 있습니다.

예를 들어, 사용자는 수신자 스키마에 연결된 **[!UICONTROL Country]** 테이블에 있는 **[!UICONTROL Internet Extension]**&#x200B;을 통합하려고 합니다.

![](assets/dlv_seeds_usecase_06.png)

따라서 섹션에 자세히 설명된 대로 시드 주소 데이터 스키마를 확장해야 합니다. 그러나 **4단계**&#x200B;에 통합할 코드 줄은 다음과 같습니다.

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

다음 내용이 표시됩니다.

* 사용자가 **[!UICONTROL Internet Extension]**(이)라는 새 요소를 만들고자 하는 경우
* 이 요소는 **[!UICONTROL Country]** 테이블에서 가져옵니다.

>[!CAUTION]
>
>연결된 테이블 이름에서 해당 연결된 테이블의 **xpath-dst**&#x200B;를 지정해야 합니다.
>
>수신자 테이블의 **[!UICONTROL Country]** 요소에서 찾을 수 있습니다.

![](assets/dlv_seeds_usecase_07.png)

그런 다음 섹션의 **단계 5**&#x200B;에서 따르고 시드 주소의 **[!UICONTROL Input form]**&#x200B;를 업데이트할 수 있습니다.

[입력 양식 업데이트](#updating-the-input-form) 섹션을 참조하십시오.

#### 입력 양식 업데이트 {#updating-the-input-form}

1. **[!UICONTROL Administration > Configuration > Input forms]** 노드에서 시드 주소 입력 양식을 찾습니다.

   ![](assets/dlv_seeds_usecase_19.png)

1. 양식을 편집하고 **[!UICONTROL Recipient]** 컨테이너에 다음 줄을 삽입합니다.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. 변경 내용을 저장합니다.
1. 시드 주소를 엽니다. **[!UICONTROL Department]** 필드가 **[!UICONTROL Recipient]** 테이블에 나타납니다.

   ![](assets/dlv_seeds_usecase_22.png)

1. 게재에 사용할 시드 주소를 편집하고 **[!UICONTROL Department]** 필드에 **Purchasing**&#x200B;을 값으로 입력합니다.

## 3단계 - 조건 정의 {#step-3---defining-the-condition}

이제 게재할 시드 주소의 동적 조건을 지정할 수 있습니다. 방법은 다음과 같습니다.

1. 게재를 엽니다.

   ![](assets/dlv_seeds_usecase_01.png)

1. **[!UICONTROL To]** 링크를 클릭한 다음 **[!UICONTROL Seed addresses]** 탭을 클릭하여 **[!UICONTROL Edit the dynamic condition...]** 링크에 액세스합니다.

   ![](assets/dlv_seeds_usecase_02.png)

1. 원하는 시드 주소를 선택할 수 있는 표현식을 선택합니다. 여기서 사용자가 **[!UICONTROL Department (@workField)]** 표현식을 선택합니다.

   ![](assets/dlv_seeds_usecase_03.png)

1. 원하는 값을 선택합니다. 이 예제에서는 사용자가 값 드롭다운 목록에서 **Purchasing** 부서를 선택합니다.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >앞에서 만든 스키마 확장은 **수신자** 스키마에서 가져옵니다. 위의 화면에 표시되는 값은 **recipient** 스키마의 열거형에서 가져옵니다.

1. **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다.

   쿼리가 **[!UICONTROL Select target]** 창에 표시됩니다.

   ![](assets/dlv_seeds_usecase_04.png)

1. **[!UICONTROL Ok]** 을 클릭하여 쿼리를 승인합니다.
1. 게재를 분석한 다음 **[!UICONTROL Delivery]** 탭을 클릭하여 게재 로그에 액세스합니다.

   구매 부서의 시드 주소는 수신자나 다른 시드 주소와 마찬가지로 보류 중인 게재로 표시됩니다.

   ![](assets/dlv_seeds_usecase_05.png)

1. **[!UICONTROL Send]** 버튼을 클릭하여 배달을 시작합니다.

   구매 부서의 회원들은 이메일 받은 편지함에서 배달을 받을 시드 주소의 일부를 구성합니다.

   ![](assets/dlv_seeds_usecase_18.png)

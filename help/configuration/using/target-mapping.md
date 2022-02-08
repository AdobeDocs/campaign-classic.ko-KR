---
product: campaign
title: 대상 매핑
description: 대상 매핑을 만드는 방법을 알아봅니다
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 2%

---

# 대상 매핑{#target-mapping}

![](../../assets/common.svg)

다음 두 가지 경우 대상 매핑 작성이 필요합니다.

* Adobe Campaign에서 제공한 수신자 테이블 이외의 수신자 테이블을 사용하는 경우
* 대상 매핑 화면에서 표준 타깃팅 차원과 다른 필터링 차원을 구성하는 경우,

대상 매핑 생성 마법사는 사용자 지정 테이블을 사용하는 데 필요한 모든 스키마를 만드는 데 도움이 됩니다.

## 사용자 지정 테이블에 연결된 스키마 만들기 및 구성 {#creating-and-configuring-schemas-linked-to-the-custom-table}

대상 매핑을 만들기 전에 Adobe Campaign이 새 수신자 데이터 스키마로 작동하려면 몇 가지 구성이 필요합니다.

그렇게 하려면 다음 단계를 적용합니다.

1. 사용하려는 사용자 지정 테이블의 필드를 통합하는 새 데이터 스키마를 만듭니다.

   자세한 내용은 [스키마 참조(xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   이 예제에서는 다음 필드를 포함하는 매우 간단한 테이블인 고객 스키마를 만듭니다. ID, 이름, 성, 이메일 주소, 휴대폰 번호. 목적은 이 표에 저장된 개인에게 이메일 또는 SMS 경고를 보낼 수 있도록 하는 것입니다.

   예제 스키마(cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. =&quot;true&quot; 속성을 사용하여 스키마를 외부 보기로 선언합니다. 을(를) 참조하십시오. [보기 속성](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. DM 주소를 추가해야 하는 경우 다음 유형의 구조를 사용하십시오.

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. 을(를) 클릭합니다. **[!UICONTROL Administration > Campaign management > Target mappings]** 노드 아래에 있어야 합니다.
1. 을(를) 클릭합니다. **새로 만들기** 단추를 클릭하여 대상 매핑 생성 마법사를 엽니다.
1. 을(를) 입력합니다. **레이블** 필드를 작성하고 에서 방금 만든 스키마를 선택합니다 **타겟팅 차원** 필드.

   ![](assets/mapping_diffusion_wizard_1.png)

1. 에서 **주소 양식 편집** 창에서 다양한 배달 주소와 일치하는 스키마 필드를 선택합니다. 여기서는 **@email** 및 **@mobile** 필드.

   ![](assets/mapping_diffusion_wizard_2.png)

1. 다음 **스토리지** 창에서 **확장 스키마의 접미사** 필드를 사용하여 새 스키마를 Adobe Campaign에서 제공하는 기본 스키마와 구별할 수 있습니다.

   클릭 **[!UICONTROL Define new additional fields]** 을 클릭하여 게재에서 타겟팅할 차원을 선택합니다.

   기본적으로 제외 관리는 메시지와 동일한 테이블에 저장됩니다.

   을(를) 확인합니다. **추적을 위한 스토리지 스키마 생성** 대상 매핑에 연결된 추적에 대한 저장소를 구성하려면 상자를 선택합니다.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign은 동일한 브로드로그 및/또는 trackinglog 스키마에 연결된 타겟팅 스키마와 같은 여러 수신자 스키마를 지원하지 않습니다. 그렇지 않으면 나중에 데이터 조정에서 예외 항목이 발생할 수 있습니다. 자세한 내용은 [권장 사항 및 제한 사항](../../configuration/using/about-custom-recipient-table.md) 페이지.

1. 에서 **확장** 창에서 생성하려는 선택적 스키마를 선택합니다(사용 가능한 스키마 목록은 Adobe Campaign 플랫폼에 설치된 모듈에 따라 다름).

   ![](assets/mapping_diffusion_wizard_4.png)

1. 을(를) 클릭합니다. **저장** 단추를 클릭하여 마법사를 닫습니다.

   마법사는 시작 스키마를 사용하여 새 대상 매핑이 작동되도록 하는 데 필요한 다른 모든 스키마를 만듭니다.

   ![](assets/mapping_schema_list.png)

## 대상 매핑 사용 {#using-target-mapping}

새 스키마를 게재 대상으로 사용하는 방법에는 두 가지가 있습니다.

* 매핑을 기반으로 하나 이상의 게재 템플릿 만들기
* 아래 그림과 같이 게재를 만들 때 대상 선택 중에 직접 매핑을 선택합니다.

![](assets/mapping_selection_ciblage.png)

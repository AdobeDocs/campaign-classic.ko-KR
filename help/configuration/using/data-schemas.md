---
title: 데이터 스키마
seo-title: 데이터 스키마
description: 데이터 스키마
seo-description: null
page-status-flag: never-activated
uuid: 9f08750a-e125-4531-8c2c-1ab218190210
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b65e8d27-f427-464e-ad42-51c0a88eee86
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 데이터 스키마{#data-schemas}

## 원칙 {#principles}

스키마를 편집, 생성 및 구성하려면 Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Administration > Configuration > Data schemas]** 노드를 클릭합니다.

>[!NOTE]
>
>기본 데이터 스키마는 Adobe Campaign Classic 콘솔의 관리자만 삭제할 수 있습니다.

![](assets/d_ncs_integration_schema_navtree.png)

편집 필드에는 소스 스키마의 XML 내용이 표시됩니다.

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>&quot;이름&quot; 편집 컨트롤을 사용하면 이름 및 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 스키마의 루트 요소의 &quot;name&quot; 및 &quot;namespace&quot; 속성은 스키마의 XML 편집 영역에서 자동으로 업데이트됩니다.

미리 보기는 확장 스키마를 자동으로 생성합니다.

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>소스 스키마가 저장되면 확장 스키마 생성이 자동으로 시작됩니다.

스키마의 전체 구조를 확인해야 하는 경우 미리 보기 탭을 사용할 수 있습니다. 스키마가 확장되면 모든 확장자를 시각화할 수 있습니다. 문서 탭에는 모든 스키마 속성 및 요소와 속성(SQL 필드, 유형/길이, 레이블, 설명)이 표시됩니다. 설명서 탭은 생성된 스키마에만 적용됩니다. 자세한 내용은 스키마 [재생성](../../configuration/using/regenerating-schemas.md) 섹션을 참조하십시오.

## 예:계약 테이블 생성 {#example--creating-a-contract-table}

다음 예에서는 Adobe Campaign 데이터베이스의 데이터베이스 모델에서 **계약에** 대한 새 테이블을 만듭니다. 이 표를 사용하면 각 계약에 대해 보유자 및 공유자의 이름과 이메일 주소를 저장할 수 있습니다.

이렇게 하려면 테이블의 스키마를 만들고 데이터베이스 구조를 업데이트하여 해당 테이블을 생성해야 합니다. 다음 단계를 적용합니다.

1. Adobe Campaign 트리의 **[!UICONTROL Administration > Configuration > Data schemas]** 노드를 편집하고 을 클릭합니다 **[!UICONTROL New]** .
1. 옵션을 **[!UICONTROL Create a new table in the data model]** 선택하고 을 클릭합니다 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. 테이블과 네임스페이스의 이름을 지정합니다.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >기본적으로 사용자가 만든 스키마는 &#39;cus&#39; 네임스페이스에 저장됩니다. 자세한 내용은 스키마 [식별을 참조하십시오](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. 표의 컨텐츠를 만듭니다. 누락된 설정이 없는지 확인하려면 시작 마법사를 사용하는 것이 좋습니다. 이렇게 하려면 **[!UICONTROL Insert]** 단추를 클릭하고 추가할 설정 유형을 선택합니다.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. 계약 테이블에 대한 설정을 정의합니다.

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   계약 유형을 추가하고 계약 번호에 색인을 배치합니다.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. 스키마를 저장하여 구조를 생성합니다.

   ![](assets/s_ncs_configuration_structure.png)

1. 스키마를 연결할 테이블을 만들려면 데이터베이스 구조를 업데이트합니다. 자세한 내용은 데이터베이스 [구조](../../configuration/using/updating-the-database-structure.md)업데이트를 참조하십시오.


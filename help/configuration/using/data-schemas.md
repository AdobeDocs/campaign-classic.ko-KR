---
product: campaign
title: 데이터 스키마
description: Campaign 데이터 스키마 시작
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---

# 데이터 스키마{#data-schemas}

## 원칙 {#principles}

스키마를 편집, 생성 및 구성하려면 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign 클라이언트 콘솔의 노드입니다.

>[!NOTE]
>
>기본 제공 데이터 스키마는 Adobe Campaign Classic 콘솔의 관리자만 삭제할 수 있습니다.

![](assets/d_ncs_integration_schema_navtree.png)

편집 필드에는 소스 스키마의 XML 콘텐츠가 표시됩니다.

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>이름 편집 컨트롤을 사용하면 이름과 네임스페이스로 구성된 스키마 키를 입력할 수 있습니다. 스키마의 루트 요소에 대한 &quot;name&quot; 및 &quot;namespace&quot; 속성은 스키마의 XML 편집 영역에서 자동으로 업데이트됩니다.

미리보기는 확장 스키마를 자동으로 생성합니다.

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>소스 스키마를 저장하면 확장 스키마 생성이 자동으로 실행됩니다.

스키마의 전체 구조를 확인해야 하는 경우 미리보기 탭을 사용할 수 있습니다. 스키마가 확장된 경우 모든 해당 확장을 시각화할 수 있습니다. 보완적으로 문서 탭에는 모든 스키마 속성 및 요소와 해당 속성(SQL 필드, 유형/길이, 레이블, 설명)이 표시됩니다. 설명서 탭은 생성된 스키마에만 적용됩니다. 자세한 내용은 [스키마 다시 생성](../../configuration/using/regenerating-schemas.md) 섹션.

## 예: 계약 테이블 생성 {#example--creating-a-contract-table}

다음 예제에서는 새 테이블을 **계약** (Adobe Campaign 데이터베이스의 데이터베이스 모델). 이 테이블을 사용하면 각 계약에 대한 보유자 및 공동 보유자의 이름과 성 및 이메일 주소를 저장할 수 있습니다.

이렇게 하려면 테이블의 스키마를 만들고 데이터베이스 구조를 업데이트하여 해당 테이블을 생성해야 합니다. 다음 단계를 적용합니다.

1. 편집 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign 트리의 노드 및 클릭 **[!UICONTROL New]** .
1. 다음을 선택합니다. **[!UICONTROL Create a new table in the data model]** 옵션 및 클릭 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. 테이블 이름 및 네임스페이스를 지정합니다.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >기본적으로 사용자가 만든 스키마는 &#39;cus&#39; 네임스페이스에 저장됩니다. 자세한 내용은 다음을 참조하십시오. [스키마 식별](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. 테이블의 내용을 만듭니다. 시작 마법사를 사용하여 설정이 누락되지 않았는지 확인하는 것이 좋습니다. 이렇게 하려면 **[!UICONTROL Insert]** 버튼을 클릭하고 추가할 설정 유형을 선택합니다.

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

   계약 유형을 추가하고 계약 번호에 인덱스를 지정합니다.

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

1. 데이터베이스 구조를 업데이트하여 스키마가 연결될 테이블을 만듭니다. 자세한 내용은 다음을 참조하십시오. [데이터베이스 구조 업데이트](../../configuration/using/updating-the-database-structure.md).

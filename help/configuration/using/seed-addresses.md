---
product: campaign
title: 시드 주소
description: 시드 주소
role: Data Engineer, Developer
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 6%

---

# 시드 주소{#seed-addresses}



수신자 테이블이 사용자 지정 테이블인 경우 추가 구성이 필요합니다. 다음 **[!UICONTROL nms:seedMember]** 스키마를 확장해야 합니다. 아래에서 보듯이 적절한 필드를 정의하기 위해 시드 주소에 탭이 더 추가됩니다.

![](assets/s_ncs_user_seedlist_new_tab.png)

시드 주소 사용에 대한 자세한 내용은 을 참조하십시오. [이 섹션](../../delivery/using/about-seed-addresses.md).

## 구현 {#implementation}

다음 **nms:seedMember** 기본 제공되는 스키마 및 연결된 양식은 필요한 모든 필드를 참조하기 위해 고객 구성을 위해 확장되어야 합니다. 스키마 정의에는 구성 모드를 자세히 설명하는 주석이 포함되어 있습니다.

수신자 테이블 확장 스키마의 정의:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

다음 단계를 적용합니다.

1. 의 확장을 만듭니다. **nms:seedMember** 스키마. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/extending-a-schema.md)을 참조하십시오.
1. 이 새 확장에서 의 루트에 새 요소를 추가합니다. **[!UICONTROL seedMember]** 다음 매개 변수를 사용하여

   ```
   name="custom_customNamespace_customSchema"
   ```

   이 요소에는 캠페인을 내보내는 데 필요한 필드가 포함되어야 합니다. 이러한 필드의 이름은 외부 스키마의 해당 필드와 동일해야 합니다. 예를 들어 스키마가 **[!UICONTROL cus:person]** , **[!UICONTROL nms:seedMember]** 스키마는 다음과 같이 확장되어야 합니다.

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >의 확장 **nms:seedMember** 스키마는 Adobe Campaign의 캠페인 및 게재 구조를 준수해야 합니다.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 확장 중에 다음을 지정해야 합니다 **SQL 이름(@sqlname)** 이메일 필드. SQL 이름은 수신자 스키마에 대해 예약된 &#39;sEmail&#39;과 달라야 합니다.
   >    * 확장할 때 생성된 스키마로 데이터베이스 구조를 업데이트해야 합니다 **nms:seedMember**.
   >    * 다음에서 **nms:seedMember** 확장 프로그램, 이메일 주소가 포함된 필드는 다음과 같아야 합니다. **name=&quot;email&quot;** 를 속성으로 사용하십시오. SQL 이름은 수신자 스키마에 이미 사용된 &#39;sEmail&#39;과 달라야 합니다. 이 속성은 바로 아래에 선언되어야 합니다. **`<element name="custom_cus_person" />`** 요소를 생성하지 않습니다.
   >    
   >

1. 수정 **[!UICONTROL seedMember]** 에 새 &quot;내부 수신자&quot; 탭을 정의할 수 있는 양식 **[!UICONTROL Seed addresses]** 창. 자세한 정보는 이 [페이지](../../configuration/using/form-structure.md)를 참조하십시오.

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

시드 주소의 모든 속성을 입력하지 않으면 Adobe Campaign은 프로필을 자동으로 대체합니다. 기존 프로필의 데이터를 사용하여 개인화하는 동안 이 속성을 자동으로 입력합니다.

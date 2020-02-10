---
title: 시드 주소
seo-title: 시드 주소
description: 시드 주소
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 시드 주소{#seed-addresses}

수신자 테이블이 사용자 정의 테이블인 경우 추가 구성이 필요합니다. 스키마를 확장해야 **[!UICONTROL nms:seedMember]** 합니다. 아래와 같이 적절한 필드를 정의하기 위한 추가 탭이 시드 주소에 추가됩니다.

![](assets/s_ncs_user_seedlist_new_tab.png)

시드 주소 사용에 대한 자세한 내용은 [이 섹션을](../../delivery/using/about-seed-addresses.md)참조하십시오.

## 구현 {#implementation}

nms: **seedMember** 스키마와 즉시 제공되는 연결된 양식은 고객 구성을 위해 확장되어야 하며 필요한 모든 필드를 참조합니다. 스키마 정의에는 구성 모드를 설명하는 주석이 포함되어 있습니다.

받는 사람 테이블 확장 스키마 정의:

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

1. nms:seedMember **스키마의 확장을** 만듭니다. 자세한 내용은 스키마 [확장을](../../configuration/using/extending-a-schema.md)참조하십시오.
1. 이 새 확장 기능에서 다음 매개 변수를 사용하여 루트에 새 요소를 **[!UICONTROL seedMember]** 추가합니다.

   ```
   name="custom_customNamespace_customSchema"
   ```

   이 요소에는 캠페인을 내보내는 데 필요한 필드가 포함되어야 합니다. 이러한 필드는 외부 스키마의 해당 필드와 동일한 이름을 가져야 합니다. 예를 들어 스키마가 **[!UICONTROL cus:person]** 있는 경우 **[!UICONTROL nms:seedMember]** 다음과 같이 스키마를 확장해야 합니다.

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
   >nms: **seedMember** 스키마의 확장은 캠페인 구조와 Adobe Campaign의 전달을 준수해야 합니다.

   >[!CAUTION]
   >
   >
   >    
   >    
   >    * 확장 중에 &#39;email&#39; 필드에 **SQL 이름(@sqlname)** 을 지정해야 합니다. SQL 이름은 받는 사람 스키마용으로 예약된 &#39;sEmail&#39;과 달라야 합니다.
   >    * nms:seedMember를 확장할 때 생성된 스키마로 데이터베이스 구조를 **업데이트해야 합니다**.
   >    * nms: **seedMember** 확장명에 있는 필드에는 **name=&quot;email&quot;** 속성이 있어야 합니다. SQL 이름은 받는 사람 스키마에 이미 사용되는 &#39;sEmail&#39;과 달라야 합니다. 이 속성은 **`<element name="custom_cus_person" />`** 요소 아래에 즉시 선언되어야 합니다.


1. 따라서 **[!UICONTROL seedMember]** 양식을 수정하여 **[!UICONTROL Seed addresses]** 창에서 새 &quot;내부 수신자&quot; 탭을 정의합니다. 자세한 내용은 양식 구조를 [참조하십시오](../../configuration/using/form-structure.md).

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

시드 주소의 모든 속성을 입력하지 않으면 Adobe Campaign은 자동으로 프로파일을 대체합니다.기존 프로필의 데이터를 사용하여 개인화하는 동안 자동으로 입력됩니다.

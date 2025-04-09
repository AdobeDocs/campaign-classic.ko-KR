---
product: campaign
title: 시드 주소
description: 시드 주소
role: Data Engineer, Developer
badge-v8: label="다음 대상에도 적용 v8" type="Positive" tooltip="다음 대상에도 적용 Campaign v8"
feature: Seed Address
level: Intermediate, Experienced
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 6%

---

# 시드 주소{#seed-addresses}



수신자 테이블이 사용자 지정 테이블인 경우 추가 구성이 필요합니다. 스키마를 **[!UICONTROL nms:seedMember]** 확장해야 합니다. 적절한 필드를 정의하기 위해 아래와 같이 시드 주소에 추가 탭이 추가됩니다.

![](assets/s_ncs_user_seedlist_new_tab.png)

시드 주소 사용에 대한 자세한 내용은 이 섹션을](../../delivery/using/about-seed-addresses.md) 참조하십시오[.

## 이행 {#implementation}

**nms:seedMember** 즉시 제공되는 스키마 및 연결된 양식은 필요한 모든 필드를 참조하기 위해 고객 구성을 위해 확장되어야 합니다. 스키마 정의에는 구성 모드를 자세히 설명하는 댓글 등이 들어 있습니다.

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

다음 단계를 적용 합니다.

1. nms:seedMember **스키마의 확장을**&#x200B;만들기. 이 작업에 대한 자세한 정보는 [이 섹션](../../configuration/using/extending-a-schema.md)을 참조하십시오.
1. 이 새 확장에서 다음 매개 변수를 사용하여 루트 **[!UICONTROL seedMember]** 에 새 요소를 추가합니다.

   ```
   name="custom_customNamespace_customSchema"
   ```

   이 요소에는 캠페인을 내보내는 데 필요한 필드가 포함되어야 합니다. 이러한 필드는 외부 스키마의 해당 필드와 이름이 같아야 합니다. 예를 들어 스키마가 **[!UICONTROL cus:person]** 인 경우 스키마를 **[!UICONTROL nms:seedMember]** 다음과 같이 확장해야 합니다.

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
   >nms:seedMember **스키마의**&#x200B;확장은 Adobe Campaign의 캠페인 및 게재 구조를 준수해야 합니다.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 확장 중에 &#39;이메일&#39; 필드에 SQL 이름(@sqlname)**을 지정**&#x200B;해야 합니다. SQL 이름은 받는 사람 스키마에 예약된 &#39;sEmail&#39;과 달라야 합니다.
   >    * nms:seedMember **를 확장할**&#x200B;때 생성된 스키마로 데이터베이스 구조를 업데이트해야 합니다.
   >    * nms:seedMember 확장에서 **이메일 주소가 포함된 필드에는 속성으로 name=&quot;email&quot;**&#x200B;이 있어야 합니다&#x200B;**.** SQL 이름은 받는 사람 스키마에 이미 사용된 &#39;sEmail&#39;과 달라야 합니다. 이 특성은 요소 아래에 **`<element name="custom_cus_person" />`** 즉시 선언되어야 합니다.
   >    
   >

1. 그에 따라 양식을 수정 **[!UICONTROL seedMember]** 하여 창에서 새 &quot;내부 수신자&quot; 탭 **[!UICONTROL Seed addresses]** 정의를 수행합니다. 자세한 정보는 이 [페이지](../../configuration/using/form-structure.md)를 참조하십시오.

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

시드 주소의 모든 속성이 입력되지 않은 경우 Adobe Campaign은 자동으로 프로필을 대체합니다. 기존 프로필의 데이터를 사용하여 개인화 중에 자동으로 입력됩니다.

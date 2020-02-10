---
title: 타겟 매핑
seo-title: 타겟 매핑
description: 타겟 매핑
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8b3ab02d1fd90c3f14314508a8fa7d99df82436c

---


# 타겟 매핑{#target-mapping}

다음 두 가지 경우 타겟 매핑 생성이 필요합니다.

* adobe Campaign에서 제공한 수신자 테이블 이외의 수신자 테이블을 사용하는 경우,
* 대상 매핑 화면의 표준 타깃팅 차원과 다른 필터링 차원을 구성하는 경우

대상 매핑 생성 마법사를 사용하면 사용자 지정 테이블을 사용하는 데 필요한 모든 스키마를 만들 수 있습니다.

## 사용자 정의 테이블에 연결된 스키마 만들기 및 구성 {#creating-and-configuring-schemas-linked-to-the-custom-table}

타겟 매핑을 만들기 전에 Adobe Campaign이 새 수신자 데이터 스키마와 연동되도록 하기 위해 여러 구성이 필요합니다.

이렇게 하려면 다음 단계를 적용합니다.

1. 사용할 사용자 지정 테이블의 필드를 통합하는 새 데이터 스키마를 만듭니다.

   자세한 내용은 스키마 [참조(xtk:srcSchema)를](../../configuration/using/about-schema-reference.md)참조하십시오.

   이 예에서는 다음 필드를 포함하는 매우 간단한 테이블인 고객 스키마를 만듭니다.ID, 이름, 성, 이메일 주소, 휴대폰 번호. 이 이메일이나 문자 메시지를 이 표에 저장된 개인에게 보낼 수 있는 것이 목표입니다.

   스키마 예(cus:individual)

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

1. =&quot;true&quot; 속성을 사용하여 스키마를 외부 보기로 선언합니다. 보기 [속성을](../../configuration/using/schema-characteristics.md#the-view-attribute)참조하십시오.

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

1. 노드를 **[!UICONTROL Administration > Campaign management > Target mappings]** 클릭합니다.
1. 새로 **만들기** 단추를 클릭하여 대상 매핑 생성 마법사를 엽니다.
1. 레이블 **필드를** 입력하고 타깃팅 차원 **필드에 방금 만든** 스키마를 선택합니다.

   ![](assets/mapping_diffusion_wizard_1.png)

1. 주소 **양식** 편집 창에서 다양한 배달 주소와 일치하는 스키마 필드를 선택합니다. 여기에서 **@email** 및 **@mobile** 필드를 매핑할 수 있습니다.

   ![](assets/mapping_diffusion_wizard_2.png)

1. 다음 **저장소** 창에서 확장 스키마 **** 접미사 필드를 입력하여 새 스키마를 Adobe Campaign에서 제공하는 기본 스키마와 구별합니다.

   을 **[!UICONTROL Define new additional fields]** 클릭하여 게재에서 타깃팅할 차원을 선택합니다.

   기본적으로 제외 관리는 메시지와 동일한 테이블에 저장됩니다. 타겟 **매핑에 연결된 추적에 대한 저장소를 구성하려면 추적할** 스토리지 스키마 생성 상자를 선택합니다.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!CAUTION]
   >
   >Adobe Campaign은 타깃팅 스키마로 알고 있는 여러 수신자 스키마를 지원하지 않습니다. 동일한 브로드로그 및/또는 추적 로그 스키마에 연결되어 있습니다. 그렇지 않으면 나중에 데이터 조정에서 예외 항목이 발생할 수 있습니다. 자세한 내용은 권장 사항 및 제한 [사항](../../configuration/using/about-custom-recipient-table.md) 페이지를 참조하십시오.

1. 확장 **창에서** 생성할 선택적 스키마를 선택합니다(사용 가능한 스키마 목록은 Adobe Campaign 플랫폼에 설치된 모듈에 따라 다름).

   ![](assets/mapping_diffusion_wizard_4.png)

1. 저장 **단추를** 클릭하여 마법사를 닫습니다.

   마법사는 시작 스키마를 사용하여 새 대상 매핑을 수행하는 데 필요한 다른 모든 스키마를 만듭니다.

   ![](assets/mapping_schema_list.png)

## 대상 매핑 사용 {#using-target-mapping}

새 스키마를 배달 대상으로 사용하는 방법에는 두 가지가 있습니다.

* 매핑을 기반으로 하나 이상의 배달 템플릿 만들기
* 아래 그림과 같이 배달을 만들 때 대상 선택 중에 직접 매핑을 선택합니다.

![](assets/mapping_selection_ciblage.png)

**관련 항목**

* [고객 요청에 신속하게 응답하여 데이터 액세스](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)
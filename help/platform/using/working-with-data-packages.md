---
solution: Campaign Classic
product: campaign
title: 데이터 패키지 작업
description: 데이터 패키지 작업
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '2442'
ht-degree: 2%

---


# 데이터 패키지 사용{#working-with-data-packages}

## 데이터 패키지 {#about-data-packages} 정보

Adobe Campaign을 사용하면 패키지 시스템을 통해 플랫폼 구성 및 데이터를 내보내거나 가져올 수 있습니다. 패키지에는 서로 다른 종류의 구성, 요소 또는 필터링되거나 포함되지 않을 수 있습니다.

데이터 패키지를 사용하면 Adobe Campaign 데이터베이스의 엔터티가 XML 형식의 파일을 통해 표시될 수 있습니다. 패키지에 포함된 각 엔티티는 모든 데이터로 표시됩니다.

**데이터 패키지**&#x200B;의 원칙은 데이터 구성을 내보내고 다른 Adobe Campaign 시스템에 통합하는 것입니다. 이 [섹션](#data-package-best-practices)에서 일관된 데이터 패키지 집합을 유지 관리하는 방법을 알아봅니다.

### 패키지 유형 {#types-of-packages}

내보낼 수 있는 패키지의 유형은 다음과 같습니다.사용자 패키지, 플랫폼 패키지 및 관리 패키지.

* **사용자 패키지**:내보낼 엔티티 목록을 선택할 수 있습니다. 이 유형의 패키지는 종속성을 관리하고 오류를 확인합니다.
* **플랫폼 패키지**:여기에는 추가된 모든 기술 리소스(비표준)가 포함됩니다.스키마, JavaScript 코드 등

   ![](assets/ncs_datapackage_package_platform.png)

* **관리 패키지**:여기에는 추가된 모든 템플릿과 비즈니스 개체(비표준)가 포함되어 있습니다.템플릿, 라이브러리 등

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>**platform** 및 **admin** 유형에는 내보낼 사전 정의된 개체 목록이 포함되어 있습니다. 각 엔티티는 만든 패키지의 바로 사용 가능한 리소스를 제거할 수 있는 필터링 조건에 연결됩니다.

## 데이터 구조 {#data-structure}

데이터 패키지에 대한 설명은 **xrk:navtree** 데이터 스키마의 문법을 준수하는 구조화된 XML 문서입니다.

데이터 패키지 예:

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

XML 문서는 **`<package>`** 요소로 시작하고 끝나야 합니다. 문서 유형별로 데이터를 배포하는 모든 **`<entities>`** 요소

**`<entities>`** 요소에는 **schema** 특성에 입력한 데이터 스키마 형식의 패키지 데이터가 포함됩니다.

패키지의 데이터에는 자동 생성된 키(**자동 생성** 옵션)와 같이 기본 간에 호환하지 않는 내부 키가 포함되어야 합니다.

이 예제에서는 &quot;folder&quot; 및 &quot;company&quot; 링크의 조인이 대상 테이블의 &quot;상위 수준&quot; 키로 대체되었습니다.

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

값 &quot;none&quot;이 있는 **`operation`** 속성은 조정 링크를 정의합니다.

데이터 패키지는 텍스트 편집기에서 수동으로 구성할 수 있습니다. XML 문서의 구조가 &quot;xtk:navtree&quot; 데이터 스키마를 따르는지 확인하기만 하면 됩니다. Adobe Campaign 콘솔에는 데이터 패키지 내보내기 및 가져오기 모듈이 있습니다.

## 패키지 내보내기 {#exporting-packages}

### 패키지 내보내기 {#about-package-export} 정보

패키지는 다음과 같은 3가지 방법으로 내보낼 수 있습니다.

* **[!UICONTROL Package Export Wizard]**&#x200B;을 사용하면 단일 패키지에서 객체 세트를 내보낼 수 있습니다. 자세한 내용은 [패키지에서 개체 집합 내보내기](#exporting-a-set-of-objects-in-a-package)를 참조하십시오.
* **단일 객체**&#x200B;는 마우스 오른쪽 버튼을 클릭하고 **[!UICONTROL Actions > Export in a package]**&#x200B;를 선택하여 패키지에서 직접 내보낼 수 있습니다.
* **패키지** 정의를 사용하면 나중에 패키지에서 내보낼 객체를 추가할 패키지 구조를 만들 수 있습니다. 자세한 내용은 [패키지 정의 관리](#managing-package-definitions)를 참조하십시오.

패키지를 내보내면 해당 패키지와 추가된 모든 엔티티를 다른 Campaign 인스턴스로 가져올 수 있습니다.

### 패키지 {#exporting-a-set-of-objects-in-a-package}에 있는 객체 집합 내보내기

패키지 내보내기 마법사는 Adobe Campaign 클라이언트 콘솔의 **[!UICONTROL Tools > Advanced > Export package...]** 메뉴를 통해 액세스할 수 있습니다.

![](assets/ncs_datapackage_typepackage.png)

3가지 유형의 패키지에 대해 마법사는 다음 단계를 제공합니다.

1. 문서 유형별로 내보낼 엔티티를 나열합니다.

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >**[!UICONTROL Offer category]**, **[!UICONTROL Offer environment]**, **[!UICONTROL Program]** 또는 **[!UICONTROL Plan]** 유형 폴더를 내보낼 경우 데이터가 손실될 수 있으므로 **xtk:folder**&#x200B;를 선택하지 마십시오. 폴더에 해당하는 엔티티를 선택합니다.오퍼 카테고리의 **nms:offerCategory**, 오퍼 환경의 경우 **nms:offerEnv**, 프로그램의 경우 **nms:program**, 계획의 경우 **nms:plan**.

   목록 관리를 사용하면 구성에서 내보낼 엔티티를 추가하거나 삭제할 수 있습니다. **[!UICONTROL Add]**&#x200B;을 클릭하여 새 엔티티를 선택합니다.

   **[!UICONTROL Detail]** 단추는 선택한 구성을 편집합니다.

   >[!NOTE]
   >
   >종속성 메커니즘은 엔티티 내보내기 시퀀스를 제어합니다. 자세한 내용은 [종속성 관리](#managing-dependencies)를 참조하십시오.

1. 엔티티 구성 화면은 추출할 문서 유형에 대한 필터 쿼리를 정의합니다.

   데이터 추출을 위해 필터링 절을 구성해야 합니다.

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >쿼리 편집기는 [이 섹션](../../platform/using/about-queries-in-campaign.md)에 있습니다.

1. **[!UICONTROL Next]**&#x200B;을(를) 클릭하고 추출 중에 데이터를 정렬하려면 정렬 열을 선택합니다.

   ![](assets/ncs_datapackage_export5.png)

1. 내보내기를 실행하기 전에 추출할 데이터를 미리 봅니다.

   ![](assets/ncs_datapackage_export6.png)

1. 패키지 내보내기 마법사의 마지막 페이지에서 내보내기를 시작할 수 있습니다. 데이터는 **[!UICONTROL File]** 필드에 지정된 파일에 저장됩니다.

   ![](assets/ncs_datapackage_export7.png)

### 종속성 관리 {#managing-dependencies}

내보내기 메커니즘을 통해 Adobe Campaign은 다양한 내보낸 요소 간의 링크를 추적할 수 있습니다.

이 메커니즘은 두 가지 규칙으로 정의됩니다.

* **자체** 또는 **owncopy** 유형 무결성이 있는 링크에 연결된 개체는 내보낸 개체와 동일한 패키지에서 내보내집니다.
* **중립** 또는 **정의** 유형 무결성(정의된 링크)이 있는 링크에 연결된 개체를 별도로 내보내야 합니다.

>[!NOTE]
>
>스키마 요소에 연결된 무결성 유형은 [이 섹션](../../configuration/using/database-mapping.md#links--relation-between-tables)에 정의됩니다.

#### 캠페인 {#exporting-a-campaign} 내보내기

캠페인을 내보내는 방법에 대한 예가 여기에 있습니다. 내보낼 마케팅 캠페인에는 작업(레이블:&quot;MyTask&quot;) 및 워크플로우(레이블:&quot;MyWorkflow&quot; 폴더(노드:관리/프로덕션/기술 워크플로우/캠페인 프로세스/MyWorkflow).

일치 스키마는 &quot;자체&quot; 유형 무결성이 있는 링크로 연결되어 있으므로 작업 및 워크플로우는 캠페인과 동일한 패키지에서 내보내집니다.

패키지 컨텐츠:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

패키지 유형에 대한 가입은 **@pkgAdmin 및 @pkgPlatform** 특성이 있는 스키마에 정의됩니다. 이러한 두 속성은 패키지에 대한 제휴 조건을 정의하는 XTK 표현식을 받습니다.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

마지막으로 **@pkgStatus** 속성을 사용하여 이러한 요소 또는 속성에 대한 내보내기 규칙을 정의할 수 있습니다. 특성 값에 따라 내보낸 패키지에 요소 또는 속성이 있습니다. 이 속성에 사용할 수 있는 세 가지 값은 다음과 같습니다.

* **안 함**:필드/링크를 내보내지 않음
* **항상**:이 필드에 대해 내보내기
* **preCreate**:연결된 엔티티의 생성을 허용합니다.

>[!NOTE]
>
>**preCreate** 값은 링크 유형 이벤트에 대해서만 허용됩니다. 내보낸 패키지에 아직 로드되지 않은 엔티티를 생성하거나 가리키는 권한을 가집니다.

## 패키지 정의 관리 {#managing-package-definitions}

패키지 정의를 사용하면 단일 패키지에서 나중에 내보낼 엔티티를 추가할 패키지 구조를 만들 수 있습니다. 그러면 이 패키지 및 추가된 모든 개체를 다른 Campaign 인스턴스로 가져올 수 있습니다.

**관련 항목:**

* [패키지 정의 만들기](#creating-a-package-definition)
* [패키지 정의에 개체 추가](#adding-entities-to-a-package-definition)
* [패키지 정의 생성 구성](#configuring-package-definitions-generation)
* [패키지 정의에서 패키지 내보내기](#exporting-packages-from-a-package-definition)

### 패키지 정의 {#creating-a-package-definition} 만들기

패키지 정의는 **[!UICONTROL Administration > Configuration > Package management > Package definitions]** 메뉴에서 액세스할 수 있습니다.

패키지 정의를 만들려면 **[!UICONTROL New]** 단추를 클릭한 다음 패키지 정의 일반 정보를 입력합니다.

![](assets/packagedefinition_create.png)

그런 다음 패키지 정의에 엔티티를 추가하고 XML 파일 패키지로 내보낼 수 있습니다.

**관련 항목:**

* [패키지 정의에 개체 추가](#adding-entities-to-a-package-definition)
* [패키지 정의 생성 구성](#configuring-package-definitions-generation)
* [패키지 정의에서 패키지 내보내기](#exporting-packages-from-a-package-definition)

### 패키지 정의 {#adding-entities-to-a-package-definition}에 개체 추가

**[!UICONTROL Content]** 탭에서 **[!UICONTROL Add]** 버튼을 클릭하여 패키지와 함께 내보낼 엔티티를 선택합니다. 개체를 선택할 때의 우수 사례는 [이 섹션](#exporting-a-set-of-objects-in-a-package) 섹션에 있습니다.

![](assets/packagedefinition_addentities.png)

인스턴스의 위치에서 직접 패키지 정의에 엔티티를 추가할 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. 원하는 엔티티를 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Actions > Export in a package]**&#x200B;을 선택합니다.

   ![](assets/packagedefinition_singleentity.png)

1. **[!UICONTROL Add to a package definition]**&#x200B;을 선택한 다음 엔티티를 추가할 패키지 정의를 선택합니다.

   ![](assets/packagedefinition_packageselection.png)

1. 개체가 패키지 정의에 추가되면 패키지와 함께 내보내집니다([이 섹션](#exporting-packages-from-a-package-definition) 참조).

   ![](assets/packagedefinition_entityadded.png)

### 패키지 정의 생성 {#configuring-package-definitions-generation} 구성

패키지 생성 작업은 패키지 정의 **[!UICONTROL Content]** 탭에서 구성할 수 있습니다. 이렇게 하려면 **[!UICONTROL Generation parameters]** 링크를 클릭합니다.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**:패키지 정의에 현재 사용되는 정의를 포함합니다.
* **[!UICONTROL Include an installation script]**:패키지 가져오기에서 실행할 javascript 스크립트를 추가할 수 있습니다. 이 옵션을 선택하면 패키지 정의 화면에 **[!UICONTROL Script]** 탭이 추가됩니다.
* **[!UICONTROL Include default values]**:를 패키지에 추가하면 모든 엔티티 속성의 값이 추가됩니다.

   긴 내보내기를 방지하기 위해 이 옵션은 기본적으로 선택되어 있지 않습니다. 즉, 기본값(&#39;empty string&#39;, &#39;0&#39; 및 &#39;false&#39;(스키마에 달리 정의되지 않은 경우)이 있는 엔터티&#39; 특성이 패키지에 추가되지 않으므로 내보낼 수 없습니다.

   >[!CAUTION]
   >
   >이 옵션을 선택하지 않으면 로컬 버전과 가져온 버전이 병합될 수 있습니다.
   >
   >패키지를 가져오는 인스턴스에 패키지의 엔티티와 동일한 엔티티가 포함된 경우(예: 동일한 외부 ID) 해당 속성이 업데이트되지 않습니다. 이전 인스턴스의 속성에 기본값이 있는 경우 패키지에 포함되지 않으므로 이러한 오류가 발생할 수 있습니다.
   >
   >이 경우 이전 인스턴스의 모든 속성을 패키지와 함께 내보내므로 **[!UICONTROL Include default values]** 옵션을 선택하면 버전 병합이 금지됩니다.

### 패키지 정의 {#exporting-packages-from-a-package-definition}에서 패키지 내보내기

패키지 정의에서 패키지를 내보내려면 아래 절차를 따르십시오.

1. 내보낼 패키지 정의를 선택한 다음 **[!UICONTROL Actions]** 단추를 클릭하고 **[!UICONTROL Export the package]**&#x200B;을 선택합니다.
1. 내보낸 패키지에 해당하는 XML 파일이 기본적으로 선택됩니다. 패키지 정의 네임스페이스 및 이름에 따라 이름이 지정됩니다.
1. 패키지 이름과 위치가 정의된 후 **[!UICONTROL Start]** 버튼을 클릭하여 내보내기를 시작합니다.

   ![](assets/packagedefinition_packageexport.png)

## 패키지 가져오기 {#importing-packages}

패키지 가져오기 마법사는 Adobe Campaign 클라이언트 콘솔의 기본 메뉴 **[!UICONTROL Tools > Advanced > Package import...]**&#x200B;을 통해 액세스할 수 있습니다.

라이선스 약관에 따라 이전에 수행한 내보내기(예: 다른 Adobe Campaign 인스턴스에서) 또는 [내장 패키지](../../installation/using/installing-campaign-standard-packages.md)에서 패키지를 가져올 수 있습니다.

![](assets/ncs_datapackage_import.png)

### {#installing-a-package-from-a-file} 파일에서 패키지 설치

기존 데이터 패키지를 가져오려면 XML 파일을 선택하고 **[!UICONTROL Open]**&#x200B;을 클릭합니다.

![](assets/ncs_datapackage_import_1.png)

가져올 패키지의 내용이 편집기의 가운데 섹션에 표시됩니다.

**[!UICONTROL Next]** 및 **[!UICONTROL Start]**&#x200B;을 클릭하여 가져오기를 시작합니다.

![](assets/ncs_datapackage_import_2.png)

### 내장 패키지 {#installing-a-standard-package} 설치

표준 패키지는 Adobe Campaign을 구성할 때 설치되는 내장 패키지입니다. 사용 권한 및 배포 모델에 따라 새 옵션이나 추가 기능을 획득하거나 새 오퍼로 업그레이드하는 경우 새 표준 패키지를 가져올 수 있습니다.

설치할 수 있는 패키지를 확인하려면 라이선스 계약을 참조하십시오.

내장 패키지에 대한 자세한 내용은 [이 페이지](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.

## 데이터 패키지 우수 사례 {#data-package-best-practices}

이 섹션에서는 프로젝트 수명 전반에 걸쳐 일관된 방식으로 데이터 패키지를 구성하는 방법에 대해 설명합니다.

패키지에는 필터링되거나 필터링되지 않은 다양한 구성 및 요소가 포함될 수 있습니다. 일부 요소가 없거나 요소/패키지를 올바른 순서로 가져오지 않으면 플랫폼 구성이 중단될 수 있습니다.

또한 여러 가지 다양한 기능을 갖춘 동일한 플랫폼을 사용하는 사용자가 여러 명 있으므로 패키지 사양 폴더가 빠르게 복잡해질 수 있습니다.

필수 사항은 아니지만 이 섹션에서는 대규모 프로젝트를 위해 Adobe Campaign에서 패키지를 구성하고 사용하는 데 도움이 되는 솔루션을 제공합니다.

기본 제한 사항은 다음과 같습니다.
* 패키지를 구성하고 변경된 내용과 시기를 추적할 수 있습니다.
* 구성이 업데이트되는 경우, 업데이트에 직접 연결되지 않은 항목을 끊을 위험을 최소화합니다.

>[!NOTE]
>
>패키지를 자동으로 내보내는 작업 과정을 설정하는 방법에 대한 자세한 내용은 [이 페이지](https://helpx.adobe.com/campaign/kb/export-packages-automatically.html)를 참조하십시오.

### 추천 {#data-package-recommendations}

항상 동일한 버전의 플랫폼에서 가져올 수 있습니다. 빌드가 동일한 두 인스턴스 사이에 패키지를 배포하는지 확인해야 합니다. 가져오도록 강제 적용하지 않고 항상 먼저 플랫폼을 업데이트하십시오(빌드가 다른 경우).

>[!IMPORTANT]
>
>다른 버전 간 가져오기는 Adobe에서 지원되지 않습니다.
<!--This is not allowed. Importing from 6.02 to 6.1, for example, is prohibited. If you do so, R&D won’t be able to help you resolve any issues you encounter.-->

스키마 및 데이터베이스 구조에 집중할 수 있습니다. 스키마가 있는 패키지 가져오기 뒤에 스키마를 생성해야 합니다.

### 솔루션 {#data-package-solution}

#### 패키지 유형 {#package-types}

먼저 다양한 유형의 패키지를 정의합니다. 4가지 유형만 사용됩니다.

**엔티티**
* 스키마, 양식, 폴더, 배달 템플릿 등과 같은 Adobe Campaign의 모든 &quot;xtk&quot; 및 &quot;nms&quot; 특정 요소
* 엔티티를 &quot;관리자&quot; 및 &quot;플랫폼&quot; 요소 모두로 간주할 수 있습니다.
* Campaign 인스턴스에서 업로드할 때 패키지에 둘 이상의 엔티티를 포함해서는 안 됩니다.

<!--Nothing “works” alone. An entity package does not have a specific role or objective.-->

새 인스턴스에 구성을 배포해야 하는 경우 모든 엔티티 패키지를 가져올 수 있습니다.

**기능**

이 유형의 패키지:
* 클라이언트 요구 사항/사양에 대한 답변
* 하나 이상의 기능을 포함합니다.
* 다른 패키지 없이 기능을 실행할 수 있도록 모든 종속성을 포함해야 합니다.

**캠페인**

이 패키지는 필수가 아닙니다. 캠페인이 기능으로 보여질 수 있더라도 모든 캠페인에 대한 특정 유형을 만드는 것이 때때로 유용합니다.

**업데이트**

구성한 후에는 기능을 다른 환경으로 내보낼 수 있습니다. 예를 들어 개발 환경에서 테스트 환경으로 패키지를 내보낼 수 있습니다. 이번 테스트에서 결함이 발견되었습니다. 첫째, 개발 환경에서 수정해야 합니다. 그런 다음 패치를 테스트 플랫폼에 적용해야 합니다.

첫 번째 방법은 전체 기능을 다시 내보내는 것입니다. 그러나 위험을 피하기 위해(원치 않는 요소 업데이트), 수정만 포함된 패키지를 포함하는 것이 더 안전합니다.

따라서 기능의 엔티티 유형이 하나만 포함된 &quot;업데이트&quot; 패키지를 만드는 것이 좋습니다.

업데이트는 수정일 뿐만 아니라 개체/기능/캠페인 패키지의 새 요소이기도 합니다. 전체 패키지를 배포하지 않으려면 업데이트 패키지를 내보낼 수 있습니다.

### 이름 지정 규칙 {#data-package-naming}

이제 유형이 정의되었으므로 이름 지정 규칙을 지정해야 합니다. Adobe Campaign에서는 패키지 사양에 대한 하위 폴더를 만들 수 없습니다. 즉, 숫자는 정리하는 데 가장 좋은 솔루션입니다. 숫자 접두어 패키지 이름. 다음 규칙을 사용할 수 있습니다.

* 엔티티:1~99
* 기능:100~199
* 캠페인:200~299
* 업데이트:5000~599

### 패키지 {#data-packages}

>[!NOTE]
>
>올바른 패키지 수를 정의하기 위한 규칙을 설정하는 것이 좋습니다.

#### 엔티티 패키지 주문 {#entity-packages-order}

가져오기에 도움이 되도록 엔티티 패키지를 가져올 때 순서대로 정렬합니다. 예제:
* 001 - 스키마
* 002 - 양식
* 003 - 이미지
* 등.

>[!NOTE]
>
>Forms은 스키마 업데이트 후에만 가져와야 합니다.

#### 패키지 200 {#package-200}

패키지 번호 &quot;200&quot;은 특정 캠페인에 사용할 수 없습니다.이 숫자는 모든 캠페인과 관련된 내용을 업데이트하는 데 사용됩니다.

#### 업데이트 패키지 {#update-package}

마지막 지점은 업데이트 패키지 번호 매기기에 관한 것입니다. &quot;5&quot;가 접두사로 추가된 패키지 번호(엔티티, 기능 또는 캠페인)입니다. 예제:
* 하나의 스키마 업데이트 5001
* 5200을 사용하여 모든 캠페인 업데이트
* 5101 - 101 기능 업데이트

업데이트 패키지에는 쉽게 다시 사용할 수 있도록 특정 엔터티만 포함되어야 합니다. 분할하려면 새 번호를 추가합니다(1부터 시작). 이러한 패키지에 대한 특정 주문 규칙이 없습니다. 더 잘 이해하려면 101 기능인 소셜 애플리케이션이 있다고 가정해 보십시오.
* 여기에는 webApp 및 외부 계정이 포함됩니다.
   * 패키지 레이블은 다음과 같습니다.101 - 소셜 애플리케이션(socialApplication).
* webApp에 결함이 있습니다.
   * wepApp이 수정되었습니다.
   * 다음 이름으로 수정 패키지를 만들어야 합니다.5101 - 1 - 소셜 애플리케이션 webApp(socialApplication_webApp)
* 소셜 기능을 사용하려면 새 외부 계정을 추가해야 합니다.
   * 외부 계정이 만들어집니다.
   * 새 패키지는 다음과 같습니다.5101 - 2 - Social 응용 프로그램 외부 계정(socialApplication_extAccount).
   * 이와 동시에 101 패키지는 외부 계정에 추가되도록 업데이트되지만 배포되지는 않습니다.
      ![](assets/ncs_datapackage_best-practices-1.png)

#### 패키지 설명서 {#package-documentation}

패키지를 업데이트할 때는 항상 설명 필드에 설명을 추가하여 수정 사항과 이유를 자세히 설명해야 합니다(예: &quot;새 스키마 추가&quot; 또는 &quot;결함 수정&quot;).

![](assets/ncs_datapackage_best-practices-2.png)

또한 댓글을 날짜 지정해야 합니다. 업데이트 패키지에 대한 주석을 항상 &quot;상위&quot;(5개의 접두사가 없는 패키지)에 보고합니다.

>[!IMPORTANT]
>
>설명 필드에는 최대 2.000자까지 입력할 수 있습니다.

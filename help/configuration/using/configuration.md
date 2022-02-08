---
product: campaign
title: 구성
description: 구성
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 1%

---

# Campaign Explorer 탐색 트리 구성{#configuration}

![](../../assets/v7-only.svg)

전문가 사용자로서 탐색기 트리에서 폴더를 추가하고 사용자 지정할 수 있습니다.

Campaign 탐색기 및 탐색 계층에 대해 자세히 알아보십시오 [이 섹션](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

탐색 목록에 사용되는 폴더 유형은 XML 문서에 설명되어 있습니다. 이 문서는 **xtk:navtree** 스키마.

XML 문서는 다음과 같이 구조화됩니다.

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

XML 문서에는 다음 항목이 포함되어 있습니다 **`<navtree>`** 루트 요소가 있는 요소 **이름** 및 **namespace** 문서 이름 및 네임스페이스를 지정할 속성입니다. 이름 및 네임스페이스는 문서 식별 키를 구성합니다.

응용 프로그램의 전역 명령은 **`<commands>`** 요소를 생성하지 않습니다.

파일 유형의 선언은 문서에 다음 요소를 사용하여 구성됩니다. **`<model>`** 및 **`<nodemodel>`**.

## 전역 명령 {#global-commands}

전역 명령을 사용하면 작업을 시작할 수 있습니다. 이 작업은 입력 양식 또는 SOAP 호출일 수 있습니다.

글로벌 명령은 기본 **[!UICONTROL Tools]** 메뉴 아래의 제품에서 사용할 수 있습니다.

명령 구성 구조는 다음과 같습니다.

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

글로벌 명령에 대한 설명은 **`<command>`** 다음 속성을 갖는 요소:

* **이름**: 명령의 내부 이름: 이름을 입력하고 고유해야 합니다.
* **레이블**: 명령의 레이블입니다.
* **desc**: 기본 화면의 상태 표시줄에 표시되는 설명입니다.
* **양식**: 시작할 양식: 입력할 값은 입력 양식의 식별 키(예: &quot;cus:recipient&quot;)
* **권한**: 이 명령에 액세스할 수 있는 명명된 권한 목록(쉼표로 구분됨) 사용 가능한 권한 목록은 **[!UICONTROL Administration > Access management > Named rights]** 폴더를 입력합니다.
* **promptLabel**: 명령을 실행하기 전에 확인 상자를 표시합니다.

A **`<command>`** 요소를 포함할 수 있습니다. **`<command>`** 하위 요소를 생성하지 않습니다. 이 경우 상위 요소를 사용하면 이러한 하위 요소로 구성된 하위 메뉴를 표시할 수 있습니다.

명령은 XML 문서에 선언된 것과 같은 순서로 표시됩니다.

명령 구분 기호를 사용하면 명령 간 분리 막대를 표시할 수 있습니다. 이것은 **&#39;-&#39;** 명령 레이블에 포함된 값입니다.

선택 사항인 **`<soapcall>`** 입력 매개 변수를 사용하는 태그는 실행할 SOAP 메서드 호출을 정의합니다. SOAP API에 대한 자세한 내용은 [Campaign JSAPI 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=ko).

양식 컨텍스트는 **`<enter>`** 태그에 가깝게 포함했습니다. 이 태그에 대한 자세한 내용은 입력 양식에 대한 설명서를 참조하십시오.

**예제**:

* &quot;xtk:import&quot; 양식을 시작하는 전역 명령 선언:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   &#39;I&#39; 문자에는 **&amp;** 명령 레이블에 있습니다.

* 구분 기호가 있는 하위 메뉴의 예:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* SOAP 메서드 실행:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## 폴더 유형 {#folder-type}

폴더 유형을 사용하면 스키마의 데이터에 액세스할 수 있습니다. 폴더와 연관된 보기는 목록과 입력 양식으로 구성됩니다.

폴더 유형 구성 구조는 다음과 같습니다.

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

폴더 유형 선언에는 **`<model>`** 요소를 생성하지 않습니다. 이 요소를 사용하면 **[!UICONTROL Add new folder]** 메뉴 아래의 제품에서 사용할 수 있습니다. A **`<model>`** 요소를 포함해야 합니다. **`<nodemodel>`** 요소 및 기타 **`<model>`** 요소를 생성하지 않습니다.

다음 **이름** 및 **레이블** 속성은 요소의 내부 이름과 **[!UICONTROL Add new folder]** 메뉴 아래의 제품에서 사용할 수 있습니다.

다음 **`<nodemodel>`** 요소에는 다음 속성을 사용하는 폴더 유형에 대한 설명이 포함되어 있습니다.

* **이름**: 내부 이름
* **레이블**: 에 사용된 레이블 **[!UICONTROL Add new folder]** 폴더를 삽입할 때 및 를 기본 레이블로 사용합니다.
* **img**: 폴더 삽입의 기본 이미지입니다.
* **hiddenCommands**: 마스크할 명령 목록(쉼표로 구분) 가능한 값: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; 및 &quot;adbdup&quot;.
* **newFolderShortCuts**: 모델의 단축키 목록(**`<nodemodel>`** 폴더를 만들 때 쉼표로 구분됩니다.
* **insertRight**, **editRight**, **deleteRight**: 폴더 삽입, 편집 및 삭제에 대한 권한.

다음 **`<view>`** 아래의 요소 **`<nodemodel>`** 요소에는 보기와 연관된 목록의 구성이 포함되어 있습니다. 목록의 스키마는 **스키마** 의 속성 **`<view>`** 요소를 생성하지 않습니다.

목록의 레코드를 편집하려면 목록 스키마와 이름이 같은 입력 양식이 암시적으로 사용됩니다. 다음 **유형** 속성 **`<view>`** 요소는 양식 표시에 영향을 줍니다. 가능한 값은 다음과 같습니다.

* **listdet**: 목록 맨 아래에 양식을 표시합니다.
* **list**: 목록만 표시합니다. 양식을 두 번 클릭하거나 목록 선택 메뉴의 &quot;열기&quot;를 통해 시작합니다.
* **양식**: 읽기 전용 양식을 표시합니다.
* **editForm**: 편집 모드로 양식을 표시합니다.

>[!NOTE]
>
>입력 양식 이름은 **양식** 의 속성 **`<view>`** 요소를 생성하지 않습니다.

목록 열의 기본 구성은 **`<columns>`** 요소를 생성하지 않습니다. 열은 **`<node>`** 를 포함하는 요소 **xpath** 스키마에서 해당 값으로 참조할 필드를 포함하는 속성입니다.

**예**: &quot;nms:recipient&quot; 스키마의 폴더 유형 선언입니다.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

해당 폴더 삽입 메뉴:

![](assets/d_ncs_integration_navigation_exemple2.png)

목록을 로드하는 동안 필터링 및 정렬을 적용할 수 있습니다.

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### 바로 가기 명령 {#shortcut-commands}

바로 가기 명령을 사용하면 목록을 선택하는 작업을 시작할 수 있습니다. 작업은 입력 양식 또는 SOAP 호출일 수 있습니다.

명령은 **[!UICONTROL Action]** 목록 메뉴 또는 관련 메뉴 단추

명령 구성 구조는 다음과 같습니다.

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

명령에 대한 설명은 **`<command>`** 다음 속성을 갖는 요소:

* **이름**: 명령의 내부 이름: 이름을 입력하고 고유해야 합니다.
* **레이블**: 명령의 레이블입니다.
* **desc**: 기본 화면의 상태 표시줄에 표시되는 설명입니다.
* **양식**: 시작할 양식: 입력할 값은 입력 양식의 식별 키(예: &quot;cus:recipient&quot;)
* **권한**: 이 명령에 액세스할 수 있는 명명된 권한 목록(쉼표로 구분됨) 사용 가능한 권한 목록은 **[!UICONTROL Administration > Access management > Named rights]** 폴더를 입력합니다.
* **promptLabel**: 명령 실행 전에 확인 상자를 표시합니다.
* **monoSelection**: 모노 선택을 강제 적용합니다(기본적으로 여러 선택).
* **refreshView**: 명령 실행 후 목록을 다시 로드합니다.
* **enabledIf**: 입력한 표현식에 따라 명령을 활성화합니다.
* **img**: 목록 도구 모음에서 명령에 액세스할 수 있는 이미지를 입력합니다.

A **`<command>`** 요소를 포함할 수 있습니다. **`<command>`** 하위 요소를 생성하지 않습니다. 이 경우 상위 요소를 사용하면 이러한 하위 요소로 구성된 하위 메뉴를 표시할 수 있습니다.

명령은 XML 문서에 선언된 것과 같은 순서로 표시됩니다.

명령 구분 기호를 사용하면 명령 간 분리 막대를 표시할 수 있습니다. 이것은 **&#39;-&#39;** 명령 레이블에 포함된 값입니다.

선택 사항인 **`<soapcall>`** 입력 매개 변수를 사용하는 태그는 실행할 SOAP 메서드 호출을 정의합니다. SOAP API에 대한 자세한 내용은 [Campaign JSAPI 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

양식 컨텍스트는 **`<enter>`** 태그에 가깝게 포함했습니다. 이 태그에 대한 자세한 내용은 입력 양식 설명서를 참조하십시오.

**예제**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### 연결된 폴더 {#linked-folder}

폴더 관리 작업에는 두 가지 유형이 있습니다.

1. 폴더는 보기입니다. 이 목록에는 스키마와 연결된 모든 레코드가 표시되고 폴더 속성에 입력한 시스템 필터링 가능성이 있습니다.
1. 폴더가 연결되어 있습니다. 목록의 레코드는 폴더 링크에서 암시적으로 필터링됩니다.

연결된 폴더의 경우 **folderLink** 속성 **`<nodemodel>`** 요소를 채워야 합니다. 이 속성에는 데이터 스키마에 구성된 폴더에 있는 링크의 이름이 포함되어 있습니다.

데이터 스키마에 있는 링크된 폴더의 선언의 예:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

의 구성 **`<nodemodel>`** &quot;folder&quot;라는 폴더의 링크에는 다음과 같습니다.

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

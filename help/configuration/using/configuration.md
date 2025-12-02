---
product: campaign
title: Campaign 탐색기 탐색 트리 구성
feature: Application Settings
description: Campaign 탐색기 탐색 트리를 구성하는 방법 알아보기
role: Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---

# Campaign 탐색기 탐색 트리 구성{#configuration}

전문가 사용자는 탐색기 트리에 폴더를 추가하고 사용자 정의할 수 있습니다.

[Adobe Campaign v8(콘솔) 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}에서 Campaign 사용자 인터페이스에 대해 자세히 알아보세요.

탐색 목록에 사용되는 폴더 유형은 **xtk:navtree** 스키마의 문법을 따르는 XML 문서에 설명되어 있습니다.

XML 문서는 다음과 같이 구성됩니다.

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

XML 문서에 문서 이름과 네임스페이스를 지정하는 **`<navtree>`** name **및** namespace **특성이 있는** 루트 요소가 있습니다. 문서 식별 키는 이름과 네임스페이스로 구성됩니다.

응용 프로그램의 전역 명령은 **`<commands>`** 요소의 문서에서 선언됩니다.

파일 형식 선언은 **`<model>`** 및 **`<nodemodel>`** 요소를 사용하여 문서에서 구조화되었습니다.

## 전역 명령 {#global-commands}

글로벌 명령을 사용하면 작업을 시작할 수 있습니다. 이 작업은 입력 양식 또는 SOAP 호출일 수 있습니다.

전역 명령은 기본 **[!UICONTROL Tools]** 메뉴에서 액세스할 수 있습니다.

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

전역 명령에 대한 설명은 다음 속성과 함께 **`<command>`** 요소에 입력됩니다.

* **이름**: 명령의 내부 이름: 이름을 입력하고 고유해야 합니다.
* **label**: 명령의 레이블입니다.
* **desc**: 기본 화면의 상태 표시줄에 설명이 표시됩니다.
* **form**: 시작할 양식: 입력할 값은 입력 양식의 식별 키입니다(예: &quot;cus:recipient&quot;).
* **권한**: 이 명령에 대한 액세스를 허용하는 명명된 권한 목록(쉼표로 구분). **[!UICONTROL Administration > Access management > Named rights]** 폴더에서 사용 가능한 권한 목록에 액세스할 수 있습니다.
* **promptLabel**: 명령을 실행하기 전에 확인 상자를 표시합니다.

**`<command>`** 요소에는 **`<command>`**&#x200B;개의 하위 요소가 포함될 수 있습니다. 이 경우 상위 요소를 사용하여 이러한 하위 요소로 구성된 하위 메뉴를 표시할 수 있습니다.

명령은 XML 문서에서 선언된 순서와 동일한 순서로 표시됩니다.

명령 구분 기호를 사용하면 명령 사이에 분리 막대를 표시할 수 있습니다. 명령 레이블에 포함된 **&#39;-&#39;** 값으로 식별됩니다.

입력 매개 변수와 함께 선택적으로 **`<soapcall>`** 태그가 있으면 실행할 SOAP 메서드 호출이 정의됩니다. SOAP API에 대한 자세한 내용은 [Campaign JSAPI 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=ko)를 참조하세요.

**`<enter>`** 태그에서 초기화 시 양식 컨텍스트를 업데이트할 수 있습니다. 이 태그에 대한 자세한 내용은 입력 양식에 대한 설명서를 참조하십시오.

**예**:

* &quot;xtk:import&quot; 양식을 시작하는 전역 명령 선언:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  명령 레이블에 **&amp;**&#x200B;이(가) 있으면 &#39;I&#39; 문자에 키보드 단축키가 선언됩니다.

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

폴더 유형을 사용하면 스키마 데이터에 대한 액세스 권한을 부여할 수 있습니다. 폴더와 연관된 보기는 목록과 입력 양식으로 구성됩니다.

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

**`<model>`** 요소 아래에 폴더 형식 선언을 입력해야 합니다. 이 요소를 사용하면 **[!UICONTROL Add new folder]** 메뉴에 표시되는 계층 구조를 정의할 수 있습니다. **`<model>`** 요소에는 **`<nodemodel>`** 요소와 다른 **`<model>`** 요소가 있어야 합니다.

**name** 및 **label** 특성이 요소의 내부 이름과 **[!UICONTROL Add new folder]** 메뉴에 표시된 레이블을 채웁니다.

**`<nodemodel>`** 요소에는 다음 속성이 있는 폴더 유형에 대한 설명이 포함되어 있습니다.

* **이름**: 내부 이름
* **label**: **[!UICONTROL Add new folder]** 메뉴에 사용되는 레이블이며 폴더를 삽입할 때 기본 레이블로 사용됩니다.
* **img**: 폴더 삽입 시 기본 이미지.
* **hiddenCommands**: 마스킹할 명령 목록(쉼표로 구분)입니다. 가능한 값: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; 및 &quot;adbdup&quot;.
* **newFolderShortCuts**: 폴더를 만들 때 모델의 바로 가기 목록(**`<nodemodel>`** 쉼표로 구분)입니다.
* **insertRight**, **editRight**, **deleteRight**: 폴더 삽입, 편집 및 삭제에 대한 권한입니다.

**`<view>`** 요소 아래의 **`<nodemodel>`** 요소에는 보기와 연결된 목록의 구성이 포함됩니다. 목록의 스키마가 **요소의** schema **`<view>`** 특성에 입력되었습니다.

목록의 레코드를 편집하려면 목록 스키마와 같은 이름의 입력 양식이 암시적으로 사용됩니다. **요소의** type **`<view>`** 특성이 양식 표시에 영향을 줍니다. 가능한 값:

* **listdet**: 목록 맨 아래에 양식을 표시합니다.
* **list**: 목록만 표시합니다. 양식을 두 번 클릭하거나 목록 선택 시 메뉴의 &quot;열기&quot;를 통해 시작합니다.
* **form**: 읽기 전용 양식을 표시합니다.
* **editForm**: 편집 모드에서 양식을 표시합니다.

>[!NOTE]
>
>**요소에** form **`<view>`** 특성을 입력하여 입력 폼의 이름을 오버로드할 수 있습니다.

목록 열의 기본 구성은 **`<columns>`** 요소를 통해 입력됩니다. 스키마에서 참조할 필드가 해당 값으로 있는 **`<node>`** xpath **특성이 포함된** 요소에 열이 선언되었습니다.

**예**: &quot;nms:recipient&quot; 스키마에서 폴더 형식을 선언했습니다.

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

해당 폴더 삽입 메뉴는 다음과 같습니다.

![](assets/d_ncs_integration_navigation_exemple2.png)

필터링 및 정렬은 목록이 로드될 때 적용할 수 있습니다.

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

바로 가기 명령을 사용하면 목록을 선택할 때 작업을 실행할 수 있습니다. 작업은 입력 양식 또는 SOAP 호출일 수 있습니다.

목록의 **[!UICONTROL Action]** 메뉴 또는 연결된 메뉴 단추에서 명령에 액세스할 수 있습니다.

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

다음 속성을 사용하여 **`<command>`** 요소에 명령 설명을 입력합니다.

* **이름**: 명령의 내부 이름: 이름을 입력하고 고유해야 합니다.
* **label**: 명령의 레이블입니다.
* **desc**: 기본 화면의 상태 표시줄에 설명이 표시됩니다.
* **form**: 시작할 양식: 입력할 값은 입력 양식의 식별 키입니다(예: &quot;cus:recipient&quot;).
* **권한**: 이 명령에 대한 액세스를 허용하는 명명된 권한 목록(쉼표로 구분). **[!UICONTROL Administration > Access management > Named rights]** 폴더에서 사용 가능한 권한 목록에 액세스할 수 있습니다.
* **promptLabel**: 명령을 실행하기 전에 확인 상자를 표시합니다.
* **monoSelection**: 모노 선택을 적용합니다(기본적으로 다중 선택).
* **refreshView**: 명령을 실행한 후 목록을 강제로 다시 로드합니다.
* **enabledIf**: 입력한 식에 따라 명령을 활성화합니다.
* **img**: 목록 도구 모음에서 명령에 액세스할 수 있는 이미지를 입력합니다.

**`<command>`** 요소에는 **`<command>`**&#x200B;개의 하위 요소가 포함될 수 있습니다. 이 경우 상위 요소를 사용하여 이러한 하위 요소로 구성된 하위 메뉴를 표시할 수 있습니다.

명령은 XML 문서에서 선언된 순서와 동일한 순서로 표시됩니다.

명령 구분 기호를 사용하면 명령 사이에 분리 막대를 표시할 수 있습니다. 명령 레이블에 포함된 **&#39;-&#39;** 값으로 식별됩니다.

입력 매개 변수와 함께 선택적으로 **`<soapcall>`** 태그가 있으면 실행할 SOAP 메서드 호출이 정의됩니다. SOAP API에 대한 자세한 내용은 [Campaign JSAPI 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=ko)를 참조하세요.

**`<enter>`** 태그를 통해 초기화 시 양식 컨텍스트를 업데이트할 수 있습니다. 이 태그에 대한 자세한 내용은 입력 양식 설명서를 참조하십시오.

**예**:

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

1. 폴더는 보기입니다. 목록에는 스키마와 연결된 모든 레코드가 표시되며, 폴더 속성에 입력된 시스템 필터링의 가능성이 있습니다.
1. 폴더가 연결됨: 목록의 레코드는 폴더 링크에서 암시적으로 필터링됩니다.

연결된 폴더의 경우 **요소의** folderLink **`<nodemodel>`** 특성을 채워야 합니다. 이 속성에는 데이터 스키마에 구성된 폴더의 링크 이름이 포함됩니다.

데이터 스키마에서 연결된 폴더 선언의 예:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

이름이 &quot;folder&quot;인 폴더의 링크에서 **`<nodemodel>`**&#x200B;의 구성은 다음과 같습니다.

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

---
product: campaign
title: 인터페이스 구성
description: 인터페이스 구성
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# 인터페이스 구성{#configuring-the-interface}

Adobe Campaign 인터페이스에서 새 수신자 테이블을 보고 대화 상자를 표시하려면 다음 단계를 적용합니다.

* 새 양식을 만들어 새 수신자 테이블의 내용을 편집합니다.
* 탐색기 트리의 폴더에 새 유형을 입력합니다.
* Adobe Campaign 홈 페이지를 통해 사용자 지정 테이블에 액세스할 새 웹 애플리케이션을 만듭니다.

Adobe Campaign은 &quot;Nms_DefaultRcpSchema&quot; 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와의 대화 상자를 사용합니다. 따라서 이 변수를 변경해야 합니다.

1. 탐색기의 **[!UICONTROL Administration>Platform>Options]** 노드로 이동합니다.
1. 외부 수신자 테이블과 일치하는 스키마의 이름으로 **Nms_DefaultRcpSchema** 변수의 값을 변경합니다(이 경우:cus:personal).
1. 변경 사항을 저장합니다.

## 새 양식 만들기 {#creating-a-new-form-}

새 양식을 만들면 외부 수신자 테이블의 데이터를 보고 편집할 수 있습니다.

>[!IMPORTANT]
>
>양식의 이름은 관련된 스키마 이름과 동일해야 합니다.

1. 탐색기의 **관리 > 구성 > 입력 양식** 노드로 이동합니다.
1. 새 **xtk:form** 유형을 **form** 파일로 만듭니다.
1. 테이블 템플릿에 따라 필요한 모든 모니터링 및 필드를 설명합니다.

   >[!NOTE]
   >
   >**form** 유형 파일에 대한 자세한 내용은 [이 페이지](../../configuration/using/identifying-a-form.md)를 참조하십시오.

   현재 예제에서 **form** 파일은 **cus:individual** 스키마를 기반으로 해야 하므로 다음 레이아웃이 있어야 합니다.

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. 만들기를 저장합니다.

## 탐색 계층 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}에서 새 유형의 폴더 만들기

1. **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 노드로 이동합니다.
1. 새 **xtk:navtree** **navtree** 문서를 만듭니다.
1. 테이블 템플릿에 따라 필요한 모든 모니터링 및 필드를 설명합니다.

   >[!NOTE]
   >
   >**navtree** 유형 파일에 대한 자세한 내용은 [이 페이지](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)를 참조하십시오.

   현재 예에서 **navtree** 파일은 **cus:individual** 스키마를 기반으로 해야 하므로 다음 양식이 있어야 합니다.

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. 만들기를 저장합니다.

---
title: 인터페이스 구성
seo-title: 인터페이스 구성
description: 인터페이스 구성
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 3%

---


# 인터페이스 구성{#configuring-the-interface}

Adobe Campaign 인터페이스에서 새 수신자 테이블을 보고 대화하려면 다음 단계를 적용합니다.

* 새 양식을 만들어 새 받는 사람 테이블의 내용을 편집합니다.
* 탐색기 트리 폴더에 새 유형을 입력합니다.
* Adobe Campaign 홈 페이지를 통해 사용자 정의 표에 액세스하는 새 웹 응용 프로그램을 만듭니다.

Adobe Campaign은 &quot;Nms_DefaultRcpSchema&quot; 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와 대화 상자를 엽니다. 따라서 이 변수를 변경해야 합니다.

1. 탐색기의 **[!UICONTROL Administration>Platform>Options]** 노드로 이동합니다.
1. 외부 받는 사람 테이블 **과 일치하는 스키마의 이름으로 Nms_DefaultRcpSchema** 변수의 값을 변경합니다(이 경우:cus:individual).
1. 변경 사항을 저장합니다.

## Creating a new form {#creating-a-new-form-}

새 양식을 만들면 외부 수신자 테이블의 데이터를 보고 편집할 수 있습니다.

>[!IMPORTANT]
>
>양식의 이름은 해당 스키마 이름과 동일해야 합니다.

1. 탐색기의 **관리 > 구성 > 입력 양식** 노드로 이동합니다.
1. 새 xtk:form **** type **양식** 파일을 만듭니다.
1. 테이블 템플릿에 따라 필요한 모든 모니터와 필드를 설명합니다.

   >[!NOTE]
   >
   >양식 **유형** 파일에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../configuration/using/identifying-a-form.md).

   현재 예에서 **양식** 파일은 **cus:individual** 스키마를 기반으로 해야 하므로 다음 레이아웃이 있어야 합니다.

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

1. 만든 내용을 저장합니다.

## 탐색 계층에서 새 유형의 폴더 만들기 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Go to the **[!UICONTROL Administration>Configuration>Navigation hierarchies]** node.
1. 새 xtk: **navtree** type **navtree** 문서를 만듭니다.
1. 테이블 템플릿에 따라 필요한 모든 모니터와 필드를 설명합니다.

   >[!NOTE]
   >
   >navtree **형식** 파일에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../configuration/using/about-navigation-hierarchy.md).

   현재 예에서 **navtree** 파일은 **cus:individual** 스키마를 기반으로 하므로 다음 양식이 있어야 합니다.

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

1. 만든 내용을 저장합니다.


---
product: campaign
title: 인터페이스 구성
description: Campaign 인터페이스를 구성하는 방법 알아보기
feature: Application Settings
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# 인터페이스 구성{#configuring-the-interface}

Adobe Campaign 인터페이스에서 새 수신자 테이블을 보고 대화 상자를 표시하려면 다음 단계를 적용합니다.

* 새 수신자 테이블의 콘텐츠를 편집할 새 양식을 만듭니다.
* 탐색기 트리의 폴더에 새 유형을 입력합니다.
* Adobe Campaign 홈 페이지를 통해 사용자 지정 테이블에 액세스할 새 웹 애플리케이션을 만듭니다.

Adobe Campaign은 &quot;Nms_DefaultRcpSchema&quot; 전역 변수를 사용하여 기본 수신자 데이터베이스(nms:recipient)와 대화를 나눕니다. 따라서 이 변수를 변경해야 합니다.

1. 로 이동 **[!UICONTROL Administration>Platform>Options]** 탐색기의 노드입니다.
1. 값 변경 **Nms_DefaultRcpSchema** 외부 수신자 테이블과 일치하는 스키마 이름의 변수입니다(이 경우 cus:individual).
1. 변경 내용 저장.

## 새 양식 만들기 {#creating-a-new-form-}

새 양식을 만들면 외부 수신자 테이블의 데이터를 보고 편집할 수 있습니다.

>[!IMPORTANT]
>
>양식 이름은 관련된 스키마의 이름과 동일해야 합니다.

1. 로 이동 **관리 > 구성 > 입력 양식** 탐색기의 노드입니다.
1. 새로 만들기 **xtk:form** 유형 **양식** 파일.
1. 테이블 템플릿에 따라 필요한 모든 모니터링 및 필드를 설명합니다.

   >[!NOTE]
   >
   >에 대해 자세히 알아보려면 **양식** 파일 입력, 참조 [이 페이지](../../configuration/using/identifying-a-form.md).

   현재 예제에서는 **양식** 파일은 다음을 기반으로 해야 합니다. **cus:individual** 스키마이므로 다음 레이아웃이 있습니다.

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

1. 생성을 저장합니다.

## 탐색 계층에 새 유형의 폴더 만들기 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 로 이동 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 노드.
1. 새로 만들기 **xtk:navtree** 유형 **탐색** 문서.
1. 테이블 템플릿에 따라 필요한 모든 모니터링 및 필드를 설명합니다.

   >[!NOTE]
   >
   >에 대한 자세한 내용 **탐색** 파일 입력, 참조 [이 페이지](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   현재 예제에서는 **탐색** 파일은 다음을 기반으로 해야 합니다. **cus:individual** 스키마이므로 다음 형식을 갖습니다.

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

1. 생성을 저장합니다.

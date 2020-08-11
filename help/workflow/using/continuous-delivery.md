---
title: 지속적인 전달
seo-title: 지속적인 전달
description: 지속적인 전달
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# 지속적인 전달{#continuous-delivery}

연속 **배달** 유형 작업을 사용하면 기존 배달에 새 받는 사람을 추가할 수 있습니다. 이 배달 유형은 매번 새 배달을 만들지 않아도 됩니다.이 모드는 특히 필요한 경우 소량 경고나 알림을 보낼 때 보다 효율적인 경우가 많습니다. 배달 템플릿 수준에서, 연결된 게재의 레이블(및 캠페인 폴더)을 계산하는 스크립트를 지정할 수 있습니다. 스크립트가 아직 존재하지 않는 배달을 계산하면 즉시 만들어집니다.

![](assets/edit_diffusion_fil.png)

이 **[!UICONTROL Process errors]** 옵션은 오류가 생성될 때 활성화되는 특정 전환을 표시합니다. 이 경우 워크플로우는 오류 모드로 전환되지 않고 계속 실행됩니다.

파일 시스템 오류(파일을 이동할 수 없음, 디렉터리에 액세스할 수 없음 등)를 고려한 오류입니다.

이 옵션은 활동 구성과 관련된 오류(예: 잘못된 값)를 처리하지 않습니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

옵션을 선택한 경우에만 **[!UICONTROL Specified by the inbound event]** 이 옵션을 선택합니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 가지 값 집합은 순시 게재에서 발생한 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상의 식별자를 기억하는 테이블의 이름이며, 모집단(일반적으로 nms:recipient)의 스키마 **[!UICONTROL schema]** 이며 표의 요소 **[!UICONTROL recCount]** 수입니다.

보완과 연결된 전환에는 동일한 매개 변수가 있습니다.

## 연속 배달을 설정하는 방법

이 섹션에서는 연속 배달을 설정하는 방법을 설명합니다.

연속 배달 **** 기능을 사용하면 기존 전달에 새 받는 사람을 추가할 수 있으며 새 받는 사람이 추가될 때마다 새 배달을 만들지 않아도 됩니다. 캠페인 워크플로우에서 직접 크리에이티브를 업데이트할 수 있으며 게재 템플릿 리소스 폴더의 템플릿을 업데이트합니다.

연속 배달은 SINGLE 배달 로그(broadLog)와 배달이 실행될 때마다 1개가 추가되었음을 참조하는 추적 로그를 만듭니다.

![연속 전달](assets/delivery_continuous.jpg)

이 비디오에서는 증분 쿼리를 사용하여 연속 배달을 구성하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

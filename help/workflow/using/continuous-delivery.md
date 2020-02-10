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
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 지속적인 전달{#continuous-delivery}

연속 **배달** 유형 작업을 사용하면 새 수신자를 기존 배달에 추가할 수 있습니다. 이 배달 유형을 사용하면 매번 새 배달을 만들 필요가 없습니다.이 모드는 특히 필요한 경우 소량 경고나 알림을 발송하는 경우 보다 효율적인 경우가 많습니다. 배달 템플릿 수준에서 스크립트를 지정하여 연결된 게재의 레이블(및 캠페인 폴더)을 계산할 수 있습니다. 스크립트가 아직 존재하지 않는 배달을 계산하면 즉시 생성됩니다.

![](assets/edit_diffusion_fil.png)

이 **[!UICONTROL Process errors]** 옵션은 오류가 생성될 때 활성화되는 특정 전환을 표시합니다. 이 경우 워크플로우는 오류 모드로 전환되지 않고 계속 실행됩니다.

파일 시스템 오류(파일을 이동할 수 없음, 디렉토리에 액세스할 수 없음 등)를 고려하여 발생한 오류입니다.

이 옵션은 활동 구성과 관련된 오류(예: 잘못된 값)를 처리하지 않습니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수에 의해 정의된 대상을 지정해야 합니다.

옵션을 선택한 경우에만 **[!UICONTROL Specified by the inbound event]** 적용됩니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 가지 값 집합은 즉시 배달에서 발생한 대상을 식별합니다. **[!UICONTROL tableName]** 은 대상의 식별자를 기억하는 테이블의 이름이며, **[!UICONTROL schema]** 모집단(일반적으로 nms:recipient)의 스키마이며, **[!UICONTROL recCount]** 표의 요소 수입니다.

보수와 연결된 전환에는 동일한 매개 변수가 있습니다.

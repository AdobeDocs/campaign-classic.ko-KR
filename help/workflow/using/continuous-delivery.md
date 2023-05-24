---
product: campaign
title: 지속적인 게재
description: 지속적인 게재
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 10%

---

# 지속적인 게재{#continuous-delivery}



A **연속 게재** 유형 작업을 사용하면 기존 게재에 새 수신자를 추가할 수 있습니다. 이 게재 유형은 매번 새 게재를 만들 필요가 없습니다. 특히 필요할 때 저볼륨 경고 또는 알림을 보내는 경우 이 모드가 더 효율적입니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#continuous-delivery-video)

게재 템플릿 수준에서 관련 게재의 레이블(및 캠페인 폴더)을 계산하는 스크립트를 지정할 수 있습니다. 스크립트가 아직 존재하지 않는 게재를 계산하는 경우 바로 생성됩니다.

![](assets/edit_diffusion_fil.png)

다음 **[!UICONTROL Process errors]** 옵션은 오류가 생성되면 활성화될 특정 전환을 표시합니다. 이 경우 워크플로우는 오류 모드로 전환되지 않고 계속 실행됩니다.

파일 시스템 오류(파일 이동 불가, 디렉터리 액세스 불가 등)를 고려하는 오류는 다음과 같습니다.

이 옵션은 활동 구성과 관련된 오류, 즉 잘못된 값을 처리하지 않습니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

다음 경우에만 **[!UICONTROL Specified by the inbound event]** 옵션이 선택되어 있습니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 즉시 게재 시 발생하는 대상을 식별합니다. **[!UICONTROL tableName]** 은 대상의 식별자를 기억하는 표의 이름입니다. **[!UICONTROL schema]** 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

보체와 관련된 전환은 동일한 매개 변수를 갖는다.

## 연속 게재를 설정하는 방법

이 섹션에서는 연속 게재를 설정하는 방법을 설명합니다.

다음 **연속 게재** 기존 게재에 새 수신자를 추가할 수 있으며, 새 수신자가 추가될 때마다 새 게재를 만들 필요가 없습니다. 캠페인 워크플로우에서 직접 크리에이티브를 업데이트할 수 있으며 게재 템플릿 리소스 폴더에서 템플릿을 업데이트합니다.

연속 게재를 사용하면 단일 게재 및 게재 로그(broadLog)와 게재가 실행될 때마다 이 게재를 참조하는 추적 로그가 추가됩니다.

![연속 게재](assets/delivery_continuous.jpg)

## 튜토리얼 비디오 {#continuous-delivery-video}

이 비디오에서는 증분 쿼리를 사용하여 연속 게재를 구성하는 방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).

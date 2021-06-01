---
product: campaign
title: 지속적인 게재
description: 지속적인 게재
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 6%

---

# 지속적인 게재{#continuous-delivery}

**연속 게재** 유형 작업을 사용하면 새 수신자를 기존 게재에 추가할 수 있습니다. 이 게재 유형을 사용하면 다음과 같이 매번 새 게재를 만들 수 없습니다.이 모드는 종종 더 효율적입니다. 특히 필요한 경우 출력되는 낮은 볼륨 경고나 알림에 유용합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#continuous-delivery-video)

게재 템플릿 수준에서 스크립트를 지정하여 연결된 게재의 레이블(및 캠페인 폴더)을 계산할 수 있습니다. 스크립트가 아직 존재하지 않는 게재를 계산하는 경우 즉시 생성됩니다.

![](assets/edit_diffusion_fil.png)

오류가 발생하면 활성화되는 특정 전환이 **[!UICONTROL Process errors]** 옵션에 표시됩니다. 이 경우 워크플로우는 오류 모드로 전환되지 않고 실행을 계속합니다.

파일 시스템 오류(파일을 이동할 수 없음, 디렉토리에 액세스할 수 없음 등)를 고려한 오류

이 옵션은 활동 구성과 관련된 오류(즉, 잘못된 값)를 처리하지 않습니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

**[!UICONTROL Specified by the inbound event]** 옵션이 선택된 경우에만 해당됩니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 즉시 게재에서 발생한 타겟을 식별합니다. **[!UICONTROL tableName]** 는 대상의 식별자를 암기하는 테이블의 이름 **[!UICONTROL schema]** 으로, 모집단(일반적으로 nms:recipient)의 스키마이며  **[!UICONTROL recCount]** 이 테이블의 요소 수입니다.

보어와 연관된 전환에는 동일한 매개 변수가 있습니다.

## 연속 게재를 설정하는 방법

이 섹션에서는 연속 게재를 설정하는 방법을 설명합니다.

**연속 게재**&#x200B;를 사용하면 기존 게재에 새 수신자를 추가할 수 있으며, 새 수신자가 추가될 때마다 새 게재를 만들 필요가 없습니다. 캠페인 워크플로우에서 직접 크리에이티브를 업데이트할 수 있으며 게재 템플릿 리소스 폴더에서 템플릿을 업데이트합니다.

연속 게재를 사용하면 단일 게재 및 게재 로그(broadLog)와 게재가 실행될 때마다 하나의 게재를 참조하는 추적 로그가 생성됩니다.

![연속 게재](assets/delivery_continuous.jpg)

## 튜토리얼 비디오 {#continuous-delivery-video}

이 비디오에서는 증분 쿼리를 사용하여 연속 게재를 구성하는 방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

추가 Campaign Classic 방법 동영상은 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에 있습니다.

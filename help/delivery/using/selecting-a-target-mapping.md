---
product: campaign
title: 대상 매핑 선택
description: 타깃 매핑 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 12%

---

# 대상 매핑 선택{#selecting-a-target-mapping}



기본적으로 게재 템플릿은 타겟팅합니다 **[!UICONTROL Recipients]**. 따라서 대상 매핑은 의 필드를 사용합니다 **nms:recipient** 테이블. Adobe Campaign은 필요에 따라 사용할 게재에 대한 다른 target 매핑을 제공합니다.

![](assets/delivery_select_mapping.png)

이러한 매핑은 다음과 같습니다.

| 이름 | 사용 | 표준 스키마 |
|---|---|---|
| 수신자 | Adobe Campaign 데이터베이스 수신자에게 게재 | nms:recipient |
| 방문자 | 예를 들어 추천(바이럴 마케팅) 또는 소셜 네트워크(Facebook, Twitter)를 통해 프로필이 수집된 방문자에게 제공합니다. | mns:visitor |
| 구독 | 뉴스레터 등 정보 서비스를 구독한 수신자에게 게재 | nms:subscription |
| 방문자 구독 | 정보 서비스를 구독한 방문자에게 게재 | nms:visitorSub |
| 서비스 | twitter 계정 또는 Facebook 페이지에 게시 | nms:service |
| 연산자 | Adobe Campaign 운영자에게 게재 | nms:operator |
| 외부 파일 | 게재에 필요한 모든 정보가 포함된 파일을 통해 게재 | 연결된 스키마 없음, 입력된 대상 없음 |

>[!NOTE]
>
>새 대상 매핑을 만들 수도 있습니다. 이 작업은 전문가 사용자용으로 예약되어 있습니다. 자세한 정보는 [이 섹션](../../configuration/using/target-mapping.md)을 참조하십시오.

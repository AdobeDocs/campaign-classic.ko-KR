---
product: campaign
title: 대상 매핑 선택
description: 대상 매핑 선택
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---

# 대상 매핑 선택{#selecting-a-target-mapping}

![](../../assets/common.svg)

기본적으로 게재 템플릿 타겟 **[!UICONTROL Recipients]**. 따라서 대상 매핑은 **nms:recipient** 테이블. Adobe Campaign은 사용자의 요구 사항에 따라 사용할 게재에 대한 다른 target 매핑을 제공합니다.

![](assets/delivery_select_mapping.png)

이러한 매핑은 다음과 같습니다.

| 이름 | 사용 | 표준 스키마 |
|---|---|---|
| 수신자 | Adobe Campaign 데이터베이스의 수신자에게 전달 | nms:recipient |
| 방문자 수 | 참조(바이럴 마케팅) 또는 소셜 네트워크(Facebook, Twitter)을 통해 프로필을 수집한 방문자에게 게재합니다. | mns:visitor |
| 구독 | 뉴스레터와 같은 정보 서비스를 구독한 수신자에게 게재 | nms:구독 |
| 방문자 구독 | 정보 서비스를 구독한 방문자에게 게재 | nms:visitorSub |
| 서비스 | twitter 계정 또는 Facebook 페이지에 게시 | nms:service |
| 연산자 | Adobe Campaign 운영자에게 게재 | nms:operator |
| 외부 파일 | 게재에 필요한 모든 정보가 포함된 파일을 통해 게재 | 연결된 스키마 없음, 대상 입력 없음 |

>[!NOTE]
>
>새 대상 매핑을 만들 수도 있습니다. 이 작업은 전문가 사용자를 위해 예약되어 있습니다. 자세한 내용은 [구성 안내서](../../configuration/using/target-mapping.md).

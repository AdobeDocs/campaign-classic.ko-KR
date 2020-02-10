---
title: 대상 매핑 선택
seo-title: 대상 매핑 선택
description: 대상 매핑 선택
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 대상 매핑 선택{#selecting-a-target-mapping}

기본적으로 배달 템플릿은 타깃팅합니다 **[!UICONTROL Recipients]**. 따라서 대상 매핑은 **nms:recipient** 테이블의 필드를 사용합니다. Adobe Campaign은 필요에 따라 사용할 게재에 대한 다른 대상 매핑을 제공합니다.

![](assets/delivery_select_mapping.png)

이러한 매핑은 다음과 같습니다.

| 이름 | 사용 | 표준 스키마 |
|---|---|---|
| 수신자 | Adobe Campaign 데이터베이스의 수신자에게 전달 | nms:수신자 |
| 방문자 수 | 참조(바이럴 마케팅) 또는 소셜 네트워크(Facebook, Twitter)를 통해 프로필을 수집한 방문자에게 제공합니다. | mns:visitor |
| 구독 | 뉴스레터와 같은 정보 서비스에 가입한 수신자에게 전달 | nms:구독 |
| 방문자 구독 | 정보 서비스에 가입한 방문자에게 제공 | nms:visitorSub |
| 서비스 | Twitter 계정 또는 Facebook 페이지에 게시 | nms:서비스 |
| 연산자 | Adobe Campaign 운영자에게 전달 | nms:연산자 |
| 외부 파일 | 전달에 필요한 모든 정보가 포함된 파일을 통해 전달 | 연결된 스키마 없음, 대상 입력 없음 |

>[!NOTE]
>
>새 대상 매핑을 만들 수도 있습니다. 이 작업은 전문가 사용자를 위해 예약되었습니다. 자세한 내용은 구성 [안내서를](../../configuration/using/target-mapping.md)참조하십시오.

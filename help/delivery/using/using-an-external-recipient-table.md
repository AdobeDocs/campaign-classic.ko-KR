---
title: 외부 수신자 테이블 사용
seo-title: 외부 수신자 테이블 사용
description: 외부 수신자 테이블 사용
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 외부 수신자 테이블 사용{#using-an-external-recipient-table}

배달 테이블이 외부 테이블인 경우 추가 구성을 만들어야 합니다. 스키마를 확장해야 **[!UICONTROL nms:seedmember]** 합니다. 아래와 같이 시드 주소에 탭이 추가되어 적절한 필드를 정의합니다.

![](assets/s_ncs_user_seedlist_new_tab.png)

이 경우 시드 주소를 게재에 추가하려면 일치하는 탭에 적절한 필드를 직접 입력하거나 주소 템플릿을 가져옵니다.

![](assets/s_ncs_user_seedlist_add_new_tab.png)

nms: **seedMember** 스키마 확장은 [이 섹션입니다](../../configuration/using/seed-addresses.md).

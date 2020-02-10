---
title: 캠페인 패키지 게시
seo-title: 캠페인 패키지 게시
description: 캠페인 패키지 게시
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 캠페인 패키지 게시{#publishing-the-campaign-package}

중앙 엔티티 연산자는 에서 로컬 엔티티에 제공하려는 캠페인을 게시합니다 **[!UICONTROL list of campaign packages]**.

캠페인 패키지 목록에 게시하려면 먼저 중앙 엔티티에서 캠페인 패키지를 승인해야 합니다. 이렇게 하려면 캠페인 패키지의 **[!UICONTROL Approval parameters]** 링크를 통해 검토자 또는 검토자 그룹을 지정할 수 있습니다.

## 검토자 할당 {#assigning-a-reviewer}

검토자를 선택하려면 캠페인 패키지에서 **[!UICONTROL Approval parameters]** 링크를 클릭하고 드롭다운 목록에서 관련 검토자를 선택합니다.

![](assets/s_advuser_mkg_dist_define_valid.png)

그런 다음 을 클릭하여 승인 프로세스를 시작할 수 **[!UICONTROL Submit for approval]**&#x200B;있습니다.

![](assets/s_advuser_mkg_dist_valid_process.png)

그런 다음 검토자에게 알림 메시지를 보내 이 캠페인 패키지의 가용성을 확인합니다. 메시지에는 웹 액세스를 통해 승인을 수락하거나 거부할 수 있는 링크가 포함되어 있습니다.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>조직 엔티티 수준에서, 주문을 승인할 검토자를 지정할 수도 있습니다. 자세한 내용은 조직 [엔티티를](../../campaign/using/about-distributed-marketing.md#organizational-entities)참조하십시오.

## 다른 검토자 추가 {#adding-other-reviewers}

캠페인 패키지의 **[!UICONTROL Edit...]** **[!UICONTROL Approval parameters...]** 탭에 있는 링크에서 다른 검토자를 추가할 수 있습니다.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 승인 기간 {#approval-periods}

기본적으로 검토자는 제출 날짜로부터 승인을 처리하기 위해 3일 동안 주어집니다.

검토자 편집 창에서 캠페인 패키지가 승인되지 않은 경우 하나 또는 여러 개의 메시지를 보내도록 미리 알림을 설정할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Add reminder]** 링크를 클릭한 다음 **[!UICONTROL Add]** 단추를 클릭합니다.

미리 알림은 지정된 날짜 및/또는 제출 날짜 **x** 이후에 보낼 수 있습니다. 미리 알림 유형은 미리 알림 테이블의 첫 번째 열에 구성할 수 있습니다. 아래 예에서 검토자는 2014년 29월 1일에 알림 메시지를 수신하게 됩니다. 즉, **[!UICONTROL Date]** 열에서 선택한 날짜보다 2일 전에, 예를 들어 승인 날짜의 제출 후 2일 전에 두 번째 미리 알림을 받게 됩니다.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

패키지가 정의되고 승인을 위해 패키지가 제출되면 실행 일정이 **[!UICONTROL Audit]** 탭에 표시됩니다. 이전 구성을 기준으로 계산된 처리 마감일과 구성된 모든 미리 알림 날짜를 표시합니다.

## Adobe Campaign 콘솔을 통한 승인 {#approving-via-the-adobe-campaign-console}

검토자가 지정되지 않았거나 알림을 받은 연산자 중 아무도 패키지를 승인하지 않은 경우 이 **[!UICONTROL Approve the package]** 단추를 사용하면 캠페인 패키지 **[!UICONTROL Dashboard]** 또는 패키지 개요에서 승인을 직접 진행할 수 있습니다.

![](assets/s_advuser_mkg_dist_valid_button.png)

승인 후 캠페인이 게시되고 목록에 추가되며 가용 일자에 도달하면 로컬 개체가 사용할 수 있습니다. 캠페인을 만들 때 로컬 개체가 지정된 경우 알림 그룹의 운영자에게 캠페인을 사용할 수 있음을 알리는 메시지가 전송됩니다. 이전에 엔티티가 지정되지 않은 경우 기본적으로 모든 로컬 엔티티에서 캠페인을 사용할 수 있습니다. 자세한 내용은 조직 [엔티티를](../../campaign/using/about-distributed-marketing.md#organizational-entities)참조하십시오.

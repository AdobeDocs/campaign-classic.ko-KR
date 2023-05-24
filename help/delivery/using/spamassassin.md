---
product: campaign
title: SpamAssassin
description: SpamAssassin을 사용하여 이메일 스팸 감지를 설정하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email, Deliverability
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}



Adobe Campaign은 다음으로 작동하도록 구성할 수 있습니다. [SpamAssassin](https://spamassassin.apache.org)이메일 스팸 필터링에 사용되는 서드파티 서비스. 이를 통해 이메일에 점수를 매겨 수신 시 사용되는 스팸 방지 도구에 의해 메시지가 스팸으로 간주될 위험이 있는지 여부를 확인할 수 있습니다.

SpamAssassin은 다음을 포함한 다양한 스팸 감지 기술을 활용합니다.

* DNS 기반 및 Fuzzy-Checksum 기반 스팸 탐지
* 베이지안 필터링
* 외부 프로그램
* 차단 목록
* 온라인 데이터베이스

>[!NOTE]
>
>SpamAssassin은 Adobe Campaign 애플리케이션 서버에 설치하고 구성해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-spamassassin.md)을 참조하십시오.
>
>요소가 스팸인지 여부를 제어하는 규칙은 SpamAssassin을 통해 관리되며 권한이 있는 관리자가 편집할 수 있습니다.

## Campaign에서 SpamAssassin 사용 {#using-spamassassin}

이메일 게재를 만들고 콘텐츠를 정의했으면 아래 단계에 따라 위험을 평가합니다.

게재 만들기 및 디자인에 대한 자세한 내용은 [이 섹션](about-email-channel.md).

1. **[!UICONTROL Preview]** 탭으로 이동합니다. 
1. 게재를 미리 볼 수신자를 선택하십시오.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >수신자를 선택하지 않으면 스팸 방지 확인을 수행할 수 없습니다.

1. 경고 메시지는 테스트 결과를 제공합니다. 높은 수준의 위험이 감지되면 다음과 같은 경고 메시지가 표시됩니다.

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 다음을 클릭합니다. **[!UICONTROL More...]** 경고 옆에 있는 링크입니다.
1. **[!UICONTROL Anti-spam checking]** 탭을 선택합니다. 
1. 로 이동 **[!UICONTROL Points / Rule / Description]** 섹션을 통해 이 위험의 이유를 살펴볼 수 있습니다.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>을 클릭할 때마다 **[!UICONTROL Anti-spam checking]**, SpamAssassin 서비스가 호출되고 메시지가 스팸 방지 검색을 위해 다시 분석됩니다. 스팸 방지 분석을 다시 실행하기 전에 콘텐츠를 변경했는지 확인하십시오.

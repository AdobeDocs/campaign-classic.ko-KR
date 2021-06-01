---
product: campaign
title: SpamAssassin
description: SpamAssassin을 사용하여 이메일 스팸 감지를 설정하는 방법 알아보기
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}

## SpamAssassin {#about-spamassassin} 정보

Adobe Campaign은 이메일 스팸 필터링에 사용되는 타사 서비스인 [SpamAssassin](https://spamassassin.apache.org)과 작동하도록 구성할 수 있습니다. 이를 통해 이메일에 점수를 매겨 수신 시 사용되는 스팸 방지 도구에 의해 메시지가 스팸으로 간주될 위험이 있는지 여부를 결정할 수 있습니다.

SpamAssassin은 다음과 같은 다양한 스팸 감지 기술을 활용합니다.

* DNS 기반 및 퍼지 체크섬 기반 스팸 감지
* 베이시안 필터링
* 외부 프로그램
* 차단 목록
* 온라인 데이터베이스

>[!NOTE]
>
>Adobe Campaign 애플리케이션 서버에 SpamAssassin을 설치 및 구성해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-spamassassin.md)을 참조하십시오.
>
>요소가 스팸인지 여부를 제어하는 규칙은 SpamAssassin을 통해 관리되며 권한이 있는 관리자가 편집할 수 있습니다.

## SpamAssassin {#using-spamassassin} 사용

전자 메일 게재를 만들고 해당 콘텐츠를 정의했으면 아래 단계에 따라 위험을 평가하십시오.

게재 만들기 및 디자인에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-email-channel.md)을 참조하십시오.

1. **[!UICONTROL Preview]** 탭으로 이동합니다. 
1. 게재를 미리 볼 수신자를 선택합니다.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >수신자를 선택하지 않으면 스팸 방지 검사를 수행할 수 없습니다.

1. 경고 메시지에 테스트 결과가 표시됩니다. 위험 수준이 높은 경우 다음 경고 메시지가 표시됩니다.

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 경고 옆에 있는 **[!UICONTROL More...]** 링크를 클릭합니다.
1. **[!UICONTROL Anti-spam checking]** 탭을 선택합니다. 
1. 이 위험의 이유를 보려면 **[!UICONTROL Points / Rule / Description]** 섹션으로 이동하십시오.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>**[!UICONTROL Anti-spam checking]**&#x200B;을 클릭할 때마다 SpamAssassin 서비스가 호출되고 스팸 방지 감지를 위해 메시지가 다시 분석됩니다. 스팸 방지 분석을 다시 실행하기 전에 콘텐츠를 변경했는지 확인하십시오.

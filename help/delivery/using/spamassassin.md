---
solution: Campaign Classic
product: campaign
title: SpamAssassin
description: SpamCharacter를 사용하여 이메일 스팸 감지를 설정하는 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---


# SpamAssassin{#spamassassin}

## SpamCharacter {#about-spamassassin} 정보

Adobe Campaign은 이메일 스팸 필터링에 사용되는 제3자 서비스인 [SpamCharacter](https://spamassassin.apache.org)와 작동하도록 구성할 수 있습니다. 이 기능을 사용하면 이메일에 점수를 매겨 메시지를 받을 때 사용되는 스팸 방지 도구에 의해 스팸으로 간주될 수 있는 위험 여부를 결정할 수 있습니다.

SpamCharacter는 다음과 같은 다양한 스팸 감지 기법을 활용합니다.

* DNS 기반 및 퍼지 체크섬 기반 스팸 감지
* Bayesian 필터링
* 외부 프로그램
* 차단 목록
* 온라인 데이터베이스

>[!NOTE]
>
>Adobe Campaign 응용 프로그램 서버에 SpamCharacter를 설치하고 구성해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-spamassassin.md)을 참조하십시오.
>
>요소가 스팸인지 여부를 제어하는 규칙이며 권한이 있는 관리자가 편집할 수 있습니다.

## SpamCharacter {#using-spamassassin} 사용

이메일 전송을 만들고 컨텐츠를 정의했으면 아래 절차에 따라 위험을 평가하십시오.

배달 만들기 및 디자인에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-email-channel.md)을 참조하십시오.

1. **[!UICONTROL Preview]** 탭으로 이동합니다. 
1. 배달을 미리 볼 수신자를 선택합니다.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >수신자를 선택하지 않으면 스팸 방지 확인을 수행할 수 없습니다.

1. 경고 메시지는 테스트 결과를 제공합니다. 위험 수준이 높은 경우 다음 경고 메시지가 표시됩니다.

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. 경고 옆에 있는 **[!UICONTROL More...]** 링크를 클릭합니다.
1. **[!UICONTROL Anti-spam checking]** 탭을 선택합니다. 
1. 이 위험의 이유를 보려면 **[!UICONTROL Points / Rule / Description]** 섹션으로 이동하십시오.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>**[!UICONTROL Anti-spam checking]**&#x200B;을(를) 클릭할 때마다 SpamCharacter 서비스가 호출되고 스팸 방지 감지를 위해 메시지가 다시 분석됩니다. 스팸 방지 분석을 다시 실행하기 전에 컨텐츠를 변경했는지 확인하십시오.

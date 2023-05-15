---
product: campaign
title: 인바운드 이메일
description: 인바운드 이메일 워크플로우 활동에 대해 자세히 알아보십시오
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# 인바운드 이메일{#inbound-emails}



다음 **인바운드 전자 메일** 활동을 사용하면 POP3 메일 서버에서 전자 메일 메시지를 다운로드하고 처리할 수 있습니다.

![](assets/email_rec_edit_1.png)

의 첫 번째 탭 **인바운드 전자 메일** 활동을 사용하면 POP3 서버의 매개 변수를 입력하고 각 메시지를 받으면 실행할 스크립트를 입력할 수 있습니다. 두 번째 탭에서는 활동에 일정을 할당할 수 있으며, 세 번째 탭에서는 활동 만료 조건을 정의합니다.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      이 옵션이 활성화되면 연결 매개 변수를 입력하는 대신 외부 POP3 계정을 선택할 수 있습니다. 다음 **[!UICONTROL External account]** 필드에서는 전자 메일 서비스에 연결하는 데 사용할 외부 POP3 계정을 지정합니다. 이 필드는 &#39;외부 계정 사용&#39; 옵션이 활성화되어 있을 경우에만 표시됩니다.

      이 옵션을 선택하지 않으면 다음 매개 변수를 지정해야 합니다.

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         POP3 서버의 이름입니다.

      * **[!UICONTROL POP3 account]**

         사용자의 이름입니다.

      * **[!UICONTROL Password]**

         사용자 계정 암호입니다.

      * **[!UICONTROL Port]**

         POP3 연결 포트 번호입니다. 기본 포트는 110입니다.
   * **[!UICONTROL Stop as soon as email is processed]**

      이 옵션을 사용하면 전자 메일을 하나씩 처리할 수 있습니다. 이 활동은 전환을 한 번만 활성화한 다음 처리를 완료하여 처리되지 않은 메시지를 서버에 남습니다.


1. **[!UICONTROL Script]**

   스크립트를 사용하면 메시지를 처리하고 메시지 내용에 따라 다양한 작업을 수행할 수 있습니다. 스크립트는 각 메시지에 대해 실행되며 메시지에 대해 수행할 작업(메시지를 종료하거나 삭제)과 아웃바운드 전환의 활성화를 결정할 수 있습니다.

   반환 코드는 다음 값 중 하나여야 합니다.

   * 1 - 서버에서 메시지를 삭제하고 아웃바운드 전환을 활성화합니다.
   * 2 - 메시지를 서버에 두고 아웃바운드 전환을 활성화합니다.
   * 3 - 서버에서 메시지를 삭제합니다.
   * 4 - 서버에 메시지를 둡니다.

   메시지의 콘텐츠는 글로벌에서 액세스할 수 있습니다 **[!UICONTROL mailMessage]** 변수를 채우는 방법을 설명합니다.

1. **[!UICONTROL Schedule]**

   활동의 일정을 정의하려면 **[!UICONTROL Scheduling]** 탭 및 확인 **[!UICONTROL Plan execution]**. 을(를) 클릭합니다. **[!UICONTROL Change]** 단추를 클릭하여 일정을 구성합니다.

   예약 구성은 예약 활동과 동일합니다. 을(를) 참조하십시오. [스케줄러](scheduler.md).

1. **[!UICONTROL Expiration]**

   를 통해 만료 지연을 정의할 수 있습니다 **[!UICONTROL Expiration]** 탭.

   ![](assets/email_rec_edit_3.png)

   구성은 예약 활동과 동일합니다. 을(를) 참조하십시오. [만료](defining-approvals.md).

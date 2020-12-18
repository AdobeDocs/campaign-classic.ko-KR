---
solution: Campaign Classic
product: campaign
title: 유효성 검사
description: 유효성 검사
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# 유효성 검사{#validating}

배달을 확인할 때의 글로벌 개념이 [이 섹션](../../delivery/using/steps-validating-the-delivery.md)에 표시됩니다.

배달 분석 중에 다이렉트 메일 배달의 출력 파일이 생성됩니다. 파일의 내용은 선택한 출력 열에 따라 달라집니다([추출 파일](../../delivery/using/defining-the-direct-mail-content.md#extraction-file) 참조).

>[!NOTE]
>
>분석 단계는 [배달 분석](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)에 자세히 설명되어 있습니다.

분석 단계 중에 파일이 생성되지만 받는 사람(예: 배달 로그)에 대한 정보는 업데이트되지 않습니다. 따라서 위험을 실행하지 않고 이 작업을 취소할 수 있습니다.

**[!UICONTROL Confirm delivery]**&#x200B;을 클릭하기 전에 분석 결과와 출력 파일의 내용을 확인합니다. 확인 메시지를 사용하여 배달을 시작할 수 있습니다.

보내기 확인은 지정된 파일에서 데이터 추출을 시작합니다.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

그런 다음 마법사를 닫고 배달 세부 정보를 통해 액세스할 수 있는 **[!UICONTROL Delivery]** 탭을 통해 배달 로그를 볼 수 있습니다.

배달 속성의 **[!UICONTROL Analysis]** 탭에서 배달 로그 검색 모드를 구성할 수 있습니다.

두 가지 모드가 있습니다.

* **[!UICONTROL Messages are considered sent after validation]** (기본 모드):이 함수 모드에서는 연산자가 전송을 확인하면(상태는 &#39;Pending delivery&#39;에서 &#39;Sent&#39;로 전달) 모든 브로드로그가 업데이트되고 배달은 자동으로 로 설정됩니다 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :이 모드를 사용하면 서비스 공급자가 보낸 외부 파일을 통해 브로드로그를 업데이트할 수 있습니다. 이 경우 브로드캐스트 상태를 업데이트하려면 이 정보를 처리하는 작업 과정을 사용해야 합니다.

   >[!NOTE]
   >
   >이 경우 브로드로그가 업데이트되는 즉시 사용자가 배달 상태를 **[!UICONTROL Finished]**&#x200B;으로 변경해야 합니다.

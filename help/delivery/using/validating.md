---
title: 유효성 검사
seo-title: 유효성 검사
description: 유효성 검사
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 1%

---


# 유효성 검사{#validating}

배달을 확인할 때의 글로벌 개념이 [이 섹션에 나와 있습니다](../../delivery/using/steps-validating-the-delivery.md).

배달 분석 중에 다이렉트 메일 배달의 출력 파일이 생성됩니다. 파일의 내용은 선택한 출력 열에 따라 다릅니다(추출 파일 [참조](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>분석 단계는 배달 [분석에서 자세히 설명합니다](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

분석 단계 중에는 파일이 생성되지만 받는 사람(예: 배달 로그)에 대한 정보는 업데이트되지 않습니다. 따라서 위험을 실행하지 않고 이 작업을 취소할 수 있습니다.

클릭 전에 분석 결과와 출력 파일의 내용을 확인합니다 **[!UICONTROL Confirm delivery]**. 확인 메시지를 사용하여 배달을 시작할 수 있습니다.

보내기 확인은 지정된 파일에서 데이터 추출을 시작합니다.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

그런 다음 마법사를 닫고 탭을 통해 배달 로그를 볼 수 있습니다. 이 **[!UICONTROL Delivery]** 탭은 배달 세부 정보를 통해 액세스할 수 있습니다.

배달 속성의 **[!UICONTROL Analysis]** 탭에서 배달 로그 검색 모드를 구성할 수 있습니다.

두 가지 모드가 있습니다.

* **[!UICONTROL Messages are considered sent after validation]** (기본 모드):이 함수 모드에서는 연산자가 전송을 확인하고(상태는 &#39;배달 대기 중&#39;에서 &#39;전송&#39;(Sent)으로 전달되면) 배달을 자동으로 설정하여 모든 브로드로그가 업데이트됩니다 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :이 모드에서는 서비스 제공업체에서 전송하는 외부 파일을 통해 브로드로그를 업데이트할 수 있습니다. 이 경우 브로드캐스트 상태를 업데이트하려면 이 정보를 처리하는 워크플로우를 사용해야 합니다.

   >[!NOTE]
   >
   >이 경우 브로드로그가 업데이트되는 즉시 사용자가 전달 상태 **[!UICONTROL Finished]** 를 변경해야 합니다.

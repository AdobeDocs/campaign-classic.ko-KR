---
product: campaign
title: 유효성 검사
description: 유효성 검사
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 유효성 검사{#validating}

게재 유효성 검사 시 전반적 개념이 [이 섹션](../../delivery/using/steps-validating-the-delivery.md)에 표시됩니다.

게재 분석 중에 DM 게재의 출력 파일이 생성됩니다. 파일의 컨텐츠는 선택한 출력 열에 따라 다릅니다( [추출 파일](../../delivery/using/defining-the-direct-mail-content.md#extraction-file) 참조).

>[!NOTE]
>
>분석 단계는 [게재 분석](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)에 자세히 설명되어 있습니다.

분석 단계 동안 파일이 생성되지만 수신자(즉, 게재 로그)에 대한 정보는 업데이트되지 않습니다. 따라서 위험 요소를 실행하지 않고 이 작업을 취소할 수 있습니다.

**[!UICONTROL Confirm delivery]**&#x200B;을 클릭하기 전에 분석 결과와 출력 파일의 내용을 확인하십시오. 확인 메시지를 통해 게재를 시작할 수 있습니다.

전송 확인을 통해 지정된 파일의 데이터 추출을 시작합니다.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

그런 다음 마법사를 닫고 게재 세부 사항을 통해 액세스할 수 있는 **[!UICONTROL Delivery]** 탭을 통해 게재 로그를 볼 수 있습니다.

게재 속성의 **[!UICONTROL Analysis]** 탭에서 게재 로그 검색 모드를 구성할 수 있습니다.

다음 두 가지 모드가 있습니다.

* **[!UICONTROL Messages are considered sent after validation]** (기본 모드):이 함수 모드에서는 연산자가 전송을 확인하고(상태가 &#39;게재 보류 중&#39;에서 &#39;전송됨&#39;으로 전달됨) 게재를 자동으로 로 설정되면 모든 브로드로그가 업데이트됩니다 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :이 모드에서는 서비스 공급자가 보낸 외부 파일을 통해 브로드로그를 업데이트할 수 있습니다. 이 경우 브로드로그 상태를 업데이트하려면 이 정보를 처리하는 워크플로우를 사용해야 합니다.

   >[!NOTE]
   >
   >이 경우 브로드로그가 업데이트되는 즉시 사용자가 게재 상태를 **[!UICONTROL Finished]** 로도 변경해야 합니다.

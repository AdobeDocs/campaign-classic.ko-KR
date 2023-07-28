---
product: campaign
title: 첨부 파일이 있는 트랜잭션 이메일 보내기
description: Adobe Campaign을 사용하여 개별 및/또는 개인화된 첨부 파일이 있는 트랜잭션 이메일을 보내는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 728fc285fbd562003199c53339899bbc4441bfc6
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 4%

---

# 사용 사례: 첨부 파일이 있는 트랜잭션 이메일 보내기 {#transactional-email-with-attachments}



이 사용 사례의 목적은 아웃바운드 디스패치에 이메일 첨부 파일을 즉시 추가하는 것입니다.

## 주요 단계 {#key-steps}

이 시나리오에서는 개별 및/또는 개인화된 첨부 파일이 있는 트랜잭션 이메일을 보내는 방법을 배웁니다. 첨부 파일은 트랜잭션 메시지 서버에 미리 업로드되지 않습니다. 대신 즉시 생성됩니다.

고객 상호 작용 또는 세부 정보를 캡처할 때 프로세스가 끝날 때(예: 이메일에 첨부된 PDF 파일) 이 정보를 고객에게 다시 보내야 할 수 있습니다.

다음은 이 시나리오의 주요 단계입니다.

1. 고객이 웹 사이트에 들어가 구매하고 싶은 제품을 찾는다.
1. 고객이 제품을 선택하고 몇 가지 옵션을 맞춤화합니다.
1. 고객이 트랜잭션을 완료합니다.
1. 거래를 확인하는 이메일이 고객에게 전송됩니다. 이메일에 PII(개인 식별 정보)를 외부로 보내는 것은 권장되지 않으므로 보안 PDF이 생성되고 이메일에 첨부됩니다.
1. 고객은 관련 데이터가 포함된 이메일과 해당 첨부 파일을 수신합니다.

이 시나리오에서는 첨부 파일이 미리 만들어지지 않고 아웃바운드 이메일에 즉시 추가되므로 다음과 같은 이점이 있습니다.

* 이렇게 하면 첨부 파일의 컨텐츠를 개인화할 수 있습니다.
* 위에서 설명한 예제 시나리오와 같이 첨부 파일이 트랜잭션과 연결된 경우 고객 프로세스 중에 생성된 동적 데이터가 포함될 수 있습니다.
* PDF 파일을 첨부하면 암호화하여 HTTPS를 통해 전송할 수 있으므로 보안이 최적화됩니다.

## Recommendations 및 보호 기능 {#important-notes}

성능 문제를 방지하기 위해 이메일에 포함된 이미지는 100KB를 초과할 수 없습니다. 기본적으로 설정된 이 제한은 `NmsDelivery_MaxDownloadedImageSize` 옵션을 선택합니다. 그러나 Adobe은 이메일 게재에서 큰 이미지를 피하는 것을 강력히 권장합니다.

Adobe은 또한 첨부 파일의 크기와 수를 제한하는 것을 권장합니다. 기본적으로 하나의 파일만 전자 메일에 첨부 파일로 추가할 수 있습니다. 이 임계값은 다음에서 구성할 수 있습니다. `NmsDelivery_MaxRecommendedAttachments` 옵션을 선택합니다.

다음에서 자세히 알아보기 [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).

이 시나리오를 구현하기 전에 아래 지침을 주의 깊게 읽어 보십시오.

* 트랜잭션 메시지 인스턴스는 파일 또는 데이터를 저장, 내보내기 또는 업로드하는 데 사용해서는 안 됩니다. 이벤트 데이터 및 관련 정보에만 사용할 수 있습니다. 파일 스토리지 시스템으로 간주해서는 안 됩니다.
* Adobe 외부의 트랜잭션 메시지 인스턴스 또는 서버에 직접 액세스할 수 없으므로 이러한 서버에 이러한 파일을 푸시할 수 있는 표준 방법은 없습니다(FTP 액세스 없음).
* 트랜잭션 메시지 인스턴스의 디스크 공간을 사용하여 첨부 파일도 아닌 모든 종류의 파일을 저장하는 것은 계약상 맞지 않습니다.
* 이러한 파일을 호스팅하려면 다른 온라인 디스크 시스템을 사용해야 합니다. 이 시스템에 대한 FTP 액세스 권한이 필요하며 파일을 쓰고 삭제할 수 있어야 합니다.

>[!NOTE]
>
>성능 문제를 방지하려면 이메일당 둘 이상의 첨부 파일을 포함하지 않는 것이 좋습니다. 권장 임계값은 다음 위치에서 구성할 수 있습니다. [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).

## 구현 {#implementation}

아래 다이어그램은 이 시나리오를 구현할 때의 여러 단계를 보여 줍니다.

![](assets/message-center-uc1.png)

트랜잭션 메시지에 이메일 첨부 파일을 즉시 추가하려면 아래 단계를 따르십시오.

1. 먼저 첨부 파일을 디자인합니다. 자세한 내용은 [이 섹션](../../delivery/using/attaching-files.md#attach-a-personalized-file)을 참조하십시오.

   이렇게 하면 실행 인스턴스에서 호스팅되지 않는 파일도 이메일에 첨부할 수 있습니다.

1. SOAP 메시지 트리거를 통해 이메일을 보낼 수 있습니다. SOAP 호출에는 URL 매개 변수(attachmentURL)가 있습니다.

   SOAP 요청에 대한 자세한 내용은 [이벤트 설명](../../message-center/using/event-description.md).

1. 이메일을 디자인할 때 **[!UICONTROL Attachment]**.

1. 다음에서 **[!UICONTROL Attachment definition]** 화면에서 SOAP 첨부 파일 매개 변수를 입력합니다.

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. 메시지가 처리되면 시스템은 원격 위치(타사 서버)에서 파일을 가져와 개별 메시지에 첨부합니다.

   이 매개 변수는 변수가 될 수 있으므로 SOAP 호출을 통해 전송된 파일의 완전한 형식의 원격 URL 변수를 허용해야 합니다.

   ![](assets/message-center-uc2.png)

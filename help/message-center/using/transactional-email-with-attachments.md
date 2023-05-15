---
product: campaign
title: 첨부 파일이 있는 트랜잭션 이메일 보내기
description: Adobe Campaign을 사용하여 개별 및/또는 개인화된 첨부 파일을 사용하여 트랜잭션 이메일을 보내는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 5%

---

# 사용 사례: 첨부 파일이 있는 트랜잭션 전자 메일 보내기 {#transactional-email-with-attachments}



이 사용 사례의 목적은 아웃바운드 디스패치에 전자 메일 첨부 파일을 즉시 추가하는 것입니다.

## 주요 단계 {#key-steps}

이 시나리오에서는 개별 및/또는 개인화된 첨부 파일이 있는 트랜잭션 이메일을 보내는 방법을 알아봅니다. 첨부 파일은 트랜잭션 메시지 서버에 미리 업로드되지 않습니다. 대신 즉시 생성됩니다.

고객 상호 작용이나 세부 사항을 캡처할 경우 프로세스 종료 시, 예를 들어 전자 메일에 첨부된 PDF 파일에서 이 정보를 고객에게 다시 보내야 할 수 있습니다.

다음은 이 시나리오의 주요 단계입니다.

1. 고객이 웹 사이트에 들어가 구매할 제품을 찾습니다.
1. 고객은 제품을 선택하고 일부 옵션을 사용자 지정합니다.
1. 고객이 트랜잭션을 완료합니다.
1. 트랜잭션을 확인하는 이메일이 고객에게 전송됩니다. 이메일에서 PII(개인 식별 정보)를 전송하지 않는 것이 권장되므로 보안 PDF이 생성되고 이메일에 첨부됩니다.
1. 고객은 관련 데이터가 포함된 이메일 및 첨부 파일을 받습니다.

이 시나리오에서는 첨부 파일이 미리 만들어지지 않고 아웃바운드 전자 메일에 즉시 추가되므로 다음과 같은 이점이 있습니다.

* 첨부 파일의 컨텐츠를 개인화할 수 있습니다.
* 첨부 파일이 트랜잭션과 연관된 경우(위에 설명된 예제 시나리오에서 처럼) 고객 프로세스 중에 생성된 동적 데이터가 포함될 수 있습니다.
* PDF 파일을 첨부하면 HTTPS를 통해 암호화하고 전송할 수 있으므로 보안이 최적화됩니다.

>[!NOTE]
>
>성능 문제를 방지하려면 개인화된 URL에서 즉시 다운로드한 이미지를 첨부 파일로 포함하는 경우 각 이미지 크기가 기본적으로 10만 바이트를 초과해서는 안 됩니다. 이 권장 임계값은 다음에서 구성할 수 있습니다. [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).

## 권장 사항 {#important-notes}

이 시나리오를 구현하려면 먼저 아래 지침을 자세히 살펴보십시오.

* 트랜잭션 메시지 인스턴스는 파일 또는 데이터를 저장, 내보내기 또는 업로드하는 데 사용하지 않아야 합니다. 이벤트 데이터 및 관련 정보에만 사용할 수 있습니다. 파일 스토리지 시스템으로 간주해서는 안 됩니다.
* Adobe 외부의 트랜잭션 메시지 인스턴스 또는 서버에 직접 액세스할 수 없으므로 이러한 서버에 이러한 파일을 푸시할 수 있는 표준 방법은 없습니다(FTP 액세스 권한 없음).
* 첨부 파일이 아닌 모든 종류의 파일을 저장하는 데 트랜잭션 메시지 인스턴스의 디스크 공간을 사용하는 것은 계약상 정확하지 않습니다.
* 이러한 파일을 호스팅하려면 다른 온라인 디스크 시스템을 사용해야 합니다. 이 시스템에 대한 FTP 액세스 권한이 있어야 하며 파일을 작성하고 삭제할 수 있어야 합니다.

>[!NOTE]
>
>성능 문제를 방지하려면 이메일당 둘 이상의 첨부 파일을 포함하지 않는 것이 좋습니다. 권장 임계값은 [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).

## 구현 {#implementation}

아래 다이어그램은 이 시나리오를 구현할 때 여러 단계를 보여줍니다.

![](assets/message-center-uc1.png)

트랜잭션 메시지에 바로 전자 메일 첨부 파일을 추가하려면 아래 단계를 따르십시오.

1. 먼저 첨부 파일을 디자인합니다. 자세한 내용은 [이 섹션](../../delivery/using/attaching-files.md#attach-a-personalized-file)을 참조하십시오.

   이 경우 실행 인스턴스에서 호스팅되지 않았더라도 전자 메일에 파일을 첨부할 수 있습니다.

1. SOAP 메시지 트리거를 통해 이메일을 보낼 수 있습니다. SOAP 호출에는 URL 매개 변수(attachmentURL)가 있습니다.

   SOAP 요청에 대한 자세한 내용은 [이벤트 설명](../../message-center/using/event-description.md).

1. 이메일을 디자인할 때 **[!UICONTROL Attachment]**.

1. 에서 **[!UICONTROL Attachment definition]** 화면에서 SOAP 첨부 파일 매개 변수를 입력합니다.

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. 메시지가 처리되면 시스템은 원격 위치(타사 서버)에서 파일을 가져와 개별 메시지에 첨부합니다.

   이 매개 변수는 변수가 될 수 있으므로 SOAP 호출을 통해 전송된 파일의 완전히 형성된 원격 URL 변수를 허용해야 합니다.

   ![](assets/message-center-uc2.png)

---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic을 사용하여 트랜잭션 메시지에 첨부 파일 추가
description: Adobe Campaign Classic을 사용하여 개별 및/또는 개인화된 첨부 파일을 통해 트랜잭션 이메일을 전송하는 방법 살펴보기
audience: message-center
content-type: reference
topic-tags: use-case
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 1%

---


# 사용 사례:첨부 파일이 있는 트랜잭션 이메일 보내기{#transactional-email-with-attachments}

이 사용 사례는 이메일 첨부 파일을 아웃바운드 디스패치에 신속하게 추가하는 것입니다.

## 키 단계 {#key-steps}

이 시나리오에서는 개별 및/또는 개인화된 첨부 파일로 트랜잭션 이메일을 보내는 방법을 알아봅니다. 첨부 파일은 트랜잭션 메시지 서버에 미리 업로드되지 않습니다.대신 즉시 생성됩니다.

고객과의 상호 작용 또는 세부 사항을 캡처할 때 이 정보를 프로세스 종료 시 고객에게 다시 보내야 할 수 있습니다(예: 이메일에 첨부된 PDF 파일).

다음은 이 시나리오의 주요 단계입니다.

1. 고객은 웹 사이트에 들어가 구매하려는 제품을 찾습니다.
1. 고객은 제품을 선택하고 일부 옵션을 사용자 정의합니다.
1. 고객이 거래를 완료합니다.
1. 거래를 확인하는 이메일이 고객에게 전송됩니다. PII(개인 식별 정보)를 이메일로 보내는 것이 권장되지 않으므로, 보안 PDF가 생성되고 이메일에 첨부됩니다.
1. 고객은 관련 데이터가 포함된 이메일 및 첨부 파일을 받습니다.

이 시나리오에서는 첨부 파일이 미리 만들어지지 않고 아웃바운드 이메일에 바로 추가되므로 다음과 같은 이점이 있습니다.

* 이렇게 하면 첨부 파일의 컨텐츠를 개인화할 수 있습니다.
* 첨부가 트랜잭션과 연관되어 있는 경우(위에 설명된 예제 시나리오에서) 고객 프로세스 중에 생성된 동적 데이터를 포함할 수 있습니다.
* PDF 파일을 첨부하면 암호화하여 HTTPS를 통해 전송할 수 있으므로 보안을 최적화할 수 있습니다.

>[!NOTE]
>
>성능 문제를 방지하기 위해 개인화된 URL에서 즉시 다운로드한 이미지를 첨부 파일로 포함하는 경우 각 이미지 크기는 기본적으로 100,000바이트를 초과할 수 없습니다. 이 권장 임계값은 [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery)에서 구성할 수 있습니다.

## 추천 {#important-notes}

이 시나리오를 구현하기 전에 아래 지침을 주의 깊게 읽으십시오.

* 트랜잭션 메시지 인스턴스는 파일이나 데이터를 저장, 내보내기 또는 업로드하는 데 사용할 수 없습니다. 이벤트 데이터 및 관련 정보에만 사용할 수 있습니다. 파일 스토리지 시스템으로 간주해서는 안 됩니다.
* Adobe 외부의 트랜잭션 메시징 인스턴스나 서버에 직접 액세스할 수 없으므로 이러한 서버에서 이러한 파일을 푸시할 수 있는 표준 방법은 없습니다(FTP 액세스 없음).
* 트랜잭션 메시징 인스턴스의 디스크 공간을 사용하여 첨부 파일이 아닌 모든 종류의 파일을 저장하는 것은 계약상 올바르지 않습니다.
* 이러한 파일을 호스팅하려면 다른 온라인 디스크 시스템을 사용해야 합니다. 이 시스템에 대한 FTP 액세스가 필요하며 파일을 작성하고 삭제할 수 있어야 합니다.

>[!NOTE]
>
>성능 문제를 방지하려면 이메일에 둘 이상의 첨부 파일을 포함하지 않는 것이 좋습니다. 권장 임계값은 [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery)에서 구성할 수 있습니다.

## 구현 {#implementation}

아래 다이어그램은 이 시나리오를 구현할 때의 여러 단계를 보여줍니다.

![](assets/message-center-uc1.png)

트랜잭션 메시지에 즉각적으로 이메일 첨부 파일을 추가하려면 아래 단계를 따르십시오.

1. 먼저 첨부 파일을 디자인합니다. 자세한 내용은 [이 섹션](../../delivery/using/attaching-files.md#attach-a-personalized-file)을 참조하십시오.

   실행 인스턴스에서 호스팅되지 않더라도 이메일에 파일을 첨부할 수 있습니다.

1. SOAP 메시지 트리거를 통해 이메일을 보낼 수 있습니다. SOAP 호출에는 URL 매개 변수(attachmentURL)가 있습니다.

   SOAP 요청에 대한 자세한 내용은 [이벤트 설명](../../message-center/using/event-description.md)을 참조하십시오.

1. 이메일을 디자인할 때 **[!UICONTROL Attachment]**&#x200B;을 클릭합니다.

1. **[!UICONTROL Attachment definition]** 화면에서 SOAP 첨부 파일 매개 변수를 입력합니다.

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. 메시지가 처리되면 시스템은 원격 위치(타사 서버)에서 파일을 가져와 개별 메시지에 첨부합니다.

   이 매개 변수는 변수가 될 수 있으므로 SOAP 호출을 통해 전송된 파일의 전체 형식의 원격 URL 변수를 수락해야 합니다.

   ![](assets/message-center-uc2.png)

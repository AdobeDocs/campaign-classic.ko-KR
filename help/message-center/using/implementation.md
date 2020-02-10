---
title: 구현
seo-title: 구현
description: 구현
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 구현{#implementation}

이 시나리오와 관련된 다른 단계가 있는 다이어그램입니다.

![](assets/message-center-uc1.png)

먼저, 첨부 파일을 디자인하는 것부터 시작합니다. 이 [문서를](../../delivery/using/attaching-files.md#attach-a-personalized-file)참조하십시오. 이렇게 하면 실행 인스턴스에서 호스팅되지 않더라도 이메일에 파일을 첨부할 수 있습니다.

SOAP 메시지 트리거를 통해 이메일을 보낼 수 있습니다. SOAP 요청에 대한 자세한 내용은 이벤트 [설명을](../../message-center/using/event-description.md)참조하십시오. SOAP 호출에는 URL 매개 변수(attachmentURL)가 있습니다.

이메일을 디자인할 때 을 클릭합니다 **[!UICONTROL Attachment]** . 화면에 SOAP 첨부 매개 변수를 **[!UICONTROL Attachment definition]** 입력합니다.

```
<%= rtEvent.ctx.attachementUrl %>
```

메시지가 처리/배포되면 시스템은 원격 위치(타사 서버)에서 파일을 가져와 개별 메시지에 첨부합니다.

이 매개 변수는 변수가 될 수 있으므로 SOAP 호출을 통해 전송된 파일의 전체 형식의 원격 URL 변수를 수락해야 합니다.

![](assets/message-center-uc2.png)


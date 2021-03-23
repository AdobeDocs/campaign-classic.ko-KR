---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic에서 전달 가능성을 관리할 때 중요 사항
description: Adobe Campaign Classic에서 제공 기능을 관리할 때 확인해야 할 주요 사항은 무엇입니까?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# 배달 가능 문제 해결{#deliverability-faq}

배달할 수 없는 문제가 발생합니까? 여기에서 해결 방법을 찾을 수 있습니다.

## MX 규칙 오류 {#mx-rule-error}

**&#39;할당량이 충족됨&#39; 오류 메시지가 의미하는 것은 무엇입니까?**

이 메시지는 특정 MX의 할당량 제한에 도달했으며 이 공급자에게 다른 이메일을 보낼 수 있을 때까지 기다려야 한다는 것을 나타냅니다.

Adobe Campaign에서는 전송할 수 있는 시간당 이메일 수와 관련된 구성이 있습니다. 인스턴스에 정의된 숫자는 실제로 전송되는 이메일 수가 아니라 ISP로 수행되는 연결 수와 관련되기 때문에 이 구성을 경계와 함께 사용해야 합니다.

즉, 성공적으로 이메일을 보내지 않고도 MX 규칙을 사용할 수 있습니다. 이 경우 IP 또는 명성 낮은 도메인이 있는 구성은 이메일을 보내기 전에 여러 연결을 시도해야 합니다. 각 시도에 대해 시간 크레디트당 메시지가 사용됩니다. 그 결과, 마케팅 캠페인 성능에 큰 영향이 미칠 것입니다.

따라서 &#39;할당량 달성&#39;은 구성 문제일 뿐만 아니라 평판에 연결될 수도 있다. [SMTP 로그](../../production/using/monitoring-processes.md#smtp-errors-per-domain)에서 오류 메시지를 분석해야 합니다.

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.

## ISP {#same-error-for-an-isp}에 대한 동일한 오류 메시지

**특정 ISP에 대해 항상 동일한 오류 메시지가 표시되는 이유는 무엇입니까?**

ISP에 대해 항상 동일한 오류 메시지가 표시되는 경우, 이메일 또는 IP가 ISP에 의해 오류로 감지되었을 수 있습니다. 다음 권장 사항을 수행합니다.
* 존재하지 않는 이메일 주소(**사용자 알 수 없음** 실패)에 연결된 실패 중 상당 부분을 받았는지 확인합니다.
* 입력한 도메인 이름의 오류를 감지하도록 구독 양식을 업데이트합니다(예:gamaul.com 또는 yaho.com)을 참조하십시오.
* 메시지가 스팸으로 선언되거나 메시지가 지속적으로 차단된다는 오류가 발견되면 대상에서 지난 12개월 동안 메시지 중 하나를 열거나 클릭하지 않은 수신자를 제외해 보십시오.

문제가 지속되면 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 상업용 또는 배달 가능 서비스에 문의하십시오.

## 격리 차단 목록 대비 {#denylist-versus-quarantine}

* **에 게시된 이메일 주소와 격리된 이메일 차단 목록 주소 간의 차이점은 무엇입니까?**

   * 상태 **[!UICONTROL Denylisted]**&#x200B;은 피드백 루프(사용자가 스팸으로 메시지를 보고하는 경우)의 결과입니다.

   * 상태 **[!UICONTROL Quarantined]**&#x200B;은(는) 소프트 바운스의 결과입니다.
   자세한 내용은 [이 섹션](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)을 참조하십시오.

* **다른 격리 오류 이유는 무엇입니까?**

   다음과 같은 10가지 이유가 있습니다.정의되지 않음, 사용자 알 수 없음, 잘못된 도메인,차단 목록, 거부됨, 오류 무시, 접근 불가, 계정 비활성화, 사서함 가득 참, 연결되지 않음.

   자세한 내용은 [격리 관리 이해](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

## {#remove-from-denylist}차단 목록에서 제거 중

* **수신인 중 한 명이 실수로 차단 목록에 추가되었습니다. 메시지를 다시 보낼 수 있도록 데니 목록에서 어떻게 제거합니까?**

   * **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;으로 이동합니다.
   * 해당 레코드의 세부 정보에서 **[!UICONTROL Status]** 필드의 값을 **[!UICONTROL Valid]**&#x200B;로 설정합니다.
   * 레코드를 저장합니다.

* **내 IP 중 하나가에 있는지 어떻게 알 수 차단 목록 있습니까? 내 IP를에서 어떻게 차단 목록 제거합니까?**

   IP 주소가에 있는지 확인하려면 다양한 웹 사이트를 사용하여 다음과 차단 목록 같이 확인할 수 있습니다.
   * [MX 도구 상자](https://mxtoolbox.com/)
   * [내 IP 주소](https://whatismyipaddress.com)

   일반적으로 IP 주소 확인 결과는 해당의 세부 정보와 IP 주소를 차단 목록 거부한 웹 사이트의 이름이 포함된 목록을 반환합니다.

   해당 링크를 클릭하면 웹 사이트 세부 정보에 액세스할 수 있습니다. 그런 다음 IP 주소를에 추가한 웹 사이트에서 웹 사이트를 삭제하도록 요청할 수 차단 목록 있습니다.

   >[!NOTE]
   >
   >삭제 프로세스는 웹 사이트에 따라 다를 수 있습니다. 일부 사이트에서는 계정을 만들어야 하지만 다른 사이트에서는 IP 주소를 제공해야 합니다.

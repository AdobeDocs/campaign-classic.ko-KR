---
product: campaign
title: Adobe Campaign Classic에서 게재 기능을 관리할 때 주요 사항
description: Adobe Campaign Classic에서 게재 기능을 관리할 때 확인할 주요 사항은 무엇입니까?
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# 게재 기능 문제 해결{#deliverability-faq}

게재 능력에 문제가 있습니까? 여기서 해결 방법을 찾을 수 있습니다.

## MX 규칙 오류 {#mx-rule-error}

**&#39;할당량이 충족됨&#39; 오류 메시지는 무엇을 의미합니까?**

이 메시지는 특정 MX의 할당량 제한에 도달했으며 이 공급자에게 다른 전자 메일을 보낼 수 있도록 기다려야 한다는 것을 나타냅니다.

Adobe Campaign에는 전송할 수 있는 시간당 이메일 수와 관련된 구성이 있습니다. 인스턴스에 정의된 숫자가 실제로 보낸 이메일 수가 아니라 ISP에서 수행한 연결 수에 영향을 주므로 이 구성은 경보와 함께 사용해야 합니다.

즉, 연결에 전자 메일을 성공적으로 보내지 않고 MX 규칙을 사용할 수 있습니다. 이 경우 IP 또는 도메인에 대한 평판이 낮은 구성은 이메일을 보내기 전에 여러 연결을 시도해야 합니다. 각 시도에 대해 시간 크레딧당 메시지가 사용됩니다. 따라서 마케팅 캠페인 성능에 상당한 영향을 주게 됩니다.

따라서 &#39;할당량이 충족됨&#39;은 구성 문제뿐만 아니라 평판과 연결될 수 있습니다. [SMTP 로그](../../production/using/monitoring-processes.md#smtp-errors-per-domain)에서 오류 메시지를 분석하는 것이 중요합니다.

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.

## ISP에 대해 동일한 오류 메시지 {#same-error-for-an-isp}

**특정 ISP에 대해 항상 동일한 오류 메시지가 표시되는 이유는 무엇입니까?**

ISP에 대해 항상 동일한 오류 메시지가 표시되는 경우, 이메일 또는 IP가 ISP에서 오류로 감지되었을 수 있습니다. 다음 권장 사항을 수행합니다.
* 존재하지 않는 이메일 주소(**사용자 알 수 없음** 실패)에 연결된 많은 오류를 수신하는지 확인합니다.
* 가입 양식을 업데이트하여 입력한 도메인 이름의 오류를 검색합니다(예:gmaul.com 또는 yaho.com)
* 메시지가 스팸으로 선언되거나 메시지가 항상 차단된다는 오류가 표시되면 지난 12개월 동안 메시지 중 하나에서 열지 또는 클릭되지 않은 수신자를 대상에서 제외하십시오.

문제가 지속되면 커머셜 또는 게재 가능성 서비스, [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

## 격리 차단 목록과 비교 {#denylist-versus-quarantine}

* **의 이메일 주소와 격리된 이메일 차단 목록 주소 간의 차이점은 무엇입니까?**

   * 상태 **[!UICONTROL Denylisted]**&#x200B;은 피드백 루프의 결과입니다(사용자가 메시지를 스팸으로 보고할 때).

   * 상태 **[!UICONTROL Quarantined]**&#x200B;은(는) 소프트 또는 하드 바운스의 결과입니다.
   자세한 내용은 [이 섹션](understanding-quarantine-management.md#quarantine-vs-denylist)을 참조하십시오.

* **다른 격리 오류 이유는 무엇입니까?**

   다음은 10가지 가능한 이유입니다.정의되지 않음, 사용자 알 수 없음, 잘못된 도메인, 도메인 차단 목록, 거부, 오류 무시, 접근 불가, 계정 사용 안 함, 사서함 가득 참, 연결되지 않음.

   자세한 내용은 [격리 관리 이해](understanding-quarantine-management.md)를 참조하십시오.

## 에서 차단 목록 제거 {#remove-from-denylist}

* **받는 사람 중 한 명이 실수로에 차단 목록 추가되었습니다. 메시지를 다시 전송할 수 있도록 데니스트에서 제거하려면 어떻게 합니까?**

   * **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**(으)로 이동합니다.
   * 해당 레코드의 세부 정보에서 **[!UICONTROL Status]** 필드의 값을 **[!UICONTROL Valid]**&#x200B;로 설정합니다.
   * 레코드를 저장합니다.

* **IP 중 하나가에 있는지 어떻게 알 수 차단 목록 있습니까? 에서 IP를 제거하려면 어떻게 차단 목록 합니까?**

   IP 주소가에 있는지 확인하려면 차단 목록 다양한 웹 사이트를 사용하여 다음과 같이 확인할 수 있습니다.
   * [MX 도구 상자](https://mxtoolbox.com/)
   * [내 IP 주소는 무엇입니까](https://whatismyipaddress.com)

   일반적으로 IP 주소 확인 결과는 세부 사항이 포함된 목록과 차단 목록 IP 주소를 거부한 웹 사이트의 이름을 반환합니다.

   해당 링크를 클릭하면 웹 사이트 세부 사항에 액세스할 수 있습니다. 그런 다음 해당 웹 사이트에 IP 주소를 추가한 웹 사이트의 삭제를 요청할 수 차단 목록 있습니다.

   >[!NOTE]
   >
   >삭제 프로세스는 웹 사이트에 따라 달라질 수 있습니다. 일부 사이트에서는 계정을 만들어야 하지만 다른 사이트에서는 IP 주소를 제공해야 합니다.

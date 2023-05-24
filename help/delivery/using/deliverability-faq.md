---
product: campaign
title: Adobe Campaign Classic의 게재 기능 관리 시 주요 사항
description: Adobe Campaign에서 게재 능력을 관리할 때 확인할 주요 사항 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---

# 전달성 문제 해결{#deliverability-faq}



전달에 문제가 있습니까? 여기에서 해결책을 찾을 수 있습니다.

## MX 규칙 오류 {#mx-rule-error}

**&#39;할당량이 충족됨&#39;이라는 오류 메시지는 무엇을 의미합니까?**

이 메시지는 특정 MX에 대한 할당량 한도에 도달했으며 이 공급자에게 다른 전자 메일을 보낼 때까지 기다려야 함을 나타냅니다.

Adobe Campaign에는 전송할 수 있는 시간당 이메일 수에 대한 구성이 있습니다. 인스턴스에 정의된 숫자는 실제로 전송된 이메일 수가 아닌 ISP로 수행된 연결 수와 관련되므로 이 구성은 주의력과 함께 사용해야 합니다.

즉, 전자 메일을 성공적으로 보내지 않고 연결에서 MX 규칙을 사용할 수 있습니다. 이 경우 IP 또는 낮은 신뢰도의 도메인이 있는 구성은 이메일을 보내기 전에 여러 연결을 시도해야 합니다. 각 시도에 대해 시간당 크레딧당 메시지가 사용됩니다. 그 결과 마케팅 캠페인 성과는 상당한 영향을 받게 됩니다.

따라서 &#39;할당량이 충족됨&#39;은 구성 문제일 뿐만 아니라 평판과 연결될 수도 있습니다. 에서 오류 메시지를 분석하는 것이 중요합니다. [SMTP 로그](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration).

## ISP에 대해 동일한 오류 메시지 {#same-error-for-an-isp}

**특정 ISP에 대해 항상 동일한 오류 메시지가 표시되는 이유는 무엇입니까?**

ISP에 대해 항상 동일한 오류 메시지가 표시되는 경우 ISP에서 이메일이나 IP가 잘못된 것으로 감지되었을 수 있습니다. 다음 권장 사항을 수행합니다.
* 존재하지 않는 이메일 주소에 연결된 대량의 오류를 수신하는지 확인(**알 수 없는 사용자** 실패).
* 가입 양식을 업데이트하여 입력한 도메인 이름의 오류를 감지합니다(예: gmaul.com 또는 yaho.com).
* 메시지가 스팸으로 선언되거나 메시지가 계속 차단된다는 오류가 표시되면 지난 12개월 동안 메시지 중 하나를 열거나 클릭하지 않은 수신자를 대상에서 제외해 보십시오.

문제가 지속되면 상업용 또는 게재 가능 서비스에 문의하십시오. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 차단 목록 격리 대 격리 {#denylist-versus-quarantine}

* **차단 목록의 이메일 주소와 격리된 이메일 주소의 차이점은 무엇입니까?**

   * 상태 **[!UICONTROL Denylisted]** 는 피드백 루프(사용자가 메시지를 스팸으로 보고할 때)의 결과입니다.

   * 상태 **[!UICONTROL Quarantined]** 소프트 또는 하드 바운스의 결과입니다.
   자세한 내용은 [이 섹션](understanding-quarantine-management.md#quarantine-vs-denylist)을 참조하십시오.

* **다른 격리 오류 이유는 무엇을 의미합니까?**

   차단 목록 정의되지 않음, 잘못된 도메인, 알 수 없는 사용자, 거부, 오류 무시, 연결할 수 없음, 계정 비활성화, 사서함 가득 참, 연결되지 않음 등 10가지 가능한 이유가 있습니다.

   자세한 내용은 [격리 관리 이해](understanding-quarantine-management.md).

## 차단 목록 제거 {#remove-from-denylist}

* **수신인 중 한 명이 실수로 차단 목록에 추가되었습니다. 메시지를 다시 보내기 시작할 수 있도록 차단 목록에서 삭제하려면 어떻게 해야 합니까?**

   * 다음으로 이동 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * 해당 레코드의 세부 정보에서 **[!UICONTROL Status]** 필드 대상 **[!UICONTROL Valid]**.
   * 레코드를 저장합니다.

* **내 IP 중 하나가 차단 목록에 있는지 어떻게 알 수 있습니까? 차단 목록에서 내 IP를 제거하려면 어떻게 해야 합니까?**

   IP 주소가 차단 목록에 있는지 확인하려면 다음과 같이 다양한 웹 사이트를 사용하여 확인할 수 있습니다.
   * [MX 도구 상자](https://mxtoolbox.com/)
   * [내 IP 주소는 무엇입니까](https://whatismyipaddress.com)

   일반적으로 IP 주소 검사 결과는 차단 목록 웹 사이트의 세부 정보와 IP 주소를 거부한 이름이 포함된 목록을 반환합니다.

   해당 링크를 클릭하면 웹 사이트 세부 정보에 액세스할 수 있습니다. 그런 다음 IP 주소를 차단 목록에 추가한 웹 사이트에서 웹 사이트를 삭제할 것을 요청할 수 있습니다.

   >[!NOTE]
   >
   >상장 폐지 절차는 웹 사이트에 따라 다를 수 있습니다. 일부 사이트에서는 계정을 만들어야 하지만 다른 사이트에서는 IP 주소를 제공해야 합니다.

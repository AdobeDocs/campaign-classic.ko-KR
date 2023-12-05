---
product: campaign
title: 전자 메일 보관
description: 전자 메일 보관
feature: Installation, Instance Settings, Email
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: e808e71ccf949bdaf735cdb2895389f03638bd71
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 2%

---

# 이메일 BCC 구성 {#email-archiving}



플랫폼에서 전송된 이메일 사본을 유지하도록 Adobe Campaign을 구성할 수 있습니다.

그러나 Adobe Campaign 자체는 보관된 파일을 관리하지 않습니다. 원하는 메시지를 외부 시스템을 사용하여 처리하고 보관할 수 있는 전용 주소로 전송할 수 있습니다.

이를 위해 보낸 이메일에 해당하는 .eml 파일을 SMTP 이메일 서버와 같은 원격 서버로 전송합니다. 보관 대상은 지정해야 하는 BCC 이메일 주소(게재 수신자에게는 보이지 않음)입니다.

## Recommendations 및 제한 사항 {#recommendations-and-limitations}

* 이메일 BCC 기능은 선택 사항입니다. 사용권 계약을 확인하십시오.
* 대상 **호스팅 및 하이브리드 아키텍처**, 계정 관리자에게 문의하여 활성화하십시오. 선택한 BCC 이메일 주소를 구성할 Adobe 팀에 제공해야 합니다.
* 대상 **온-프레미스 설치**&#x200B;를 활성화하려면 아래 지침을 따르십시오. 를 참조하십시오. [이메일 BCC 활성화 중(온-프레미스)](#activating-email-archiving--on-premise-) 및 [BCC 이메일 주소 구성(온-프레미스)](#configuring-the-bcc-email-address--on-premise-) 섹션.
* 숨은 참조 이메일 주소는 하나만 사용할 수 있습니다.
* 이메일 BCC가 구성되면 게재 템플릿 또는 을 통한 게재에서 기능이 활성화되어 있는지 확인합니다. **[!UICONTROL Email BCC]** 옵션을 선택합니다. 자세한 내용은 [이 섹션](../../delivery/using/sending-messages.md#archiving-emails)을 참조하십시오.
* 성공적으로 전송된 이메일만 고려되며 바운스는 고려되지 않습니다.
* 전자 메일 보관 시스템이 Adobe Campaign 17.2(빌드 8795)로 변경되었습니다. 이미 전자 메일 보관을 사용하고 있는 경우 수동으로 새 전자 메일 BCC 시스템으로 업그레이드해야 합니다. 자세한 내용은 [새 이메일 BCC로 이동](#updated-email-archiving-system--bcc-) 섹션.

## 이메일 BCC 활성화 중(온-프레미스) {#activating-email-archiving--on-premise-}

[!BADGE 온-프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"}


Adobe Campaign이 온프레미스에 설치되어 있을 때 BCC 전자 메일 보관을 활성화하려면 아래 단계를 따르십시오.

### 로컬 폴더 {#local-folder}

BCC 이메일 주소로 보낸 이메일을 전송하려면 보낸 이메일의 정확한 원시 복사본을 먼저 .eml 파일로 로컬 폴더에 저장해야 합니다.

로컬 폴더의 경로를에 지정해야 합니다. **config-`<instance>`.xml** 파일, 구성 예제:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>보안 설정에서 을 통해 정의된 폴더에 대한 액세스를 허용하도록 하는 것은 프로젝트를 구현하는 팀의 책임입니다. **데이터 로그 경로** 매개 변수.

전체 경로는 다음과 같습니다. **`<datalogpath>  YYYY-MM-DDHHh`**. 날짜와 시간은 MTA 서버의 시계(UTC)에 따라 설정됩니다. 예제:

```
C:\emails\2018-12-02\13h
```

아카이브 파일 이름은 입니다. **`<deliveryid>-<broadlogid>.eml`** 이메일 상태가 다음과 같지 않은 경우 **[!UICONTROL Sent]**. 상태가 다음으로 변경되면 **[!UICONTROL Sent]**, 파일 이름은 다음과 같이 됩니다. **`<deliveryid>-<broadlogid>-sent.eml`**. 예제:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>중간 소싱 인스턴스에서 BCC 이메일의 디렉토리는 중간 소싱 서버에 있습니다.
>
>deliveryID 및 broadlogID는 이메일 상태가 전송되지 않을 때 중간 소싱 서버에서 가져옵니다. 상태가 다음으로 변경되면 **[!UICONTROL Sent]**, 이러한 ID는 마케팅 서버에서 가져옵니다.

### 매개 변수 {#parameters}

로컬 폴더 경로가 정의되면에서 원하는 대로 다음 요소를 추가하고 편집합니다. **config-`<instance name>.xml`** 파일. 기본값은 다음과 같습니다.

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **압축 형식**: .eml 파일을 압축할 때 사용하는 형식입니다. 가능한 값은 다음과 같습니다.

  **0**: 압축 없음(기본값)

  **1**: 압축(.zip 형식)

* **압축 일괄 처리 크기**: 보관 파일에 추가된 .eml 파일 수(.zip 파일).


* **보관 유형**: 사용할 보관 전략 가능한 유일한 값은 입니다. **1**. 보낸 이메일의 원시 사본은 .eml 형식으로 **데이터 로그 경로** 폴더와 SMTP를 통해 BCC 이메일 주소로 전송됩니다. BCC 주소로 e- 메일 사본이 전송되면 아카이브 파일 이름이 **`<deliveryid>-<broadlogid>-sent-archived.eml`** 파일이 **dataLogPath/아카이브** 폴더를 삭제합니다. 그러면 전송 및 BCC 보관된 이메일 파일 경로가 **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: .eml 파일이 보관되는 일 수입니다. 그런 다음 자동으로 로 이동합니다. **dataLogPath/아카이브** 압축을 위한 폴더입니다. 기본적으로 .eml 파일은 2일 후에 만료됩니다.
* **purgeArchivesDelay**: 아카이브가 다음 위치에 보관되는 일 수 **dataLogPath/`<archives>`** 폴더를 삭제합니다. 해당 기간이 지나면 영구적으로 삭제됩니다. MTA가 시작되면 제거가 시작됩니다. 기본적으로 7일마다 수행됩니다.
* **pollDelay**: (으)로 전송되는 새 수신 전자 메일의 빈도(초) 확인 **데이터 로그 경로** 폴더를 삭제합니다. 예를 들어 이 매개 변수를 60으로 설정하면 1분마다 보관 프로세스가 **dataLogPath/`<date and time>`** 폴더는 필요한 경우 비우기를 적용하고 BCC 주소로 이메일 복사본을 전송하거나 필요할 때마다 보관된 파일을 압축합니다.
* **acquireLimit**: 보관 프로세스가 다시 적용되기 전에 한 번에 처리된 .eml 파일 수에 따라 **pollDelay** 매개 변수. 예를 들어, **acquireLimit** 매개 변수를 100으로 **pollDelay** 매개 변수가 60개로 설정되어 있으면 분당 100.eml 파일이 처리됩니다.
* **smtpNbConnection**: BCC 이메일 주소에 대한 SMTP 연결 수.

이메일 전송 처리량에 따라 이러한 매개 변수를 조정해야 합니다. 예를 들어 MTA가 시간당 30,000개의 이메일을 전송하는 구성에서 다음을 설정할 수 있습니다. **pollDelay** 매개 변수를 600으로, **acquireLimit** 매개 변수를 5000 및 **smtpNbConnection** 매개 변수를 2로 변경합니다. 즉, 2개의 SMTP 연결을 사용하면 10분마다 5,000개의 이메일이 BCC 주소로 전송됩니다.

## BCC 이메일 주소 구성(온-프레미스) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE 온-프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"}


>[!IMPORTANT]
>
>개인정보 보호를 위해 BCC 이메일은 PII(개인 식별 정보)를 안전하게 저장할 수 있는 보관 시스템에 의해 처리되어야 합니다.

다음에서 **config-`<instance name>.xml`** 파일, 다음 매개 변수를 사용하여 저장된 파일을 전송할 SMTP 전자 메일 서버를 정의합니다.

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: 대상 보관
* **smtpEnableTLS**: 보안 SMTP 연결 사용(TLS/SSL 프로토콜)
* **smtpRelayAddress**: 사용할 릴레이 주소
* **smtpRelayPort**: 사용할 릴레이 포트

>[!NOTE]
>
>SMTP 릴레이를 사용하는 경우 릴레이가 수행한 이메일 변경 사항은 보관 프로세스에서 고려되지 않습니다.
>
>또한 릴레이는 **[!UICONTROL Sent]** 전송되지 않은 상태를 포함하여 모든 이메일에 대한 상태. 따라서 모든 메시지가 보관됩니다.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## 이메일 BCC 모범 사례 {#best-practices}

* **BCC 주소 사서함**: MTA에서 전송하는 모든 이메일을 보관할 수 있는 충분한 수신 용량이 있는지 확인하십시오.
* **MTA 풀링**: BCC 아카이빙 기능은 MTA 수준에서 작동합니다. MTA에서 보낸 모든 이메일을 복제할 수 있습니다. 여러 인스턴스(예: 개발, 테스트 또는 프로덕션)나 여러 클라이언트(중간 소싱 환경)에서 MTA를 풀링할 수 있으므로 이 기능을 설정하면 보안에 영향을 줍니다.

   * 여러 클라이언트와 MTA를 공유하는데 클라이언트 중 하나에서 이 옵션이 활성화된 경우 이 클라이언트는 동일한 MTA를 공유하는 다른 클라이언트의 모든 전자 메일에 액세스합니다. 이러한 상황을 방지하려면 각 클라이언트에 대해 다른 MTA를 사용하십시오.
   * 단일 클라이언트에 대해 여러 인스턴스(개발, 테스트, 프로덕션)에서 동일한 MTA를 사용하는 경우 세 인스턴스 모두에서 전송된 메시지는 dataLogPath 옵션에 의해 복제됩니다.

* **연결당 이메일 수**: BCC 전자 메일 보관은 연결을 열고 해당 연결을 통해 모든 전자 메일을 보내려고 하여 작동합니다. Adobe은 내부 기술 담당자에게 주어진 연결에서 허용되는 이메일 수를 확인하는 것을 권장합니다. 이 수를 늘리면 BCC 처리량에 큰 영향을 미칠 수 있습니다.
* **BCC 전송 IP**: 현재 BCC 이메일은 일반 MTA 프록시를 통해 전송되지 않습니다. 대신 MTA 서버에서 대상 이메일 서버로 직접 연결이 열립니다. 즉, 이메일 서버 구성에 따라 네트워크의 허용 목록에 추가하다에 추가 IP를 추가해야 할 수 있습니다.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->
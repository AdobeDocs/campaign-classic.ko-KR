---
product: campaign
title: 전자 메일 보관
description: 전자 메일 보관
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 3%

---

# 이메일 BCC 구성 {#email-archiving}

![](../../assets/v7-only.svg)

플랫폼에서 보낸 이메일 사본을 유지하도록 Adobe Campaign을 구성할 수 있습니다.

그러나 Adobe Campaign 자체는 보관된 파일을 관리하지 않습니다. 선택한 메시지를 전용 주소로 전송할 수 있습니다. 여기서 외부 시스템을 사용하여 처리 및 아카이빙할 수 있습니다.

이렇게 하려면 보낸 전자 메일에 해당하는 .eml 파일이 SMTP 전자 메일 서버와 같은 원격 서버로 전송됩니다. 보관 대상은 지정해야 하는 BCC 전자 메일 주소(게재 수신자에게 표시되지 않음)입니다.

## Recommendations 및 제한 사항 {#recommendations-and-limitations}

* 이메일 BCC 기능은 선택 사항입니다. 사용권 계약을 확인하십시오.
* 대상 **호스팅 및 하이브리드 아키텍처**&#x200B;를 활성화하려면 계정 관리자에게 문의하십시오. 선택한 BCC 이메일 주소는 Adobe 팀이 대신 구성하도록 제공해야 합니다.
* 대상 **온-프레미스 설치**&#x200B;를 활성화하려면 아래 지침을 따르십시오. 자세한 내용은 [이메일 BCC 활성화(온-프레미스)](#activating-email-archiving--on-premise-) 및 [BCC 이메일 주소 구성(온-프레미스)](#configuring-the-bcc-email-address--on-premise-) 섹션에 자세히 설명되어 있습니다.
* 숨은 참조 이메일 주소는 하나만 사용할 수 있습니다.
* 이메일 BCC가 구성되면 게재 템플릿이나 을 통한 게재에서 기능이 활성화되어 있는지 확인합니다 **[!UICONTROL Email BCC]** 선택 사항입니다. 자세한 내용은 [이 섹션](../../delivery/using/sending-messages.md#archiving-emails)을 참조하십시오.
* 성공적으로 전송된 이메일만 고려하며 바운스는 고려되지 않습니다.
* 전자 메일 보관 시스템이 Adobe Campaign 17.2(빌드 8795)로 변경되었습니다. 이미 전자 메일 보관을 사용하고 있다면 새 전자 메일 BCC 시스템으로 수동으로 업그레이드해야 합니다. 자세한 내용은 [새 전자 메일 BCC로 이동](#updated-email-archiving-system--bcc-) 섹션을 참조하십시오.

## 이메일 BCC 활성화(온-프레미스) {#activating-email-archiving--on-premise-}

Adobe Campaign이 전후에 설치될 때 BCC 전자 메일 보관을 활성화하려면 아래 단계를 수행하십시오.

### 로컬 폴더 {#local-folder}

보낸 전자 메일을 BCC 전자 메일 주소로 전송할 수 있도록 하려면 보낸 전자 메일의 정확한 원시 사본을 먼저 .eml 파일로 로컬 폴더에 저장해야 합니다.

로컬 폴더의 경로는 **config-`<instance>`.xml** 파일에서 읽어올 수 있습니다. 예제:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>보안 설정에서 을 통해 정의된 폴더에 액세스할 수 있도록 하는 것은 프로젝트를 구현하는 팀의 책임입니다 **dataLogPath** 매개 변수.

전체 경로는 다음과 같습니다. **`<datalogpath>  YYYY-MM-DDHHh`**. 날짜와 시간은 MTA 서버의 시계(UTC)에 따라 설정됩니다. 예제:

```
C:\emails\2018-12-02\13h
```

아카이브 파일 이름은 **`<deliveryid>-<broadlogid>.eml`** 이메일의 상태가 아닐 때 **[!UICONTROL Sent]**. 상태가 (으)로 변경되면 **[!UICONTROL Sent]**&#x200B;로 지정하는 경우 파일 이름은 **`<deliveryid>-<broadlogid>-sent.eml`**. 예제:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>중간 소싱 인스턴스에서 BCC 이메일의 디렉토리가 중간 소싱 서버에 있습니다.
>
>deliveryID 및 broadlogID는 전자 메일의 상태가 전송되지 않을 때 중간 소싱 서버에서 가져옵니다. 상태가 (으)로 변경되면 **[!UICONTROL Sent]**, 이러한 ID는 마케팅 서버에서 가져옵니다.

### 매개 변수 {#parameters}

로컬 폴더 경로가 정의되면 다음에서 원하는 대로 요소를 추가하고 편집합니다 **config-`<instance name>.xml`** 파일. 아래는 기본값입니다.

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: .eml 파일을 압축할 때 사용되는 형식입니다. 가능한 값은 다음과 같습니다.

   **0**: 압축 없음(기본값)

   **1**: 압축(.zip 형식)

* **compressBatchSize**: 보관 파일(.zip 파일)에 추가된 .eml 파일의 수입니다.
* **archivingType**: 사용할 아카이빙 전략입니다. 가능한 값은 다음과 같습니다.

   **0**: 보낸 전자 메일의 원시 사본은 .eml 형식으로 다음 위치에 저장됩니다. **dataLogPath** 폴더(기본값) 의 아카이빙 복제본 **`<deliveryid>-<broadlogid>-sent.eml`** 파일이 **dataLogPath/archives** 폴더를 입력합니다. 보낸 전자 메일 파일 경로는 가 됩니다. **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: 보낸 전자 메일의 원시 사본은 .eml 형식으로 다음 위치에 저장됩니다. **dataLogPath** 폴더가 전송되고 SMTP를 통해 BCC 전자 메일 주소로 전송됩니다. 전자 메일 복사본이 BCC 주소로 전송되면 보관 파일 이름은 **`<deliveryid>-<broadlogid>-sent-archived.eml`** 파일이 **dataLogPath/archives** 폴더를 입력합니다. 그러면 보낸 사람 및 BCC 보관된 전자 메일 파일 경로가 됩니다 **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: 보관을 위해 보관되는 일 수 .eml 파일 지연 후 자동으로 **dataLogPath/archives** 압축할 폴더입니다. 기본적으로 .eml 파일은 2일 후에 만료됩니다.
* **purgeArchivesDelay**: 아카이브의 수는 **dataLogPath/`<archives>`** 폴더를 입력합니다. 해당 기간 이후에는 영구적으로 삭제됩니다. 제거는 MTA가 시작될 때 시작됩니다. 기본적으로 7일마다 수행됩니다.
* **pollDelay**: 수신한 새 전자 메일에 대한 빈도(초) 확인 **dataLogPath** 폴더를 입력합니다. 예를 들어 이 매개 변수가 60으로 설정되면 1분마다 보관 프로세스가 내의 .eml 파일을 통과함을 의미합니다 **dataLogPath/`<date and time>`** 폴더에서 필요한 경우 제거 기능을 적용하고 BCC 주소로 전자 메일 사본을 보내거나 필요에 따라 보관된 파일을 압축합니다.
* **acquireLimit**: 보관 프로세스가 다시 적용되기 전에 처리된 .eml 파일 수입니다. **pollDelay** 매개 변수. 예를 들어 **acquireLimit** 매개 변수를 100으로 설정하고 **pollDelay** 매개 변수가 60으로 설정되어 있으면 분당 100.eml 파일이 처리됩니다.
* **smtpNbConnection**: 숨은 참조 전자 메일 주소에 대한 SMTP 연결 수입니다.

전자 메일 전송 처리량에 따라 이러한 매개 변수를 조정해야 합니다. 예를 들어 MTA가 시간당 30,000개의 이메일을 전송하는 구성에서 다음을 설정할 수 있습니다 **pollDelay** 매개 변수를 600으로 설정하고 **acquireLimit** 매개 변수와 **smtpNbConnection** 매개 변수가 2. 즉, SMTP 연결 2개를 사용하면 10분마다 5,000개의 이메일이 BCC 주소로 전송됩니다.

## BCC 이메일 주소 구성(온-프레미스) {#configuring-the-bcc-email-address--on-premise-}

>[!IMPORTANT]
>
>개인 정보 보호를 위해 BCC 이메일은 PII(보안 개인 식별 정보)를 저장할 수 있는 보관 시스템에 의해 처리되어야 합니다.

에서 **config-`<instance name>.xml`** 파일에서 다음 매개 변수를 사용하여 저장된 파일을 전송할 SMTP 전자 메일 서버를 정의합니다.

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: 대상 보관
* **smtpEnableTLS**: 보안 SMTP 연결 사용(TLS/SSL 프로토콜)
* **smtpRelayAddress**: 사용할 릴레이 주소
* **smtpRelayPort**: 사용할 릴레이 포트

>[!NOTE]
>
>SMTP 릴레이를 사용하는 경우 릴레이에서 수행한 전자 메일의 변경 사항은 보관 프로세스에서 고려하지 않습니다.
>
>게다가, 릴레이는 **[!UICONTROL Sent]** 전송되지 않은 전자 메일 등 모든 전자 메일에 대한 상태입니다. 따라서 모든 메시지가 보관됩니다.

## 새 전자 메일 BCC로 이동 {#updated-email-archiving-system--bcc-}

>[!IMPORTANT]
>
>전자 메일 보관 시스템(BCC)이 Adobe Campaign 17.2(빌드 8795)로 변경되었습니다. 이전 빌드에서 업그레이드하고 이미 전자 메일 보관 기능을 사용하고 있는 경우 수동으로 새 BCC(전자 메일 보관 시스템)로 업그레이드해야 합니다.

이렇게 하려면 **`config-<instance>.xml`** 파일:

1. 제거 **zipPath** 매개 변수( **`<archiving>`** 노드 아래에 있어야 합니다.
1. 설정 **compressionFormat** 매개 변수 대상 **1** 필요한 경우
1. 설정 **archivingType** 매개 변수 대상 **1**.

이메일 BCC가 구성되면 **[!UICONTROL Email BCC]** 옵션 을 선택할 수 있습니다. 자세한 내용은 [이 섹션](../../delivery/using/sending-messages.md#archiving-emails)을 참조하십시오.

## 이메일 BCC 우수 사례 {#best-practices}

* **숨은 참조 주소 사서함**: MTA에서 보내는 모든 이메일을 보관하기에 충분한 수신 용량이 있는지 확인합니다.
* **MTA 풀링**: bcc 보관 기능은 MTA 수준에서 작동합니다. MTA에서 보낸 모든 이메일을 복제할 수 있도록 해줍니다. MTA가 여러 인스턴스(예: 개발, 테스트 또는 프로덕션)에서 풀링될 수 있거나 중간 소싱 환경에서 여러 클라이언트(예: 중간 소싱 환경)에서도 풀링될 수 있으므로 이 기능을 설정하면 보안에 영향을 줍니다.

   * 여러 클라이언트와 MTA를 공유하고 그 중 하나에 이 옵션이 활성화되면 이 클라이언트는 동일한 MTA를 공유하는 다른 클라이언트의 모든 이메일에 액세스합니다. 이러한 상황을 방지하려면 각 클라이언트에 대해 다른 MTA를 사용합니다.
   * 단일 클라이언트에 대해 여러 인스턴스(개발, 테스트, prod)에서 동일한 MTA를 사용하는 경우 세 개 인스턴스 모두에서 전송된 메시지는 dataLogPath 옵션에 의해 복제됩니다.

* **연결당 이메일 수**: BCC 전자 메일 보관은 연결을 열고 해당 연결을 통해 모든 전자 메일을 전송하려고 하여 작동합니다. Adobe은 내부 기술 담당자에게 주어진 연결에서 수락되는 이메일 수를 확인하는 것이 좋습니다. 이 수를 늘리면 숨은 참조 처리량에 큰 영향을 줄 수 있습니다.
* **숨은 참조 전송 IP**: 현재 숨은 참조 이메일은 일반적인 MTA 프록시를 통해 전송되지 않습니다. 대신 MTA 서버에서 대상 이메일 서버로 직접 연결이 열립니다. 즉, 이메일 서버 구성에 허용 목록에 추가하다 따라 네트워크의에 IP를 추가해야 할 수 있습니다.

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
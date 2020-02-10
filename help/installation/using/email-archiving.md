---
title: 이메일 보관
seo-title: 이메일 보관
description: 이메일 보관
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# 이메일 보관{#email-archiving}

플랫폼에서 보낸 이메일 사본을 유지하도록 Adobe Campaign을 구성할 수 있습니다.

그러나 Adobe Campaign 자체는 보관된 파일을 관리하지 않습니다. 외부 시스템을 사용하여 처리 및 보관할 수 있는 전용 주소로 원하는 메시지를 보낼 수 있습니다.

이렇게 하려면 보낸 이메일에 해당하는 .eml 파일이 SMTP 이메일 서버와 같은 원격 서버로 전송됩니다. 보관 대상은 지정해야 하는 숨은 참조 이메일 주소입니다(배달 받는 사람에게 보이지 않음).

## 권장 사항 및 제한 사항 {#recommendations-and-limitations}

* 이메일 보관 기능은 선택 사항입니다. 사용권 계약을 확인하십시오.
* 호스팅 및 하이브리드 아키텍처의 경우 계정 담당자에게 문의하여 활성화합니다. 온-프레미스 설치의 경우 아래 지침을 따르십시오. [전자 메일 보관 활성화(온-프레미스)](#activating-email-archiving--on-premise-) 및 [숨은 참조 전자 메일 주소(온-프레미스)](#configuring-the-bcc-email-address--on-premise-) 구성을 참조하십시오.
* 이메일 BCC가 구성되면 배달 템플릿에서 또는 **[!UICONTROL Archive emails]** 옵션을 통해 배달에서 기능이 활성화되어 있는지 확인합니다. 자세한 내용은 [이 섹션을](../../delivery/using/sending-messages.md#archiving-emails)참조하십시오.
* 숨은 참조 이메일 주소는 하나만 사용할 수 있습니다.
* 성공적으로 전송된 이메일만 고려되므로 바운스 수가 없습니다.
* 이메일 보관 시스템이 Adobe Campaign 17.2(빌드 8795)로 변경되었습니다. 이미 전자 메일 보관을 사용하고 있는 경우 새 BCC(전자 메일 보관 시스템)로 수동으로 업그레이드해야 합니다. 자세한 내용은 업데이트된 [BCC(이메일 보관 시스템)](#updated-email-archiving-system--bcc-) 섹션을 참조하십시오.

## 이메일 보관 활성화(온-프레미스) {#activating-email-archiving--on-premise-}

Adobe Campaign이 사전 설치된 경우 BCC 이메일 보관을 활성화하려면 아래 단계를 따르십시오.

### 로컬 폴더 {#local-folder}

보낸 이메일을 BCC 이메일 주소로 전송하려면, 보낸 이메일의 정확한 Raw 복사본을 먼저 .eml 파일로 로컬 폴더에 저장해야 합니다.

로컬 폴더의 경로는 구성에서 **config-`<instance>`.xml** 파일에 지정해야 합니다. 예:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>보안 설정을 통해 dataLogPath 매개 변수를 통해 정의된 폴더에 액세스할 수 있도록 하려면 프로젝트를 구현하는 **팀의 책임입니다** .

전체 경로는 다음과 같습니다. **`<datalogpath>  YYYY-MM-DDHHh`** Adobe 날짜와 시간은 MTA 서버의 시계(UTC)에 따라 설정됩니다. 예:

```
C:\emails\2018-12-02\13h
```

아카이브 파일 이름은 **`<deliveryid>-<broadlogid>.eml`** 이메일의 상태가 아닐 **[!UICONTROL Sent]**&#x200B;때입니다. 상태가 로 변경되면 **[!UICONTROL Sent]**&#x200B;파일 이름이 **`<deliveryid>-<broadlogid>-sent.eml`**&#x200B;됩니다. 예:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>중간 소싱 인스턴스에서 보관된 이메일의 디렉토리는 중간 소싱 서버에 있습니다.
>
>deliveryID 및 broadlogID는 이메일 상태가 전송되지 않을 때 mid-sourcing 서버에서 가져옵니다. 상태가 로 변경되면 **[!UICONTROL Sent]**&#x200B;이 ID는 마케팅 서버에서 가져옵니다.

### 매개 변수 {#parameters}

로컬 폴더 경로가 정의되면 **config-`<instance name>.xml`**파일에서 원하는 대로 다음 요소를 추가하고 편집합니다. 기본값은 다음과 같습니다.

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**:.eml 파일을 압축할 때 사용되는 형식입니다. 가능한 값은 다음과 같습니다.

   **0**:압축 없음(기본값)

   **1**:압축(.zip 형식)

* **compressBatchSize**:아카이브(.zip 파일)에 추가된 .eml 파일의 수입니다.
* **archivingType**:아카이빙 전략 가능한 값은 다음과 같습니다.

   **0**:전송된 이메일의 원시 사본은 .eml 형식으로 **dataLogPath** 폴더(기본값)에 저장됩니다. 파일의 보관 사본은 dataLogPath/archives **`<deliveryid>-<broadlogid>-sent.eml`** **** 폴더에 저장됩니다. 보낸 이메일 파일 경로가 **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**&#x200B;됩니다.

   **1**:전송된 이메일의 원시 사본은 .eml 형식으로 **dataLogPath** 폴더에 저장되며 SMTP를 통해 BCC 이메일 주소로 전송됩니다. 이메일 사본이 BCC 주소로 전송되면 보관 파일 이름이 **`<deliveryid>-<broadlogid>-sent-archived.eml`** 되고 파일이 dataLogPath/archives **폴더로** 이동합니다. 그런 다음 보낸 사람 및 숨은 참조 보관된 이메일 파일 경로가 **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**&#x200B;됩니다.

* **expirationDelay**:보관을 위해 보관되는 일 수. 지연 후 압축을 위해 **dataLogPath/archives** 폴더로 자동으로 이동합니다. 기본적으로 .eml 파일은 2일 후 만료됩니다.
* **purgeArchivesDelay**:dataLogPath/ **폴더에 보관되는 일 수`<archives>`**. 이 기간이 지나면 영구적으로 삭제됩니다. MTA가 시작될 때 제거가 시작됩니다. 기본적으로 7일마다 수행됩니다.
* **pollDelay**:dataLogPath 폴더로 들어오는 새 이메일의 빈도(초)를 **확인합니다** . 예를 들어, 이 매개 변수가 60으로 설정된 경우, 보관 프로세스는 매 분 단위로 dataLogPath/ **폴더 내의 .eml 파일을`<date and time>`**거치고, 필요한 경우 삭제를 적용하고, BCC 주소로 이메일 복사본을 전송하거나, 필요할 때마다 보관된 파일을 압축합니다.
* **acquireLimit**:pollDelay 매개 변수에 따라 보관 프로세스가 다시 적용되기 전에 한 번에 처리된 .eml **파일의** 수입니다. 예를 들어 **acquireLimit** 매개 변수를 100으로 설정하고 pollDelay **** 매개 변수를 60으로 설정하면 분당 100.eml 파일이 처리됩니다.
* **smtpNbConnection**:숨은 참조 이메일 주소에 대한 SMTP 연결 수입니다.

이메일 전송 처리량에 따라 이러한 매개 변수를 조정해야 합니다. 예를 들어 MTA가 시간당 30,000개의 이메일을 전송하는 구성에서 **pollDelay** 매개 변수를 600으로, **acquireLimit** 매개 변수를 5000으로, smtpNbConnection **매개 변수를 2로** 설정할 수 있습니다. 즉, 2개의 SMTP 연결을 사용하면 10분마다 5,000개의 이메일이 BCC 주소로 전송됩니다.

## 숨은 참조 이메일 주소 구성(온-프레미스) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>개인 정보 보호를 위해 BCC 이메일은 PII(개인 식별 정보)를 안전하게 저장할 수 있는 보관 시스템에서 처리해야 합니다.

구성 **-`<instance name>.xml`**파일에서 다음 매개 변수를 사용하여 저장된 파일을 전송할 SMTP 이메일 서버를 정의합니다.

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**:대상 보관
* **smtpEnableTLS**:보안 SMTP 연결 사용(TLS/SSL 프로토콜)
* **smtpRelayAddress**:릴레이 주소 사용
* **smtpRelayPort**:릴레이 포트를 사용합니다.

>[!NOTE]
>
>SMTP 릴레이를 사용하는 경우 릴레이에서 수행한 이메일에 대한 변경 사항이 보관 프로세스에서 고려되지 않습니다.
>
>또한, 릴레이는 전송되지 않은 이메일을 포함하여 모든 이메일에 **[!UICONTROL Sent]** 상태를 할당합니다. 따라서 모든 메시지가 보관됩니다.

## 업데이트된 BCC(이메일 보관 시스템) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>BCC(이메일 보관 시스템)가 Adobe Campaign 17.2(빌드 8795)로 변경되었습니다. 이전 빌드에서 업그레이드하고 이미 이메일 보관 기능을 사용하고 있는 경우 새 BCC(이메일 보관 시스템)로 수동으로 업그레이드해야 합니다.

이렇게 하려면 **`config-<instance>.xml`** 파일을 다음과 같이 변경합니다.

1. **노드에서 zipPath** 매개 변수를 제거합니다 **`<archiving>`** .
1. 필요한 경우 **compressionFormat** 매개 변수를 **1** 로 설정합니다.
1. archivingType **매개** 변수를 **1**&#x200B;로 설정합니다.

이메일 BCC가 구성되면 배달 템플릿이나 배달에서 **[!UICONTROL Archive emails]** 옵션을 선택해야 합니다. 자세한 내용은 [이 섹션을](../../delivery/using/sending-messages.md#archiving-emails)참조하십시오.

## 모범 사례 {#best-practices}

* **숨은 참조 주소 사서함**:MTA가 전송한 모든 이메일을 보관할 수 있는 수신 용량이 충분한지 확인하십시오.
* **MTA 상호 작용**:숨은 참조 보관 기능은 MTA 수준에서 작동합니다. MTA에서 보낸 모든 이메일을 복제할 수 있습니다. MTA를 여러 인스턴스(예: 개발, 테스트 또는 제품)에서 상호 구성할 수 있고 여러 클라이언트(예: 중간 소싱 환경)에서도 상호 통합할 수 있으므로 이 기능을 설정하면 보안에 영향을 줍니다.

   * 여러 클라이언트와 MTA를 공유하는 경우 이 클라이언트 중 하나가 이 옵션을 활성화하면 이 클라이언트는 동일한 MTA를 공유하는 다른 클라이언트의 모든 이메일에 액세스합니다. 이러한 상황을 방지하려면 각 클라이언트에 대해 다른 MTA를 사용합니다.
   * 단일 클라이언트에 대해 여러 인스턴스(개발, 테스트, prod)에서 동일한 MTA를 사용하는 경우 세 인스턴스 모두에서 전송된 메시지는 dataLogPath 옵션으로 복제됩니다.

* **연결당**&#x200B;이메일:숨은 참조 이메일 보관은 연결을 열고 해당 연결을 통해 모든 이메일을 전송하려고 하면 작동합니다. Adobe에서는 내부 기술 담당자에게 해당 연결에서 수락된 이메일 수를 확인하는 것이 좋습니다. 이 숫자를 늘리면 숨은 참조 처리량에 큰 영향을 줄 수 있습니다.
* **BCC 전송 IP**:현재, 숨은 참조 이메일은 일반 MTA 프록시를 통해 전송되지 않습니다. 대신 MTA 서버에서 대상 이메일 서버로 직접 연결이 열립니다. 즉, 이메일 서버 구성에 따라 네트워크에 추가 IP를 허용 목록에 추가해야 할 수 있습니다.


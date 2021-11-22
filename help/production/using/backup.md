---
product: campaign
title: 백업
description: 백업
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# 백업{#backup}

![](../../assets/v7-only.svg)

시스템에서 문제가 발생할 경우(물리적 또는 시스템 관련) 데이터가 손실되지 않도록 백업해야 합니다.

데이터는 두 개의 별도 위치에 저장됩니다.

* 실제 파일은 Adobe Campaign 디렉토리에 저장됩니다.
* 다른 데이터는 데이터베이스에 저장됩니다.

대부분의 데이터는 데이터베이스에 있습니다. 이는 백업할 정보의 99%를 나타냅니다.

## 물리적 파일 {#physical-files}

파일은 여러 범주로 구분됩니다.

* 구성 파일, 위치 **nl6/conf**

   이를 통해 Adobe Campaign을 매우 신속하게 다시 구성할 수 있습니다.

* 리디렉션 파일 ** nl6/var/`<instancename>`/redir**

   이들은 추적(일명 &#39;전두부&#39;) 서버에 있으며 모든 이전 캠페인 리디렉션을 포함합니다. 이전 캠페인에서 여전히 사용됩니다.

* 로그 파일: **nl6/var/`<instancename>`/log**

   이는 문제를 추적하는 데 사용할 수 있습니다.

따라서 백업할 디렉터리는 다음과 같습니다.

* nl6/conf

* nl6/var/`<instanceName>`/redir(각 인스턴스에 대해)

* nl6/var/`<instanceName>`/log(선택 사항)

* nl6/var/`<instanceName>`/relay(선택 사항)

>[!IMPORTANT]
>
>데이터베이스를 백업하는 것은 필수입니다.

## 데이터베이스 {#database}

데이터베이스에는 모든 비즈니스 라인 데이터와 Adobe Campaign 리치 클라이언트 콘솔에 표시되는 모든 정보가 포함되어 있습니다.

호스팅 회사와 특히 데이터베이스 관리자는 이 작업을 수행합니다.

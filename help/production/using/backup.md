---
product: campaign
title: 백업
description: 백업
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 6%

---

# 백업{#backup}

컴퓨터에 문제가 발생할 경우(물리적 문제이든 시스템 관련 문제이든) 데이터 손실을 방지하려면 반드시 백업을 수행해야 합니다.

데이터는 두 개의 별도 위치에 저장됩니다.

* 물리적 파일은 Adobe Campaign 디렉토리에 저장됩니다.
* 다른 데이터는 데이터베이스에 저장됩니다.

대부분의 데이터는 데이터베이스에 있습니다. 이는 백업할 정보의 99%를 나타냅니다.

## 물리적 파일 {#physical-files}

파일은 여러 카테고리로 나뉩니다.

* 구성 파일, 저장 위치 **nl6/conf**&#x200B;을(를) 사용하면 Adobe Campaign을 매우 빠르게 재구성할 수 있습니다.

* 리디렉션 파일, 저장  **nl6/var/`<instance-name>`/redir**&#x200B;는 추적(&#39;전면&#39;이라고도 함) 서버에 있으며 이전의 모든 캠페인 리디렉션을 포함합니다. 이전 캠페인에서도 여전히 사용됩니다.

* 로그 파일, 저장 위치 **nl6/var/`<instance-name>`/log**&#x200B;를 사용하여 문제를 추적할 수 있습니다.

따라서 백업할 디렉토리는 다음과 같습니다.

* nl6/conf

* nl6/var/`<instance-name>`/redir (각 인스턴스에 대해)

* nl6/var/`<instance-name>`/log (선택 사항)

* nl6/var/`<instance-name>`/relay (선택 사항)


## 데이터베이스 {#database}

>[!IMPORTANT]
>
>반드시 데이터베이스를 백업해야 합니다.


데이터베이스에는 모든 LOB(기간 업무) 데이터와 Adobe Campaign 리치 클라이언트 콘솔에 표시되는 모든 정보가 포함되어 있습니다.

호스팅 회사와 특히 해당 데이터베이스 관리자는 이 작업을 담당합니다.

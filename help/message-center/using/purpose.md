---
title: 목적
seo-title: 목적
description: 목적
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 목적{#purpose}

이 사용 사례의 목적은 이메일 첨부 파일을 아웃바운드 디스패치에 신속하게 추가하는 것입니다.

이 시나리오에서는 개별/개인화된 첨부 파일로 트랜잭션 이메일을 보내는 방법을 확인할 수 있습니다. 첨부 파일은 Transactional Messaging 서버에 미리 업로드되지 않고 즉시 생성됩니다.

고객과의 상호 작용 또는 세부 사항을 캡처할 때 이 정보를 프로세스 종료 시 고객에게 다시 보내야 할 수 있습니다. 예를 들어 이메일에 첨부된 PDF 파일로 이러한 정보를 보내야 합니다. 다음은 이 시나리오의 일반적인 단계입니다.

1. 고객은 웹 사이트에 들어가 구입하려는 제품을 찾습니다.
1. 고객은 제품을 선택하고 일부 옵션을 사용자 정의합니다.
1. 고객이 거래를 완료합니다.
1. 거래를 확인하는 이메일이 고객에게 전송됩니다. PII(개인 식별 정보)를 이메일에 보내지 않으므로 안전한 PDF를 생성하여 이메일에 첨부합니다.
1. 고객은 필요한 모든 데이터가 포함된 이메일 및 첨부 파일을 받습니다.

이 시나리오에서는 첨부 파일이 미리 만들어지지 않고 아웃바운드 이메일에 즉시 추가됩니다. 또한 첨부 파일의 컨텐츠를 개인화할 수 있습니다. 또한 첨부가 거래와 연결된 경우(위 예에서처럼) 고객 프로세스 중에 생성되는 동적 데이터를 포함해야 할 수 있습니다. 이러한 방식으로 PDF를 첨부하면 암호화하여 HTTPS를 통해 전송할 수 있으므로 보안이 최적화됩니다.

---
product: campaign
title: 데이터 가져오기 및 내보내기 시작
description: Campaign에서 데이터 가져오기 및 내보내기에 대해 자세히 알아보기
feature: Data Management, Encryption
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 12%

---

# 데이터 가져오기 및 내보내기 시작 {#get-started-data-import-export}



Adobe Campaign Classic은 데이터를 가져오고 내보낼 수 있는 데이터 관리 기능을 제공합니다. 이러한 작업은 워크플로우 또는 일반 가져오기 및 내보내기를 사용하여 수행할 수 있습니다.

>[!IMPORTANT]
>
>이 기능을 사용하는 동안 Adobe Campaign 계약에 따라 SFTP 스토리지, 데이터베이스 스토리지 및 활성 프로필 제한을 염두에 두십시오.

## 워크플로 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**워크플로** 는 가져오기 프로세스를 자동화하는 유용한 방법입니다. 로컬 파일에서 데이터를 가져오든 SFTP에서 데이터를 가져오든 간에 데이터 관리 절차를 표준화할 수 있습니다.

워크플로우를 사용하면 일정에 따라 가져오기 및 내보내기 작업을 자동으로 반복할 수 있습니다. 예를 들어 여러 정보 시스템 간의 데이터 교환을 자동화할 수 있습니다.

이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/import-export-workflows.md)을 참조하십시오.

## 일반 가져오기 및 내보내기 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

또한 Campaign Classic은 **일반 가져오기 및 내보내기** 이를 통해 가끔씩 가져오기 또는 내보내기 작업을 만들 수 있습니다.

가져오기 및 내보내기는 전용 템플릿에서 구성되며 가져오기 및 내보내기 작업을 시작하고 모니터링하는 데 사용하고 구성할 수 있습니다.

일반 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>일반 수입과 수출은 수시 작업에만 사용해야 합니다. 데이터 일관성을 보장하고 효율성을 높이려면 워크플로우를 사용하여 가져오기 및 내보내기 작업을 수행하는 것이 좋습니다.

## 데이터 암호화 및 압축 {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic을 사용하면 압축 또는 암호화된 파일을 가져오고 압축 또는 암호화된 파일을 내보낼 수 있습니다.

이러한 작업은 활용하려는 데이터에 사전 처리 단계를 적용하여 워크플로우 내에서 수행됩니다.

자세한 정보는 다음 섹션을 참조하십시오.

* [파일 압축 풀기 또는 암호 해독](../../platform/using/unzip-decrypt.md)
* [파일 압축 또는 암호화](../../platform/using/zip-encrypt.md)

## 모범 사례 및 문제 해결 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

몇 군데를 따라가셔야 합니다 [우수 사례](../../platform/using/import-export-best-practices.md) 데이터베이스 내에서 데이터 일관성을 보장하고 업데이트 또는 내보내기 작업 중 일반적인 오류를 방지하기 위해 가져오기 및 내보내기 작업을 수행할 때.

또한 SFTP 서버 사용과 관련된 권장 사항 및 일반적인 문제는에서 사용할 수 있습니다. [이 섹션](../../platform/using/sftp-server-usage.md).

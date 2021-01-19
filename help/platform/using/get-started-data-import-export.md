---
solution: Campaign Classic
product: campaign
title: 데이터 가져오기 및 내보내기 시작하기
description: Campaign Classic에서 데이터 가져오기 및 내보내기에 대한 자세한 내용을 살펴보십시오.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 6%

---


# 데이터 가져오기 및 내보내기 {#get-started-data-import-export} 시작하기

Adobe Campaign Classic은 데이터를 가져오고 내보낼 수 있는 데이터 관리 기능을 제공합니다. 이러한 작업은 워크플로우 또는 일반 가져오기 및 내보내기를 사용하여 수행할 수 있습니다.

>[!IMPORTANT]
>
>이 기능을 사용하는 동안 Adobe Campaign 계약에 따라 SFTP 저장소, 데이터베이스 저장소 및 활성 프로필 제한에 주의하십시오.

## 워크플로우 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**워크플로우** 는 가져오기 프로세스를 자동화하는 유용한 방법입니다. 로컬 파일 또는 SFTP에서 데이터를 가져오더라도 데이터 관리 절차를 표준화할 수 있습니다.

워크플로우를 사용하면 일정에 따라 가져오기 및 내보내기 작업을 자동으로 반복할 수 있습니다. 예를 들어 여러 정보 시스템 간의 데이터 교환을 자동화할 수 있습니다.

이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/import-export-workflows.md)을 참조하십시오.

## 일반 가져오기 및 내보내기 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

또한 Campaign Classic은 가져오기 또는 내보내기 작업을 가끔 만들 수 있는 **범용 가져오기 및 내보내기**&#x200B;를 제공합니다.

가져오기 및 내보내기는 가져오기 및 내보내기 작업을 시작하고 모니터하는 데 사용할 수 있도록 전용 템플릿에 구성됩니다.

일반 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/about-generic-imports-exports.md)을 참조하십시오.

>[!IMPORTANT]
>일반 가져오기 및 내보내기 기능은 임시 작업에 대해서만 사용해야 합니다. 데이터 일관성을 유지하고 효율성을 향상시키려면 워크플로우를 사용하여 가져오기 및 내보내기 작업을 수행하는 것이 좋습니다.

## 데이터 암호화 및 압축 {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic을 사용하면 압축 또는 암호화된 파일을 가져오고 압축 또는 암호화된 파일을 내보낼 수 있습니다.

이러한 작업은 활용하려는 데이터에 사전 처리 단계를 적용하여 워크플로우 내에서 수행됩니다.

자세한 정보는 다음 섹션을 참조하십시오.

* [파일의 압축을 풀거나 해독합니다.](../../platform/using/unzip-decrypt.md)
* [파일 압축 또는 암호화](../../platform/using/zip-encrypt.md)

## 우수 사례 및 문제 해결 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

가져오기 및 내보내기 작업을 수행할 때 데이터베이스 내의 데이터 일관성을 유지하고 업데이트 또는 내보내기 중에 발생하는 오류 발생을 방지하기 위해 몇 가지 [우수 사례](../../platform/using/import-export-best-practices.md)가 뒤따라야 합니다.

또한 SFTP 서버 사용과 관련된 권장 사항 및 일반적인 문제는 [이 섹션](../../platform/using/sftp-server-usage.md)에서 사용할 수 있습니다.

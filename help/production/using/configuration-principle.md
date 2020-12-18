---
solution: Campaign Classic
product: campaign
title: 구성 원칙
description: 구성 원칙
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---


# 구성 원칙{#configuration-principle}

Adobe Campaign 플랫폼은 Apache에서 사용하는 가상 호스트 개념과 유사한 인스턴스 개념을 기반으로 합니다. 이 작업 모드를 사용하면 서버에 여러 인스턴스를 할당하여 서버를 공유할 수 있습니다. 인스턴스는 서로 완전히 분리되며 자체 데이터베이스 및 구성 파일을 사용하여 작동합니다.

지정된 서버의 경우 모든 Adobe Campaign 인스턴스에 공통으로 적용되는 2개의 요소가 있습니다.

* **내부** 암호:일반 관리자 암호입니다. 특정 응용 프로그램 서버의 모든 인스턴스에는 일반적으로 사용됩니다.

   >[!IMPORTANT]
   >
   >**내부** 식별자로 로그온하려면 사전에 암호를 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/campaign-server-configuration.md#internal-identifier)을 참조하십시오.

* 다양한 기술 서버 구성:이러한 구성은 모두 인스턴스의 특정 구성에서 오버로드될 수 있습니다.

구성 파일은 설치 디렉토리의 **conf** 디렉토리에 저장됩니다. 구성은 다음 3개의 파일로 분류됩니다.

* **serverConf.xml**:모든 인스턴스에 대한 전체 구성.
* **config-**`<instance>`**.xml** (여기서 **`<instance>`** 는 인스턴스 이름):인스턴스의 특정 구성.
* **serverConf.xml.diff**:초기 구성과 현재 구성 사이의 델타입니다. 이 파일은 응용 프로그램에 의해 자동으로 생성되며 수동으로 수정해서는 안 됩니다. 빌드 버전을 업데이트할 때 사용자 수정 사항을 자동으로 전파하는 데 사용됩니다.

인스턴스 구성은 다음과 같이 로드됩니다.

* 이 모듈은 모든 인스턴스에서 공유하는 매개 변수를 얻기 위해 **serverConf.xml** 파일을 로드합니다.
* 그런 다음 **config-**`<instance>`**.xml** 파일을 로드합니다. 이 파일에 있는 값은 **serverConf.xml**&#x200B;에 포함된 값보다 우선합니다.

   이 두 파일의 형식은 동일합니다. **serverConf.xml**&#x200B;의 모든 값은 **config-`<instance>`.xml** 파일의 지정된 인스턴스에 대해 오버로드할 수 있습니다.

이 운영 모드는 구성에 매우 유연하게 적용됩니다.

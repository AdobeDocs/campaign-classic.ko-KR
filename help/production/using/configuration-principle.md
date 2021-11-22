---
product: campaign
title: 구성 원칙
description: 구성 원칙
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 구성 원칙{#configuration-principle}

![](../../assets/v7-only.svg)

Adobe Campaign 플랫폼은 Apache에서 사용하는 가상 호스트의 개념과 유사한 인스턴스 개념을 기반으로 합니다. 이 작업 모드에서는 여러 인스턴스를 할당하여 서버를 공유할 수 있습니다. 인스턴스는 서로 완전히 분리되며 자체 데이터베이스 및 구성 파일로 작동합니다.

주어진 서버의 경우 모든 Adobe Campaign 인스턴스에 공통되는 두 가지 요소가 있습니다.

* 다음 **내부** 암호: 일반 관리자 암호입니다. 특정 애플리케이션 서버의 모든 인스턴스에는 일반적으로 사용됩니다.

   >[!IMPORTANT]
   >
   >을 사용하여 로그온하려면 **내부** 식별자, 미리 암호를 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

* 여러 기술 서버 구성: 이러한 구성은 인스턴스의 특정 구성에서 모두 오버로드될 수 있습니다.

구성 파일은 **conf** 설치 디렉토리의 디렉토리입니다. 구성은 세 개의 파일로 분류됩니다.

* **serverConf.xml**: 모든 인스턴스에 대한 전체 구성입니다.
* **config-**`<instance>`**.xml** (다음과 같은 경우) **`<instance>`** 는 인스턴스 이름입니다. 인스턴스의 특정 구성
* **serverConf.xml.diff**: 초기 구성과 현재 구성 간의 델타. 이 파일은 응용 프로그램에서 자동으로 생성되므로 수동으로 수정해서는 안 됩니다. 빌드 버전을 업데이트할 때 사용자 수정 사항을 자동으로 전파하는 데 사용됩니다.

인스턴스 구성은 다음과 같이 로드됩니다.

* 모듈은 **serverConf.xml** 모든 인스턴스에서 공유하는 매개 변수를 가져올 수 있습니다.
* 그런 다음 를 로드합니다 **config-**`<instance>`**.xml** 파일. 이 파일에 있는 값은 **serverConf.xml**.

   이 두 파일의 형식은 동일합니다. 의 모든 값 **serverConf.xml** 의 특정 인스턴스에 대해 오버로드될 수 있습니다. **config-`<instance>`.xml** 파일.

이 운영 모드에서는 구성에 매우 유연하게 사용할 수 있습니다.

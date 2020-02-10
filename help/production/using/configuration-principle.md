---
title: 구성 원칙
seo-title: 구성 원칙
description: 구성 원칙
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 구성 원칙{#configuration-principle}

Adobe Campaign 플랫폼은 Apache에서 사용하는 가상 호스트의 인스턴스와 유사한 인스턴스 개념을 기반으로 합니다. 이 작업 모드를 사용하면 서버에 여러 인스턴스를 할당하여 서버를 공유할 수 있습니다. 인스턴스는 서로 완전히 분리되며 자체 데이터베이스 및 구성 파일을 사용하여 작동합니다.

지정된 서버의 경우 모든 Adobe Campaign 인스턴스에 공통으로 사용되는 두 가지 요소가 있습니다.

* 내부 **암호** :일반 관리자 암호입니다. 특정 응용 프로그램 서버의 모든 인스턴스에는 일반적으로 사용됩니다.

   >[!CAUTION]
   >
   >내부 식별자를 사용하여 **로그온하려면** 미리 암호를 정의해야 합니다. For more on this, refer to [this section](../../installation/using/campaign-server-configuration.md#internal-identifier).

* 다양한 기술 서버 구성:이러한 구성은 모두 인스턴스의 특정 구성에서 오버로드될 수 있습니다.

구성 파일은 설치 디렉토리의 **conf** 디렉토리에 저장됩니다. 구성은 세 개의 파일로 분류됩니다.

* **serverConf.xml**:모든 인스턴스에 대한 전체 구성.
* **config-**`<instance>`**.xml** (여기서 **`<instance>`** 인스턴스 이름은):인스턴스의 특정 구성.
* **serverConf.xml.diff**:초기 구성과 현재 구성 간의 델타입니다. 이 파일은 응용 프로그램에 의해 자동으로 생성되므로 수동으로 수정해서는 안 됩니다. 빌드 버전을 업데이트할 때 사용자 수정 사항을 자동으로 전파하는 데 사용됩니다.

인스턴스 구성은 다음과 같이 로드됩니다.

* 모듈은 모든 인스턴스에서 공유되는 **매개변수를 얻기 위해 serverConf.xml** 파일을 로드합니다.
* 그런 다음 **config-**`<instance>`**.xml** 파일을 로드합니다. 이 파일에 있는 값의 우선 순위는 serverConf.xml에 포함된 값보다 **높습니다**.

   이 두 파일의 형식은 동일합니다. serverConf. **xml의** 모든 값은 **config-`<instance>`.xml** 파일의 지정된 인스턴스에 대해 오버로드될 수 있습니다.

이 운영 모드는 구성에 탁월한 유연성을 제공합니다.

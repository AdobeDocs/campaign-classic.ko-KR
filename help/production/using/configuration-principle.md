---
product: campaign
title: 구성 원칙
description: 구성 원칙
feature: Monitoring, Configuration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# 구성 원칙{#configuration-principle}



Adobe Campaign 플랫폼은 Apache에서 사용하는 가상 호스트와 유사한 인스턴스 개념을 기반으로 합니다. 이 작업 모드를 사용하면 여러 인스턴스를 할당하여 서버를 공유할 수 있습니다. 인스턴스는 서로 완전히 분리되어 있으며 자체 데이터베이스 및 구성 파일로 작동합니다.

주어진 서버의 경우 모든 Adobe Campaign 인스턴스에 공통인 두 가지 요소가 있습니다.

* **내부** 암호: 일반 관리자 암호입니다. 특정 애플리케이션 서버의 모든 인스턴스에 대해 일반적입니다.

  >[!IMPORTANT]
  >
  >**내부** 식별자로 로그온하려면 미리 암호를 정의해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

* 여러 기술 서버 구성: 이러한 구성은 모두 인스턴스의 특정 구성에서 오버로드될 수 있습니다.

구성 파일은 설치 디렉터리의 **conf** 디렉터리에 저장됩니다. 구성은 세 개의 파일로 분류됩니다.

* **serverConf.xml**: 모든 인스턴스에 대한 전체 구성
* **config-**`<instance>`**.xml**(여기서 **`<instance>`**&#x200B;은(는) 인스턴스 이름): 특정 인스턴스 구성.
* **serverConf.xml.diff**: 초기 구성과 현재 구성 간의 델타입니다. 이 파일은 응용 프로그램에 의해 자동으로 생성되므로 수동으로 수정해서는 안 됩니다. 빌드 버전을 업데이트할 때 사용자 수정 사항을 자동으로 전파하는 데 사용됩니다.

인스턴스 구성은 다음과 같이 로드됩니다.

* 모듈이 **serverConf.xml** 파일을 로드하여 모든 인스턴스에서 공유하는 매개 변수를 가져옵니다.
* 그런 다음 **config-**`<instance>`**.xml** 파일을 로드합니다. 이 파일에 있는 값은 **serverConf.xml**&#x200B;에 포함된 값보다 우선 순위가 높습니다.

  이 두 파일의 형식은 동일합니다. **serverConf.xml**&#x200B;의 모든 값을 **config-`<instance>`.xml** 파일의 특정 인스턴스에 대해 오버로드할 수 있습니다.

이 운영 모드는 구성을 위한 뛰어난 유연성을 제공합니다.

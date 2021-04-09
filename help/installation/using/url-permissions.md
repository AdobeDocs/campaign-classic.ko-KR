---
solution: Campaign Classic
product: campaign
title: URL 권한 구성
description: URL 권한을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 27%

---


# URL 권한 구성 {#url-permissions}

Campaign Classic 인스턴스에서 워크플로우 등의 JavaScript 코드를 통해 호출할 수 있는 URL의 기본 목록은 제한되어 있습니다. 인스턴스는 이러한 URL이 있어야 정상 작동합니다.

기본적으로 인스턴스는 외부 URL에 연결할 수 없습니다. 그러나 외부 URL을 승인된 URL 목록에 추가할 수 있으므로 인스턴스가 URL에 연결할 수 있습니다. 이렇게 하면 파일 및/또는 데이터를 전송할 수 있도록 SFTP 서버나 웹 사이트 등의 외부 시스템에 Campaign 인스턴스를 연결할 수 있습니다.

**하이브리드** 및 **온-프레미스** 배포의 경우 관리자는 **serverConf.xml** 파일의 새 **urlPermission**&#x200B;을 참조해야 합니다.

다음 3가지 연결 보호 모드를 사용할 수 있습니다.

* **차단**:에 허용 목록에 추가하다 속하지 않은 모든 URL이 차단되고 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **자유로운**:에 속하지 않는 모든 허용 목록에 추가하다 URL이 허용됩니다.
* **경고**:에 속하지 않는 모든 URL은 허용 목록에 추가하다 허용되지만 JS 인터프리터는 관리자가 수집할 수 있도록 경고를 전송합니다. 이 모드에서는 JST-310027 경고 메시지가 추가됩니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>기본적으로 새 구현에서는 **차단** 모드를 사용합니다.
>
>마이그레이션에서 오는 기존 고객은 **경고** 모드를 임시로 사용할 수 있습니다. URL을 허용하기 전에 아웃바운드 트래픽을 분석합니다. 허용되는 URL 목록이 정의되면 URL을에 추가하고 허용 목록에 추가하다 **차단** 모드를 활성화할 수 있습니다.

자세한 내용은 다음 섹션을 참조하십시오.

* [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [호스팅 모델](hosting-models.md)
* [Campaign 서버 구성](configuring-campaign-server.md)
* [캠페인 서버 구성 파일 매개 변수](the-server-configuration-file.md)
* [보안 및 개인 정보 확인 목록](get-started-security-privacy.md)
---
product: campaign
title: URL 권한 구성
description: URL 권한을 구성하는 방법 알아보기
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4fd69aa28c2e9325f4738ec571a6632c42ec26b8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# URL 권한 구성(온-프레미스){#url-permissions}

![](../../assets/v7-only.svg)

Campaign Classic 인스턴스에서 워크플로우 등의 JavaScript 코드를 통해 호출할 수 있는 URL의 기본 목록은 제한되어 있습니다. 인스턴스는 이러한 URL이 있어야 정상 작동합니다.

기본적으로 인스턴스는 외부 URL에 연결할 수 없습니다. 그러나 인스턴스가 연결할 수 있도록 권한이 부여된 URL 목록에 일부 외부 URL을 추가할 수 있습니다. 이렇게 하면 파일 및/또는 데이터를 전송할 수 있도록 SFTP 서버나 웹 사이트 등의 외부 시스템에 Campaign 인스턴스를 연결할 수 있습니다.

>[!NOTE]
>
>이 절차는 **온-프레미스** 배포.
>
>로서의 **호스팅** 고객, [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko)에서는 URL 권한 셀프 서비스 인터페이스를 사용할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=ko)
>
>기타 **하이브리드/호스팅** 고객은 Adobe 지원 팀에 연락하여에 IP를 추가해야 허용 목록에 추가하다 합니다.

대상 **하이브리드** 및 **On-premise** 배포 시 관리자는 새로운 **urlPermission** 에서 **serverConf.xml** 파일.


다음 세 가지 연결 보호 모드를 사용할 수 있습니다.

* **차단**: 에 속하지 않는 허용 목록에 추가하다 모든 URL이 차단되며 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **허용**: 에 속하지 않는 모든 URL이 허용 목록에 추가하다 허용됩니다.
* **경고**: 에 속하지 않는 모든 URL이 허용 목록에 추가하다 허용되지만 JS 인터프리터가 경고를 표시하여 관리자가 수집할 수 있습니다. 이 모드에서는 JST-310027 경고 메시지가 추가됩니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>기본적으로 새 구현에서는 **차단** 모드.
>
>마이그레이션에서 오는 기존 고객은 임시 를 사용할 수 있습니다. **경고** 모드. URL을 허용하기 전에 아웃바운드 트래픽을 분석합니다. 허용된 URL 목록이 정의되면 URL을에 추가하고 을(를) 활성화할 수 허용 목록에 추가하다 있습니다. **차단** 모드.

자세한 정보는 다음 섹션을 참조하십시오.

* [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [호스팅 모델](hosting-models.md)
* [Campaign 서버 구성](configuring-campaign-server.md)
* [Campaign 서버 구성 파일 매개 변수](the-server-configuration-file.md)
* [보안 및 개인 정보 확인 목록](get-started-security-privacy.md)

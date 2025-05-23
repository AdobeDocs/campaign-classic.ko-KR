---
product: campaign
title: 인스턴스 만들기 및 로그온
description: 인스턴스 만들기 및 로그온
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# 인스턴스 만들기 및 로그온{#creating-an-instance-and-logging-on}



새 인스턴스 및 Adobe Campaign 데이터베이스를 생성하려면 다음 프로세스를 적용합니다.

1. 연결을 만듭니다.
1. 로그온하여 관련 인스턴스 만들기.
1. 데이터베이스를 만들기 및 구성합니다.

>[!NOTE]
>
>내부&#x200B;**식별자만**&#x200B;이러한 작업을 수행할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#internal-identifier)을 참조하십시오.

Adobe Campaign 콘솔이 시작되면 로그인 페이지에 액세스합니다.

새 인스턴스 생성 하려면 아래 단계를 팔로우 수행하십시오.

1. 자격 증명 필드의 오른쪽 상단 모서리에 있는 링크 를 클릭하여 연결 구성 창에 액세스합니다. 이 링크는 **[!UICONTROL New...]** 또는 기존 인스턴스 이름일 수 있습니다.

   ![](assets/s_ncs_install_define_connection_01.png)

1. **[!UICONTROL Add > Connection]**&#x200B;을(를) 클릭하고 Adobe Campaign 응용 프로그램 서버의 레이블과 URL을 입력합니다.

   ![](assets/s_ncs_install_define_connection_02.png)

1. URL을 통해 Adobe Campaign 애플리케이션 서버에 대한 연결을 지정합니다. 컴퓨터의 DNS, 별칭 또는 IP 주소를 사용합니다.

   예를 들어 `https://<machine>.<domain>.com` 유형 URL을 사용할 수 있습니다.

   >[!CAUTION]
   >
   >연결 URL의 `[a-z]`경우 , , `[A-Z]` `[0-9]` 대시(-) 또는 마침표만 사용하십시오.

1. 설정을 확인하려면 클릭 **[!UICONTROL Ok]** : 이제 인스턴스 생성 프로세스를 시작할 수 있습니다.
1. **[!UICONTROL Connection settings]** 창에서 내부&#x200B;**로그인와 암호 입력하여** Adobe Campaign 애플리케이션 서버에 연결합니다. 연결되면 인스턴스 생성 도우미에 액세스하여 새 인스턴스를 선언합니다
1. **[!UICONTROL Name]** 필드에 인스턴스 이름을&#x200B;**입력합니다**. 이 이름은 구성 파일 **config-`<instance>`.xml** 를 생성하는 데 사용되며 명령줄 매개 변수에서 인스턴스 식별하는 데 사용되므로 특수 문자가 없는 짧은 이름을 선택해야 합니다. 예: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   도메인 이름에 추가되는 인스턴스 이름은 40자를 초과할 수 없습니다. 이렇게 하면 &quot;메시지 보내기 ID&quot; 헤더의 크기를 제한하고 특히 SpamAssassin과 같은 도구에서 메시지가 스팸으로 간주되는 것을 방지할 수 있습니다.

1. **[!UICONTROL DNS masks]** 필드에 인스턴스 연결 대상 DNS 마스크&#x200B;**목록을 입력합니다**. Adobe Campaign 서버는 HTTP 요청에 나타나는 호스트 이름을 사용하여 연결할 인스턴스를 결정합니다.

   호스트 이름은 문자열 **https://**&#x200B;과(와) 서버 주소의 첫 번째 슬래시 문자 **/** 사이에 포함되어 있습니다.

   쉼표로 구분된 값 목록을 정의할 수 있습니다.

   ? &#42; 문자를 와일드카드로 사용하여 하나 이상의 다양한 문자(DNS, 포트 등)를 대체할 수 있습니다. 인스턴스 **경우 데모&#42;** 값은 &quot;https://demo:8080&quot;와 &quot;https://demo2&quot;균일 마찬가지로 &quot;https://demo&quot;에서도 작동합니다.

   사용되는 이름은 DNS에 정의되어 있어야 합니다. Windows의 c:/windows/system32/drivers/etc/hosts **파일과 Linux의 /etc/hosts** 파일에서 DNS 이름과 IP 주소 **간의 대응을**&#x200B;알릴 수도 있습니다. 따라서 선택한 인스턴스 호출에 연결하려면 이 DNS 이름을 사용하도록 연결 설정을 수정해야 합니다.

   서버는 특히 이메일에 이미지를 업로드하는 경우 이 이름으로 식별해야 합니다.

   또한 서버는 이 이름으로 자신에게 연결할 수 있어야 하며, 가능한 경우 루프백 주소(127.0.0.1)로 연결할 수 있어야 하며, 특히 보고서를 PDF 포맷로 내보낼 수 있어야 합니다.

1. **[!UICONTROL Language]** 드롭다운 목록에서 인스턴스 언어&#x200B;**(**&#x200B;영어(미국), 영어(영국), 프랑스어 또는 일본어를 선택합니다.

   미국 영어와 영국 영어의 차이점은 [이 섹션](../../platform/using/adobe-campaign-workspace.md#date-and-time)에 설명되어 있습니다.

   >[!CAUTION]
   >
   >이 단계 후에는 인스턴스 언어를 수정할 수 없습니다. Adobe Campaign 인스턴스는 다국어가 아닙니다. 인터페이스를 언어에서 다른 언어로 전환할 수 없습니다.

1. 인스턴스 선언을 확인하려면 **[!UICONTROL Ok]**&#x200B;을(를) 클릭하십시오. 데이터베이스를 선언하려면 로그오프했다가 다시 로그온합니다.

   >[!NOTE]
   >
   >명령줄에서 인스턴스를 만들 수 있습니다. 자세한 정보는 명령 줄을[&#128279;](../../installation/using/command-lines.md) 참조하십시오.

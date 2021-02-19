---
solution: Campaign Classic
product: campaign
title: 인스턴스 만들기 및 로그온
description: 인스턴스 만들기 및 로그온
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 3%

---


# 인스턴스 만들기 및 로그온{#creating-an-instance-and-logging-on}

새 인스턴스와 Adobe Campaign 데이터베이스를 만들려면 다음 프로세스를 적용합니다.

1. 연결을 만듭니다.
1. 관련 인스턴스를 만들려면 로그온합니다.
1. 데이터베이스를 만들고 구성합니다.

>[!NOTE]
>
>**internal** 식별자만 이러한 작업을 수행할 수 있습니다. 자세한 내용은 [내부 식별자](../../installation/using/campaign-server-configuration.md#internal-identifier)를 참조하십시오.

Adobe Campaign 콘솔을 시작하면 로그인 페이지에 액세스합니다.

새 인스턴스를 만들려면 아래 단계를 수행하십시오.

1. 자격 증명 필드의 오른쪽 상단에 있는 링크를 클릭하여 연결 구성 창에 액세스합니다. 이 링크는 **[!UICONTROL New...]** 또는 기존 인스턴스 이름일 수 있습니다.

   ![](assets/s_ncs_install_define_connection_01.png)

1. **[!UICONTROL Add > Connection]**&#x200B;을 클릭하고 Adobe Campaign 응용 프로그램 서버의 레이블과 URL을 입력합니다.

   ![](assets/s_ncs_install_define_connection_02.png)

1. URL을 통해 Adobe Campaign 응용 프로그램 서버에 대한 연결을 지정합니다. 컴퓨터의 DNS 또는 별칭 또는 IP 주소를 사용합니다.

   예를 들어 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 유형 URL을 사용할 수 있습니다.

   >[!CAUTION]
   >
   >연결 URL의 경우 다음 문자만 사용하십시오.`[a-z]`, `[A-Z]`, `[0-9]` 및 대시(-) 또는 전체 중지

1. 설정을 확인하려면 **[!UICONTROL Ok]**&#x200B;을 클릭합니다.이제 인스턴스 생성 프로세스로 시작할 수 있습니다.
1. **[!UICONTROL Connection settings]** 창에서 Adobe Campaign 응용 프로그램 서버에 연결할 **내부** 로그인 및 암호를 입력합니다. 연결된 후에는 인스턴스 만들기 마법사에 액세스하여 새 인스턴스를 선언합니다
1. **[!UICONTROL Name]** 필드에 **인스턴스 이름**&#x200B;을 입력합니다. 이 이름은 구성 파일 **config-`<instance>`.xml**&#x200B;을 생성하는 데 사용되며 명령줄 매개 변수에서 인스턴스를 식별하는 데 사용되므로 특수 문자 없이 짧은 이름을 선택해야 합니다. 예:**eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   도메인 이름에 추가된 인스턴스의 이름은 40자를 초과할 수 없습니다. 이를 통해 &quot;Message-ID&quot; 헤더의 크기를 제한하고, 특히 SpamCharacter와 같은 도구로 메시지가 스팸으로 간주되지 않도록 합니다.

1. **[!UICONTROL DNS masks]** 필드에 인스턴스를 연결해야 하는 DNS 마스크&#x200B;**의** 목록을 입력합니다. Adobe Campaign 서버는 HTTP 요청에 나타나는 호스트 이름을 사용하여 도달할 인스턴스를 결정합니다.

   호스트 이름은 문자열 **https://**&#x200B;과 서버 주소의 첫 번째 슬래시 문자 **/** 사이에 포함됩니다.

   쉼표로 구분된 값 목록을 정의할 수 있습니다.

   입력한 URL의 유효성 검사가 완료되고 나면 입력한 페이지의 모든 하위 페이지도 포함되도록 URL 끝에 ? 및 * 문자를 와일드카드로 사용하여 하나 이상의 다양한 문자(DNS, 포트 등)를 바꿀 수 있습니다. 예를 들어 **demo*** 값은 &quot;https://demo:8080&quot; 및 &quot;https://demo2&quot;에서와 마찬가지로 &quot;https://demo&quot;과 함께 작동합니다.

   사용되는 이름은 DNS에 정의해야 합니다. 또한 Windows의 **/etc/hosts** 파일과 Linux의 **/etc/hosts** 파일에서 DNS 이름과 IP 주소 간 통신을 알릴 수 있습니다. 따라서 선택한 인스턴스에 연결하려면 이 DNS 이름을 사용하도록 연결 설정을 수정해야 합니다.

   서버는 이 이름으로 식별되어야 합니다. 특히 이메일에 이미지를 업로드할 때 그렇습니다.

   또한 이 이름으로 서버에 연결할 수 있어야 하며, 루프백 주소(127.0.0.1)으로 가능한 경우 특히 보고서를 PDF 형식으로 내보낼 수 있도록 해야 합니다.

1. **[!UICONTROL Language]** 드롭다운 목록에서 **인스턴스 언어**&#x200B;를 선택합니다.영어(미국), 영어(영국), 프랑스어 또는 일본어

   미국 영어와 영국 영어 간의 차이는 [이 섹션](../../platform/using/adobe-campaign-workspace.md#date-and-time)에 설명되어 있습니다.

   >[!CAUTION]
   >
   >이 단계 후에는 인스턴스 언어를 수정할 수 없습니다. Adobe Campaign 인스턴스는 다국어를 구사하지 않습니다.인터페이스를 언어에서 다른 언어로 전환할 수 없습니다.

1. 인스턴스 선언을 확인하려면 **[!UICONTROL Ok]**&#x200B;을 클릭합니다. 데이터베이스를 선언하려면 로그오프하고 다시 로그온하십시오.

   >[!NOTE]
   >
   >명령줄에서 인스턴스를 만들 수 있습니다. 자세한 내용은 [명령줄](../../installation/using/command-lines.md)을 참조하십시오.


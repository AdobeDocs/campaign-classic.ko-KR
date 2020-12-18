---
solution: Campaign Classic
product: campaign
title: SMS 채널
description: SMS 채널
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '3149'
ht-degree: 20%

---


# SMS 채널{#sms-channel}

Adobe Campaign을 사용하면 SMS 메시지를 대량으로 개인화하여 전달할 수 있습니다. 받는 사람 프로필에는 모바일 전화 번호 이상이 포함되어야 합니다.

>[!NOTE]
>
>또한 Adobe Campaign에서는 **Adobe Campaign Mobile App Channel(NMAC)** 옵션을 통해 모바일 터미널에서 알림을 제출할 수 있습니다.
> 
>자세한 내용은 [모바일 앱 채널](../../delivery/using/about-mobile-app-channel.md) 정보 섹션을 참조하십시오.

아래 섹션에서는 SMS 채널과 관련된 정보를 제공합니다. 배달을 만드는 방법에 대한 글로벌 정보는 [이 섹션](../../delivery/using/steps-about-delivery-creation-steps.md)을 참조하십시오.

## SMS 채널 {#setting-up-sms-channel} 설정

휴대폰으로 전송하려면 다음이 필요합니다.

1. 커넥터와 메시지 유형을 지정하는 외부 계정.

   다음 커넥터는 릴리스 20.2부터 사용되지 않습니다.NetSize, 범용 SMPP(SMPP 버전 3.4 지원 바이너리 모드), Sybase365(SAP SMS 365), CLX Communications, Tele2, O2 및 iOS 더 이상 사용되지 않는 기능은 여전히 사용할 수 있지만 더 이상 향상되거나 지원되지 않습니다. 자세한 정보는 이 [페이지](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html)를 참조하십시오.

1. 이 외부 계정이 참조되는 배달 템플릿입니다.

### SMPP 외부 계정 {#creating-an-smpp-external-account} 만들기

휴대폰에 SMS를 보내려면 먼저 SMPP 외부 계정을 만들어야 합니다.
SMS 프로토콜 및 설정에 대한 자세한 내용은 이 [기술 정보](https://helpx.adobe.com/kr/campaign/kb/sms-connector-protocol-and-settings.html)를 참조하십시오.

이렇게 하려면 아래 단계를 수행합니다:

1. 트리의 **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** 노드에서 **[!UICONTROL New]** 아이콘을 클릭합니다.
1. 계정 유형을 **라우팅**, 채널을 **모바일(SMS)**&#x200B;으로 정의하고 배달 모드는 **대량 배달**&#x200B;으로 정의합니다.

   ![](assets/extended_smpp_create_account.png)

1. **[!UICONTROL Enabled]** 상자를 선택합니다.
1. **[!UICONTROL Mobile]** 탭의 **[!UICONTROL Connector]** 드롭다운 목록에서 **[!UICONTROL Extended generic SMPP]**&#x200B;을 선택합니다.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 릴리스 20.2부터 레거시 커넥터는 사용되지 않으며 지원되지 않습니다. **[!UICONTROL Extended generic SMPP]** 커넥터를 사용하는 것이 좋습니다. 권장 커넥터로 마이그레이션하는 방법에 대한 자세한 내용은 이 [페이지](https://helpx.adobe.com/kr/campaign/kb/sms-connector.html)를 참조하십시오.

1. **[!UICONTROL Enable verbose SMPP traces in the log file]** 옵션을 사용하면 모든 SMPP 트래픽을 로그 파일에 덤프할 수 있습니다. 커넥터의 문제를 해결하고 공급자가 보는 트래픽과 비교하려면 이 옵션을 활성화해야 합니다.

1. **[!UICONTROL Connection settings]** 탭에서 다른 외부 계정 필드를 완료하는 방법에 대해 설명하는 SMS 서비스 공급업체에 문의하십시오.

   그런 다음 선택한 항목에 따라 **[!UICONTROL SMSC implementation name]** 필드에 입력할 값을 제공하는 공급자에게 문의하십시오.

   MTA 하위 항목당 공급자에 대한 연결 수를 정의할 수 있습니다. 기본적으로 1로 설정됩니다.

1. 기본적으로 SMS의 문자 수는 GSM 표준을 충족합니다.

   GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 또는 여러 부분으로 나누어 전송되는 메시지의 경우 153자로 제한됩니다.

   >[!NOTE]
   >
   >특정 문자(중괄호, 대괄호, 유로 심벌 등)는 두 글자로 계산합니다.
   >
   >사용 가능한 GSM 문자 목록은 아래에 나와 있습니다.

   원하는 경우 해당 상자를 선택하여 문자 변환을 승인할 수 있습니다.

   ![](assets/extended_smpp_transliteration.png)

   이 작업에 대한 자세한 정보는 [이 섹션](#about-character-transliteration)을 참조하십시오.

1. **[!UICONTROL Throughput and delays]** 탭에서 아웃바운드 메시지의 최대 처리량(&quot;MT&quot;, 모바일 종료됨)을 초당 MT로 지정할 수 있습니다. 해당 필드에 &quot;0&quot;을 입력하면 처리량이 무제한이 됩니다.

   지속 시간에 해당하는 모든 필드의 값은 초 단위로 입력해야 합니다.

1. **[!UICONTROL Mapping of encodings]** 탭에서 인코딩을 정의할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](#about-text-encodings)을 참조하십시오.

1. **[!UICONTROL SMSC specificities]** 탭에서 기본적으로 **[!UICONTROL Send full phone number]** 옵션이 비활성화됩니다. SMPP 프로토콜을 존중하고 SMS 공급자(SMSC)의 서버에 숫자만 전송하려는 경우 활성화하지 마십시오.

   그러나 특정 공급자가 &#39;+&#39; 접두사를 사용해야 하는 경우 공급자에게 확인하는 것이 좋습니다. 필요한 경우 이 옵션을 사용하도록 설정하는 것이 좋습니다.

   **[!UICONTROL Enable TLS over SMPP]** 확인란을 사용하여 SMPP 트래픽을 암호화할 수 있습니다. 자세한 내용은 이 [기술 노트](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)를 참조하십시오.

1. **[!UICONTROL Extended generic SMPP]** 커넥터를 구성하는 경우 자동 답글을 설정할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](#automatic-reply)을 참조하십시오.

### 문자 변환 정보 {#about-character-transliteration}

문자 변환 기능은 SMPP 모바일 배달 외부 계정의 **[!UICONTROL Mobile]** 탭에서 설정할 수 있습니다.

변환은 GSM 표준에서 고려하지 않는 SMS 문자를 다른 문자로 바꾸는 작업입니다.

* 음역법이 **[!UICONTROL authorized]**&#x200B;이면 메시지를 보낼 때 고려되지 않는 각 문자가 GSM 문자로 대체됩니다. 예를 들어 &quot;ë&quot;라는 글자는 &quot;e&quot;로 대체됩니다. 따라서 메시지는 약간 변경되지만 글자 수 제한은 그대로 유지됩니다.
* 음역설이 **[!UICONTROL not authorized]**&#x200B;이면 계산에 포함되지 않은 문자가 포함된 각 메시지가 이진 형식(유니코드)으로 전송됩니다.따라서 모든 문자가 그대로 전송됩니다. 그러나 유니코드를 사용하는 SMS 메시지는 70자(또는 여러 부분으로 나누어 보내는 SMS의 경우 67자)로 제한됩니다. 최대 글자 수를 초과하면 메시지가 여러 개로 보내져 추가 비용이 발생할 수 있습니다.

>[!IMPORTANT]
>
>SMS 메시지의 콘텐츠에 개인화 필드를 삽입하면 GSM 인코딩에서 고려하지 않는 문자가 들어갈 수 있습니다.

문자 변환은 기본적으로 비활성화되어 있습니다. SMS 메시지의 모든 문자를 그대로 유지하려는 경우, 예를 들어 제대로 된 이름이 바뀌지 않게 하려는 경우 이 옵션을 활성화하지 않는 것을 추천합니다.

그러나 SMS 메시지에 유니코드 메시지를 생성하는 문자가 많이 포함된 경우, 이 옵션을 활성화하여 메시지 전송 비용을 제한할 수 있습니다.

다음 표에서는 GSM 표준에서 고려하여 지정한 문자를 보여 줍니다. 아래에 언급된 문자 외에 메시지 본문에 삽입된 모든 문자는 전체 메시지를 이진 형식(유니코드)으로 전환하여 70자로 제한합니다.

**기본 문자**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> "라는 </td> 
   <td> P </td> 
   <td> 음란 </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> ] </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: 스페이스

ESC: 이스케이프

LF: 라인 피드

CR: 캐리지 리턴

**고급 문자(두 글자로 계산)**

^ { } `[ ~ ]` | €

### 텍스트 인코딩 정보 {#about-text-encodings}

SMS 메시지를 보낼 때 Adobe Campaign에서는 하나 또는 여러 개의 텍스트 인코딩을 사용할 수 있습니다. 각 인코딩은 고유한 문자 세트를 가지며 SMS 메시지에 맞는 글자 수를 정합니다.

새 SMPP 모바일 배달 외부 계정을 구성할 때 **[!UICONTROL Mobile]** 탭에서 **[!UICONTROL Mapping of encodings]**&#x200B;을 정의할 수 있습니다.**[!UICONTROL data_coding]** 필드를 사용하면 Adobe Campaign에서 SMSC에 사용되는 인코딩을 통신할 수 있습니다.

>[!NOTE]
>
>**data_coding** 값과 실제로 사용되는 인코딩 간의 매핑은 표준화되어 있습니다. 그러나 특정 SMSC에는 고유한 매핑이 있습니다.이 경우 **Adobe Campaign** 관리자가 이 매핑을 선언해야 합니다. 자세한 내용은 공급자에게 문의하십시오.

**data_condings**&#x200B;를 선언할 수 있으며 필요한 경우 인코딩을 강제 적용할 수 있습니다.이렇게 하려면 표에 단일 인코딩을 지정합니다.

* 인코딩의 매핑을 정의하지 않으면 커넥터는 일반 비헤이비어를 수행합니다.

   * 이는 GSM 인코딩을 사용하여 **data_coding = 0** 값을 할당하려고 합니다.
   * GSM 인코딩이 실패할 경우 **UCS2** 인코딩을 사용하여 **data_coding = 8** 값을 할당합니다 .

* 연결된 **[!UICONTROL data_coding]** 필드 값과 함께 사용할 인코딩을 정의할 때 Adobe Campaign은 목록에서 첫 번째 인코딩을 사용하려고 합니다. 첫 번째 인코딩이 불가능하다고 확인되면 다음 사항이 표시됩니다.

>[!IMPORTANT]
>
>선언의 순서가 중요합니다. 목록을 **비용** 오름차순으로 배치하는 것을 추천합니다. 이렇게 하면 각 SMS 메시지에 가능한 많은 문자를 입력할 수 있는 인코딩을 선호하도록 할 수 있습니다.
>
>사용하려는 인코딩만 선언해야 합니다. SMSC에서 제공하는 인코딩 중 일부가 사용자의 사용 목적에 맞지 않을 경우 목록에 선언하지 마십시오.

### 자동 답글 {#automatic-reply}

확장된 일반 SMPP 커넥터를 설정할 때 자동 응답을 구성할 수 있습니다.

구독자가 Adobe Campaign을 통해 전송한 SMS 메시지에 답글을 보내고 &quot;STOP&quot;과 같은 키워드가 포함된 경우 **[!UICONTROL Automatic reply sent to the MO]** 섹션에서 자동으로 다시 보내는 메시지를 구성할 수 있습니다.

>[!NOTE]
>
>키워드는 대/소문자를 구분하지 않습니다.

각 키워드에 대해 일반적으로 배달을 보내는 데 사용되는 숫자인 짧은 코드를 지정하고 발신자 이름으로 사용할 메시지를 가입자에게 입력합니다.

동작을 자동 응답에 연결할 수도 있습니다.**[!UICONTROL Send to quarantine]** 또는 **[!UICONTROL Remove from quarantine]**. 예를 들어 수신자가 &quot;STOP&quot; 키워드를 보낼 경우 구독 취소 확인 메시지를 자동으로 수신하여 격리하도록 전송됩니다.

![](assets/extended_smpp_reply.png)

**[!UICONTROL Remove from quarantine]** 액션을 자동 응답에 연결하면 해당 키워드를 전송하는 수신자는 자동으로 격리되지 않습니다.

수신자는 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 메뉴를 통해 사용할 수 있는 **[!UICONTROL Non deliverables and addresses]** 테이블에 나열됩니다.

* 짧은 코드가 무엇이든 동일한 응답을 보내려면 **[!UICONTROL Short code]** 열을 비워 두십시오.
* 키워드에 상관없이 동일한 응답을 보내려면 **[!UICONTROL Keyword]** 열을 비워 두십시오.
* 응답을 보내지 않고 작업을 수행하려면 **[!UICONTROL Response]** 열을 비워 두십시오. 예를 들어 &quot;중지&quot; 이외의 메시지로 응답하는 사용자를 격리 조치에서 제거할 수 있습니다.

동일한 공급자 계정의 확장 일반 SMPP 커넥터를 사용하는 외부 계정이 여러 개 있는 경우 다음 문제가 발생할 수 있습니다.짧은 코드에 회신을 보낼 때 외부 계정 연결 시 회신을 받을 수 있습니다. 따라서 전송된 자동 회신은 예상 메시지가 될 수 없습니다.
이를 방지하려면 사용 중인 공급자에 따라 다음 솔루션 중 하나를 적용합니다.

* 각 외부 계정에 대해 공급자 계정을 하나 만듭니다.
* **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** 탭에서 **[!UICONTROL System type]** 필드를 사용하여 각 짧은 코드를 구분합니다. 각 계정에 대해 다른 값을 제공자에게 요청합니다.

   ![](assets/extended_smpp_system-type.png)

확장 범용 SMPP 커넥터를 사용하여 외부 계정을 설정하는 단계는 [SMPP 외부 계정 만들기](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) 섹션에 자세히 설명되어 있습니다.

### 배달 템플릿 {#changing-the-delivery-template} 변경

Adobe Campaign은 모바일에 전달하기 위한 템플릿을 제공합니다. 이 템플릿은 **[!UICONTROL Resources > Templates > Delivery templates]** 노드에서 사용할 수 있습니다. 자세한 내용은 [템플릿 정보](../../delivery/using/about-templates.md) 섹션을 참조하십시오.

SMS 채널을 통해 전달하려면 채널 커넥터를 참조하는 템플릿을 만들어야 합니다.

기본 배달 템플릿을 유지하려면 복제한 다음 구성하는 것이 좋습니다.

아래 예에서, 이전에 활성화된 SMPP 계정을 통해 메시지를 전달하는 템플릿을 만듭니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Delivery templates]** 노드로 이동합니다.
1. **[!UICONTROL Send to mobiles]** 템플릿을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Duplicate]** 을 선택합니다.

   ![](assets/s_user_mobile_template_change_01.png)

1. 템플릿의 레이블을 변경합니다(예: **모바일로 전송(SMPP)**).

   ![](assets/s_user_mobile_template_change_02.png)

1. **[!UICONTROL Properties]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL General]** 탭에서 이전 단계에서 만든 외부 계정에 해당하는 라우팅 모드를 선택합니다.

   ![](assets/s_user_mobile_template_change_03.png)

1. 템플릿을 만들려면 **[!UICONTROL Save]**&#x200B;을 클릭합니다.

   ![](assets/s_user_mobile_template_list.png)

이제 외부 계정 및 SMS를 통해 전달할 수 있는 배달 템플릿이 있습니다.

## SMS 배달 {#creating-a-sms-delivery} 만들기

### 배달 채널 {#selecting-the-delivery-channel} 선택

새 SMS 배달을 만들려면 아래 절차를 따르십시오.

>[!NOTE]
>
>배달 생성에 대한 글로벌 개념은 [이 섹션](../../delivery/using/steps-about-delivery-creation-steps.md)에 있습니다.

1. 배달 대시보드와 같은 새 배달을 만듭니다.
1. 이전에 만든 배달 템플릿 **모바일로 전송(SMPP)**&#x200B;을 선택합니다. 자세한 내용은 [배달 템플릿 변경](#changing-the-delivery-template) 섹션을 참조하십시오.

   ![](assets/s_user_mobile_wizard.png)

1. 레이블, 코드 및 설명을 사용하여 배달을 식별합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.
1. 이 정보를 확인하고 메시지 구성 창을 표시하려면 **[!UICONTROL Continue]**&#x200B;을 클릭합니다.

## SMS 컨텐츠 정의 {#defining-the-sms-content}

SMS의 컨텐츠를 만들려면 아래 단계를 따르십시오.

1. 마법사의 **[!UICONTROL Text content]** 섹션에 메시지 내용을 입력합니다. 도구 모음 단추를 사용하여 내용을 가져오거나 저장 또는 검색할 수 있습니다. 마지막 단추는 개인화 필드를 삽입하는 데 사용됩니다.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   개인화 필드는 [개인화 정보](../../delivery/using/about-personalization.md) 섹션에 표시됩니다.

1. 페이지 하단에 있는 **[!UICONTROL Preview]**&#x200B;을 클릭하여 개인화로 메시지 렌더링을 표시합니다. 미리 보기를 시작하려면 도구 모음에서 **[!UICONTROL Test personalization]** 단추를 사용하여 수신자를 선택합니다. 정의된 타겟에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   SMS 메시지를 승인할 수 있습니다. 컨텐츠 편집기의 오른쪽에 표시되는 휴대폰 화면에서 SMS 컨텐츠를 볼 수도 있습니다. 화면을 클릭하고 마우스를 사용하여 내용을 스크롤합니다.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. 수신자에 대한 정보를 보려면 **[!UICONTROL Data loaded]** 링크를 클릭합니다.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Latin-1(ISO-8859-1) 코드 페이지가 사용되는 경우 SMS 메시지 길이는 160자로 제한됩니다. 유니코드로 작성된 메시지는 70자를 초과할 수 없습니다. 특정 특수 문자는 메시지 길이에 영향을 줄 수 있습니다. 메시지 길이에 대한 자세한 내용은 [문자 변환 정보](#about-character-transliteration) 섹션을 참조하십시오.
   >
   >개인화 필드 또는 조건부 컨텐츠 필드가 있는 경우 메시지 크기는 받는 사람마다 다릅니다. 개인화가 수행되면 메시지의 길이를 평가해야 합니다.
   >
   >분석을 실행하면 메시지 길이가 확인되고 오버플로가 발생한 경우 경고가 표시됩니다.

1. NetSize 커넥터 또는 SMPP 커넥터를 사용하는 경우 배달 보낸 사람의 이름을 개인화할 수 있습니다. 자세한 내용은 [고급 매개 변수](#advanced-parameters) 섹션을 참조하십시오.

## 대상 모집단 선택 {#selecting-the-target-population}

게재의 대상 모집단을 선택할 때의 자세한 프로세스는 [이 섹션](../../delivery/using/steps-defining-the-target-population.md)에 표시됩니다.

개인화 필드 사용에 대한 자세한 내용은 [개인화 정보](../../delivery/using/about-personalization.md)를 참조하십시오.

시드 목록 포함에 대한 자세한 내용은 [시드 주소 정보](../../delivery/using/about-seed-addresses.md)를 참조하십시오.

## SMS 메시지 전송 {#sending-sms-messages}

메시지를 승인하고 만드는 배달의 받는 사람에게 메시지를 보내려면 **[!UICONTROL Send]**&#x200B;을 클릭합니다.

게재의 유효성을 확인하고 전송할 때의 자세한 프로세스는 아래 섹션에 있습니다.

* [게재 유효성 검사](../../delivery/using/steps-validating-the-delivery.md)
* [게재 보내기](../../delivery/using/steps-sending-the-delivery.md)

### 고급 매개 변수 {#advanced-parameters}

**[!UICONTROL Properties]** 단추를 사용하면 고급 배달 매개 변수에 액세스할 수 있습니다. SMS 게재와 관련된 매개 변수는 **[!UICONTROL Delivery]** 탭의 **[!UICONTROL SMS parameters]** 섹션에 있습니다.

다음 옵션을 사용할 수 있습니다.

* **보낸 사람 주소**:11자로 제한된 영숫자 문자열을 사용하여 배달 보낸 사람의 이름을 개인화할 수 있습니다. 그 분야는 숫자만 가지고 있지 않아야 한다. 표시할 조건(예: 수신자의 영역 코드에 따라 다른 이름)을 정의할 수 있습니다.

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >발신자 이름 편집과 관련하여 해당 국가의 법률을 확인하십시오. 이 기능을 제공하는지 여부를 운영자도 확인해야 합니다.

* **전송 모드**:SMS로 메시지 전송
* **우선 순위**:메시지에 할당된 중요도 수준입니다. **[!UICONTROL Normal]** 우선 순위는 기본적으로 선택됩니다. 서비스 공급업체에 **[!UICONTROL High]** 우선 순위와 함께 보낸 SMS 비용을 문의하십시오.
* **응용 프로그램** 유형:SMS 전달에 할당할 애플리케이션을 선택합니다. **[!UICONTROL Direct Marketing]** 옵션은 기본적으로 선택되어 있으며 가장 일반적으로 사용되는 옵션입니다.

**NetSize 커넥터에 대한 매개 변수**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **단일 메시지에 여러 SMS를 사용합니다**.여러 SMS 메시지를 통해 160자 이상의 메시지를 보낼 수 있습니다.

**SMPP 커넥터에 대한 매개 변수**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **메시지당 최대 SMS 수**:이 옵션을 사용하면 메시지를 보내는 데 사용할 SMS 수를 설정할 수 있습니다. 번호가 0으로 설정된 경우 SMS를 사용하여 메시지를 전달할 수 있습니다. 예를 들어 SMS 수가 1이나 2로 설정되어 있고 메시지가 이 임계값을 초과하는 경우 전송되지 않습니다.

## SMS 배달 모니터링 및 추적 {#monitoring-and-tracking-sms-deliveries}

메시지를 보낸 후 배달을 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [게재 모니터링](../../delivery/using/about-delivery-monitoring.md)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [메시지 추적 기본 정보](../../delivery/using/about-message-tracking.md)

## 인바운드 메시지 처리 중 {#processing-inbound-messages}

**nlserver sms** 모듈은 정기적으로 SMS 라우터를 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서와 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**:배달 로그를 확인하여 메시지 상태를 확인합니다.

   >[!NOTE]
   >
   >전송된 모든 SMS는 기본 키로 외부 계정에 연결됩니다. 이 방법으로 다음을 수행합니다.
   >
   > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
   > * SMS 계정은 상태 보고서가 올바른 계정에 속하도록 단일 외부 계정에만 연결할 수 있습니다


* **구독 취소**:SMS 배달 알림을 받지 않으려면 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 조항에 따라 메시지를 허용하는 경우 **인바운드 SMS** 워크플로 활동을 통해 메시지를 검색한 다음 쿼리를 작성하여 해당 수신자에게 **더 이상 연락하지 않음** 옵션을 사용하도록 할 수 있습니다.

   [워크플로](../../workflow/using/architecture.md) 안내서를 참조하십시오.

## InSMS 스키마 {#insms-schema}

InSMS 스키마는 들어오는 SMS와 관련된 정보를 포함합니다. 이러한 필드에 대한 설명은 desc 속성을 통해 사용할 수 있습니다.

* **메시지**:수신한 SMS 컨텐츠
* **원본**:메시지의 원본에서 모바일 번호입니다.
* **providerId**:SMSC(메시지 센터)가 반환하는 메시지의 식별자입니다.
* **만든 날짜**:수신 메시지 날짜가 Adobe Campaign에 삽입되었습니다.
* **extAccount**:Adobe Campaign 외부 계정.

   >[!IMPORTANT]
   >
   >다음 필드는 NetSize에만 적용됩니다.
   >
   >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**:수신 메시지의 별칭입니다.
* **구분 기호**:메시지의 별칭과 본문 사이의 구분 기호.
* **messageDate**:연산자가 제공한 메시지 날짜입니다.
* **receivvalDate**:SMSC(메시지 센터)에서 연산자의 날짜 메시지를 받았습니다.
* **deliveryDate**:SMSC가 보낸 날짜 메시지(메시지 센터).
* **largeAccount**:수신 SMS에 연결된 고객 계정 코드
* **countryCode**:연산자 국가 코드.
* **operatorCode**:연산자 네트워크 코드.
* **linkedSmsId**:이 SMS가 응답인 나가는 SMS에 연결된 Adobe Campaign 식별자(broadlogId)입니다.

## 자동 답글 관리(미국 규정) {#managing-automatic-replies--american-regulation-}

Adobe Campaign을 통해 전송한 SMS 메시지에 댓글을 단 구독자가 STOP, HELP 또는 YES 등의 키워드를 사용하는 경우 미국 시장에서 자동으로 반환되는 메시지를 구성해야 합니다.

예를 들어 수신자가 키워드 STOP을 보내면 구독 취소되었음을 알리는 확인 메시지가 자동으로 수신됩니다.

이 유형의 메시지에 대한 보낸 사람 이름은 일반적으로 배달을 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>다음 세부 절차는 확장된 범용 SMPP 커넥터를 제외한 SMPP 커넥터에만 유효합니다. 자세한 내용은 [SMPP 외부 계정 만들기](#creating-an-smpp-external-account) 섹션을 참조하십시오.
>
>이것은 미국 마케팅 캠페인에 대해 미국 운영자들이 수행하는 인증 과정의 일부를 차지한다. 이 키워드가 포함된 가입자 SMS 메시지에 대한 이러한 응답은 수신자가 메시지를 받은 즉시 가입자에게 전송해야 합니다.

1. 다음 유형의 XML 파일을 만듭니다.

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. **`<shortcode>`** 태그의 **name** 특성에 대해 메시지 보낸 사람 이름 대신 표시할 짧은 코드를 지정합니다.

   각 **`<reply>`** 태그에 **키워드** 속성과 **text** 속성을 이 키워드에 대해 보낼 메시지와 함께 입력합니다.

   >[!NOTE]
   >
   >각 키워드는 대문자로 작성해야 합니다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예제:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 완료되면 **smsAutoReply.xml** 이름으로 이 파일을 저장합니다.

   파일 이름은 Linux에서 대/소문자를 구분합니다.

1. 이 파일을 웹 서버와 동일한 위치에 있는 Adobe Campaign의 **conf** 디렉토리로 복사합니다.

>[!IMPORTANT]
>
>이런 자동 메시지는 역사를 보존하지 않는다. 따라서 [배달 대시보드](../../delivery/using/delivery-dashboard.md)에는 표시되지 않습니다.
>
>이러한 메시지는 [상업용 압력 규칙](../../campaign/using/pressure-rules.md)의 일부로 간주되지 않습니다.

---
solution: Campaign Classic
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic 릴리스 정보
feature: 개요
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: 2c2dff554c716468c0984f3d893bd29aa9fd4453
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# 최신 릴리스{#latest-release}

이 페이지에는 **최신 Campaign Classic 릴리스 후보 버전**&#x200B;에 포함된 새로운 기능, 개선 사항 및 수정 사항이 나와 있습니다.

>[!NOTE]
>
>캠페인 **GA(일반 가용성) 빌드는**&#x200B;입니다.[[!DNL Gold Standard] 11 릴리스](../../rn/using/gold-standard.md#gs-11) 및 [캠페인 20.2.5 릴리스](../../rn/using/release--20-2.md).


## ![](assets/do-not-localize/blue_2.png) 릴리스 21.1.2 - 빌드 9282 {#release-21-1-2-build-9282}

_2021년 4월 14일_

* 보안을 최적화하기 위해 암호 관리가 향상되었습니다.
* MTA 충돌을 발생시킬 수 있는 문제를 수정했습니다.

## ![](assets/do-not-localize/red_2.png) 릴리스 21.1.1 - 빌드 9277 {#release-21-1-1-build-9277}

_2021년 2월 22일_

**향상된 보안 기능**

* 보안을 최적화하도록 콘솔 인증 메커니즘이 개선되었습니다. (NEO-26944)
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-28532)

**호환성 업데이트**

이제 다음 시스템이 Campaign에서 지원됩니다.

* Salesforce API 버전 49가 이제 Salesforce CRM 외부 계정을 사용할 때 지원됩니다.

**사용되지 않는 기능**

이제 **기술 제공 모니터링** 보고서를 더 이상 사용하지 않습니다.

더 자세한 내용은 [사용되지 않거나 제거된 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

**개선 사항**

**EFS(이메일 피드백 서비스)**&#x200B;는 Enhanced MTA의 피드백을 바로 캡처하여 보고 정확도를 향상하는 확장 가능한 서비스입니다. 이 기능은 개인 베타 버전으로 출시되며 모든 고객은 향후 릴리스에서 점진적으로 사용할 수 있습니다.

* 이제 완벽하고 정밀한 보고를 위해 모든 카테고리의 피드백을 캡처합니다.
* 이제 게재됨 표시기의 계산은 정확도 및 반응도 향상을 위해 Enhanced MTA의 실시간 피드백을 기반으로 합니다.
* EFS는 동기식 소프트 바운스 보고로 지연되는 문제를 해결합니다.

자세한 내용은 [세부 설명서](../../delivery/using/sending-with-enhanced-mta.md#efs)를 참조하십시오.
이 개인 베타에 참가하려면 [양식](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)을 작성해 주십시오. 그러면 연락을 드리겠습니다.

**기타 변경 사항**

* 압축을 사용하여 큰 추적 로그에 대한 전송 속도가 향상되었습니다.
* 여러 작업으로 워크플로우를 실행 시 시간 초과를 방지하기 위해 Workflow Heatmap을 개선했습니다. (NEO-27423).
* 종료 날짜가 지나도 오퍼를 표시할 수 있는 문제를 해결했습니다. 이제 Campaign Classic은 종료 날짜만 계산하지 않고 전체 타임스탬프를 고려합니다. (NEO-27590)
* Google+ 링크가 **소셜 네트워크 공유 링크** 개인화 블록에서 제거되었습니다.
* 마지막 릴리스에서 버그 수정 구현 후 문제를 해결했습니다. SMS 게재 실패를 유발하는 SSL/TLS를 통해 연결할 때 호스트 이름에 검사가 추가되었습니다. 프록시가 있는 POP3, SMS, HTTP 등 대부분의 프로토콜에 대해 호스트 이름 확인이 비활성화되었으며, SMS 외부 계정에 대한 인증서 검사가 3가지 값으로 향상되었습니다(NEO-29581). [자세히 알아보기](../../delivery/using/sms-protocol.md#skip-tls)

**패치**

* Tab, Enter 및 Escape 단축키가 새 로그온 화면에서 작동하지 않던 문제를 해결했습니다.
* 새로 만든 워크플로우의 이름이 저장 후 기본값으로 대체되는 새로 고침 문제를 해결했습니다(NEO-26106).
* 워크플로우를 실행할 때 **외부 파일** 타겟 매핑을 사용하여 **게재** 활동 이전에 **데이터 보강** 활동의 일부로 새 필드가 추가되는 문제가 해결되었습니다. 원치 않는 필드가 **외부 파일** 타겟 매핑에 추가되었습니다. (NEO-27687)
* 이전에 만들어 저장한 웹 애플리케이션을 다시 열 때 소스 코드의 일부 문자가 변경되는 문제를 해결했습니다. (NEO-27597)
* 링크 추적을 위한 새 서명 메커니즘을 포함한 빌드로 업그레이드할 때 발생할 수 있는 문제가 해결되었습니다(빌드 19.1.4 및 Campaign 20.2부터). 여러 템플릿이 하나의 이벤트에 연결되어 있는 경우 업그레이드하면 트랜잭션 메시지를 보낼 때 잘못된 템플릿이 선택될 수 있습니다. (NEO-28326)
* MTA가 응답하지 않고 다시 시작하지 않으면 게재를 처리할 수 없는 문제를 해결했습니다. (NEO-27455)
* 날짜/시간 형식 열에 대한 대량 로드 작업 중 타임스탬프 관리와 관련된 MSSQL 데이터베이스의 문제를 수정했습니다.
* Redshift xtk 함수를 사용할 때 발생하는 워크플로우 쿼리 문제를 해결했습니다. 이제 SubDays, SubSeconds, SubMinutes 및 SubHours는 두 Redshift 타임스탬프 유형(NEO-24962)을 모두 허용합니다.
* 익명 액세스 권한이 있는 보고서를 미리 보기할 때 스크립트 오류 메시지가 표시되는 문제를 해결했습니다. (NEO-27081)
* 게재 분석을 수행할 때 서버의 메모리 사용을 줄일 수 있는 문제를 해결했습니다.
* 복잡한 특정 쿼리를 실행하려 할 때 인스턴스가 작동하지 않는 문제를 해결했습니다.
* **Twitter 페이지 동기화** 기술 워크플로우가 실행되지 않는 문제를 해결했습니다. (NEO-28634)
* **트윗(twitter)** 게재 템플릿을 사용하여 Twitter에 게시하려고 할 때 decryptPassword  기능과 관련된 오류 메시지를 표시할 수 있는 문제를 수정했습니다. (NEO-28216)
* 워크플로우에서 **JavaScript** 활동을 사용하여 HTTP 요청을 할 때 발생하는 문제를 해결했습니다. 호스트 이름에서 포트 번호를 정의한 후 다음 오류로 호출이 실패합니다(NEO-29146).

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* 타켓 데이터 개인화를 통한 새 게재를 보낼 수 없는 문제를 해결했습니다(NEO-30323).
* 마케팅 인스턴스에서 코어 파일을 발생시키는 몇 가지 충돌 문제를 해결습니다.
* 다음 오류로 인해 **추적** 워크플로우가 실패하던 문제를 해결했습니다(NEO-25206).

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* 캠페인의 **타겟팅 및 워크플로우** 탭 내에서 게재를 만들고 저장할 때 발생하는 문제를 해결했습니다. 다음 오류로 미리 보기가 실패합니다(NEO-29440).

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* 마케팅 인스턴스와 Adobe Campaign Standard 인스턴스 또는 Campaign Classic 중간 소싱 인스턴스 간에 외부 계정을 설정하고 &quot;DisableFOH2=1&quot; 옵션을 사용할 때 발생하는 오류를 해결했습니다. 외부 계정에서 &quot;DisableFOH2=1&quot; 옵션을 사용할 때 연결이 올바르게 닫혀 있지 않고 충돌하면 다음 오류가 발생합니다(NEO-26258).

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* 서버와 공급자 간에 연결 문제가 발생하는 경우 SMS 오류를 해결습니다. 그러면 MTA 하위 모듈에 의해 연결이 자동으로 비활성화됩니다. 새 하위 모듈이 시작되지 않은 경우 Adobe Campaign Classic은 이 실패한 연결에 연결하지 않습니다.

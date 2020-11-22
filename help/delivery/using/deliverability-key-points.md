---
solution: Campaign Classic
product: campaign
title: 제공 기능 주요 포인트
description: 택배 능력을 개선하기 위한 주요 내용
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

---


# 제공 기능 주요 포인트{#deliverability-key-points}

Adobe Campaign 이메일의 전달 가능성을 최적화하려면 아래 나열된 우수 사례를 사용하는 것이 좋습니다. 제공 능력 문제는 일반적으로 인터넷 서비스 제공업체와 메일 서버 관리자가 시행하는 스팸으로부터 보호하는 조치와 관련이 있습니다.

**이메일 전달 능력은** 메시지 수신 시, 이메일 주소를 통해, 짧은 시간 내에, 컨텐츠와 포맷의 예상 품질을 결정하는 일련의 특성을 의미합니다.

이러한 특성은 다음 네 가지 주요 카테고리로 분류됩니다.
* 데이터 품질
* 메시지 및 내용
* 인프라 전송
* 평판

이들은 성공적인 이메일 전달 프로그램의 기반이 됩니다.

배달율 **은** 수신자에게 성공적으로 배달된 이메일 수입니다.

배달 가능 비율은 많은 요인, 특히
* 인스턴스의 올바른 구성
* 귀하의 IP 주소 평판
* 타깃팅된 주소의 품질
* 불만 및 이탈률 감소
* 메시지 내용
* 메시지 인증(SPF, DKIM, DMARC)
* 보낸 사람 평판

다음은 배달이 잘 되는지 확인할 수 있는 핵심 사항의 목록입니다.

## 네트워크 구성 확인 {#network-configuration}

스팸들은 그들의 실체를 숨기려고 노력하고 그 결과 그들의 서버를 식별하기 어렵게 만들었다. 서버의 ID를 숨기려고 하지 않는 합법적인 네트워크 구성은 대량의 이메일을 전송하는 데 반드시 필요합니다.

## 유효한 주소로 보내기 {#valid-addresses}

주소 생성기는 자주 이름과 성명 목록을 기반으로 사용한다.또한 메일 서버에서 발송한 기술 알림은 거의 처리되지 않습니다. 잘못된 주소의 비율이 높은 것은 종종 스팸의 신호로 해석됩니다. 이중 옵트인 메커니즘과 효과적인 기술 바운스 메시지 처리를 통해 이러한 문제를 방지할 수 있습니다.

## 불만 및 이탈률 감소 {#reduce-complaint-rates}

ISP는 일반적으로 수신한 메시지를 스팸으로 보고하는 중요한 방법을 가지고 있습니다. 이렇게 하면 신뢰할 수 없는 출처를 파악할 수 있다. 옵트아웃 요청을 신속하게 준수하고, 지정된 목록을 정기적으로 사용하고, 이중 옵트인 시스템을 통해 동의 여부를 확인하고, 피드백 루프를 구현함으로써 불만율을 줄일 수 있습니다.

## 허니포트 주소로 보내기 {#honeypot-addresses}

ISP와 기타 조직( [Project Honey Pot](https://www.projecthoneypot.org/) 웹 사이트 참조)은 물리적 사용자에 해당하지 않고 단순히 분자를 유도하기 위해 생성된 사서함을 사용합니다. 이른바 &#39;허니 포트&#39;라는 주소는 스팸보트가 정해서 불법 송신자를 잡기 위해 웹에 게시된다. 이중 옵트인 메커니즘의 사용은 목록에 추가되는 이러한 종류의 주소를 사용하지 못하게 합니다. 타사 목록을 사용할 때는 해당 관리자가 사용하는 방법을 반드시 확인해야 합니다.

## 메시지 내용 조정 {#message-content}

특정 메시지의 콘텐츠는 특정 필터를 스팸으로 감지할 수 있습니다. 특정 단어의 사용, 제목 줄 및 메시지 내에 느낌표를 사용하는 경우, 스팸의 등장으로 읽습니다. 스팸 차단 필터가 불쾌한 텍스트를 자동으로 분석하지 않도록 텍스트를 이미지로 바꾸기 위해 스팸 메일을 보내는 사람도 알려져 있다. 이에 대한 응답으로, 비율이 높은 메시지(HTML 형식)나 이미지가 첨부 파일로 차단될 수 있습니다.

## 명성에 걸맞게 작업 {#reputation}

스팸들은 오랜 시간 동안 명성을 유지하기 위해 프로그램 배달을 한다. 경우에 따라 ISP가 부과한 모범 사례를 충족하기 위해 마케팅 계획을 조정해야 하며 평판이 최고(경사)된 후에는 정기적으로 배송을 구성해야 합니다.

## 권장사항 {#best-practices}

Adobe Campaign와의 전달 능력과 관련된 모범 사례를 살펴보십시오. 아래 링크를 사용하여 항목을 탐색하고 지침을 찾으십시오.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="시작" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>시작</strong>
    </a>
    </div>
    <p>
    <em>새 플랫폼 시작</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="디자인" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>디자인</strong>
    </a>
    </div>
    <p>
    <em>메시지 내용 제어</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="디자인" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>보내기</strong>
    </a>
    </div>
    <p>
    <em>평판 향상</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="최적화" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>최적화</strong>
    </a>
    </div>
    <p>
    <em>기술 추천</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="확인" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>모니터</strong>
    </a>
    </div>
    <p>
    <em>모니터링 도구</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="최적화" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>문제 해결</strong>
    </a>
    </div>
    <p>
    <em>문제 해결</em>
    <p>
  </td>
</tr>
</table>

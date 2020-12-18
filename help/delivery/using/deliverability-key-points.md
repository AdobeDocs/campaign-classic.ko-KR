---
solution: Campaign Classic
product: campaign
title: 제공 가능한 주요 포인트
description: 배달할 수 있는 능력을 개선하기 위해 확인하는 핵심 포인트
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

---


# 배달 가능 키 포인트{#deliverability-key-points}

Adobe Campaign 이메일의 전달 가능성을 최적화하려면 아래에 나와 있는 우수 사례를 사용하는 것이 좋습니다. 제공 가능성 문제는 일반적으로 인터넷 서비스 제공업체와 메일 서버 관리자가 구현한 스팸 방지를 위한 방지와 연결됩니다.

**이메일** 배달은 짧은 시간 내에, 컨텐츠 및 형식 측면에서 예상되는 품질과 함께, 메시지가 대상에 도달할 수 있는 능력을 결정하는 일련의 특성을 의미합니다.

이러한 특성은 4가지 주요 카테고리로 분류됩니다.
* 데이터 품질
* 메시지 및 내용
* 인프라 전송
* 평판

성공적인 이메일 제공 프로그램의 기반이 됩니다.

**배달율**&#x200B;은 수신자에게 배달된 보낸 이메일의 수입니다.

배달 가능 비율은 많은 요인, 특히 다음과 같은 경우에 따라 달라집니다.
* 인스턴스의 올바른 구성
* IP 주소 평판
* 타깃팅된 주소의 품질
* 불만 및 이탈률 감소
* 메시지 내용
* 메시지 인증(SPF, DKIM, DMARC)
* 보낸 사람 평판

다음은 배달이 잘 되는지 확인할 수 있는 핵심 사항의 목록입니다.

## 네트워크 구성 {#network-configuration} 확인

스팸들은 그들의 진짜 신원을 숨기려고 노력하고 그 결과 그들의 서버를 식별하기 어렵게 만들었다. 서버의 ID를 숨기려고 하지 않는 적절한 네트워크 구성은 대량의 볼륨으로 이메일을 전송하는 데 반드시 필요합니다.

## 유효한 주소 {#valid-addresses}로 보내기

주소 생성기는 자주 이름과 이름이 자주 나오는 목록을 기반으로 하여 사용한다.또한 메일 서버에서 보내는 기술 알림을 처리하는 경우는 거의 없습니다. 잘못된 주소의 비율이 높은 것은 종종 스팸의 표시로 해석됩니다. 이중 옵트인 메커니즘과 효과적인 기술 바운스 메시지 처리를 통해 이러한 오류를 방지할 수 있습니다.

## 불만 및 이탈률 감소 {#reduce-complaint-rates}

ISP는 일반적으로 수신한 메시지를 스팸으로 보고하는 뛰어난 방법을 가지고 있습니다. 따라서 신뢰할 수 없는 출처를 식별할 수 있습니다. 옵트아웃 요청을 신속하게 준수하고, 지정된 목록을 정기적으로 사용하고, 이중 옵트인 시스템을 통해 동의를 확인하고, 피드백 루프를 구현함으로써 불만율을 줄일 수 있습니다.

## 허니포트 주소로 보내기 {#honeypot-addresses}

ISP 및 기타 조직([Project Honey Pot](https://www.projecthoneypot.org/) 웹 사이트 참조)은 실제 인물에 대응하지 않고 단순히 스패머를 조작하기 위해 만든 사서함을 사용합니다. 이 소위 &quot;허니 포트&quot; 주소는 스팸보트가 수집해서 불법 보낸 사람을 잡기 위해 웹에 게시된다. 이중 옵트인 메커니즘을 사용하면 이러한 유형의 주소가 목록에 추가되지 않습니다. 제3자 목록을 사용할 때는 해당 유지 관리자가 사용하는 방법을 반드시 확인해야 합니다.

## 메시지 내용 {#message-content} 조정

특정 메시지의 컨텐츠는 특정 필터를 사용하여 스팸으로 감지할 수 있습니다. 특정 단어의 사용, 제목 줄 및 메시지 내에 느낌표를 사용하는 것은 스팸의 등장으로 읽습니다. 스팸 방지 필터로 불쾌한 텍스트를 자동으로 분석하지 않도록 스팸을 스팸으로 교체할 수도 있습니다. 이에 대한 응답으로, 이미지 또는 이미지가 첨부 파일로 많은 비율이 있는 메시지(HTML 형식)가 차단될 수 있습니다.

## 명성에 따라 작업 {#reputation}

스팸들은 시간이 지남에 따라 명성을 유지하기 위해 프로그램 배달을 한다. 평판이 높은(경사 업) 후에 ISP에서 부과하는 모범 사례에 맞게 마케팅 계획을 조정해야 하는 경우가 있습니다.

## 권장사항 {#best-practices}

Adobe Campaign와의 전달 능력과 관련된 모범 사례를 살펴볼 수 있습니다. 아래 링크를 사용하여 항목을 탐색하고 지침을 찾으십시오.

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

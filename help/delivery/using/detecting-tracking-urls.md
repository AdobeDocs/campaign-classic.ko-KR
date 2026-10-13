---
product: campaign
title: 추적 URL 감지
description: URL 추적을 위한 권장 패턴에 대해 자세히 알아보기
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 3%
---
# 추적 URL 감지

Adobe Campaign은 게재 분석 중에 콘텐츠에서 추적할 URL을 감지합니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. URL 검색 방법과 사용할 패턴에 대해 알아보려면 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## 비보안 패턴

콘텐츠에 개인화된 링크를 추가할 때 잠재적인 보안 차이를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 두지 마십시오. [이 페이지](../../installation/using/privacy.md#url-personalization)에서 자세히 알아보십시오.

예를 들어 `<a href="http://<%=myURL%>">` 구문은 **안전하지 않음**&#x200B;이므로 사용하지 않아야 합니다.

* 이 구문을 사용하면 Adobe Campaign에서 생성한 링크에 하나 이상의 매개 변수가 포함된 경우 보안 문제가 발생할 수 있습니다.
* Tidy가 일부 링크를 잘못 패치할 수 있으며 임의로 발생할 수 있습니다. 일반적인 증상은 이메일 증명에는 표시되지만 미리보기에는 표시되지 않는 HTML 조각입니다.
* URL을 이스케이프 처리하는 것은 문제가 있습니다. URL의 일부 문자로 인해 문제가 발생할 수 있습니다.
* 리디렉션 URL의 매개 변수와 충돌하는 ID라는 매개 변수를 사용할 수 없습니다.
* Adobe Campaign이 &quot;myURL&quot;의 가능한 모든 값을 무의미하게 추적하므로 추적의 관심은 게재 통계로 제한됩니다.

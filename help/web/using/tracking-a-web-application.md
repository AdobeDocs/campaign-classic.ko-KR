---
solution: Campaign Classic
product: campaign
title: 웹 애플리케이션 추적
description: 웹 애플리케이션 추적
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---


# 웹 애플리케이션 추적{#tracking-a-web-application}

Adobe Campaign을 사용하면 추적 태그를 삽입하여 웹 애플리케이션 페이지의 방문을 추적하고 측정할 수 있습니다. 이 기능은 모든 웹 응용 프로그램 유형(양식, 온라인 설문 조사, DCE를 사용하여 만든 웹 페이지 등)에 사용할 수 있습니다.

따라서 여러 탐색 경로를 정의하고 성공 여부를 평가할 수 있습니다. 그런 다음 각 애플리케이션의 보고서에서 복구된 데이터를 사용할 수 있습니다.

이 버전에서 향상된 주요 기능은 다음과 같습니다.

* 탐색 경로 정의(예: 구매, 구독, 반품 등)를 용이하게 하기 위해 동일한 페이지에 여러 개의 추적 태그를 삽입할 수 있습니다.
* 웹 애플리케이션 대시보드에서 여러 페이지의 탐색 경로 및 추적 태그 보기

   ![](assets/trackers_1.png)

* 전체 추적 보고서 생성

   ![](assets/trackers_5.png)

   주요 지표는 다음과 같습니다.

   * **전환율**:탐색 경로의 모든 단계를 표시한 사람 수입니다.
   * **바운스 비율**:첫 번째 단계만 표시한 사람 수
   * **전환 단계**:각 단계 간의 손실률

   게다가, **섹터** 유형 차트는 그 출처별 인구를 보여줍니다.

## 트래픽 소스 식별 {#identifying-the-traffic-source}

두 가지 다른 모드를 사용하여 웹 응용 프로그램에 액세스할 때 방문자가 어디에서 오는지 식별할 수 있습니다.

1. 웹 응용 프로그램 페이지에 대한 액세스 권한을 부여하기 위해 특정 배달 전송:이 경우, 트래픽 소스는 이 배달이고
1. 웹 응용 프로그램을 전용 트래픽 소스에 연결:이 경우 외부 &#39;트래픽 소스&#39; 형식 배달이어야 합니다. 웹 응용 프로그램 속성이나 대상 매핑에서 선택할 수 있습니다.

   ![](assets/trackers_6.png)

웹 애플리케이션에서 트래픽 소스를 식별하기 위해 Adobe Campaign은 다음 정보를 검색할 수 있습니다.

1. 소스 배달 식별자(nlId 쿠키),
1. 웹 응용 프로그램 속성에 정의된 외부 전달의 식별자(있는 경우)
1. 대상 매핑에 정의된 외부 배달의 식별자입니다(있는 경우).

>[!NOTE]
>
>익명 추적은 배포 마법사에서 해당 옵션을 활성화한 경우에만 가능합니다.
>
>For more on this, refer to the [Installation guide](../../installation/using/deploying-an-instance.md).

## DCE(Digital Content Editor)로 디자인된 웹 애플리케이션 {#web-applications-designed-with-digital-content-editor--dce-}

HTML 컨텐츠 편집기( **DCE)를 사용하여 웹 응용 프로그램을 만들면** 추적 태그가 편집기의 **[!UICONTROL Properties]** 탭에서 삽입됩니다. DCE(Digital Content Editor)에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

웹 인터페이스를 사용할 때는 페이지 속성에서 추적 태그를 삽입해야 합니다.

![](assets/trackers_3.png)

이 **[!UICONTROL Display blocks]** 아이콘을 사용하면 페이지에 대해 정의된 추적 태그 수를 볼 수 있습니다.

![](assets/trackers_4.png)


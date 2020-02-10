---
title: 로드 중(SOAP)
seo-title: 로드 중(SOAP)
description: 로드 중(SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 로드 중(SOAP){#loading-soap}

>[!CAUTION]
>
>SOAP( **Loading)** 활동은 FDA(Federated Data Access) **** 모듈이 설치되어 있는 경우에만 사용할 수 있습니다. 사용권 계약을 확인하십시오.

SOAP **(Loading)** 활동은 외부 데이터베이스의 FDA를 통해 직접 데이터를 수집할 수 없는 경우 **데이터 로딩(RDBMS)** 작업 외에 사용됩니다.

작업은 다음과 같습니다.

1. XML 예제와 WSDL 중 하나를 선택합니다.

   다음 예는 메시지 센터 모듈의 기술 워크플로우에서 비롯됩니다.

   ![](assets/load_soap_002.png)

1. XML 예제의 경우 샘플 파일을 선택합니다. 결과 예를 설정하기 위해 파일이 분석됩니다.

   WSDL 파섹 선택한 서비스 및 호출이 자동으로 업데이트되고 표시됩니다.

   ![](assets/soap_load_003.png)

1. 식별된 각 열을 **[!UICONTROL Click here to view and edit analysis results]** 지정하려면 선택합니다.

   ![](assets/soap_load_001.png)

   예제를 업데이트하려면 을 **[!UICONTROL Re-analyze the example]**&#x200B;선택합니다.

   또한 **[!UICONTROL Advanced parameters]** 링크를 통해 열 데이터의 형식을 개인화할 수 있습니다. 가져온 데이터 서식에 대한 자세한 내용은 이 [섹션을](../../platform/using/importing-data.md#import-wizard)참조하십시오.

1. 라인 번호를 식별자로 사용하거나 SOAP 호출이 여러 요소를 반환하도록 지정할 수 있습니다.
1. 함수에 따라 다음 탭 스크립트를 입력합니다.

   * **[!UICONTROL Initialization]**:soap 연결을 설정합니다.
   * **[!UICONTROL Iteration]**:SOAP 서비스 호출을 수행합니다. 이 함수의 반환은 예제 또는 WSDL의 설명과 호환되는 XML 객체여야 합니다.

      이 탭의 코드는 null XML 개체가 반환될 때까지 Adobe Campaign에서 루프로 호출됩니다.

   * **[!UICONTROL Finalization]**:연결을 닫거나 처리 중에 만든 다른 리소스를 사용할 수 있습니다.


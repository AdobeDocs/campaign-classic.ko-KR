---
product: campaign
title: 필터 만들기
description: 사용자 지정 테이블에 대한 필터를 만드는 방법을 알아봅니다
feature: Profiles, Custom Resources
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 6fad3dac-9af0-4796-adcf-d1de4b255aca
TQID: 'https://experienceleague.adobe.com/o8D1KiuODDNW87aki7q7ZaRU0vNITegmsMRCJ08YUzo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%
---
# 필터 만들기{#creating-filters}

Adobe Campaign과 함께 제공되는 기본 제공 수신자 테이블과 마찬가지로 새 수신자 테이블은 사전 정의된 필터 배치를 받을 수 있습니다.

이러한 필터는 수신자용 세그먼트와 동일한 기능을 가진 대상 선택 창에서 사용할 수 있습니다(매개 변수 입력 양식, 폴더 등 사용).

1. **[!UICONTROL Administration > Configuration > Predefined filters]** 노드로 이동합니다.
1. 새 필터를 만듭니다.
1. 필터의 **[!UICONTROL Label]**&#x200B;을(를) 입력한 다음 **[!UICONTROL Document type]** 필드에서 외부 수신자 테이블과 일치하는 스키마를 선택합니다.
1. 스키마의 필드를 기반으로 **[!UICONTROL filtering conditions]**&#x200B;을(를) 만듭니다.
1. 필터를 저장합니다.

---
product: campaign
title: 가져오기 및 내보내기 모범 사례
description: 데이터를 가져오거나 내보낼 때 따라야 하는 모범 사례에 대해 자세히 알아보십시오
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# 가져오기 및 내보내기 모범 사례 {#import-export-best-practices}



아래 설명된 몇 가지 간단한 규칙을 주의하고 준수하면 데이터베이스 내에서 데이터 일관성을 보장하고 데이터베이스 업데이트나 데이터 내보내기 중 일반적인 오류를 방지할 수 있습니다.

## 워크플로우 템플릿 사용 {#using-import-templates}

데이터 가져오기를 목표로 하는 대부분의 워크플로우에는 다음 활동이 포함되어야 합니다. **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

워크플로우 템플릿을 사용하면 유사한 가져오기를 준비하고 데이터베이스 내에서 데이터 일관성을 유지하는 것이 매우 편리합니다.

많은 프로젝트에서 가져오기는 **[!UICONTROL Deduplication]** 프로젝트에 사용된 파일에 중복 항목이 없으므로 활동을 수행할 수 있습니다. 서로 다른 파일을 가져올 때 중복 항목이 표시되는 경우가 있습니다. 중복 제거는 매우 어렵습니다. 따라서 중복 제거 단계는 모든 가져오기 워크플로우에서 적절한 예방책입니다.

들어오는 데이터가 일관되고 정확하거나 IT 부서나 Adobe Campaign 관리자가 처리할 것이라고 가정할 때는 주의하십시오. 프로젝트 중에 데이터 청소를 염두에 두십시오. 데이터를 가져올 때 중복 제거, 조정 및 일관성을 유지합니다.

데이터를 가져오도록 디자인된 일반 워크플로우 템플릿의 예는 [예: 데이터를 가져오기 위한 워크플로우 템플릿](../../platform/using/creating-import-export-templates.md) 섹션을 참조하십시오.

## 플랫 파일 형식 사용 {#using-flat-file-formats}

가장 효율적인 가져오기 형식은 플랫 파일입니다. 플랫 파일은 데이터베이스 수준에서 일괄 모드로 가져올 수 있습니다.

예제:

* 구분 기호: 탭 또는 세미콜론
* 헤더가 있는 첫 줄
* 문자열 구분 기호 없음
* 날짜 형식: YYYY/MM/DD HH:mm:SS

가져올 파일의 예:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 압축 사용 {#using-compression}

가능하면 가져오기 및 내보내기에 압축된 파일을 사용합니다. GZIP은 기본적으로 지원됩니다. 파일을 가져올 때 사전 처리를 추가하거나 데이터를 추출할 때 각각 **[!UICONTROL Load file]** 및 **[!UICONTROL Extract file]** 워크플로우 활동.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md)
* [데이터 추출(파일) 활동](../../workflow/using/extraction--file-.md)

## 델타 모드로 가져오기 {#importing-in-delta-mode}

일반 가져오기는 델타 모드에서 수행해야 합니다. 즉, 매번 전체 테이블 대신 Adobe Campaign으로 수정 또는 새 데이터만 전송됩니다.

전체 가져오기는 초기 로드에만 사용해야 합니다.

## 일관성 유지 {#maintaining-consistency}

Adobe Campaign 데이터베이스에서 데이터 일관성을 유지하려면 아래 원칙을 따르십시오.

* 가져온 데이터가 Adobe Campaign의 참조 테이블과 일치하는 경우 워크플로우의 해당 테이블과 조정되어야 합니다. 일치하지 않는 레코드는 거부해야 합니다.
* 가져온 데이터가 항상 **&quot;normalized&quot;** (이메일, 전화 번호, DM 주소) 및 이러한 표준화는 믿을 수 있으며 수년 동안 변경되지 않을 것입니다. 그렇지 않으면 데이터베이스에 일부 중복 항목이 표시될 수 있으며, Adobe Campaign에서 &quot;퍼지&quot; 일치를 수행하는 도구를 제공하지 않으므로 관리하고 제거하는 것은 매우 어려울 것입니다.
* 트랜잭션 데이터에는 조정 키가 있어야 하며, 중복을 생성하지 않도록 기존 데이터와 조정해야 합니다.
* **관련 파일 순서 가져오기**. 가져오기가 서로 다른 여러 파일로 구성된 경우 워크플로우는 파일을 올바른 순서로 가져왔는지 확인해야 합니다. 파일이 실패하면 다른 파일은 가져오지 않습니다.
* **중복 제거**&#x200B;데이터를 가져올 때 , 조정 및 일관성을 유지합니다.

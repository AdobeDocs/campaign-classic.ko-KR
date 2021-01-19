---
solution: Campaign Standard
product: campaign
title: 가져오기 및 내보내기 모범 사례
description: 데이터를 가져오거나 내보낼 때 따라야 할 최상의 방법에 대해 자세히 알아보십시오.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
translation-type: tm+mt
source-git-commit: a2a99135bdd74d87c04262b53e074b6aa05e7915
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# 가져오기 및 내보내기 우수 사례 {#import-export-best-practices}

아래 설명된 몇 가지 간단한 규칙을 주의하고 준수하면 데이터베이스 내에서 데이터 일관성을 유지하고 데이터베이스 업데이트나 데이터 내보내기 중에 발생하는 일반적인 오류를 방지하는 데 많은 도움이 됩니다.

## 워크플로 템플릿 사용 {#using-import-templates}

데이터를 가져오려는 대부분의 워크플로우는 다음 활동을 포함해야 합니다.**[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

워크플로우 템플릿을 사용하면 유사한 가져오기를 준비하고 데이터베이스 내에서 데이터를 일관되게 유지할 수 있습니다.

많은 프로젝트에서 가져오기는 프로젝트에 사용된 파일에 중복이 없으므로 **[!UICONTROL Deduplication]** 작업 없이 빌드됩니다. 다른 파일을 가져올 때 중복이 나타나는 경우가 있습니다. 데이터 중복 제거는 매우 어렵습니다. 따라서 모든 가져오기 워크플로우에서 데이터 중복 제거 단계를 수행하는 것이 매우 좋습니다.

수신 데이터가 일관되고 올바르거나 IT 부서 또는 Adobe Campaign 관리자가 처리하도록 하는 것을 고려해 두지 마십시오. 프로젝트 중에 데이터 정리를 염두에 두십시오. 데이터를 가져올 때 중복 제거, 조정 및 일관성을 유지할 수 있습니다.

데이터를 가져오기 위해 설계된 일반 워크플로우 템플릿의 예는 [예:데이터](../../platform/using/creating-import-export-templates.md) 섹션을 가져오는 워크플로 템플릿입니다.

## 플랫 파일 형식 사용 {#using-flat-file-formats}

가장 효율적인 가져오기 형식은 플랫 파일입니다. 데이터베이스 수준에서 플랫 파일을 벌크 모드로 가져올 수 있습니다.

예제:

* 구분 기호:탭 또는 세미콜론
* 머리글이 있는 첫 줄
* 문자열 구분 기호 없음
* 날짜 형식:YYYY/MM/DD HH:mm:SS

가져올 파일의 예:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 압축 사용 {#using-compression}

가능하면 파일을 압축 파일로 가져오고 내보냅니다. GZIP은 기본적으로 지원됩니다. 데이터를 추출할 때 각각 **[!UICONTROL Load file]** 및 **[!UICONTROL Extract file]** 워크플로우 활동에서 파일을 가져올 때 사전 처리를 추가할 수 있습니다.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md)
* [데이터 추출(파일) 작업](../../workflow/using/extraction--file-.md)

## 델타 모드 {#importing-in-delta-mode}에서 가져오기

일반 가져오기는 델타 모드에서 수행해야 합니다. 즉, 수정되거나 새 데이터만 항상 전체 테이블이 아니라 Adobe Campaign으로 전송됩니다.

전체 가져오기는 초기 로드에만 사용해야 합니다.

## 일관성 유지{#maintaining-consistency}

Adobe Campaign 데이터베이스에서 데이터 일관성을 유지하려면 아래 원칙을 따르십시오.

* 가져온 데이터가 Adobe Campaign의 참조 테이블과 일치하면 워크플로우의 해당 테이블과 대사되어야 합니다. 일치하지 않는 레코드는 거부해야 합니다.
* 가져온 데이터가 항상 **&quot;정규화된&quot;**(이메일, 전화 번호, DM 주소) 이고 이 표준화가 안정적이며 수년 동안 변경되지 않는지 확인합니다. 이 경우 데이터베이스에 일부 중복 항목이 표시될 가능성이 있으며 Adobe Campaign은 &quot;퍼지&quot; 일치를 수행하는 도구를 제공하지 않으므로 이러한 항목을 관리하고 제거하는 것은 매우 어렵습니다.
* 트랜잭션 데이터에는 조정 키가 있어야 하며, 중복을 만들지 않도록 기존 데이터와 대사해야 합니다.
* **관련 파일을 순서대로** 가져옵니다. 가져오기가 서로 의존하는 여러 파일로 구성된 경우 작업 과정에서는 파일을 올바른 순서로 가져왔는지 확인해야 합니다. 파일이 실패하면 다른 파일은 가져오지 않습니다.
* **데이터를 가져올** 때 중복 제거, 조정 및 일관성을 유지할 수 있습니다.

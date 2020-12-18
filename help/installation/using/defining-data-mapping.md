---
solution: Campaign Classic
product: campaign
title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 5%

---


# 데이터 매핑 정의 {#defining-data-mapping}

Adobe Campaign을 사용하면 외부 테이블의 데이터에 대한 매핑을 정의할 수 있습니다.

이렇게 하려면 외부 테이블의 스키마가 생성되면 이 테이블의 데이터를 배달 대상으로 사용하려면 새 배달 매핑을 만들어야 합니다.

이렇게 하려면 다음 단계를 적용합니다.

1. 새 배달 매핑을 만들고 타깃팅 차원(예: 방금 만든 스키마)을 선택합니다.

   ![](assets/wf_new_mapping_create_fda.png)

1. 배달 정보가 저장되는 필드(성, 이름, 이메일, 주소 등)를 지정합니다.

   ![](assets/wf_new_mapping_define_join.png)

1. 확장 스키마를 쉽게 식별할 수 있도록 확장 스키마의 접미어를 포함하여 정보 저장 매개변수를 지정합니다.

   ![](assets/wf_new_mapping_define_names.png)

   메시지(**브로드로그**)와 함께 제외(**excludelog**)를 저장할지 또는 별도의 테이블에 저장할지 선택할 수 있습니다.

   이 배달 매핑에 대한 추적 관리 여부를 선택할 수도 있습니다(**trackinglog**).

1. 그런 다음 고려될 확장을 선택합니다. 확장 유형은 플랫폼의 매개 변수 및 옵션에 따라 다릅니다(라이센스 계약 보기).

   ![](assets/wf_new_mapping_define_extensions.png)

   **[!UICONTROL Save]** 단추를 클릭하여 배달 매핑 만들기를 시작합니다.연결된 모든 테이블은 선택한 매개변수를 기준으로 자동으로 생성됩니다.

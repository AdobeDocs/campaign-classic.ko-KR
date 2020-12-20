---
solution: Campaign Classic
product: campaign
title: 스키마 다시 생성
description: 스키마 다시 생성
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# 스키마 다시 생성{#regenerating-schemas}

스키마를 수정하고 수정 내용을 저장하면 확장 스키마가 자동으로 생성됩니다. 그렇지만 수정 사항을 적용하려면 스키마를 수동으로 다시 생성해야 할 수도 있습니다. 방법은 다음과 같습니다.

1. 재생성할 스키마를 선택합니다.
1. 마우스 오른쪽 단추를 클릭하고 **[!UICONTROL Actions > Regenerate selected schemas...]** 을 선택합니다.
1. **[!UICONTROL OK]**&#x200B;을 클릭하여 프로세스를 확인하고 시작합니다.

그런 다음 미리 보기 및 문서 탭에서 생성된 스키마의 구조를 확인할 수 있습니다. 자세한 내용은 [원칙](../../configuration/using/data-schemas.md#principles) 섹션을 참조하십시오.

>[!NOTE]
>
>역 링크에서 특정 종속성 문제를 해결하기 위해 예를 들어 모든 스키마를 강제로 재생성해야 하는 경우 Adobe Campaign 응용 프로그램 서버에서 다음 명령을 실행할 수 있습니다.
>
>**nlserver config -postupgrade -instance:&#39;&lt;instance_name>&#39;-force**
>
>그런 다음 Adobe Campaign 응용 프로그램 서버를 다시 시작하고 클라이언트 콘솔에 연결 끊기/다시 연결해야 합니다.

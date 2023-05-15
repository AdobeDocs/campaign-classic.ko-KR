---
product: campaign
title: 스키마 다시 생성
description: Campaign 스키마를 재생성하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# 스키마 다시 생성{#regenerating-schemas}

스키마를 수정하고 수정 사항을 저장하면 확장 스키마가 자동으로 생성됩니다. 그러나 수정 사항을 적용하려면 스키마를 수동으로 재생성해야 할 수 있습니다. 방법은 다음과 같습니다.

1. 재생성해야 하는 스키마를 선택합니다.
1. 마우스 오른쪽 단추를 클릭하고 을 선택합니다. **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 클릭 **[!UICONTROL OK]** 프로세스를 확인하고 실행하려면

그런 다음 미리 보기 및 설명서 탭에서 생성된 스키마의 구조를 확인할 수 있습니다. 자세한 내용은 [원칙](../../configuration/using/data-schemas.md#principles) 섹션을 참조하십시오.

>[!NOTE]
>
>역방향 링크에서 특정 종속성 문제를 해결하기 위해 예를 들어 모든 스키마를 강제로 재생해야 하는 경우 Adobe Campaign 애플리케이션 서버에서 다음 명령을 시작할 수 있습니다.
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>그런 다음 Adobe Campaign 애플리케이션 서버를 다시 시작하고 클라이언트 콘솔에 연결 끊기/다시 연결해야 합니다.

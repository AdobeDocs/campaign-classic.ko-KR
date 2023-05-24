---
product: campaign
title: Adobe Target과의 통합 구성
description: Adobe Target과의 통합을 구성하는 방법에 대해 알아봅니다.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# Adobe Target과의 통합 구성{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> 호스팅 또는 하이브리드 고객은 Adobe 담당자에게 연락하여 이 통합을 구성하십시오. 아래 단계는 온-프레미스 고객에게만 적용됩니다.

이 통합에는 다음이 필요합니다.

* Adobe Experience Cloud 및 Adobe Target 조직
* Adobe Campaign과의 연결을 설정하기 위해 지정된 Adobe Target rawbox

Adobe Campaign에서 이 통합을 구성하려면 아래 단계를 따르십시오.

1. 설치 **[!UICONTROL Integration with the Adobe Experience Cloud]** 기본 제공 패키지. [자세히 알아보기](../../platform/using/working-with-data-packages.md#importing-packages)

   이 패키지를 사용하면 Digital Asset Manager를 통해 공유 에셋에 액세스할 수 있습니다.

1. IMS(Adobe ID 연결 서비스)를 통한 연결을 활성화하여 이메일에서 Adobe Experience Cloud을 통해 공유되는 이미지를 사용합니다. [자세히 알아보기](../../integrations/using/about-adobe-id.md)
1. 다음으로 이동 **[!UICONTROL Administration > Platform > Options]** Adobe Target에 대한 서버 및 조직(테넌트) 옵션을 구성하려면 다음을 수행하십시오.

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : 통합에 사용되는 Adobe Target 서버입니다. 이 옵션은 기본적으로 이미 선택되어 있습니다. 이 값은 Adobe Target에 해당합니다 **[!UICONTROL Domain Server]**, 뒤에 값 **/m2**. 예: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Adobe Target 조직 이름 이 값은 Adobe Target의 이름에 해당합니다. **[!UICONTROL Client]**.


>[!CAUTION]
>
>하이브리드 및 호스팅 아키텍처의 경우 이러한 옵션은 다음을 포함하여 모든 서버에서 설정해야 합니다. [중간 소싱 서버](../../installation/using/mid-sourcing-server.md) 및 [실행 인스턴스](../../message-center/using/configuring-instances.md#execution-instance).
---
product: campaign
title: 암호 분실
description: 암호 분실
feature: Monitoring, Access Management
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 3%

---

# 암호 분실{#lost-password}

>[!NOTE]
>
>이 페이지는 기본 인증을 사용하여 Campaign에 연결하는 운영자에만 적용됩니다.

분실된 암호를 변경하거나 복구할 수 있습니다.
다음과 같은 두 가지 가능한 시나리오가 있습니다.

* [Adobe Campaign 운영자가 암호를 분실했습니다.](#password-lost-by-campaign-operator)
* [내부 암호 분실](#internal-password-lost) (온-프레미스 고객만 해당)

## Campaign 운영자가 암호를 분실했습니다. {#password-lost-by-campaign-operator}

Adobe Campaign 연산자가 암호를 분실하면 변경할 수 있습니다.

>[!NOTE]
>
>이 절차는 기본 인증을 사용하여 Campaign에 연결하는 운영자에만 적용됩니다. Adobe IMS 인증의 경우 다음을 참조하십시오. [이 설명서](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Campaign 암호를 재설정하려면 아래 단계를 따르십시오.

1. 관리자 권한이 있는 연산자를 통해 연결합니다.
1. 연산자를 마우스 오른쪽 버튼으로 클릭합니다.
1. 선택 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. 연산자의 새 암호를 설정합니다. 운영자는 처음 다시 연결할 때 암호를 변경하는 것이 좋습니다.

## 내부 암호 분실 {#internal-password-lost}

>[!NOTE]
>
>이 섹션은 온-프레미스 고객에게만 적용됩니다.

내부 암호가 손실되면 다시 초기화해야 합니다.

이렇게 하려면 다음 절차를 적용합니다.

1. 편집 **/usr/local/neolane/nl6/conf/serverConf.xml** 파일.

1. 로 이동 **internalPassword** 줄.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 문자열을 따옴표로 묶어 삭제합니다(이 경우). `myPassword`. 다음 줄을 볼 수 있습니다.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. 변경 내용을 저장하고 파일을 닫습니다.

1. 중지 `nlserver` 프로세스.

1. 새 암호를 구성합니다. 이렇게 하려면 다음 명령을 입력합니다.

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 시작 `nlserver` 프로세스.

1. 이제 새 암호를 사용하여 연결할 수 있습니다. **내부** 모드.

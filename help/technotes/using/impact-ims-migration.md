---
title: IMS 마이그레이션 후 Campaign 인터페이스 업데이트
description: Adobe Identity Management 시스템 마이그레이션 인터페이스가 미치는 영향을 활성화하는 방법에 대해 알아봅니다
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# IMS 마이그레이션 후 Campaign 인터페이스 업데이트 {#impact-ims-migration}

다음 작업을 완료하면 [campaign 기술 운영자를 개발자 콘솔로 마이그레이션했습니다.](ims-migration.md) 및 [최종 사용자 인증을 위해 IMS로 전환됨](migrate-users-to-ims.md)마지막 단계는 사용자 인터페이스와 API 제한을 활성화하여 기본 인증과 관련된 옵션과 기능을 제거하는 것입니다. 이 업데이트는 Campaign v7.4.1부터 사용할 수 있습니다.

## IMS 제한 사용 {#ims-restrictions}

IMS(Adobe 식별 관리 시스템)로의 마이그레이션을 완료하려면 새로운 기본 사용자 생성, 기본 사용자 로그인 및 기본 연산자에 대한 API 액세스를 차단해야 합니다. 그런 다음 환경을 보호하고 표준화합니다.

관리 Cloud Service/호스팅 사용자는 제품 사용자 인터페이스에서 이 제한 사항과 관련 업데이트를 활성화하려면 Adobe에 문의하십시오.

온-프레미스/하이브리드 사용자는 다음 단계를 수행합니다.

1. 다음으로 이동 `<imsConfig>` 인스턴스 구성 파일의 섹션입니다.
1. UI 제한을 활성화하려면 다음을 업데이트하십시오. `nonIMSOperatorMgmtInClientConsoleRestricted` 옵션, 내부 `nonIMSOperatorMgmtInClientConsole` 요소, 대상 `true`, 아래와 같이:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. API 제한을 활성화하려면 `disableAPI` 옵션, 내부 `nonIMSAuthnAPI` 요소, 대상 `true`, 아래와 같이:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

일부 연산자는 기본 인증을 사용하여 Adobe Campaign에 연결할 수 있습니다. 이러한 기술 운영자는 기본적으로 활성화되어 있으므로 수정해서는 안 됩니다. 이 예외를 허용하려면 기본적으로 이러한 기술 연산자가 허용 목록에 추가됩니다. 다음 목록에서 이 목록을 찾을 수 있습니다. `<imsConfig>` 인스턴스 구성 파일의 섹션 `allowOperator` 내 옵션 `nonIMSAuthnAPI` 요소를 생성하지 않습니다.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

연산자를 허용 목록에 추가해야 하는 경우 새 연산자를 추가합니다 `allowOperator` 연산자 이름을 사용하는 요소입니다. 예를 들어, 이름이 인 새 연산자를 추가하려면 `test`, 다음과 같이 이 섹션을 업데이트합니다.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## 사용자 인터페이스의 영향 {#ims-impacts}

마이그레이션이 완료되고 아래에 설명된 대로 제한이 적용되면 제품 및 해당 사용자 인터페이스에 다음 변경 사항이 적용됩니다.

### 운영자 관리 {#manage-admin}

더 이상 클라이언트 콘솔에서 기본 인증을 사용하여 연산자를 생성, 편집, 업데이트 또는 삭제할 수 없습니다.

따라서 이러한 작업은 클라이언트 콘솔에서 비활성화되었습니다.

운영자의 관리는 Adobe Admin Console에서 중앙 집중화되며, 이제 다음 작업이 이 콘솔을 통해 독점적으로 관리됩니다. 에서 사용자를 만들고 권한을 할당하는 방법에 대해 알아봅니다. [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### 사용할 수 없는 옵션 {#unavailable-migration}

마이그레이션 후에는 클라이언트 콘솔에서 다음 작업을 더 이상 사용할 수 없습니다.

* 사용 [선택한 라인 병합 옵션](../../platform/using/updating-data.md#merge-data) 연산자 병합.

* 연산자에 대해 다음 필드를 업데이트합니다.
   * 이름
   * 암호
   * 레이블
   * 이메일

* [Campaign 암호 재설정](../../production/using/lost-password.md)

* 연산자의 XML 소스 편집

* 연산자가 중복되었습니다.


>[!MORELIKETHIS]
>
>* [최종 사용자를 IMS로 마이그레이션](migrate-users-to-ims.md)
>* [기술 운영자를 Adobe Developer 콘솔로 마이그레이션](ims-migration.md)
>* [Adobe Campaign Classic v7 최신 릴리스 노트](../../rn/using/latest-release.md)
>* [IMS(Identity Management System) Adobe](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"}


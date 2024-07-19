---
product: campaign
title: oracle 액세스 구성
description: FDA에서 Oracle 액세스를 구성하는 방법 알아보기
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# oracle 액세스 구성 {#configure-access-to-oracle}



외부 데이터베이스에 저장된 정보를 처리하려면 Campaign [FDA(Federated Data Access](../../installation/using/about-fda.md)) 옵션을 사용하십시오. oracle 액세스를 구성하려면 아래 단계를 따르십시오.

1. [Linux](#oracle-linux) 또는 [Windows](#azure-windows)에서 Oracle 구성
1. Campaign에서 Oracle [외부 계정](#oracle-external) 구성

## Linux의 oracle {#oracle-linux}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래 추가 구성이 필요합니다.

1. 사용 중인 Oracle 버전에 해당하는 Oracle 전체 클라이언트를 설치합니다.
1. 설치에 TNS 정의를 추가합니다. 이렇게 하려면 /etc/oracle 저장소의 **tnsnames.ora** 파일에 지정합니다. 이 저장소가 없으면 만듭니다.

   oracle 그런 다음 새 TNS_ADMIN 환경 변수(TNS_ADMIN=/etc/export)를 생성하고 컴퓨터를 다시 시작합니다.

1. Adobe Campaign 서버(nlserver)에 Oracle을 통합합니다. 이렇게 하려면 **customer.sh** 파일이 Adobe Campaign 서버 트리 구조의 &quot;nl6&quot; 폴더에 있고 Oracle 라이브러리에 대한 링크가 포함되어 있는지 확인하십시오.

   예를 들어 11.2에 있는 클라이언트의 경우:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >이러한 값(특히 ORACLE_HOME)은 설치 저장소에 따라 다릅니다. 이러한 값을 참조하기 전에 트리 구조를 확인하십시오.

1. oracle에 필요한 라이브러리를 설치합니다.

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#oracle-external)을 참조하세요.

## Windows의 oracle {#oracle-windows}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에서 아래 추가 구성이 필요합니다.

1. oracle 클라이언트를 설치합니다.

1. C:Oracle 폴더에서 TNS 정의가 포함된 **tnsnames.ora** 파일을 만듭니다.

1. C:ADMIN 값이 있는 TNS_ADMIN 환경 Oracle을 추가하고 시스템을 다시 시작합니다.

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#oracle-external)을 참조하세요.

## 외부 계정 oracle {#oracle-external}

[!DNL Oracle] 외부 계정을 사용하면 Campaign 인스턴스를 Oracle 외부 데이터베이스에 연결할 수 있습니다.

1. **[!UICONTROL Explorer]** 캠페인에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL New]**&#x200B;을(를) 선택하십시오.

1. **[!UICONTROL External database]**&#x200B;을(를) 외부 계정의 **[!UICONTROL Type]**(으)로 선택합니다.

1. **[!UICONTROL Oracle]** 외부 계정을 구성하십시오. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: DNS 이름

   * **[!UICONTROL Account]**: 사용자 이름

   * **[!UICONTROL Password]**: 사용자 계정 암호

   * **[!UICONTROL Time zone]**: 서버 시간대

   ![](assets/oracle_config.png)

---
product: campaign
title: 중간 소싱 인프라에 대한 인바운드 SMS 워크플로우 활동
description: 중간 소싱 인프라에 대한 인바운드 SMS 워크플로우 활동
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# 중간 소싱 인프라에 대한 인바운드 SMS 워크플로우 활동 {#inbound-sms}

## 제한 사항 {#limitations}

* 이 사용 사례는 중간 소싱 인스턴스에서 inSMS 데이터를 수집하는 마케팅 인스턴스에만 적용됩니다.
* 중간 소싱 인스턴스에서 이 사용 사례를 구현하지 마십시오.
* 외부 중간 소싱 계정당 사용자 지정 워크플로우가 한 개만 있습니다.

## 구현 {#implementation}

1. 에 확장 추가 `nms:inSMS` 마케팅 인스턴스의 스키마. 확장 프로그램은 새 속성을 `nms:inSMS` 중간 소싱 인스턴스에서 발생하는 inSMS 레코드 기본 키를 스키마와 추적합니다.

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. 스키마에 대한 수정 사항을 적용하려면 데이터베이스 업데이트 마법사를 시작합니다. 이 마법사는 다음을 통해 액세스할 수 있습니다. **도구** > **고급** > **데이터베이스 구조 업데이트**. 데이터베이스의 물리적 구조가 논리적 설명과 일치하는지 확인하고 SQL 업데이트 스크립트를 실행합니다. [자세히 알아보기](../../configuration/using/updating-the-database-structure.md)

1. 다음 내용이 포함된 워크플로우 중지 및 백업 **인바운드 SMS 활동**.

   다음 형식으로 해당 옵션 포인터 백업 `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`.

[백업에 대한 자세한 내용](../../production/using/backup.md)

1. (**선택 사항**) 이미 스케줄러 활동을 사용 중인 경우 워크플로우를 열고 다음과 같이 다시 구성합니다.

   1. 에서 현재 설정 복제 **예약** 의 탭 **인바운드 SMS** 외부로의 활동 **스케줄러** 활동.

   1. 에서 현재 설정 비활성화 **예약** 탭 / **인바운드 SMS** 활동.

      ![](assets/inbound_sms_1.png)

1. 업데이트 **인바운드 SMS** 사용자 지정 스크립트.

   아래 블록을 바꿉니다. 이 스크립트는 이전에 이 코드를 사용자 지정한 경우에 달라질 수 있습니다.

   ```Javascript
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   중간 소싱 레코드의 기본 키와 마케팅 SMS 라우팅의 외부 계정 ID를 결합하여 복합 키를 기반으로 inSMS 데이터를 업데이트하는 다음의 새로운 사용자 지정 스크립트를 사용합니다.

   아래의 사전 요구 사항을 따르십시오.

   * 에 대한 실제 값 입력 `<EXTERNAL_ACCOUNT_ID>`, 예, `var iExtAccountId=72733155`.
   * 사용자 지정 스크립트에 다음 요소를 유지해야 합니다.
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. 인바운드 SMS 고급 초기화 스크립트를 다음 스크립트로 업데이트합니다.

   스크립트는 기본 키 포인터를 24시간 전으로 재설정합니다. 워크플로우는 이전 24시간 내에 중간 소싱 인스턴스의 모든 inSMS 데이터를 재처리하고 누락된 데이터를 마케팅 인스턴스에 추가합니다.

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * 여러 SMS 라우팅 계정이 동일한 중간 소싱 인스턴스에 연결된 경우 중간 소싱 인스턴스당 단일 워크플로우만 허용됩니다.
   > * 외부 계정 ID를 사용할 수 있습니다. 외래 키의 역할은 중간 소싱 SMS ID가 다른 중간 소싱 인스턴스에서 동일할 수 있는 서로 다른 중간 소싱 서버와 관련된 시나리오에서 데이터 조정 무결성을 유지하는 것입니다.
   > * 중간 소싱 인스턴스당 여러 개의 inSMS 워크플로우가 있는 경우 중간 소싱 SMS ID가 일정하게 유지되고 외부 계정 ID가 다르므로 데이터가 중복될 수 있습니다.

1. 워크플로우를 저장하고 다시 시작합니다.

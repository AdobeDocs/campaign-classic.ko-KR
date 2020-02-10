---
title: Linux에서 스택 추적
seo-title: Linux에서 스택 추적
description: Linux에서 스택 추적
seo-description: null
page-status-flag: never-activated
uuid: d839df47-902f-4b92-bc78-536fc4fb6c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 60f306ea-4593-4e56-896e-8933277ee26a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Linux에서 스택 추적{#stack-trace-in-linux}

스택 추적은 **** 코어 **** 유형 파일에 포함된 추적을 나타냅니다. 이 파일은 시스템 오류가 발생하는 경우 생성됩니다. 오류의 원인을 식별할 수 있습니다.

>[!NOTE]
>
>* 핵심 **파일의 이름은** core. **`<num>`**.
>* **gdb - GNU** 디버거가 컴퓨터에 설치되어 있어야 합니다.
>



Adobe Campaign 기술 지원을 통해 이 **스택 추적을**&#x200B;요청할 수 있습니다. Linux에서 다음 명령을 입력합니다.

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Adobe Campaign 기술 지원에서는 특정 실행 파일을 사용하여 이 명령을 실행하라는 요청을 할 수 있습니다(Adobe에서 제공 예정).

이 경우 nlserver를 Adobe Campaign에서 **제공하는 실행 파일로** 바꾸어 다음 명령을 실행하기만 하면 됩니다.

```
gdb nlserver <coreFile>
```

예:

```
gdb nlserver.1823 <coreFile>
```


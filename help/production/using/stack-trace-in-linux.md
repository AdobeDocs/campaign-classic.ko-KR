---
solution: Campaign Classic
product: campaign
title: Linux의 스택 추적
description: Linux의 스택 추적
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---


# Linux의 스택 추적{#stack-trace-in-linux}

**스택 추적**&#x200B;은 **core** 유형 파일에 포함된 추적을 나타냅니다. 이 파일은 컴퓨터 오류가 발생한 경우 생성됩니다. 오류의 원인을 식별할 수 있습니다.

>[!NOTE]
>
>* **core** 파일의 이름은 **core.`<num>`**&#x200B;입니다.
>* **gdb - 컴퓨터에** GNU 디버거가 설치되어 있어야 합니다.

>



Adobe Campaign 기술 지원팀에서는 이 **스택 추적**&#x200B;을(를) 요청할 수 있습니다. Linux에서 다음 명령을 입력합니다.

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

Adobe Campaign 기술 지원팀에서는 특정 실행 파일을 사용하여 이 명령을 실행할 것을 요청할 수 있습니다(Adobe에서 제공).

이 경우 **nlserver**&#x200B;를 Adobe Campaign에서 제공하는 실행 파일로 대체하여 다음 명령을 실행하기만 하면 됩니다.

```
gdb nlserver <coreFile>
```

예제:

```
gdb nlserver.1823 <coreFile>
```


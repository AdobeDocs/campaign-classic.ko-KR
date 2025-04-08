---
product: campaign
title: 새로운 GCM 기반 함수
description: 새로운 GCM 기반 함수
feature: Technote
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 1%

---

# GCM 기반 함수 {#new-functions}

보안을 개선하기 위해 암호화 작업에 CBC(Cipher Block Chaining) 모드를 사용하는 AES(Advanced Encryption Standard) 알고리즘의 사용을 중단했습니다. 새로운 암호화 기능이 도입되었습니다. 이러한 기능은 AES를 Galois/Counter Mode(AES-GCM)와 함께 사용하여 보다 안전한 대안을 제공합니다. 이러한 기능은 JavaScript, JSP, SOAP API 및 XML 스키마에서 사용할 수 있으므로 고객은 암호화 및 암호 해독을 위해 CBC에서 GCM으로 전환할 수 있습니다.

이 설명서에는 새로 도입된 AES-GCM 함수와 더 이상 사용되지 않는 CBC 기반 함수가 나열되어 있습니다.

새로운 기능:

* [EncryptString API 함수](#encryptString-api-xtk)
* [EncryptStringWithServerPassword API 함수](#EncryptStringWithServerPassword-api-xtk)
* [encryptString javascript 함수](#encryptString-javascript)

GCM에 사용할 수 있는 레거시 함수:

* [DecryptString javascript 함수](#decryptString-javascript)
* [DecryptPassword Javascript 함수](#decryptPassword-javascript)

[사용되지 않는 함수](#depracated-functions)

## API 함수

### EncryptString {#encryptString-api-xtk}

GCM 모드의 AES 알고리즘을 사용하여 인스턴스 키로 문자열을 암호화합니다.

```
            String 
            encrypted = Encrypt (
            String       
            decrypted
            

      )
         
```

**매개 변수**: 해독된 텍스트

**반환 값**: 암호화됨

**스키마**: xtk:session

**정적**: 예

## EncryptStringWith서버 암호 {#EncryptStringWithServerPassword-api-xtk}

GCM 모드의 AES 알고리즘을 사용하여 서버 키로 문자열을 암호화합니다.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**매개 변수**: 암호 해독됨

**반환 값**: 암호화됨

**스키마**: xtk:session

**정적**: 예

## Javascript 함수

### encryptString() {#encryptString-javascript}

인스턴스 키 또는 다른 키로 문자 문자열을 암호화합니다.

```
            cryptString (str [, key
      ] [, useSalt ])
         
```

**매개 변수**:

* str: 암호화할 문자열입니다.
* 키: AES 암호화 키는 기본 64에 인코딩됩니다. 키 길이가 32인 경우 256비트, 키 길이가 24인 경우 192비트, 키 길이가 16이거나 키가 지정되지 않은 경우 128비트입니다.
* useSalt: 데이터의 솔트를 사용하여 암호화합니다. 기본적으로 True입니다.

**반환 값**: 암호화된 문자열을 반환합니다.

**설명**

암호화는 다음 방법에 따라 수행됩니다.

* 유니코드 문자 문자열이 UTF-8 문자열로 변환됩니다.
* 확인 문자는 암호 텍스트의 끝에 추가됩니다.
* 이 문자열은 12바이트 초기화 벡터와 16바이트 태그가 있는 솔트를 사용하는 GCM(Galois/Counter Mode) 모드의 AES 알고리즘을 사용하여 암호화됩니다. 매개 변수로 제공된 키가 없는 경우 인스턴스 키가 사용됩니다.
* 암호 텍스트에는 태그와 초기화 벡터가 포함됩니다.
* 그 다음 암호화된 블록은 베이스(64)로 변환된다.

decryptString 함수를 사용하여 암호 해독을 수행합니다.

**기능**

사용 가능한 위치:

* 콘텐츠 관리
* 게재 속성
* 게재 메시지
* 유형화 규칙
* 가져오기
* JSSP
* SOAP 메서드
* 웹 앱
* 워크플로

### decryptString() {#decryptString-javascript}

인스턴스 키 또는 다른 키로 문자 문자열을 암호화합니다. 이 레거시 기능은 GCM과 함께 사용할 수 있습니다. AES-CBC 모드를 사용하여 암호화된 암호 텍스트의 암호 해독은 더 이상 사용되지 않습니다.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**매개 변수**:

* str: 해독할 문자열입니다.
* 키: AES 암호화 키는 기본 64에 인코딩됩니다. 키 길이가 32인 경우 256비트, 키 길이가 24인 경우 192비트, 키 길이가 16이거나 키가 지정되지 않은 경우 128비트입니다.
* useSalt: 데이터의 솔트를 사용하여 해독합니다. 기본적으로 True입니다.

**반환 값**: 복호화된 문자열을 반환합니다.

**경고**: 이 메서드를 사용하면 데이터베이스에 저장된 암호(옵션/외부 계정)의 암호를 더 이상 해독할 수 없습니다. 이를 위해 [decryptPassword](#decryptPassword-javascript)를 사용하십시오.

### decryptPassword() {#decryptPassword-javascript}

외부 계정에 저장된 암호를 해독합니다. 이 레거시 기능은 GCM과 함께 사용할 수 있습니다. AES-CBC 모드를 사용하여 암호화된 암호 텍스트의 암호 해독은 더 이상 사용되지 않습니다.

```
            decryptPassword (str)
         
```

**매개 변수**:

* str: 해독할 문자열입니다.

**반환 값**: 일반 텍스트 암호를 반환합니다.

**설명**

이 함수는 워크플로우, 웹 애플리케이션, 보고서 또는 게재에서 호출할 수 없습니다. JSSP 또는 SOAP 호출 구현에서 호출할 수 있습니다. 예:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## 사용되지 않는 함수 {#depracated-functions}

다음 함수는 완전히 더 이상 사용되지 않습니다.

* cryptString
* 암호화
* EncryptServerPassword

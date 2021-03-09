---
solution: Campaign Classic
product: campaign
title: 네트워크, 데이터베이스 및 SSL/TLS
description: 네트워크, 데이터베이스 및 SSL/TLS 구성 우수 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 2%

---


# 네트워크, 데이터베이스 및 SSL/TLS {#network-database}

## 네트워크 구성

온-프레미스 유형의 아키텍처를 배포할 때 확인해야 할 중요한 것은 [네트워킹 구성](../../installation/using/network-configuration.md)입니다. Tomcat 서버가 서버 외부에서 직접 액세스할 수 없는지 확인합니다.

* 외부 IP에서 Tomcat 포트(8080)를 닫습니다(localhost에서 작동해야 함).
* 표준 HTTP 포트(80)를 Tomcat one(8080)에 매핑하지 마십시오.

가능한 경우 보안 채널을 사용하십시오.POP3S 대신 POP3(또는 TLS를 통한 POP3).

## 데이터베이스

데이터베이스 엔진 보안을 반드시 준수해야 합니다.

### SSL/TLS 구성*

인증서를 확인하려면 Openssl을 사용할 수 있습니다. 활성 암호를 확인하려면 nmap을 사용할 수 있습니다.

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

두 작업을 모두 수행하는 [sslyze](https://github.com/nabla-c0d3/sslyze/releases) python 스크립트를 사용할 수도 있습니다.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```

---
solution: Campaign Classic
product: campaign
title: 릴리스 18.6
description: 릴리스 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 6%

---


# 릴리스 18.6{#release-18-6}

## 릴리스 18.6.2 - 빌드 8949{#release-18-6-3-build-8949}

2018년 8월 22일

>[!CAUTION]
>
>이 건물은 회수되었습니다. [최신 빌드](../../production/using/build-upgrade.md)로 업그레이드하거나 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 쿼리 밴딩<br /> </td> 
   <td> <p>여러 Campaign 사용자가 동일한 FDA Teradata 외부 계정에 연결하면 이제 각 사용자별 쿼리 밴드(키/값 쌍)를 전달할 수 있습니다. Campaign 사용자가 Teradata 데이터베이스에 대해 쿼리를 수행할 때마다 Adobe Campaign은 이제 사용자와 연관된 메타 데이터를 보낼 수 있습니다. 키 및 값 목록으로 구성된 이러한 데이터는 감사 목적으로 Teradata 관리자가 사용하거나 액세스 권한을 관리할 수 있습니다(예:</p><p>자세한 내용은 <a href="../../installation/using/external-accounts.md">세부 설명서</a>를 참조하십시오.</p> </td>
  </tr> 
 </tbody> 
</table>

**개선 사항**

* 이메일 보관 로그가 향상되어, BCC 보관을 통해 성공적으로 배달되었거나 실패한 이메일을 보다 쉽고 명확하게 확인할 수 있습니다. (NEO-10675)
* 추적 브로드로그에서 고객 IP 대신 부하 균형 조정기 IP가 표시되는 문제를 해결했습니다. (NEO-11295)
* 게재 속성이 잘못 덮어쓰여지는 무작위 문제가 수정되었습니다. (NEO-11015)
* 강화 활동 결과를 정렬할 때 구문 오류를 수정했습니다. (NEO-11394)
* **[!UICONTROL Survey answers]** 워크플로우 활동에서 계산된 필드를 사용할 때 발생하는 문제를 수정했습니다. (NEO-11382)
* Tomcat이 취약성 착취를 방지하기 위해 업데이트되었습니다. (NEO-11503)
* PostgreSQL 데이터베이스에 대한 FDA 연결을 사용할 때 LATIN1 인코딩의 오류가 수정되었습니다. (NEO-11299)
* **[!UICONTROL Prepare the personalization data with a workflow]** 배달 옵션을 사용할 때 발생하는 문제를 수정했습니다. (NEO-11047)
* 확장 커넥터를 사용할 때 SMS를 보내지 못하는 업그레이드 후 문제를 해결했습니다.
* 패키지 가져오기/내보내기 기능이 개선되었습니다(인터페이스에 로그 및 영역이 추가되었습니다).
* **[!UICONTROL Survey answers]** 워크플로우 활동이 완전히 구성되지 않은 경우 업그레이드 후 로그에 불필요한 오류가 표시되던 문제를 수정했습니다.

**기술 진화**

쿼리 밴딩

특정 키(PROXYUSER 또는 PROXYROLE)는 Teradata 사용자 또는 역할을 캠페인 사용자에게 연결하는 데 사용됩니다. 이 프록시 사용자/역할을 사용하도록 새 권한이 추가되었습니다. 데이터베이스 계정(Teradata 외부 계정에 정의된 계정)에 GRANT CONNECT THROUGH 액세스 권한을 추가해야 합니다.

teradata 외부 계정에 새 탭이 추가되었습니다. **[!UICONTROL Query banding]** 탭에는 다음 옵션이 포함되어 있습니다.

* **[!UICONTROL Active]**:이 확인란을 선택하여 기능을 활성화합니다.
* **[!UICONTROL Default]**:사용자에게 연관된 쿼리 배너가 없는 경우 사용할 기본 쿼리 배너를 입력합니다. 정의된 기본 쿼리 배너가 없는 경우 연관된 쿼리 배너를 사용하지 않는 사용자는 Teradata을 사용할 수 없습니다.
* **[!UICONTROL Users]**:각 사용자에 대해 쿼리 밴딩을 지정합니다. 필요한 만큼 키/값 쌍을 추가할 수 있습니다. 예:&#39;priority=1;workload=high;&#39;

쿼리 밴딩에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [https://docs.teradata.com/reader/cY5~EUFWjgN2kBn3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 릴리스 18.6 - 빌드 8947{#release-18-6-build-8947}

2018년 6월 25일

>[!CAUTION]
>
>이 건물은 회수되었습니다. [최신 빌드](../../production/using/build-upgrade.md)로 업그레이드하거나 [기술 지원](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 보안 개선 사항<br /> </td> 
   <td> Campaign Classic에 일련의 보안 개선 사항이 추가되었습니다. 개선 사항 및 수정 사항은 아래에 나열되어 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> Windows Server 2016 지원<br /> </td> 
   <td> Adobe Campaign은 이제 Windows Server 2016과 호환됩니다. <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic 호환성 매트릭스</a>를 참조하십시오.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

decryptString

**decryptString** 함수는 사용되지 않습니다. [사용되지 않음 및 제거된 기능](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html) 아티클을 참조하십시오.

새 고객의 경우 이 함수는 이제 랜딩 페이지에서 받는 사람의 암호화된 ID를 해독하는 데만 사용됩니다. 외부 계정에 저장된 암호를 해독하려면 새 **decryptPassword** 함수를 사용합니다.

기존 고객의 경우 이 함수의 비헤이비어는 변경되지 않았지만 **decryptString** 대신 **decryptPassword**&#x200B;를 사용하는 것이 좋습니다. **XtkSecurity_Unsafe_DecryptString** 호환성 옵션은 기본적으로 사후 업그레이드에 추가되고 활성화되므로 계속 함수를 사용할 수 있습니다. **decryptString**&#x200B;을 비활성화하려면 옵션을 비활성화하십시오.

decryptPassword

**decryptPassword** 함수가 추가되었습니다. 외부 계정에 저장된 암호를 해독할 수 있습니다. 자세한 내용은 [JSAPI](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html) 설명서를 참조하십시오.

파일 API

새 설치의 경우 파일 API를 통한 폴더 액세스는 Adobe Campaign의 **var**, **sftp** 및 임시 폴더로 제한됩니다.

기존 고객의 경우 파일 API는 Adobe Campaign의 **conf** 폴더에 더 이상 액세스할 수 없습니다. **XtkSecurity_Disable_JSFileSandboxing** 호환성 옵션은 기본적으로 사후 업그레이드에 추가되어 활성화되므로 다른 폴더에 계속 액세스할 수 있습니다. Adobe Campaign의 **var**, **sftp** 및 임시 폴더에 대한 액세스를 제한하려면 옵션을 비활성화합니다.

**패치**

* SMS 트랜잭션 메시지 성능에 영향을 줄 수 있는 문제를 수정했습니다. (NEO-9812)

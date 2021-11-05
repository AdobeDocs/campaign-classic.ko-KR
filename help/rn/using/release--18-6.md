---
product: campaign
title: Campaign 18.6 릴리스 노트
description: Campaign 18.6 릴리스 노트
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: c281d437907efb4d514bec7cacc698c383f3fe53
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---

# 릴리스 18.6{#release-18-6}

![](../../assets/v7-only.svg)

## 릴리스 18.6.2 - 빌드 8949{#release-18-6-3-build-8949}

2018년 8월 22일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> <p>여러 Campaign 사용자가 동일한 FDA Teradata 외부 계정에 연결하면 이제 각 사용자별 쿼리 대역(키/값 쌍)을 전달할 수 있습니다. Campaign 사용자가 Teradata 데이터베이스에서 쿼리를 수행할 때마다 Adobe Campaign은 이제 사용자에게 연결된 메타 데이터를 전송할 수 있습니다. 키 및 값 목록으로 구성된 이러한 데이터는 Teradata 관리자가 감사 목적으로 사용하거나 액세스 권한을 관리하는 등의 목적으로 사용할 수 있습니다.</p><p>자세한 내용은 <a href="../../installation/using/external-accounts.md">세부 설명서</a>를 참조하세요.</p> </td>
  </tr> 
 </tbody> 
</table>

**개선 사항**

* 전자 메일 보관 로그가 개선되어 BCC 보관을 통해 성공적으로 배달되었거나 실패한 전자 메일을 보다 쉽고 정확하게 확인할 수 있습니다. (NEO-10675)
* 추적 브로드로그에서 고객 IP 대신 로드 밸런서 IP가 표시되는 문제를 해결했습니다. (NEO-11295)
* 게재 속성을 잘못 덮어쓰는 무작위 문제가 수정되었습니다. (NEO-11015)
* 데이터 보강 활동 결과를 정렬할 때 구문 오류를 수정했습니다. (NEO-11394)
* 에서 계산된 필드를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Survey answers]** 워크플로우 활동. (NEO-11382)
* Tomcat이 취약점 착취를 방지하기 위해 업데이트되었습니다. (NEO-11503)
* PostgreSQL 데이터베이스에 FDA 연결을 사용할 때 LATIN1 인코딩 오류가 수정되었습니다. (NEO-11299)
* 를 사용할 때 발생하는 문제를 수정했습니다 **[!UICONTROL Prepare the personalization data with a workflow]** 배달 옵션. (NEO-11047)
* 확장 커넥터를 사용할 때 SMS 전송을 방해하는 업그레이드 후 문제를 해결했습니다.
* 패키지 가져오기/내보내기 개선(인터페이스에 로그 및 영역이 추가됨).
* 업그레이드 후 로그에 **[!UICONTROL Survey answers]** 워크플로우 활동이 완전히 구성되지 않았습니다.

**기술 진화**

쿼리 밴딩

특정 키(PROXYUSER 또는 PROXYROLE)는 Teradata 사용자 또는 역할을 Campaign 사용자에게 연결하는 데 사용됩니다. 이 프록시 사용자/역할을 사용하기 위해 새 권한이 추가되었습니다. 데이터베이스 계정(Teradata 외부 계정에 정의된 계정)에 GRANT CONNECT THROUGH 액세스 권한을 추가해야 합니다.

teradata 외부 계정에 새 탭이 추가되었습니다. 다음 **[!UICONTROL Query banding]** 탭에는 다음 옵션이 포함되어 있습니다.

* **[!UICONTROL Active]**: 이 확인란을 선택하여 기능을 활성화합니다.
* **[!UICONTROL Default]**: 사용자에게 연관된 쿼리 밴딩이 없는 경우 사용할 기본 쿼리 밴딩을 입력합니다. 정의된 기본 쿼리 밴딩이 없는 경우 연결된 쿼리 밴딩이 없는 사용자는 Teradata을 사용할 수 없습니다.
* **[!UICONTROL Users]**: 각 사용자에 대해 쿼리 밴딩을 지정합니다. 필요한 만큼 키/값 쌍을 추가할 수 있습니다. 예: &#39;priority=1;workload=high;&#39;

쿼리 밴딩에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 릴리스 18.6 - 빌드 8947{#release-18-6-build-8947}

2018년 6월 25일

>[!CAUTION]
>
>이 빌드는 리콜되었습니다. 제발 [최신 빌드로 업그레이드](../../production/using/build-upgrade.md) 또는 연락처 [기술 지원](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> 일련의 보안 개선 사항이 Campaign Classic에 추가되었습니다. 개선 사항 및 수정 사항이 아래에 나열되어 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> Windows Server 2016 지원<br /> </td> 
   <td> Adobe Campaign은 이제 Windows Server 2016과 호환됩니다. 을(를) 참조하십시오. <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic 호환성 매트릭스</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

decryptString

다음 **decryptString** 함수는 더 이상 사용되지 않습니다. 자세한 내용은 [사용이 중단되거나 제거된 기능](deprecated-features.md) 문서.

새 고객의 경우 이제 이 함수는 랜딩 페이지에서 수신자의 암호화된 ID를 해독하는 데만 사용됩니다. 외부 계정에 저장된 암호를 해독하려면 새 **decryptPassword** 함수 위에 있어야 합니다.

기존 고객의 경우 이 기능의 동작은 변경되지 않지만, **decryptPassword** 대신 **decryptString**. 다음 **XtkSecurity_Unsafe_DecryptString** 호환성 옵션이 업그레이드 후 추가되고 기본적으로 활성화되므로 함수를 계속 사용할 수 있습니다. 비활성화하려면 **decryptString**&#x200B;을 비활성화하십시오.

decryptPassword

다음 **decryptPassword** 함수가 추가되었습니다. 외부 계정에 저장된 암호를 해독할 수 있습니다. 자세한 내용은 [JSAPI](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html) 설명서 를 참조하십시오.

파일 API

새로 설치하는 경우 파일 API를 통한 폴더 액세스는 다음으로 제한됩니다 **var**, **sftp** 및 Adobe Campaign의 임시 폴더.

기존 고객의 경우 파일 API가 더 이상 **conf** Adobe Campaign 폴더. 다음 **XtkSecurity_Disable_JSFileSandboxing** 호환성 옵션이 업그레이드 후 추가되고 기본적으로 활성화되므로 다른 폴더에 계속 액세스할 수 있습니다. 액세스 권한을 **var**, **sftp** Adobe Campaign의 임시 폴더에서 옵션을 비활성화합니다.

**Patch**

* SMS 트랜잭션 메시지 성능에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-9812)

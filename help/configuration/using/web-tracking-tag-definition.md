---
product: campaign
title: 웹 추적 태그 정의
description: 웹 추적 태그 정의
feature: Application Settings
role: Data Engineer, Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# 웹 추적 태그: 정의{#web-tracking-tag-definition}



웹 추적 태그는 적절한 매개 변수로 구성된 URL일 뿐이며, HTTP 쿼리를 통해 리디렉션 서버로 전송됩니다.

## 보낼 데이터 형식 {#format-of-the-data-to-be-sent}

웹 추적 URL의 형식은 다음과 같습니다. **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>URL에 추가된 난수는 브라우저가 웹 페이지를 캐싱하여 발생하는 문제를 방지합니다.

다음 표는 리디렉션 서버에서 지원하는 특수 매개 변수 목록을 제공합니다.

<table>
                     <thead>
                        <tr>
                           <th>이름</th>
                           <th>유형</th>
                           <th>설명</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>세션 쿠키</p> 
                           </td>
                           <td>
                              <p>게재 식별자 및 수신자 식별자.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>영구 쿠키</p> 
                           </td>
                           <td>
                              <p>수신자 식별자(세션 쿠키가 없는 경우 유용함).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>태그</p> 
                           </td>
                           <td>
                              <p>URL 매개변수</p> 
                           </td>
                           <td>
                              <p>추적된 웹 페이지의 식별자: 유일한 필수 매개 변수입니다.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>작업 ID</p> 
                           </td>
                           <td>
                              <p>URL 매개변수</p> 
                           </td>
                           <td>
                              <p>세션 쿠키가 없는 경우 사용할 게재 식별자. 이 값은 다음과 같습니다.
                                 16진수로 표시됩니다.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL 매개변수</p> 
                           </td>
                           <td>
                              <p>인터넷 사용자를 식별하는 데 사용되는 매개 변수입니다. 이 매개 변수의 형식은 "name=value"입니다.
                                 여기서 name은 수신자 스키마의 필드입니다. 이 매개 변수는 보다 우선합니다.
                                 세션 쿠키에 포함된 식별자.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**몇 가지 웹 추적 URL**

* &#39;홈&#39; 식별자 페이지 방문

  **https://myserver.adobe.com/r/9862?tagid=home**

* 비즈니스 볼륨 데이터 수집

  **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 수신자를 찾기 위한 필드 지정

  **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

  계정 번호가 10인 수신자는 홈 페이지로 전송됩니다.

* 기본 게재 사용

  **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

  수신자가 홈 페이지로 전송됩니다. 이 쿼리와 함께 게재 식별자가 포함된 세션 쿠키가 전송되지 않는 한 이 정보는 식별자 230(데이터베이스 16의 e6)이 있는 게재에 저장됩니다.

>[!NOTE]
>
>URL 매개 변수를 통해 리디렉션 서버로 전송되는 모든 값은 URL로 인코딩되어야 합니다. 제공된 예제에서 문자 &#39;=&#39;와 &#39;|&#39;은 각각 &#39;%3D&#39;와 &#39;%7C&#39;(으)로 인코딩됩니다.

## 데이터 전송 방법 {#data-transmission-methods}

다음과 같은 방법을 사용할 수 있습니다.

* 추적하려는 웹 페이지에 통합된 HTML **`<img>`** 태그의 **&quot;src&quot;** 특성에 URL을 삽입합니다.
* 추적할 웹 페이지가 생성되면 리디렉션 서버에 직접 호출합니다.

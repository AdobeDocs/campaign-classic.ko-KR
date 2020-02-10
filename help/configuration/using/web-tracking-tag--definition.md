---
title: '"웹 추적 태그:definition"'
seo-title: '"웹 추적 태그:definition"'
description: '"웹 추적 태그:definition"'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# 웹 추적 태그:정의{#web-tracking-tag-definition}

웹 추적 태그는 HTTP 쿼리를 통해 리디렉션 서버로 전송되는 적절한 매개 변수로 구성된 URL입니다.

## 전송할 데이터의 형식 {#format-of-the-data-to-be-sent}

웹 추적 URL의 형식은 다음과 같습니다. **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>URL에 추가된 무작위 번호는 브라우저가 웹 페이지를 캐싱할 때 발생하는 문제를 방지합니다.

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
                              <p>배달 식별자 및 받는 사람 식별자입니다.</p> 
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
                              <p>수신자 식별자(세션 쿠키가 없는 경우 유용합니다.)</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL 매개 변수</p> 
                           </td>
                           <td>
                              <p>추적된 웹 페이지의 식별자:필수 매개 변수만 있습니다.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>조입찰</p> 
                           </td>
                           <td>
                              <p>URL 매개 변수</p> 
                           </td>
                           <td>
                              <p>세션 쿠키가 없는 경우 사용할 배달 식별자입니다. 이 값은 16진수로 표현됩니다.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL 매개 변수</p> 
                           </td>
                           <td>
                              <p>인터넷 사용자를 식별하는 데 사용되는 매개 변수입니다. 이 매개 변수의 형식은 "name=value"이며 여기서 이름은 수신자 스키마의 필드입니다. 이 매개 변수는 세션 쿠키에 포함된 식별자보다 우선합니다.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**몇 개의 웹 추적 URL**

* &#39;홈&#39; 식별자 페이지 방문

   **https://myserver.adobe.com/r/9862?tagid=home**

* 비즈니스 볼륨 데이터 수집

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 수신자를 찾을 필드 지정

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   계정 번호가 10인 수신자가 홈 페이지로 전송됩니다.

* 기본 배달 사용

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   수신자가 홈 페이지로 전송됩니다. 배달 식별자가 들어 있는 세션 쿠키가 이 쿼리와 함께 전송되지 않는 한 이 정보는 식별자 230(데이터베이스 16의 e6)으로 배달에 저장됩니다.

>[!NOTE]
>
>URL 매개 변수를 통해 리디렉션 서버로 전송된 모든 값은 URL로 인코딩되어야 합니다. 제공된 예에서 &#39;=&#39; 및 &#39;|&#39; 문자는 각각 &#39;%3D&#39; 및 &#39;%7C&#39;로 인코딩됩니다.

## 데이터 전송 방법 {#data-transmission-methods}

다음 방법을 사용할 수 있습니다.

* 추적하려는 웹 페이지에 **포함된 HTML 태그의 &quot;src&quot;** 속성에 URL을 **`<img>`** 삽입합니다.
* 추적할 웹 페이지가 생성되면 리디렉션 서버에 직접 호출합니다.


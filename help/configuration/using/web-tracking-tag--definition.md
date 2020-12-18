---
solution: Campaign Classic
product: campaign
title: '"웹 추적 태그: 정의"'
description: '"웹 추적 태그: 정의"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 4%

---


# 웹 추적 태그: 정의{#web-tracking-tag-definition}

웹 추적 태그는 간단히 적절한 매개 변수로 구성된 URL로서 HTTP 쿼리를 통해 리디렉션 서버로 전송됩니다.

## 보낼 데이터의 형식 {#format-of-the-data-to-be-sent}

웹 추적 URL의 형식은 다음과 같습니다.**https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>URL에 추가된 무작위 번호는 브라우저에서 웹 페이지를 캐시하여 발생하는 문제를 방지합니다.

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
                              <p>배달 식별자 및 수신자 식별자.</p> 
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
                              <p>받는 사람 식별자(세션 쿠키가 없는 경우 유용합니다).</p> 
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
                              <p>조비드</p> 
                           </td>
                           <td>
                              <p>URL 매개 변수</p> 
                           </td>
                           <td>
                              <p>세션 쿠키가 없는 경우 사용할 배달 식별자입니다. 이 값은
                                 16진수로 표현되었습니다.
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
                              <p>인터넷 사용자를 식별하는 데 사용되는 매개 변수입니다. 이 매개 변수의 형식은 "name=value"입니다.
                                 여기서 이름은 수신자 스키마의 필드입니다. 이 매개 변수는 우선 순위를 차지합니다.
                                 세션 쿠키에 포함된 식별자.
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
>URL 매개 변수를 통해 리디렉션 서버로 전송된 모든 값은 URL로 인코딩되어야 합니다. 지정된 예에서 &#39;=&#39; 및 &#39;|&#39; 문자는 각각 &#39;%3D&#39; 및 &#39;%7C&#39;로 인코딩됩니다.

## 데이터 전송 메서드 {#data-transmission-methods}

다음 메서드를 사용할 수 있습니다.

* 추적할 웹 페이지에 포함된 HTML **`<img>`** 태그의 **&quot;src&quot;** 속성에 URL을 삽입합니다.
* 추적할 웹 페이지가 생성되면 리디렉션 서버에 직접 호출합니다.


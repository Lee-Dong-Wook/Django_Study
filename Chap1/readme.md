### 웹 프로그래밍의 이해 

웹 프로그램 
    - 클라이언트-서버 
      - 통신 규약 HTTP 프로토콜로 통신 

ex) 웹 브라우저 : 웹 클라이언트 
    네이버 서버 : 웹 서버 
    http/https프로토콜로 요청 
   
<br>
<hr>

## 웹 브라우저 이외 웹 서버 요청 방법 

- 웹 브라우저 사용하여 요청
- 리눅스 curl 명령을 사용해 요청
- Telnet 사용해 요청 
- 직접만든 클라이언트로 요청 
    
## Example

# 웹브라우저 사용해서 요청 
![example1](https://user-images.githubusercontent.com/46260504/65831715-04b13580-e2f8-11e9-997c-0f85a54f1419.PNG)

# 리눅스 curl 명령을 사용해서 요청 
![example2](https://user-images.githubusercontent.com/46260504/65831803-58bc1a00-e2f8-11e9-9db0-f16763775955.PNG)
![example3](https://user-images.githubusercontent.com/46260504/65831804-58bc1a00-e2f8-11e9-9d5e-cf3edce4070a.PNG)

# 직접만든 클라이언트로 요청 
![example4](https://user-images.githubusercontent.com/46260504/65831820-62de1880-e2f8-11e9-8bc3-0c5bad863428.PNG)

<hr>

## HTTP 프로토콜
http는 웹 서버와 웹 클라이언트 사이에서 데이터를 주고받기 위해 사용하는 통신방식
    - 웹을 이용하려면 IP 주소를 가져야한다. 
    
# HTTP 메세지 구조 
서버로 보내는 요청 메세지와 서버에서 클라이언트로 보내는 응답 메세지 

스타트라인(start line) ========== 요청라인(요청) or 상태라인(응답)<br>
헤더(Header)===================== 헤더는 생략가능 <br>
빈줄 ============================ 헤더의 끝을 빈 줄로 식별<br>
바디(body) ====================== 생략 가능 <br>

ex) 바디가 없는 요청 메세지 예시<br> 
    GET /book/shakespeare HTTP/1.1<br>
    Host : www.example.com:8080
    
첫 번째 줄은 요청라인, 요청 방식, 요청 URL, 프로토콜 버전으로 구성<br> 
두 번째 줄은 헤더, 이름:값 형식으로 표현 <br>
Host 항목은 필수로 표시해야함. <br>

GET http://www.example.com:8080/book/shakespeare HTTP/1.1 <br>
요청라인의 URL에 Host를 표시하면 Host 헤더 생략 가능 <br>

ex) 응답 메세지 예시 
HTTP/1.1 200 ok    -> 상태라인<br>
Content-Type: application/xhtml+xml; charset=utf-8 -> 헤더<br><br>

```html
<html>      -> 바디 
   
</html>
```
<br>
첫 번째 줄의 상태라인은 프로토콜 버전, 상태코드, 상태 텍스트로 구성<br>
위 예시에서는 200 ok 이므로 정상적으로 처리 
<hr>
## 웹 어플리케이션 서버 

## 웹 서버와 웹 어플리케이션 서버 구분
<br>

| 구분 | 역할 | 프로그램 명 | 
|:------:|:-------|:-------|
|   웹 서버    |  웹 클라이언트의 요청을 받아서 요청을 처리하고, 그 결과를 웹 클라이언트에게 응답한다. 주로 정적 페이지인 HTML, 이미지, CSS, 자바스크립트 파일을 웹 클라이언트에 제공할 때 웹 서버를 사용한다. 만약 동적 페이지 처리가 필요하다면 웹 애플리케이션 서버에 처리를 넘긴다. | Apache httpd, Nginx, lighttpd, LLS 등    |
| 웹 애플리케이션 서버|웹 서버로부터 동적  페이지 요청을 받아서 요청을 처리하고, 그 결과를 웹 서버러 반환한다. 주로 동적페이지 생성을 위한 프로그램 실행과 데이터베이스 연동 기능을  처리한다.|Apache Tomcat, JBoss, WebLogic 등|
<br>

# 정적 페이지 vs 동적 페이지
정적 페이지 : 누가, 언제 요구하더라도 항상 같은 내용 표시하는 웹페이지<br>
주로 html, javascript,css, 이미지로만 이루어진 페이지 <br><br>

동적 페이지 : 동일한 리소스의 요청이라도 누가, 언제 어떻게 요구했는지에 따라 각각 다른 내용이 반환되는 페이지<br>

# CGI 방식 
정식 프로그래밍 언어나 스크립트가 아닌, 웹 서버와 독립적인 프로그램 사이에 정보를 주고받는 규격을 의미<br>
전통적인 CGI 방식은 웹 서버가 C, C++, Perl,PHP, Python 등으로 만들어진 CGI 프로그램을 직접 호출하여 개별 프로세스를 생성하는 방식<br>

CGI 방식의 단점은 각각의 클라이언트 요청에 대해 독립적인  별도의 프로세스가 생성<br>
현재는 별도어플리케이션(CGI 프로그램 역할)을 Perl, PHP 등의 스크립트 언어로 작성, 스크립트를  처리하는 스크립트 엔진(인터프리터)을 웹 서버에 내장시켜 CGI 방식의 단점이었던 별도의 프로세스를 기동시키는 오버헤드를 줄이는 방식<br>
현재 가장 많이 사용되고 있는 JSP, ASP 기술에서 애플리케이션 서버 방식 사용 

# 어플리케이션 서버 방식
웹 서버가 직접 프로그램을 호출하지않고 웹 어플리케이션 서버를 통해 간접적으로 웹 어플리케이션 프로그램을 실행<br><br>

웹클라이언트 -> 요청 -> 웹 서버 -> 처리 위임 -> 웹 어플리케이션 서버 -> 어플리케이션  <br>
웹클라이언트 <- 응답 <- 웹 서버 <- 결과 반환 <- 웹 어플리케이션 서버 <- 어플리케이션  <br><br>

웹 서버와 웹 어플리케이션 서버가 분리됨에 따라 서로의 역할도 구분하는 것이 좋음<br>
정적 페이지 처리에 특화된 웹 서버는 정적 페이지만 처리, 웹 어플리케이션 서버는 동적페이지만 처리<br>



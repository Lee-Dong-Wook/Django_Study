### 웹 프로그래밍의 이해 

웹 프로그램 
    - 클라이언트-서버 
      - 통신 규약 HTTP 프로토콜로 통신 

ex) 웹 브라우저 : 웹 클라이언트 
    네이버 서버 : 웹 서버 
    http/https프로토콜로 요청 
   
<br>   
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


## HTTP 프로토콜
http는 웹 서버와 웹 클라이언트 사이에서 데이터를 주고받기 위해 사용하는 통신방식
    - 웹을 이용하려면 IP 주소를 가져야한다. 
    
# HTTP 메세지 구조 
서버로 보내는 요청 메세지와 서버에서 클라이언트로 보내는 응답 메세지 

스타트라인(start line) ========== 요청라인(요청) or 상태라인(응답)
헤더(Header)===================== 헤더는 생략가능 
빈줄 ============================ 헤더의 끝을 빈 줄로 식별
바디(body) ====================== 생략 가능 

ex) 바디가 없는 요청 메세지 예시 
    GET /book/shakespeare HTTP/1.1
    Host : www.example.com:8080
    
첫 번째 줄은 요청라인, 요청 방식, 요청 URL, 프로토콜 버전으로 구성 
두 번째 줄은 헤더, 이름:값 형식으로 표현 
Host 항목은 필수로 표시해야함. 

GET http://www.example.com:8080/book/shakespeare HTTP/1.1
요청라인의 URL에 Host를 표시하면 Host 헤더 생략 가능 

ex) 응답 메세지 예시 






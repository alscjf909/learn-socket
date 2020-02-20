# learn-socket   
## introduce   
소켓이란 인터페이스는 UNIX(더 엄밀하게 말하자면 BSD)에서 등장했으며, OSI상에서 위치를 그려보자면 트랜스포트와 애플리케이션 사이에 존재합니다. UNIX에서 등장했단 말에서 알 수 있듯이, OS에서 제공하는 인터페이스며, 어떤 종류의 프로그램이라 하더라도 이 소켓에 접근하여 외부 네트워크와 통신을 할 수 있습니다. 지금은 당연히 윈도우 시리즈에도 있으며, 자바를 쓰든, 파이썬을 쓰든, C++를 쓰든간에 소켓의 사용방법은 크게 다르지 않습니다. 마치 어떤 언어로 프로그램을 만들어도 파일을 읽거나 쓰는 파일시스템(fs)에 관련된 모듈 사용방법이 크게 다르지 않듯이요.

### 소켓 기본 프로그래밍
1.1. 소켓 생성
````
from socket import *   

serverSock = socket(AF_INET, SOCK_STREAM)
````
소켓 생성을 하는 함수       소켓의 AF(IP)와 포트번호를 할당      

1.2. bind 함수호출   
````
serverSock.bind(('',8080))
````
bind 함수 내에 **튜플**을 입력    
그 이유로 ('',8080)자체가 AF가 되는 것이다.
즉 ('',8080)은 (ip,port이고)이 자체가 한쌍의 AF(어드레스 패밀리)가 된다.      

1.3. lisetn 함수호출
````
 serverSock.listen(1)
````
listen()안에 숫자 1이 입력되어 있는데, 이는 해당 소켓이 총몇개의 동시접속까지를 허용할 것이냐는 이야기이다.   
만약 인자를 입력하지 않으면 파이썬이 자의적으로 판단해서 임의의 숫자로 listen한다고 한다.      
   
1.4 accept 함수호출   
````
connectionSock, addr = serverSock.accept()
````
accept()는 소켓에 누군가가 접속하여 연결되었을 때에 비로소 결과값이 return되는 함수이다.   
즉 소스코드 내에 serverSock.accept()가 있더라도, 누군가가 접속할 때까지 프로그램은 바로 이 부분에서 계속 멈춰있게 된다.   
connectionSock이라는 소켓은 accept()를 통해 상대방과 데이터를 주고받기 위해서이다.
## 2. TCP/IP 채팅
## 2.1   
[가장 간단한 챗봇](https://seolin.tistory.com/97)   
## 2.2   
[무전기](https://seolin.tistory.com/98?category=762768)

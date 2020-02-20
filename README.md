# learn-socket
## TCP-IP 프로그래밍
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


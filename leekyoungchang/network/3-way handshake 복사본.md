# 📚 1. 정리
**✔️ 3-way handshake가 무엇이지?**
3-way handshake는 TCP/IP 프로토콜로 통신하기 전, 정확한 정보 전송을 위해 상대방 컴퓨터와 세션을 수립하는(연결을 하는) 과정**(TCP 연결 초기화)**

  클라이언트가 서버에게 접속을 요청하는 ``**SYN**`` 패킷을 보내면, 서버는 요청을 수락하는 `ACK`를 포함하여 `**SYN+ACK** 패킷`을 클라이언트에게 발송합니다. 클라이언트가 이것을 수신한 후, 다시 `**ACK**`를 서버에게 발송하면 연결이 이루어지고, 이로써 데이터를 주고받을 수 있게 된다.

&nbsp;


**✔️ TCP 3 way handshake 3단계 과정**
> TCP 통신은 아래와 같은 3단계의 과정을 거친다.

(1) `Connection setup` (tcp 연결 초기화) - 3 way handshaking
(2) `Data transfer` (데이터 전송)
(3) `Connection termination` (tcp 연결 종료) - 4way handshaking

=> `3-way handshaking`이 `Connection setup`의 과정이다.

![[스크린샷 2022-09-03 오후 10.09.06.png]]


&nbsp;

&nbsp;

# 📚 2. 면접에서 나올만한 질문


-   **Q. 3-way handshake는 무엇이고 각 과정은 어떻게 되나요?**
    
    3-way handshake는 TCP/IP 프로토콜로 통신하기 전, 정확한 정보 전송을 위해 상대방 컴퓨터와 세션을 수립하는(연결을 하는) 과정입니다. **(TCP 연결 초기화)**
    
    클라이언트가 서버에게 접속을 요청하는 **SYN** 패킷을 보내면, 서버는 요청을 수락하는 ACK를 포함하여 **SYN+ACK** 패킷을 클라이언트에게 발송합니다. 클라이언트가 이것을 수신한 후, 다시 **ACK**를 서버에게 발송하면 연결이 이루어지고, 이로써 데이터를 주고받을 수 있게됩니다.


&nbsp;


-   **Q. 그럼 4-way handshake는 뭔가요?**
    
    3-way handshake를 통해 ****Connection setup을 했다면 **tcp 연결을 종료**하는 **Connection termination** 과정은 **4-way handshaking**을 통해 이루어집니다.
    
    TCP connection termination은 양방향으로 2개의 연결이 독립적으로 닫히기 때문에 4-way 단계를 밟게 됩니다.




&nbsp;

&nbsp;

# 📚 3. 면접 팁에서 팁은?
면접에서는 **3-way handshake를 하는 목적은 무엇인지, 각 step의 절차는 어떻게 되는지를 중점적으로** 보면 된다.

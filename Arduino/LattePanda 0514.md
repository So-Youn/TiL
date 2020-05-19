

ConnectedCar - 연결 지향성

Android, Web으로 요청 

web - was 동작

android - tcp 서버 제작 - 장치 제어 (Serial 통신)

기술 센서 이용한 데이터 Oracle에 저장할 수 없음

node.js - javascript 기반 비동기 방식





자동 import

![image-20200514105231917](images/image-20200514105231917.png)





# [MQTT](http://mosquitto.org/download/)

>  **MQTT**(Message Queuing Telemetry Transport) : 발행-구독 기반의 메시징 프로토콜이다.

* TCP/IP 프로토콜 위에서 동작한다.
  * IOT와 모바일 어플리케이션 등의 통신에 매우 적합한 프로토콜
* `Broker`, `Publisher`, `Subscriber` 구조

![image-20200519111052134](images/image-20200519111052134.png)

* subscribe (sub) 
* publish(pub) 

* IoT장비 연결 시 사용하는 MQTT

![image-20200519100952501](images/image-20200519100952501.png)

* MQTT 서버

![image-20200519103218235](images/image-20200519103218235.png)

*실행이 되고 있는지 확인해준다.*

![image-20200519103324735](images/image-20200519103324735.png)

sub 1

![image-20200519103635724](images/image-20200519103635724.png)

sub 2

![image-20200519103837615](images/image-20200519103837615.png)



* 서버
  * sub 수신

![image-20200519103742070](images/image-20200519103742070.png)

![image-20200519103853080](images/image-20200519103853080.png)

* pub 

![image-20200519104018458](images/image-20200519104018458.png)

* 메시지 전달

![image-20200519104207147](images/image-20200519104207147.png)

* json 을 이용한 값 전달

![image-20200519104451555](images/image-20200519104451555.png)

* -h : 호스트 주소

![image-20200519105321589](images/image-20200519105321589.png)
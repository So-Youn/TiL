client는 socket객체를 만들어 통신을 한다

화면을 띄워주는 작업 외에 다른 작업을 하기 위해 Thread 작업



client가 대기하면 seversocket이 accept 해서 

Thread : 독립적인 실행 흐름 -> 접속한 사용자에 한해서 Thread 처리를 해주어야 한다.

Thread 

* 클라이언트의 접속 (연결)
* 데이터 보내기 / 받기



| Server (서비스 제공)               | Client |
| ---------------------------------- | ------ |
| 클라이언트 처리 (채팅)             |        |
| 클라이언트 접속 / 출력             |        |
| 데이터가 전송되는 것이 있는지 대기 |        |

1. 서버 실행

   chatServerView (ChatServerViewListener)

   ----------------------- 서버가 여러가지 상태를 확인할 수 있는 화면

2. 클라이언트 접속\

   1. ChatLogin (ChatLoginListener)을 먼저 실행해서 로그인(ip,port,채팅 nickname)

   2. ClientChatView가 실행 (ClientChatListener)

       ---------------------  클라이언트가 채팅하는 화면



# Swing (gui Program)

### :panda_face: java fx (css, javascript)

* 이클립스 플러그인 **window builder** 툴 설치하고 드래그앤 드랍으로 화면 디자인


# multi chat

## 5/7

spring network multichat step01



swing

- java fx(css, javascript)



이클립스 플러그인 window builder 툴을 설치파고 드래그앤 드랍으로 화면 디자인

1. 서버 실행

   - ChatServerView (ChatServerListener)

     ㅡㅡㅡㅡㅡㅡㅡㅡ

     서버가 여러 가지 상태를 확인할 수 있는 화면

2. 클라이언트 접속

   1) ChatLogin(ChatLoginListener)을 먼저 실행해서 로그인(ip, port, 채팅 nickname)

   2) ClientChatView가 실행(ClientChatListener)

   ​    ㅡㅡㅡㅡㅡㅡㅡ 

   ​	클라이언트가 채팅하는 화면





서버준비 및 문제점을 파악

실행하면 프로그램이 멈춘 것 처럼 보인다.
버튼이나 GUI가 이벤트처리를 하지 못한다.
accept때문에 계속 대기 상태
=> 클라이언트의 요청을 받는 부분은 쓰레드 처리를 해야 한다.



클라이언트의 접속 처리하기

1. 서버접속
2. 클라이언트 접속
   => 클라이언트 한 개만 접속가능
   => 클라이언트가 접속하면 서버 창에 클라이언트의 IP를 출력




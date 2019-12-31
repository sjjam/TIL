# web

## tomcat

apache.org > download> tomcat9> 32bit/64bit windows service installer


exe파일실행 
choose components에서 모두다 체크

configuration
HTTP/1.1 connector port = 8088
user name = admin / password  = admin




주소창에
http://127.0.0.1:8088 창 안뜸
시작메뉴 apachetomcat > monitortomcat > 작업표시줄에서 start service
해준뒤 다시 검색

http://127.0.0.1:8088/webapplication폴더명/webapplication파일
<docs webapplication폴더 안의 index.html의 실행결과를 확인>
http://127.0.0.1:8088/docs/index.html

c드라이브에 mypro폴더 생성 후 indew.jsp 복사해서 넣으면
http://127.0.0.1:8088/mypro/index.jsp > 웹페이지 찾을 수 없음, tomcat이 인식할 수 없는 경로이기 때문



웹 요청 방식
http://127.0.0.1:8088/context명/폴더명..../요청할web application

ㅡㅡ    ㅡㅡㅡㅡ  ㅡㅡ  ㅡㅡㅡㅡ

프로     웹서버     port    기본context는 생략(root)
토콜       ip           (web의
                              기본port 80-생략가능)

http://127.0.0.1:8088/docs/index.html

http://127.0.0.1:8088/manager/index.jsp
http://127.0.0.1:8088/examples/servlets/index.html

아이디/비밀번호 확인

C:\Program Files\Apache Software Foundation\Tomcat 9.0\conf\tomcat-users.xml





c드라이브에 mypro폴더 생성 후 indew.jsp 복사해서 넣으면
http://127.0.0.1:8088/mypro/index.jsp > 웹페이지 찾을 수 없음, tomcat이 인식할 수 없는 경로이기 때문

C:\Program Files\Apache Software Foundation\Tomcat 9.0\conf\server.xml 에서

<Context docBase="c:\mypro" path="/mypro" reloadable="true" debug="0"/>

추가해준뒤 서버 stop후 다시 서버 열면 http://127.0.0.1:8088/mypro/index.jsp 열리게 됨

logs 서버를 실행하면서 하는 모든 작업이 기록되어 저장됨

work 변환된 파일이 저장되는 위치

lib library



정적파일 지정경로에 저장된 파일이 있는 것



## 이클립스

이클립스는 통합개발환경



C:\IOT\work\webwork\.metadata

.metadata 설정파일이 저장되는 곳

이클립스상에 서버가 인식하는 위치

C:\IOT\work\webwork\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps



external로 변경

![qweqw](C:\Users\student\Desktop\qweqw.PNG)



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="EUC-KR">
		<title>기본 html연습</title>
	</head>
	<body>
		<!-- html주석 (클라이언트에 전송되는 주석 : 주의)sss -->   소스보기에 주석이 뜸
		안녕하세요&lt;<br/>   줄바꿈           &lt; <표시
		김서연입니다.
        
        <b><i>안녕하세요</i></b>&nbsp;&nbsp;입니다.  굵은글씨,기울임 &nbsp;띄어쓰기2번쓰면2번
		<hr/>                         수평선
		<hr/>
		<pre>                         pre는 작성한 그대로 보여줌
			안녕하세요
			김입니다.
			지금은                               html연습중
		</pre>
        
		<p>지금은 html의 기본을 연습하는 시간입니다.</p>   줄바꿈
		<h1>HTML연습중....</h1>
		<h2>HTML연습중....</h2>
		<h3>HTML연습중....</h3>
		<h4>HTML연습중....</h4>
		<h5>HTML연습중....</h5>
		<h6>HTML연습중....</h6>
		<h7>HTML연습중....</h7>   6까지 지원 글씨 크기
		<font>HTML연습중....</font>   본문의 글자를 나타낼때 사용
        <font size="1" color="red" face="굴림">HTML연습중....</font>
		<font size="2" color="green" face="HY견고딕">HTML연습중....</font>
		<font size="3" color="blue" face="궁서">HTML연습중....</font>
		<font size="4" color="skyblue" face="굴림">HTML연습중....</font>
		<font size="5" color="yellow" face="굴림">HTML연습중....</font>
		<font size="6" color="#990085" face="굴림">HTML연습중....</font>
        <h3>상대경로로 이미지 삽입하기</h3>
		<img src="jang1.jpg"/>       현재 작업중인 경로에서 jang1.jpg를 찾으므로 안나옴
        <img src="../images/jang1.jpg"/>   경로를 주어 이미지파일을 찾으므로 나옴
        									. 현재경로 ..현재경로에서 상위
        <img src="../images/jang1.jpg" width="200" height="300" border="1" alt="멋진"/>
		<br/>
		<br/>
		<br/>
		<h3>절대경로로 이미지 삽입하기</h3>
		<img src="http://127.0.0.1:8088/clientwhb/images/jang1,jpg" width="200" height="300" >
		<img src="/clientwhb/images/jang1,jpg" width="200" height="300" >
                  /로 해주면 루트부터 찾음
	</body>
</html>
```



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	<h1>순서가 있는 목록</h1>
	<ol>
		<li>자바</li>
		<li>JDBC</li>
		<li>오라클</li>
		<li>html5</li>
		<li>CSS</li>
		<li>javascript</li>
		<li>jQuery</li>
	</ol>
	<h1>순서가 없는 목록</h1>
	<ul>
		<li>servlet&jsp</li>
		<li>spring</li>
		<li>hadoop</li>
		<li>hive</li>
	</ul>
	<br/><br/>
	<h1>정의리스트</h1>
	<dl>
		<dt>클라이언트웹</dt>
		<dd>클라이언트에 보여지는 페이지를 만드는 기술을 살펴본다.</dd>
		<dt>서버웹</dt>
		<dd>DB연동이나 파일작업을 할 수 있는 웹의 기술</dd>
	</dl>
</body>
</html>
```


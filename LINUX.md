# LINUX

## 2/11

root => 프롬프트 #

일반계정 => 프롬프트 $

home(홈디렉토리) : 

- 특정 계정으로 로그인 했을때 자동으로 위치하는 폴더

- 모든 계정은 홈디렉토리를 갖고 있다.

- 기본설정은 홈디렉토리명이 계정명과 동일

- root의 홈디렉토리명 root폴더

cd ~ : 홈으로 이동

cd / : 시작점으로(root) 이동 > 최상위

etc => 설정정보가 담긴 폴더(중요)

usr => window로 치면 programfiles랑 비슷

dev => 리눅스에서 사용되는 장치들이 위치하는 폴더



## 2/12 <<빅데이터 플랫폼구축>>

1. vmware 설치
2. 머신생성 - centos7
3. 머신복제

 - ip확인

4. 머신4대를 클러스터링

 - 방화벽해제
 - hostname변경
 - DNS설정
   * hosts파일 등록
   * 네트워크 프로세스를 restart
   * 설정확인 - 설정을 성공완료했는지 확인
   * 네 대에 모두 적용이되도록 hadoop01머신에서 hadoop02,hadoop03,hadoop04에 직접 접속

---

hadoop01
192.168.111.131

hadoop02
192.168.111.129

hadoop03
192.168.111.128

hadoop04
192.168.111.130

----

ifconfig => ip확인

ssh ip주소 => ssh통신이용해서 접속

host 이름 변경 => hostnamectl set-hostname hadoop01

서비스 관리 => systemctl 명령어 이용해서 처리

systemctl list-units --type=service => 서비스 목록 확인

systemctl status firewalld => 방화벽 상태 확인

systemctl stop firewalld => 방화벽 서비스 스탑 >>>reboot시 다시 동작됨

systemctl disable firewalld => 작동 중지 >>>reboot해도 정지되어있음

ssh-keygen -t rsa => key 생성

ssh-copy-id -i id_rsa.pub hadoop@hadoop03 => 공개키 복사

su hadoop => root에서 hadoop으로 이동

---

내 파일 > etc에서 > hosts파일에 들어가서 hadoop과 아이피 작성 후 저장

/etc/init.d/network restart 후에 ssh hadoop02 해주면 ip가 아니라 이름으로 접속 가능

[원격 서버로 copy]

scp copy할파일(위치까지 명시) copy받을서버의 위치

scp            /etc/hosts        root@hadoop02:/etc/hosts

ㅡㅡㅡ      ㅡㅡㅡㅡㅡ       ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

명령어      copy할파일        target서버의 위치와 파일명

[원격 서버에 실행명령]

ssh 서버 "실행할명령문"

​       ㅡㅡ

​    ip, 도메인



- 암호화된 통신을 위해서 공개키생성 후 배포



## 2/13

5. 프로그램 설치

- hadoop
- jdk
- 설정



---

rpm -Uvh jdk-8u231-linux-x64.rpm : 설치한 파일 실행

rpm : setup 명령어(설치)

옵션 : U (업그레이드) v뷰 (화면에서 과정을 보겠다) h (설치과정을 #표시로 보겠다)



scp /root/jdk-8u231-linux-x64.rpm root@hadoop02:/root/ : 원격으로 hadoop02에 jdk 복사

ssh hadoop02 "rpm -Uvh jdk-8u231-linux-x64.rpm" : 원격으로 hadoop02에서 jdk 설치

apache.org에서 hadoop-1.2.1.tar.gz을 root에 다운로드 권한이 root

scp hadoop-1.2.1.tar.gz hadoop@hadoop01:/home/hadoop/ : hadoop에 home/hadoop에 파일 복사 속성확인하면 권한이 hadoop으로 되어있음

tar -zxvf hadoop-1.2.1.tar.gz : 압축 풀기



1. home/hadoop/hadoop-1.2.1/conf에서 hadoop-env.sh에서 

   export JAVA_HOME=/usr/java/jdk1.8.0_231-amd64 설정해주기

2. home/hadoop/hadoop-1.2.1/conf에서 masters에서 localhost를 hadoop02로 변경(secondaryname노드)
3. home/hadoop/hadoop-1.2.1/conf에서 slaves에서 localhost를 hadoop02, hadoop03, hadoop04로 변경

4. core-site.xml을 gedit로 열기

   property 추가

![캡처](images/캡처-1581569059691.PNG)

5. home/hadoop/hadoop-1.2.1/conf에서 hdfs-site.xml을 gedit로 열기 (hdfs 분산모드)

   property 추가

   ![image-20200213142057178](images/image-20200213142057178.png)

6. home/hadoop/hadoop-1.2.1/conf에서 mapred-site.xml gedit으로 열기

   property 추가

   ![image-20200213142456678](images/image-20200213142456678.png)

7. scp /home/hadoop/hadoop-1.2.1/conf/* hadoop@hadoop02:/home/hadoop/hadoop-1.2.1/conf/ 명령어로 복사해준 뒤 

   /home/hadoop/hadoop-1.2.1/bin/hadoop namenode -format로 namenode를 초기화 해준다

8. /home/hadoop/hadoop-1.2.1/bin/start-all.sh 하둡 실행명령어

9. jps : 역할이 무엇인지 출력하는 명령어



hadoop이 start되면 logs폴더 생김 => 기록 내용이 등록됨



## 2/14

/home/hadoop/hadoop-1.2.1/bin/hadoop fs -ls /input : 확인

/home/hadoop/hadoop-1.2.1/bin/hadoop fs -rmr /input : 제거

/home/hadoop/hadoop-1.2.1/bin/hadoop fs -mkdir /input : 생성

/home/hadoop/hadoop-1.2.1/bin/hadoop fs -copyFromLocal README.txt /input : 카피

jar 실행 명령어 jar파일

jar파일 안에 있는 wordcount class 파일 실행                                            /output 결과 저장

/bin/hadoop jar hadoop-examples-1.2.1.jar wordcount /input/README.txt /output

---

실습

haddop-examples-1.2.1.jar의 wordcount를 이용해서 작업하기

- HDFS에 myinput폴더를 작성한다.
- LICENSE.txt를 복사한다.
- wordcount를 적용
- 출력결과는 myoutput으로 작성

![image-20200214114033084](images/image-20200214114033084.png)



## 2/17

ip 바꼈을 때

- /etc/hosts 파일 변경

- scp 모든 copy

- 네트워크 프로세스 restart(모든 머신에 작업)



데이터 수집

- IOT, log - flume, RDBMS - sqoop, 웹페이지 - R, 크롤링 - R, SNS - R

데이터 저장

- HDFS, no-SQL

데이터 처리

- MapReduce -R

데이터 분석 / 분석결과활용

----

STS workspace 설정

UTF-8로 변경

tern 설치

Data Tool설치

---

fs => HDFS를 제어하는 명령어



빈도수 체크

![image-20200217133032042](images/image-20200217133032042.png)

![image-20200217133113935](images/image-20200217133113935.png)



---



![image-20200217150731263](images/image-20200217150731263.png)

만든 파일을 hadoop에서 실행

./hadoop-1.2.1/bin/hadoop jar 자르파일 실행 명령어

output.txt에 hellohadoop을 써준다

./hadoop-1.2.1/bin/hadoop jar multi-hadoop-examples.jar hdfs.exam.HDFSExam01 output.txt hellohadoop

![image-20200217153554646](images/image-20200217153554646.png)



변경사항이 생기면 저장 > build.xml 실행 후에 jar파일을 다시 덮어쓰기 해주어야 한다.



output.txt 읽어오기

![image-20200217153717255](images/image-20200217153717255.png)

![image-20200217153746455](images/image-20200217153746455.png)



HDFSCopyTest

	- hdfs의 파일을 읽어서 새로운 파일을 생성
	- input파일경로, output파일경로를 명령행매개변수로
	- 클래스파일
![image-20200219131004229](images/image-20200219131004229.png)

실행시

![image-20200219131040262](images/image-20200219131040262.png)

![image-20200219131202940](images/image-20200219131202940.png)

![image-20200219131217826](images/image-20200219131217826.png)

---

ls -a => 숨김파일까지 출력

ls -l => 목록 자세히 보기

ls *.conf => .conf인것 출력

![image-20200219141159506](images/image-20200219141159506.png)

폴더 생성 파일 생성

scp 원격 복사 / cp 로컬에서 사용

cp myfile1(복사할 대상) myfileTest1(복사된 파일명)

![image-20200219141544187](images/image-20200219141544187.png)

제거 명령어 rm

![image-20200219141612740](images/image-20200219141612740.png)

삭제할지 안 묻고 바로 제거

![image-20200219141742428](images/image-20200219141742428.png)

폴더 복사 cp

![image-20200219141926522](images/image-20200219141926522.png)

파일 이동 mv

![image-20200219142137713](images/image-20200219142137713.png)

파일명 변경도 가능 mv

![image-20200219142244613](images/image-20200219142244613.png)

디렉토리 삭제

![image-20200219142521204](images/image-20200219142521204.png)

계층형 디렉토리 생성

![image-20200219142744300](images/image-20200219142744300.png)

계층형 디렉토리 삭제시



root 홈디렉토리 hadooptest폴더 생성

- /etc/sysconfig폴더 copy하기

- /root/의 anaconda-ks.cfg파일 복사하기

- 복사한 후 my_conda.cfg로 rename

- 아래의 구조를 갖고 있는 서브 디렉토리 생성하기

- mytest1

  ​		+

  ​		|ㅡㅡㅡ/etc/hosts파일복사

  ​		|ㅡㅡㅡmytest2

  ​							+

  ​							|

  ​							|___mytest3

  

cat my_conda.cfg 전체 내용 보기

head my_conda.cfg 위에서 10줄 보기

head -5 my_conda.cfg 위에서 5줄 보기

tail my_conda.cfg 아래서 10줄 보기

tail -5 my_conda.cfg 밑에서 5줄 보기

more my_conda.cfg 페이지 단위로 끈어서 보기



mpareduce

sts

![image-20200219164630614](images/image-20200219164630614.png)

commons-cli-1.2.jar 복사해서 Local iot>setup>bigdata>lib에 붙여넣기


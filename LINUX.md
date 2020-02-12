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
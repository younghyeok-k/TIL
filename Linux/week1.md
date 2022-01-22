# week1 01/22

### Linux 환경설정
----------------------

Redhat->Centos 6,7,8 Rocky 8.5
-6,7,8 명렁어가 조금씩 다르다
위에 것만 잘배워도 거의 10%차이빼고 다똑같다

Debian ->  라즈베리 파이,kali
명령어 차이
Ubuntu->(Debian),desktop(개인사용자)
- https://www.virtualbox.org/

- https://www.centos.org/

VMware Workstation :가상 머신
kali 에서 VMware 다운받기
보안 12 qhdks 12


### 순서 
----------------------

Preferences 파일 설정하고
centOS7.ovf 파일끌어서 import 하기
kali.vmx import 하기

집에서할려면 bios 드가서 인텔 가상을 켜줘야함
켜질때 바이오스 F2 bios 드가서
오류뜰때:intel 가상화 enable 64bit 쓸수있다
centOS power start-up 보안12
 
-Devices-
virtual Network Editor
change settings
Add Network
NAT CHANGE
Subnet ip원하는걸로


VM snapshot (복구시점) 하지만 공간을 차지한다
Name: install
Take Snapshot

snapshot 이름에 체크하면 복구 된다
kali,centos 다하기

### 명령어
----------------------

마우스 오른쪽 터미널
터미널 
Ctrl+Shift+ ( + ) 확대
Ctrl+( - ) 축소

$ (일반사용자)
#(root , 관리자)
%su 사용자 전환 (su)
#ls   (디렉토리 리스트)  
#cd / (디렉토리 변경)
#pwd  (현재 디렉토리 위치)
/etc (설정 파일이 있는 디렉토리)
#exit

경로
절대경로(뿌리부터 시작) 
 -Linux :# cd /etc/sysconfig/ (절대경로)
	 http://www.naver.com
	
상대경로(나를 기준)
 	 # cd etc/sysconfig (상대경로)
	 ../images/log.png

#ls -F (뒤에 / 디렉토리, @ 심볼릭 링크 바로가기 아이콘,뒤에 X 파일)
   
#ls -a (숨김파일 포함 출력)
   . (디렉토리의 현재위치)
   ..(상위 디렉토리의 위치)
#cd ~ (사용자 홈 디렉토리로 바로가기)
#vi (메모장)



### 개념
----------------------


실행에서
ncpa.cpl(네트워크 환경)
control(제어판)
ipconfig(랜카드 정보)
ipconfig/?
ipconfig/all

-VMware 사용법
가상머신의 -네트워크 실무,가상 환경을 만들어서
리눅스를 운영하기 위해



-mac(하드웨어) 주소 (개념)
-모든 통신장비에 있다. 실제 통신에 사용된다
 48bit(24bit ->OUI,24bit->serial)
 표기 16진수

-네트워크
IPv4(32bit) / IPv6(128bit)

A Class 0.  ~ 127.255.255.255
B Class 128.~ 191.255.255.255
C Class 192.~ 223.255.255.255
D Class
-제외
127.0.0.0 ~ 127.255.255.255(Loopback 주소,자기자긴 테스트 127.0.0.1 대표적)
127.0.0.1-->localhost(hosts 의해 같이 사용됨)

-사설 IP(외부로 나가지 못함,내부에서만 사용 가능)

A Class 10.0.0.0 ~ 10.255.255.255 (암기할때 10)
B Class 172.16.0.0 ~ 172.31.255.255 (암기할때 172.16)
C Class 192.168.0.0 ~ 192.168.255.255 (암기할때 192.168)


224 ~ 멀티캐스트
240 ~ 연구용

subnetmask(서브넷마스크)
A 255.0.0.0   default subnetmask
B 255.255.0.0
C 255.255.255.0


-서버(Linux),고정IP 할당
고정IP -> 수동으로 작성(입력)
유동IP -> DHCP서버에서 할당(구축함)

IP: 192.268.0.7/24  (24비트)
    -IP 192.168.0.7
    -255.255.255.0

0 값에 의해 몇대의 컴퓨터를 연결가능하지 알 수 있다

IP: 192.268.0.7/25  
    -IP 192.168.0.7
    -255.255.255.128  (128대 연결 가능 ,실제는 126대이다.



GW: 192.168.0.1 (gateway,출구)
DNS(도메인주소를 이용해서 IP주소를 가져온다)
 -KT:168.126.63.1~2
 -google:8.8.8.8, 8.8.4.4


예시) http://www.naver.com ->1.1.1.1 (IP 전달)

나머지는 공인IP이다.

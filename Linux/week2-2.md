# week2-2

## 부팅단계   
------------------------
 프로세스(id)   
 CentOS 6 버전까지 init(PID 1번)   
 CentOS 7~    systemd(PID 1번)   
   
-개발, 운영자, 정보보안 -해커,버그,취약점   
   
fork(부모프로세스에 종속)   
exec(자신이 직접 실행)   

PID(자신의 프로세스 ID)   
PPID(부모의 프로세스 ID)   
   
   
## 런레벨(Runlevel)
------------------------------------
/etc 리눅스에서 설정파일(누가?  설정,cd /etc)   
/boot   
   
telinit [런레벨] runlevel   
0:시스템을 종료한다   
1:시스템을 단일 사용자 모드로 전환한다(안전모드)   
3:시스템을 X윈도우 사용하지 않는 멀티 유저 모드로 전환한다   
5:시스템을 X윈도우를 사용하는 멀티유저 모드로 전환한다   
6:시스템 재부팅   
s,S:실행중인 프로세를 종료하지 않고 단일 사용자 모드로 전환한다   
init 6 init 6   
   
/etc/inittab (런레벨 관련 설정파일)   
#--> 주석   
#file 파일의 종류를 출력   
systemctl set-default TARGET.target   
-multi-user.target(런레벨 3)/graphical.target(런레벨 5)   
   
## 런레벨 3 변경 방법
-----------------------
[root@localhost etc]# systemctl set-default multi-user.target   
   
재부팅후 런레벨 3로 사용할수있다   
   
#startx(그래픽환경 설치 ,GUI  설치가 되어있어야한다.)   


다시 돌리는 방법   
[root@localhost roror]# systemctl systemctl set-default graphical.target   

--------------------------------------
-서버 침해 대응시 찾아봐야 하는 폴더   
/etc/rc.d/rc*.d --> 런레벨에 따라 실행 스크립트 존재   
파일에서 S시작: 실행되는 스크립트   
파일에서 K시작: 종료된(실행되지 않는)스크립트   
lrwxrwxrwx. 1 root root 20 Nov  3  2018 K50netconsole -> ../init.d/netconsole   
lrwxrwxrwx. 1 root root 17 Nov  3  2018 S10network -> ../init.d/network   

★★★/etc/rc.d/rc.local (어느레벨 상관없이 재부팅시 명령어 실행 가능)   


## 런레벨 데몬실행 방법
---------------------------------
[root@localhost rc.d]# chmod 700 ./rc.local      
[root@localhost rc.d]# ls -l ./rc.local   
-rwx------. 1 root root 473 Apr 11  2018 ./rc.local   
[root@localhost rc.d]# systemctl start rc-local.service   

-런레벨 5 부팅시(프로그램이 자동으로 실행되도록 설정)   
ntsysv(런레벨별 데몬(프로세스)실행 설정)   

   
-자동완성형 (bash)   
cd e tap 키누르면 etc 완성된다   
   
/etc/fstab (부팅시 마운트(하드디스크 인식)설정)   
   
# df   
# fdisk -l   
# lsblk   
   
[root@localhost etc]# df | awk '{print $q}'   



- 네트워크 설정   
#ifconfig #ip addr 아이피를 보여준다   

# grep [단어] [파일위치] 단어가 들어가 있는 줄 출력   
| 파이프,  ; 다중명령어 ||  &&   
[root@localhost ~]# ifconfig | grep inet  (ifconfig 에서 inet 들어가있는거 표시)   

[root@localhost network-scripts]# cd /etc/sysconfig/network-scripts/(랜카드 설정)   
windows : ncpa.cpl (랜카드 환경설정)   
-debian(ubuntu)   
#cd/etc/network   
#vi /etc/network/interfaces (랜카드 설정파일)   
-Redhat/CentOs/Rocky Linux   
#cd/etc/sysconfig/network-scripts (랜카드 설정)   
   
-alias  (별칭,명령어를 단축키처럼 사용 가능)   
만드는법   
[root@localhost network-scripts]# echo "alias vi='vim'" >> ~/.bashrc   
[root@localhost network-scripts]# source ~/.bashrc   
[root@localhost network-scripts]# alias   
vi 확장팩 vim   
source (파일의 설정된 내용을 다시 로그인 하지 않고 읽어들인다.)   
BOOTPROTO=dhcp (네트워크 메소드,자동,수동 설정)   
 -dhcp : 자동으로 서버(DHCP)에서 IP를 할당받는다   
 -node,static :수동으로 IP를 설정   
ONBOOT=no : yes 네트워크 활성화 / no 네트워크 비황설화   
ONBOOT=yes   
   
☆☆☆   
#systemctl (데몬 리셋/시작/중지 설정하는 명령어)   
#systemctl (start|stop|restart|status) 데몬명(프로세스명)   
#systemctl (enable|disable) 데몬명(프로세스명) :재부팅시 자동실행 활성화/비활성화   
   
Rocky
#nmcli c up  ens33(네트워크 활성화)ㅍ
#nmcli c down  ens33(네트워크 비활성화)   
CentOS   
systemctl restart network(네트워크 활성화)   
하기전에 snapshot   

### CentOS 7 -고정 IP 실습   
------------------------------
파일수정: /etc/sysconfig/network-scripts/ifcfg-ens33   
BOOTPROTO=none (수정)    BOOTPROTO=dhcp(수정전)   
IPADDR=100.100.100.128(추가)   
PREFIX=24(추가)      
GATEWAY=100.100.100.2(추가,출구) route / netstat -nr   
DNS1=8.8.8.8 (추가)   
DNS2=8.8.8.7 (추가)   
//BOOTPROTO=dhcp   
//ONBOOT=yes   
   
터미널 실행   
#systemctl restart network   
#ping 8.8.8.8 (통신확인)   
64 byte from 8.8.8.8: icmp_seq=1 ttl=128 time=43.2 ms   
   
Ctrl+z 멈추는거   

   
192.168.100.0 255.255.255.0   
192.168.100.128   
192.168.74.128   

www.teamviewer.com   
   
route/netstat -nr (라우팅 출력)   

라우터(장비) -최적의 경로를 찾아 준다   
도메인: www.naver.com (ip 주소를 알아야 한다)   
 -DNS 서버에 질의   
 -nslookup www.naver.com (ip)   
   
ping 을 gateway 주소로 테스트시는 내부 네트워크의 상태를 점검가능하다   
ping 을 외부의 주소로 테스트시 외부와의 네트워크를 점검 가능하다.   
      
-IP 주소(IPv4)   
IP (IP가 지정시 고정,DHCP 서버에서 할당시 유동)   
SUBNETMASK(NETMASK) (내부네트워크의 연결 가능한 호스트의 개수)   
GATEWAT (패킷이 나가는 출구)   
DNS (도메인주소를 IP주소를 확인하기 위해 필요)   

## RockyLinux 설정 수동으로 설정방법
---------------------------
하기전에 snapshot   
nmcli 툴을 이용 자동으로 설정시   
#nmcli c   
#nmcli d   
   
#nmcli c modify ens33 ipv4.addresses  100.100.100.100/24(자기아이피 넣어야함)   
#nmcli c modify ens33 ipv4.gateway 100.100.100.2(자기게이트웨어 넣어야한다)   
#nmcli c modify ens33 ipv4.dns 8.8.8.8,8.8.4.4   
#nmcli c modify ens33 ipv4.method manual(수동으로쓰겠다 DHCP시 auto 설정)   
#nmcli c modify ens33 autoconnect yes(ONBOOT=yes)   
#nmcli c down ens33; nmcli c up ens33   
   
#vi /etc/sysconfig/network-scripts (경로확인,암기)   
   
BOOTPROTO=none (수정)   
ONBOOT=yes (수정)   
IPADDR=100.100.100.100~110 (추가)  실습할거면(삭제)   
PREFIX=24(추가) 실습할거면(삭제)   
GATEWAY=100.100.100.2(추가,출구) route / netstat -nr 실습할거면(삭제)   
DNS1=8.8.8.8 (추가) 실습할거면(삭제)   
DNS2=8.8.8.7 (추가) 실습할거면(삭제)   
한번더 #nmcli c down ens33; nmcli c up ens33   


   
   
다음주 리다이렉션에관하여 커미션 함 ★

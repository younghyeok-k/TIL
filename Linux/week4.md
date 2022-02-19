# WEEK4-1
----------------------------------
CentOS 7   
   
 vsFTPD 설치 -> 접속 확인 (실습)   
 proFTPD    
   

2022-02-19   
   
기본 명령어 학습   
shell/ifconfig/route/netstat /traceroute/arp/tcpdump/mii-tool   
ethtool/ping/stat/umask/chattr,lsattr/alias/useradd/passwd   
su/sudo/usermod/userdel/passwd/chage/gourpadd/chown   

## 1.CentOS 7 -> vsFTPD  
--------------------------
   
 -ftp port: 20,21번 사용(20 data전송,21 cmd 명령어 전송)      
  C:\Windows\System32\drivers\etc   

   
중요한 port (L4 전송계층,Transport)   
 Well -Known Port  0~1023 (privileges prot,고정 ,root port)   
 2^16 (0~65535)   
 20  ftp-dat (tcp)   
 21  ftp (tcp)   
 22  ssh (tcp)   
 23  telent (tcp)   
 25  smtp(메일서버) (tcp)   
 53 dns (tcp,udp)   
 80 http (tcp)   
 110 pop3 (tcp)   
 143 imap (tcp)      
 443 https (tcp)   
 3306 mysql (tcp)   
 
   
## centos7 ftpd 
-----------------------------------


 
#yum -y install vsftpd 설치   
-- 접근제어 -   
#rpm -qa | grep vsftp   
#rpm -ql vsftpd-3.0.2-29.el7_9.x86_64   
#rpm -ql vsftpd-3.0.2-29.el7_9.x86_64 | grep etc   

#vi /etc/vsftpd/vsftpd.conf   
ctrl +z 빠지기 fg 다시드가기 
설정값만 확인   
 #cat  /etc/vsftpd/vsftpd.conf | grep -v "^#" (-v:  제외하고  ^:그줄의 제일앞 (만약에 ^a 면 a 의 앞)   
anonymous_enable=YES        
local_enable=YES    
write_enable=YES     
local_umask=022      
dirmessage_enable=YES   
xferlog_enable=YES   
connect_from_port_20=YES   
xferlog_std_format=YES   
listen=NO   
listen_ipv6=YES   
   
```
anonymous_enable      #익명 사용자 기능을 활성화 할지     
local_enable        #로컬 사용자(리눅스 계정)의 접속 허용 여부   
write_enable        #업로드 기능 활성화(익명 사용자 제외)   
anon_upload_enable  #익명 사용자의 업로드 허용여부
anon_mkdir_write_enable    #익명 사용자의 디렉터리 생성 허용여부
dirlist_enable        #접속한 디렉터리의 파일 리스트를 보여줄지 여부
download_enable       #다운로드 허용 여부
listen_port           #FTP 서비스의 포트 번호 설정(기본은 21번이며 변경하는 경우 방화벽 설정 확인 필요)
deny_file                     #업로드를 금지할 파일명 패턴 지정 (ex deny_file={*.txt, *.zip})
max_clients                 #FTP 최대 동시 접속자 수 지정
max_per_ip               #클라이언트에서 한 PC당 몇개의 FTP를 연결 할 수 있는지
```
## fg/bg/jobs
--------------------------
  fg, 포그라운드: 화면에 출력되어 있는 상태 ,쉘이 무언가 작업을 하고 있다.   
 ctrl+z:bg 백그라운드로 간다   
  jobs    
[1]+  Stopped                 vi /etc/vsftpd/vsftpd.conf   
   
백그라운드에서 열심 일하게 실행 !, 끝에 & 기호를 붙인다   
백그라운드에서 실행하고 있는 프로그램을 포그라운드로 가지고 올때 fg 사용   
fg 를 사용시 + 기호가 1순위고 ,-가 이후 + 로 변경된다.   
fg %1 ([1]번이 실행된다. 만약 %3을 입력하면 [3] 번이 실행된다.)   
bg %2 ([2]번이 백그라운드에서 실행된다, 즉 포그라운드는 명령(대기상태)을 실행할 수 있다.)   
kill -l   
kill -9 %몇번 하면 끌수있다.   
#yum install gedit -y   
gedit   
   
ex)kill 테스트   
  #sleep 100000000&
  #ps -ef | gref sleep   
  #kill -9  (pid)   
★실수로 저장했을때   
-vi 열었을때 swp 파일이 존재한다고 나오면 해당 디렉토리로 가서   
 .파일이름 .swp 파일을 삭제한다.   
   
:set number   
:set cident   
:set autoindent   
:set smartindent   
:set showmath   
:set hlsearch   
   
ctrl + f  b 한장씩   
gg G 맨끝 맨앞   
w b 워드단위   
찾기 : /  ?  n N   
   
#systemctl enable --now vsftpd (vsftpd 는 데몬 또는 프로세스명 부른다)   
 -설치하고 처음에 한번만 실행      
 -위 명령어는 systemctl enable vsftpd 와 systemctl start vsftpd 를 사용한것과 같다   
 - systemctl enable vsftpd :vsftpd 데몬을 재부팅후에도 자동으로 작동시킨다   
- systemctl disable vsftpd: 비활성화 (재부팅해도 실행되지 않는다)   
- systemctl start vsftpd :지금 활성화 한다   

#ps (프로세스 출력)   
#ps -ef | grep vsftpd (vsftp (vsftpd 의 프로세스를 출력,즉! 실행되어 있으면 출력된다.)   
-프로세스명이 출력되지 않으면 프로그램 (주로설정)이 오류가 있다고 봐야한다.   
#ps -ef | grep vsftpd | grep -v grep   

   
-리눅스에 접근통제/방화벽   
 selinux 의 접근은 디스크 (hdd ,ssd 파일 디렉토리등)   
 방화벽은 네트워크(ip,prot) 차단 또는 해제   
 접근통제:selinux (DAC,MAC) ---> MAC 기반 --> 대부분 학습시 비활성화    
                 -Command injection:shell --> root(다른쪽으로 접근이 안된다.) DAC 기반은 접근이 된다.   
                 -setenforce 0/1 (0은 임시로 해체 ,재부팅시 활성화 된다. 1은 활성화)
                 -getenforce   
                 -/etc/sysconfig/selinux          ---> SELINUX = enforcing 를 SELINX =disabled 설정후 재부팅 (해제)   
      
 방화벽 :netfiter(kernel에 설정되어 있다)   
           -iptables,ufw,firewalld    (유틸리티 라고 한다 즉 방화벽 설정을 쉽게하기 위해 도와주는 프로그램)   
           -iptables ---> 보안기사 ,등 많이 나오며  세부적 옵션을 줄려면 사용   
           -firewalld:Redhat 계열 (Cent ,Rocky 등)   
           - ufw (우분투)   
   
   
----> 위에서 꼭 알면 좋은건   
        -setenforce 0 또는 1   
        -iptables -nL (방화벽 정책 확인)   
        -firewall -cmd --help (#firewall-cmd --list -all 정책 확인)   
           
-----

#firewall-cmd --permanent --add-service=ftp (21번 포트를 open 한다.)   
#firewall-cmd --permanent --add-port=80/tcp   
#firewall-cmd --reload  (정책 적용 및 다시 읽기)   
#yum install httpd* -y (apache 설치)   
#systemctl enable --now httpd   
#firewall-cmd --list-all   
#ifconfig  내아이피   
#netstat -antp   

192.168.230.128  roror 보안 12 연결   

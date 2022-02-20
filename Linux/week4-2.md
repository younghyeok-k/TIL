# week4-2
--------------------------------------------


2/20


## 명령어정리   
-------------------------
 ```
shell/ifconfig/route/netstat/traceroute/arp-a   
tcpdump/mii-tool/ethool/ping/stat/umask   
chattr,lsattr/alias/useradd/passwd/su/sudo   
usermod,userdel,passwd/chage/groupadd/chown   
```
절대경로 상대경로   ----> 반복연습(적용)   
.   *       ./  pcre(정규표현식) *.* 특수문자,문자 \   
 정규표현식 ,특수문자 ,문자로 인식 , \ , $, [    \[   \$   

   
cp 무엇을 어디로   
/etc/skel   <---------------     /   
cp -r /etc/skel . 복사   
 cp passwd_hard ./passwd   
   
-r, -R :디렉토리    
mkdir -p ./user/user/user (디렉토리만들기)   
rmdir(디렉토리 삭제)   
rm (파일삭제)   
rm -rf  (-r 디렉토리 f 강제)   
   
   

ln (하드링크)   
ln -s(심볼릭링크)   
/home/passwd(i-node)   
ln /home/passwd /home/passwd _hard(i-node,원본과 동일한 값을 가지고 있다.)   
ln -s /home/passwd /home/passwd_soft(i-node,원본과 다른 값을 가지고 있다.)   
   
vi   
cat 파일이름 (-n)   
-특정파일 크기를 0만들때   
touch 파일이름 (파일크기가 0으로 만들때 사용)   
  #touch file.txt (크기가 0인 file.txt 파일 생성)   
  #touch /dev/nul > /var/log/messages ( messages 파일은 크기가 0이된다)   
  -messages 는 로그에서 실시간 읽어 들이므로  삭제후 생성시 문제가 될 수 있다.   
du -h   
du -h ( 파일크기 -h ,읽기편하게 k,g,m 형식으로 출력 , -s 전체크기 , ls- h)   
df -h(디스크의 사용량 출력 ,lsblk,fdisk,mount)   
head/tail/more/less   
hlat/poweroff/init 0 /sutdown -h now (일반사용자가 사용할 수 없도록 설정)   
reboot /init 6/shutdown -r now (sync 동기화)   


-----------------------------------------------------
APM --> 서버에 프로그램 설치시 /etc/profile   
/PATH (찾는거) n 다음으로넘어가기   
   
/etc 위치에 있는 설정은 전역설정이다 (여기에는 맨앞에 .이 없다)   
/etc/profile   
예시) export PATH:$PATH:/usr/bin/java:/usr/local/mysql/bin   
/etc/bashrc (쉘 함수와 앨리어스가  설정되어 있는 전역 변수의 파일)   
   

~ 사용자 홈 디렉토리  ( &,#  <----------모양에 따라 경로가 달라진다 cp/etc/passwd ~   
/root   
/home/일반사용자   
.bashrc (사용자의 alias 및 변수)   
.bash_history (사용자의 히스티 값)   
.bash_logout (사용자 로그아웃 설정 파일)   
   
## alias 명령어 만들기   
------------------------------------------------------------------
```
#alias net='ls /etc/sysconfig/network-scripts'v
[root@localhost ~]# netv
ifcfg-ens33   
````
   
/bin/vi/etc/passwd (root 기본적용 ,보안을 위해)   
.bashrc 에 alias vu= 'vim' 설정후 source ~./bashrc 실행하면 vi를 사용해도 vim /etc/passwd 처럼 실행된다   
   
ipconfig   
ifconfig   
ip addr   
-r 디렉토리 -f 강제 -n 숫자 -v 자세히 -h help 또는 해쉬표시 (route -n,netstat -nr)   
★etstat -antp 네트워크 상태   
LISTEN:대기상태   
ESTABLISHED: 접송상태   
apache --> apache2 --> httpd 웹서버      
   

windows :trcert / linux :traceroute   
- #traceroute 8.8.8.8 (지나간 라우터의 주소를 출력해준다.)   
- #게이트웨이,라우팅 문제등 확인 가능   
   
ARP( 네트워크 계층,L3 IP주소를 이용하여 맥주소(하드웨어주소)를 가지고 온다.   
 -실제로 사용하는 통신 방식(대부분 IP 이용 통신하는걸로 알지만 ARP 맥을 이용 통신한다)   
 -arp sfooping 같은 공격에 취약하다   
 -ip    
   
stat : 파일의  Access,Modify,Change 시간을 출력해준다   
Access:파일을 읽었을때 변경된다   
Modify:파일을 수정했을때 변경된다   
Change:속성을 변경했을때 변경된다.   
-find :찾기   
SetUID/SetGIDv
chown 유저 :그룹 [파일 또는 디렉토리] (단 . 으로도 사용한다.)   
chgrp 그룹명[파일 또는 디렉토리]   
   
umask 022 (기본권한)   
디렉토리 :777 기본값   
파일: 666        기본값    (1은 실행,파일생성시 1값이 있으면 스크립트가 되어 실행이 된다.)   







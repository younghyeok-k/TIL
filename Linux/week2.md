# Week2
----------------------------------------------------
-리눅스 방화벽(netfilter 커널)       
 iptables(모든 리눅스에 적용)    
 Redhat(firewalld)    
 Ubuntu(ufw)    
cd: 디렉토리 이동 (명령어)     
Ctrl+l clear (화면 클리어)    
$su    
#yum install tree-y    
#tree | more         
-tree: 리눅스의 디렉토리 구조 출력    
    
-------------------------------------------------------
$ cd ../../../bin/usr/bin (상대경로)    
$ /bin/usr/bin (절대 경로)    
    

q 치면 빠짐    
    
#cd/etc 리눅스의 설정(환경) 파일이 존재    
    
ls 디렉토리,현재위치의 리스트를 출력    
입력/출력(모니터)    
#ls (파일,디렉토리등 목록 출력)    
#ls -l (자세히)    
#ls -l /etc/passwd (특정  파일만 출력)    
-rw-r--r--. 1 root root 2195 11월  3  2018 /etc/passwd    
- (파일의 종류) , d 디렉토리, -파일, c 장치, b 블럭, l 링크, s 소켓, p 파이프    
#ls -l | grep "^d" //파일,디렉토리만 검색    
#ls -l | grep "^c" //장치만 검색     

이거순서 설명 ↓     
-rw-r--r--. 1 root root 2195 11월  3  2018 /etc/passwd    
    
rwxr-r--r--(권한) 총 9개 ---(사용자) ---(그룹) --(그외 나머지)    
-rw-r--r-- 퍼미션 (권한) 644 이다    
-사용자는 읽고 쓰기가 가능하고 그룹과 나머지는 일기만 가능하다    
 -r,=(읽기,4), -w(쓰기,2), -x(실행,1)    
. --> acl+변경된다.    
    
    
1 하드링크된 수  (심볼릭링크, 하드링크) -->바로가기 아이콘(Windows)    
    
root(소유자,사용자) 무슨?????  /etc/passwd  (-)파일의 소유자    
root(그룹) /etc/passwd  (-)그룹의 소유자    
    
2195 파일의 크기    
    
11월  3  2018 마지막 변경된 날짜    
    
/etc/passwd 파일명(디렉토리명)    
    
    

ls -a (숨김파일포함) 모든 내용 출력    
ls -lh 파일크기를 읽기 편하게 byte 단위로 출력 G,M,K    
ls -d 디렉토리 정보출력    
    

~(홈디렉토리)    
cd (홈디렉토리 경로없을경우)    
리다이렉션  > (출력을 변경) --> 파일로 변경    
[root@localhost ~]# echo "ls" > cat  (현재경로에 cat 파일을 생성)    
[root@localhost ~]# chmod 777 ./cat  (cat 파일의 권한 변경)    
-rwx rwx rwx 7 7 7 읽고쓰고실행하고(x실행,windows .ext 파일과 똑같다)    
    
[root@localhost ~]# rm ./cat 파일삭제    
[root@localhost ~]# which cat (cat 파일의 경로를 출력)    
    
cat 치고 ctrl +d 누르면 빠져나간다    
[root@localhost ~]# cat (/usr/bin/cat 실행)    
[root@localhost ~]# ./cat (/root 내가현재있는곳의 cat 실행)    
    
/ 최상위 디렉토리 (root 디렉토리)    
./ 현재위치     
    
[root@localhost /]# echo $PATH(리눅스에서 특정 경로(디렉토리)를 메모리에 저장한다)    
 -메모리는 항상 참조 가능하다.(찾는다,열어본다)    
    
#echo $PATH    
-$ 변수값 출력시 사용한다.    
    
    
## 명령어 만드는 법    
--------------------------------
$ echo "clear" > ~/cls    
$ chmod 777 ~/cls    
$ ~/cls (~: 홈디렉토리 /root/cls )    
    
  예) /home/roror/cls --> ~/cls    
     ~ 홈디렉토리에서 ~/cls 명령어를 만들었기때문에    
cd etc 디렉토리에서는 ~/cls 명령어가 없기때문에 /root/cls 실행을해야한다    

    
[root@localhost etc]# echo $PATH    
/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/home/roror/.local/bin:/home/roror/bin    

/usr/bin path 경로    

[root@localhost ~]# cp -a ./cls /usr/bin    
[root@localhost ~]# ls -l /usr/bin/cls    


path 경로에 cls 명령어를 넣어주면 어디에서나 사용가능하다.    


## 용도
-------------------------
   
Linux   
 -수동으로 설정    
 -리눅스(어떤용도?) /운영체제 / 서버    
 -Server(네이버) <----> Client(우리 ,사용자)   
 -ftp/dhpc/web/was/nas/google play   
 -서버에 프로그램을 설치하고 서비스   
   
설치 (공간을 어떻게 할당?)   
 -로그서버 ( /var/log)   
 -웹서버   (/home )   
 -메일서버 ( /var/mail)   
 
## Rocky Linux 설치 
------------------------------------




파티션 설치   
 -디렉토리    
저장소구성에서 사용자정의로 선택하면   
전체 40G    
신규 Linux 설치에서   

현재설정보존    
LVM 으로선택   
+ 눌러서   
 /boot(1G)   
 swap (4G 4096)   
 /home (10G)   
 /     (나머지 용량선택하지않고 하면 나머지알아서 적용)    
변경적용   

-표준파티션/  LVM      

보안설정후   
사용자생성   

## 리눅스 명령어 (종료/재부팅)
------------------------------------

종료   
 -shutdown -h now   
 -halt   
 -power off   
 -init 0   
   
재부팅   
 -shutdown -r now   
 -reboot   
 -init 6   

## cat 파일 출력
----------------------------------

[1]   
#echo "my data" > data.txt (파일이 생성)   
#cat ./data.txt 파일출력   
my data   
[2] 
#vi ./data2.txt  파일출력   
i 누르고    
my data 쓰고   
esc 후    
:wq 저장하고 나오기   
#cat ./data2.txt 파일출력   
my data   
[3]   
#cat > ./data3.txt << EOF (하나의 명령어, 암기,EOF 종료한다)   
my data  글쓰고   
my data2   
EOF 쓰면 빠져나감   
#cat ./data3.txt  파일출력   

## 다시보기 + 명령어
-------------------------------------
cp   
pwd   
ls a,l   
which   
type   
head(문서의 윗부분 10줄을 출력)    
[root@localhost ~]# head etc/passwd -5   
[root@localhost ~]# head -42 /etc/passwd    
tail(문서의 마지막부분 10줄 출력)   
 - 옵션 :-n 3 세줄 출력, -5 줄여서 가능   
   
하나의(한페이지) 화면으로 출력   
more   
less   
   
| 파이프   
ls | more (less)   로그화면 하나씩내리는거 스페이스바       
Shift+Page UP/Down 로그화면 올리고 내리기       
   
   
Server( 네트워크 , 다중 사용자용으로 최적화된 시스템 소프트웨어를 설치)   
OSI 7 Layer (애플리케이션 계층 주로 서버 프로그램)   
SSH, Telnet, HTTP, FTP, DHCP, NTP   
Telnet/SSH 원격 지원 프로그램   
SSH(Secure Shell) 암호화된 원격지원(접속) 프로그램   

서버 -클라이언트   
SSH 서버 - SSH 클라이언트 가 있다!   
Windows 용 SSH client 는 putty 도 있다.   

-windows :ipconfig   
 Linux :ifconfig( 랜카드 정보, IP 번호 확인 가능)   

putty    
https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html   
에서    
putty.exe 설치후 실행   
ifconfig 의  inet 100.100.100.128  주소 복사후   
붙여넣기   
아이디 비번 넣고 roror  보안12   
실행화면 터미널 창이뜬다   

  #shutdown -h now

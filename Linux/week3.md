# week3


## 명령어(참고할만한 명령어)
---------------------------
-man cal   
-cal -h(--help)   
cal/date/hostname/uname -a/ who/ w/ whoami/   
- 명령어를 찾을때   
which/whereis/whatis ls(명령어 설명)   
컴퓨터의 이름(hostname)   
   
### - 네트워크
 1)   
   IP   
   NEKMASK(windows : SUBNET MASK), 최근에는 PREFIX=24(비트) 설정   
   GATEWAY   
   DNS   
   
  192.168.100.0/24     ---> 24   -->  255.255.255.0   
->11111111111111111111111100000000 IPv4 32bit   
   
  192.168.4.0/24      
  192.168.200.0/24      
  192.168.50.0/24      
   
### 집에서 해봐야할꺼   (하기전에 snapshot 찍기)
----------------------         
VM 세팅에서 IP설정에서 NAT 을 브릿지로 바꾸고      

Virtual Network 를 vment information Realtek 으로바꾼다.      

/etc/sysconfig/network-scripts/랜카드 설정파일이 존재
vi ifcfg-ens33
 파일을 열어서 확인 ONBOOT=yes 부팅시 랜카드 활성화      
  :wq      
#nmcli c down ens33 (랜카드 컨넥션 중지)      
#nmcli c up ens33  (랜카드 컨넥션 시작)      
#ifconfig      
#ssh      
## 실습
----------------------      

/etc/sysconfig/network-scripts      
ONBOOT=yes      
nmcli c modify ens33 ipv4.addresses 192.168.1.101/16      
nmcli c modify ens33 ipv4.gateway 192.168.0.1      
nmcli c modify ens33 ipv4.dns 8.8.8.8,8.8.4.4      
nmcli c modify ens33 ipv4.method manual (auto,disabled)      
nmcli c modify ens33 autoconnect yes      
      
nmcli c down ens33      
nmcli c up ens33      
    
## 입출력 재지정(I/O Redirection): |,>,>>,<,<< p28    
----------------------
      
| grep      
      
#ls /etc |grep ssh = ssh이름 찾기      
#ls /etc |grep yum = yum이름 찾기      
      
      
> 출력 리다이렉션      
#ls -l/etc > ./etc_ls.txt  (파일생성)       
 - ls -l /etc 의 출력값을 etc_ls 파일로 저장      
 - ls /etc > ./etc_list (결과값? 덮어쓰기가 된다.)      
      
      
[root@localhost /]# ls -l | tail -3 > ./etc_ls.txt      
[root@localhost /]# cat ./etc_ls.txt      
drwxrwxrwt.  21 root root 4096  2월 13 03:59 tmp      
drwxr-xr-x.  13 root root  158  2월  6 04:55 usr      
drwxr-xr-x.  21 root root 4096  2월  6 05:08 var      
[root@localhost /]# ls -l | head -3 > ./etc_ls.txt      
      
>> 출력 (끼워넣기)      
 - ls /etc >> ./etc_list       
[root@localhost /]# ls -l | head -3 >> ./etc_ls.txt      
[root@localhost /]# cat ./etc_ls.txt      
합계 24      
lrwxrwxrwx.   1 root root    7 10월 11 09:48 bin -> usr/bin      
dr-xr-xr-x.   5 root root 4096  2월  6 05:08 boot      
합계 28      
lrwxrwxrwx.   1 root root    7 10월 11 09:48 bin -> usr/bin      
dr-xr-xr-x.   5 root root 4096  2월  6 05:08 boot      
      
      
#cat >./test.txt  (입력받아서 test.txt 파일을 만든다)      
12312      
123123      
cat ./test.txt      
12312      
123123      
      
echo 출력      
#echo "ls" > ./dir  (현재있는위치에 dir 을만들고 "ls" 를 넣는다)         
#chmod 777 ./dir (dir 색 바꿈)      
      
#cat/etc/passwd 패스워드 파일의 내용을 출력(모니터)      
#cat/etc/passwd > /home/roror/passwd (파일로 출력)      
#cat < ./passwd > ./passwd2      
      
      
< 입력      
#cat < ./etc_ls.txt > ./ttt (etc_ls.txt 를 입력받아서 ./ttt(파일생성후 ) 에 출력한다 )      
      
      
#cp ./etc_ls.txt ./etc_ls.txt.old      
      

<< 입력 (끼워넣기)      

------------------------------------------------------

1> (표준출력)   
<0 (표준입력)   
2> (표준에러)   

find (검색, 찾을때)   
/   
-name "이름"(이름, 파일명,디렉토리)   
   
0,1,2 파일디스크립터 p28   
   
sleep 3   
ls   
$ 변수쓸때   
   
: 하나의 라인에 여러개의 명령을 실행   
&& :첫 번째 명령이 에러없이 실행되면 두 번째 실행   
|| :첫 번째가 실패해도 두 번째가 실행된다   

   
---------------------------------------------------------

-네트워크 (기본설정 34-37)   
 1) nat 설정 테스트   
 2) bridge 테스트   
   
-리다이렉션(I/O 28p)   
-r -R 디렉토리   
-f 강제   
-v 자세히   

u(사용자) g(그룹) o(나머지)   
a 모두    
   
-디렉토리 생성   
1)#mkdir 파일이름(디렉토리 만들기)   
2)#mkdir -p ./test1/test2/test3   
test1>test2>test3 처럼만들어진다   
   
-디렉토리 삭제   
1) rmdor 파일이름 (디렉토리는 삭제 안됨)   
2) rm -rf 디렉토리이름(파일 디렉토리 강제로 삭제)   
   
## 소유권과 허가권
-------------
   

사용자만 읽고 쓰고 실행   
700(rwx --- ---)   
chmod 700 ./파일이름(변경하고자하는 파일 또는 디렉토리)   
root 사용자는 읽고 쓰고 실행이 가능하고 그룹및외(other)는 접근 금지   
   
-rwxr-xr-x. (7 5 1)   
루트사용자는 읽고 쓰기가능하고 root그룹은 읽고 실행만가능하고 그외에는 실행만가능하다   
   
-rw-rw---- (660)   
사용자와 그룹은 읽고 쓰기가 가능하고 그외나머지는 접근금지   
   
   
SetUID --> 4000  --> 사용자가 rws 변경된다.   
SetGID --> 2000  --> 그룹이 rws 변경된다.   
Sticky bit --> 1000 --> other 가 rwt 로변경된다   
   
   
#hmod 7777 ./passwd   
#ls -l ./passwd   
-rwsrwsrwt. 1 root root 2548  2월 13 05:31 ./passwd   
   
   

#chmod 4777 ./passwd   
#ls -l ./passwd   
-rwsrwxrwx. 1 root root 2548  2월 13 05:31 ./passwd   

roror 사용자가 패스워드 변경시   
roror 사용자는 /usr/bin/passwd 실행시 root 권한이 자동으로 작동한다.   

   
-rws(4000) rwx(2000) rwt(1000)   
 user      group     other   
 6000,7000,300   
 777-> SetUID --->4777 (777)   


# week6-2
------------------------------------------------
## 요약
-----------
Apache+PHP+MySQL-그누보드(게시판)+Tomcat   
 마지막 PHP   
   
Rocky(CentOS 8) -dnf       
CentOS7 --> yum   
```
# yum autoremove httpd -y (dnf)
```

apache (html 웹,정적인 페이지를 읽을 수 있도록 해주는 서버)   
apahce+javascripts+jQuery+...   
apmsetup,xamp :Windows 웹서버를 사용하다록 해주는 프로그램   
   
   
Well-known prot 0~1023       
21(FTP)/22(SSH)/23(Telnet)/25(SMTP)/53(DNS)/80(HTTP)/443(HTTPS)   
22--> HTTP 이런식으로 사용불가.   
22--> SSH(애플리케이션 계층)   

## apache
------
-Rocky

-프로그램를 설치후   
재부팅시 실행 /현재실행 /방화벽 설정 (서버의 경우)/selinux 정책   
1.프로그램을 실행 해본다. 정상적인 접근 가능여부 확인   
2.방화병 정책 확인: #iptables -nL (정책 확인 가능 ,firewall-cmd --list-all 와 같은 명령어)   
   방화벽 정책 해제 :#iptables -F (방화벽 정책 임시 해제)   
3.셀리눅스 정책 해제 :#getenforce 결과값 확인 #sentenforce 0번또는 1번   
   
```
# systemctl enable httpd (httpd 데몬명 ,즉 프로그램,서버가 재부팅시 활성화된다)
# systemctl start http(프로그램 실행)
# systemctl (restart|stat|stop)데몬명 # systemctl restart httpd 식으로 사용
-CentOS 6 또는 이하버전 (Ubuntu 16버전까지)
# /etc/init.d/httpd start start         start ,stop ,restart,status 처럼 사용가능
service start httpd
-방화벽 (CentOS/Rocky)
 #systemctl status firewalld
 #firewall-cmd --permanet --add-prot=80/tcp (http 서버 오픈시)
 #firewall-cmd --permanet --add-service=http (http 서버 오픈시)
  --permanent 옵션을 꼭 사용해야 한다 (영구적으로 Open)
#firewall-cmd -reload




# dnf install http-y
#systemctl enable --now httpd
# firewall-cmd --permanent --add-service=http
# firewall-cmd --reload
```

-윈도우에서 Linux 서버 IP 로 웹 접속 확인   
 http://192.168.100.100   
 ```
#dnf install mod_ssl -y
#vi /etc/httpd/conf.d/ssl.conf
SSLCertificateFile /etc/pki/tls/certs/roror.co.kr.crt (85번쨰줄
SSLCertificateKeyFile /etc/pki/tls/private/roror.co.kr.key (93번째줄
# killall -HUP httpd (프로그램  전체적으로 재실행 하지 않고 설정만 재실행)
    -systemctl restat httpd

```
## 리눅스 파일 전송 방법
-----------------------------------------
 FTP /SFTP /FTPS   
 FTP : proFTPD , vsFTPD 와 같은 서버 프로그램을 설치   
 FTP Client :filezilla, 알FTP 같은 프로그램을 사용   
 SFTP :SSH를 이용하여 파일전송    
 SFTP Client: filezilla, 알FTP 같은 프로그램을 사용   
->Rocky 리눅스는 ssh 가 설치되어 있으므로 기본적으로 sftp 를 이용하여 파일전송 가능   
   
-21(FTP) / 22 (SSH) /23(Telnet)   
-암호화 22(SSH,Secure Shell)   
-인증서 기반 접속(ftps,암호화)   
   
-접속방법(SFTP)   
 호스트 :서버의 IP주소 (Rocky) , 사용자명 :아이디 ,비밀번호 :비번,포트 :22  <---- 포트로 FTP/FTPS/SFTP 구분한다.   

  
## DB 설치
----------------------------------
   

```
#dnf module lsit mariadb
#dnf module install mariadb:10.3 -y (mariadb 10.3 버전 설치)
# firewall-cmd --permanent --add-service=mysql
# firewall-cmd --reload 
# systemctl enable --now mariadb
# mysql_secure_installation  (초기 관리자 설정,및 설치후 DB 초기화,설치후 한번만 해준다.)
Enter
Set root password? [Y/n] Y
-뒤에 나머지는 전부 Y 후 마무리한다.
```

## DB 접속 방법(mariaDB)
----------------------
```
# mysql -u -root -p'비번'
>show databases;
>use mysql (mysql database 이동)
>show tables;
>desc user; (테이블의 구조)
select host,user,password from user;

>quit

# vi /etc/my.cnf.d/charset.cnf

[mysqld]
character-set-server = utf8mb4

[client]
default-character-set = utf8mb4

# systemctl restart mariadb
```
# PHP 설치
-----------------
```
-PHP 설치            tomcat(jsp) --->apm +tomcat
"etc/my.cnf.d/charset.cnf"

# dnf module list php
# dnf module install php:7.4 -y

# php -vv
# vi /etc/php.ini
short_open_tag=Off -> On (187번째)(php 구문 시작 </php 끝은 ?> 끝난다 On 설정시 <? 사용 가능하다.)
   -옵션 값에 따라 SQL injection 을 방지할 수 도 있다. (어느정도)
 select user from user where user=" "

# cat /etc/php.ini | grep -Ev "^;|^$"

# systemctl restart httpd
# systemctl restart php-fpm
# echo "<? phpinfo(); ?>" > /var/www/html/info.php
확인
http://192.168.123.200/info.php
# dnf install php-gd
# dnf install php-devel

# systemctl restart httpd
# systemctl restart php-fpm

```

## 그누보드 PHP 서버 연동
-------------------
```
-sir.kr(그누보드,소스공개)
.tar 다운받기
# tar xvfz  gnuboard5-5.5.3.tar.gz  -C /var/www/html/
# mv gnuboard5-5.5.3 gnuboard

# cd gnuboard
# mkdir data
# chmod 707 data

192.168.123.200 드가서 글남기기 클릭

-리눅스 (대부분의 서버 ,프로그램은 --> 데이터베이스명 ,아이디 ,비번 , 호스트명)

#mysql -uroot -p 'qhdks12'
>create database gnuboard;
>grant all privileges on gnuboard.* to roror@localhost identified by 'qhdks12';
>flush privileges;
>quit
user :roror passwd :qhdks12
db:gnuboard
# dnf install php-mysqlnd
# systemctl restart httpd
# systemctl restart php-fpm
```

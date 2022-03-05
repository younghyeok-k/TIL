# week6


## ip 다시설정
--------------
vitual network 192.168.123.0 으로 맞추기   
```
[root@localhost roror]# nmcli c modify ens160 ipv4.addresses 192.168.123.200/24
[root@localhost roror]# nmcli c modify ens160 ipv4.gateway 192.168.123.2
[root@localhost roror]# nmcli c modify ens160 ipv4.dns 8.8.8.8,8.8.4.4
[root@localhost roror]# nmcli c modify ens160 ipv4.method  manual 
[root@localhost roror]# nmcli c modify ens160 autoconnect yes
[root@localhost roror]# nmcli c down ens160;nmcli c up ens160
```

- fdisk 파티션 설정(74page)
```
# fdisk /dev/nvme0n2   (하드디스크 추가후 진행)
1) n 파티션 생성
2) p (primary 설정)  - 4개까지 가능
3) 1 (파티션 넘버)
4) 용량(섹터 또는 g,k,m) 엔터 두번
- t 파티션 타입 지정(운영체제별)
5) t
6) L
7) 8e
8) w
```
## LVM 추가
 --------------------------------
 ```
# pvcreate /dev/nvme0n2p1 (PV볼륨 생성)
# vgcreate vg_home /dev/nvme0n2p1
# vgdisplay
# vgchange -a y vg_home  (볼륨 활성화)
# lvscan (logical volume 스캔) 
  - Free  PE / Size  2559
# lvcreate -l 2559 vg_home -n lv_home   ( lv 추가)
```
## 파티션 설정 끝
------------------------------------
```
# mkfs -t xfs /dev/vg_home/lv_home (포맷)
  /mnt --> 마운트 포인터(위치)
# df -h  장치가 없다. (윈도우로 예를 들면, D드라이브가 표시 되지 않는다.)
   - 마운트 : 장치를 활성화 시켜준(특정 디렉토리로 disk를 연결 시킨다.)
# mkdir /mnt/home
# mount -t xfs /dev/vg_home/lv_home /mnt/home/
# df -h
/dev/mapper/vg_home-lv_home   10G  104M  9.9G   2% /mnt/home
# cp -a /home /mnt/home
# ls /mnt/home
# umount /mnt/home
# ls /mnt/home
```
위 상황을한후 재부팅시   
인식만되어있기때문에 지정을해야한다   
```
 vi /etc/fstab
/dev/vg_home/lv_home

/dev/vg_home/lv_home    /home   xfs defaults  0  0
```
## 사용자 생성 삭제
---------------------
-사용자 생성  useradd/ adduser (똑같은 명령어,useradd를 사용)   
### 관련 파일및 디렉토리 
```
      /etc/passwd , /etc/shadow, /home/. /var/mail, /etc/skel
      예)useradd -M -s /bin/nologin -d /usr/local/mysql-k /etc/skel2 mysql
     -k /etc/skel (사용자 생성시 해당 폴더의 내용을 /home/계정명으로 복사한다)
      복사:/etc/skel -->/etc/skel2
      # cp -a /etc/skel  /etc/skel2
     # useradd -k /etc/skel2 -m  user2
# mkdir /etc/skel/public_html
# echo "My Homepage..." > /etc/skel/public_hteml/index.html
# useradd user (/home/user 위치에 public_html 디렉토리 및 index.html 파일이 생성되어있다.)
```
-사용자추가:user add 유저명   
```
# useradd -o -g 0 -u 0 -d /root -M user
```
-- k/etc/skel2 폴더를 생성하여 해당 내용을 복사하도록 설정

-패스워드변경   
1.자기자신을 바꿀때:passwd   
2.다른 사용자의 패스워드를 변경(root만 가능): passwd 계정명   


-사용자 삭제
```
userdel 계정명 (root만)
userdel -r 계정명 (root만,관련 디렉토리 및 파일 삭제)
```
## Quota
--------------------------------

ID:user (로그인)   
```
#vi /etc/fstab
/dev/vg_home/lv_home /home       xfs   defaults,uquota,gquota 0 0
재부팅

# xfs_quota-x /home (stat,report -h) 용량/파일개수
xfs_quota>state
>limit bsoft=2G  bhard=3G user
>report -h -u
quit
```




# 인증서
-------------------

- 편의상 root 홈디렉토리서 실행
```
# openssl genrsa -aes256 -out /etc/pki/tls/private/roror-rootca.key 2048
# vi rootca_openssl.conf 파일생성
```
### vi rootaca_openssl 파일안에 
```
[ req ]
default_bits            = 2048
default_md              = sha1
default_keyfile         = roror-rootca.key
distinguished_name      = req_distinguished_name
extensions             = v3_ca
req_extensions = v3_ca
  
[ v3_ca ]
basicConstraints       = critical, CA:TRUE, pathlen:0
subjectKeyIdentifier   = hash
##authorityKeyIdentifier = keyid:always, issuer:always
keyUsage               = keyCertSign, cRLSign
nsCertType             = sslCA, emailCA, objCA
[req_distinguished_name ]
countryName                     = Country Name (2 letter code)
countryName_default             = KR
countryName_min                 = 2
countryName_max                 = 2
 
# 회사명 입력
organizationName              = Organization Name (eg, company)
organizationName_default      = roror Inc.
  
# 부서 입력
#organizationalUnitName          = Organizational Unit Name (eg, section)
#organizationalUnitName_default  = Condor Project
  
# SSL 서비스할 domain 명 입력
commonName                      = Common Name (eg, your name or your server's hostname)
commonName_default             = roror's Self Signed CA
commonName_max                  = 64
```

## 키생성 순서
```
# chmod 600 /etc/pki/tls/private/roror-rootca.key
# openssl req -new -key /etc/pki/tls/private/roror-rootca.key -out /etc/pki/tls/certs/roror-rootca.csr -config ./rootca_openssl.conf
# openssl x509 -req -days 3650 -extensions v3_ca -set_serial 1 -in /etc/pki/tls/certs/roror-rootca.csr -signkey /etc/pki/tls/private/roror-rootca.key -out /etc/pki/tls/certs/roror-rootca.crt -extfile rootca_openssl.conf
# openssl x509 -text -in /etc/pki/tls/certs/roror-rootca.crt
```
[ SSL ]
--------------------
```
# openssl genrsa -aes256 -out /etc/pki/tls/private/roror.co.kr.key 2048
# cp /etc/pki/tls/private/roror.co.kr.key /etc/pki/tls/private/roror.co.kr.key.enc (백업)
# openssl rsa -in /etc/pki/tls/private/roror.co.kr.key.enc -out /etc/pki/tls/private/roror.co.kr.key(암호제거)
# chmod 600 /etc/pki/tls/private/roror.co.kr.key*
# vi host_openssl.conf 생성
```
### vi host_openssl.conf
--------------------
```
[ req ]
default_bits            = 2048
default_md              = sha1
default_keyfile         = roror-rootca.key
distinguished_name      = req_distinguished_name
extensions             = v3_user
## 인증서 요청시에도 extension 이 들어가면 authorityKeyIdentifier 를 찾지 못해 에러가 남으로 막아둔다.
## req_extensions = v3_user
 
[ v3_user ]
# Extensions to add to a certificate request
basicConstraints = CA:FALSE
authorityKeyIdentifier = keyid,issuer
subjectKeyIdentifier = hash
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
## SSL 용 확장키 필드
extendedKeyUsage = serverAuth,clientAuth
subjectAltName          = @alt_names
[ alt_names]
## Subject AltName의 DNSName field에 SSL Host 의 도메인 이름을 적어준다.
## 멀티 도메인일 경우 *.roror.co.kr 처럼 쓸 수 있다.
DNS.1   = www.roror.co.kr
DNS.2   = roror.co.kr
DNS.3   = *.roror.co.kr
 
[req_distinguished_name ]
countryName                     = Country Name (2 letter code)
countryName_default             = KR
countryName_min                 = 2
countryName_max                 = 2
 
# 회사명 입력
organizationName              = Organization Name (eg, company)
organizationName_default      = roror Inc.
  
# 부서 입력
organizationalUnitName          = Organizational Unit Name (eg, section)
organizationalUnitName_default  = roror SSL Project
  
# SSL 서비스할 domain 명 입력
commonName                      = Common Name (eg, your name or your server's hostname)
commonName_default             = roror.co.kr
commonName_max                  = 64
```
### 키생성
```
# openssl req -new -key /etc/pki/tls/private/roror.co.kr.key -out /etc/pki/tls/certs/roror.co.kr.csr -config ./host_openssl.conf (인증서요청)
# 
openssl x509 -req -days 1825 -extensions v3_user -in /etc/pki/tls/certs/roror.co.kr.csr \
-CA /etc/pki/tls/certs/roror-rootca.crt -CAcreateserial \
-CAkey /etc/pki/tls/private/roror-rootca.key \
-out /etc/pki/tls/certs/roror.co.kr.crt -extfile host_openssl.conf

# openssl x509 -text -in /etc/pki/tls/certs/roror.co.kr.crt
```

yum install http*   
yum install mod_ssl   
### 방화벽 열기
```
# firewall-cmd --permanent  --add-service=http
# firewall-cmd --permanent  --add-service=dns
# firewall-cmd --reload 
# systemctl enable httpd
# systemctl start  httpd
```

창에 뜨는지확인 http://192.168.123.200/   
## 파일질라연동후 사이트 키 인증
```
파일질라 192.168.123.200 roror qhdks12 22prot
vi /etc/httpd/conf.d/ssl.conf
85번째줄
SSLCertificateFile /etc/pki/tls/certs/roror.co.kr.crt (85번쨰줄
SSLCertificateKeyFile /etc/pki/tls/private/roror.co.kr.key (93번째줄
cd /home/roror
unzip -d /var/www/html ./html.zip
```

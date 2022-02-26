# week5

#리눅스 순서
-----------------
1.네트워크(nmcli 및 본딩)   
-가상(충돌)    
2.DHCP 서버 구축   
3.LVM/ 일반 파티션    
  -Quota   
    
4.인증서설치,Apache,PHP,MySQL (게시판, gnuboard,wordpress,zeroboard)   
5.DNS Server 구축   
6.SAMBA/NFS 구축   
7.메일서버    
8.APM(Source) ,board   
9.SSH/FTP Secure   
   
## -VM nat 설정
----------------------------------------

Virtual Network Editor   
   
192.168.123.0   
   
Devices    
-CD/DVD(IDE) 클릭   
Network Adapter add   
추가하고 applay    
   
## 네트워크 설정
------------------------------------
### -네트워크와 관련 파일들
```
nmcli
1.# cd /etc/sysconfig/network-scripts/
2.# cat/etc/resov.conf(DNS 서버참조)
3.# netstat -nr / route -n (게이트웨이)
   ping 8.8.8.8
   ping 192.168.123.100 (예,나)
```
DNS 서버 (도메인 --> IP) 예 ) www.naver.com ---> 1.1.1.1   
   
IP & Genmask (and 연산한다.) ---> Destination 값이 동일하면 -> Gateway 로 보낸다   

### 생성방법
```
# nmcli c (connection 연결,유틸리티,접속 보조 프로그램 )

# nmcli d (device 물리적인 장치)

# nmcli c add type ethernet con-name 'ens35' ifname ens35
```
35 활성화 되어있는지 확인 33일수도 있음   
-이더넷/랜카드/네트워크 카드 --> ethernet(CSMA/CD), LAN , WAN,BAN PAN   

### 삭제방법
```
# nmcli connection  delete  ens35

# nmcli c  d 5c44ed5c-8312-4afa-8d80-367a0ff96638 
```
안지워지면 이름말고 UUID  값 써도 삭제된다.   



## Device bonding (39page)
----------------------------------------
bonding   
 -랜카드 2개를 묶어서 1개로  사용한다   

nmcli c add type bond con-name bond0 ifname bond0 mode    
상태에서 TAP 키를 두번두르면 밑에와같이 나온다   
802.3ad        balance-alb    balance-tlb    broadcast         
active-backup  balance-rr     balance-xor       
   
## 1)bond0 라는 device 생성
```
# nmcli c add type bond con-name bond0 ifname bond0 mode active-backup

nmcli c add type bon
```

## 2)bond0() 에 그룹(묶음) 화 시킬 device 설정
```
# nmcli c add type bond-slave ifname ens160 master bond0
# nmcli c add type bond-slave ifname ens35 master bond0
```
## 3)옵션설정
```
# nmcli c modify bond0 +bond.options primary=ens160 +bond.options miimon=100 +bond.options updelay=0 +bond.options downdelay=0
```
## 4)prefix ip설정
```
# nmcli c modify bond0 ipv4.address 192.168.123.200/24
# nmcli c modify bond0 ipv4.gateway 192.168.123.2
# nmcli c modify bond0 ipv4.dns 8.8.8.8,8.8.4.4
# nmcli c modify bond0 ipv4.method manual 
# nmcli c modify bond0 ipv4.method 
# nmcli c modify bond0 autoconnect yes
-자동 (DHCP ) 설정 (참고)
# nmcli c modify bond0 ipv4.method auto
# nmcli c modify bond0 autoconnect yes
# nmcli c down bond0
# nmcli c up bond0
```
## 5)백업
```
# mv ./ifcfg-ens160 ./ifcfg-ens35 ~
백업 이동
# init 6 

```
## 6) 물리적인 하나의 랜카드에 여러개 IP주소 할당하기 (page 44)
```
# cp  ifcfg-bond0 ./ifcfg-bond0:1
   
# vi ./ifcfg-bond0:1   
☆☆dd (삭제명령어)   
device 랑 name  :1 붙이고   
게이트웨이랑 dns 삭제 하고 ippaddr 192.168.100.1 교체   
ip v6 다삭제  
 
BONDING_OPTS="mode=active-backup downdelay=0 miimon=100 primary=ens160 updelay=0"
TYPE=Bond
BONDING_MASTER=yes
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=none
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
NAME=bond0:1
UUID=e8ddd477-d910-427f-91dd-fe8a28704171
DEVICE=bond0:1
ONBOOT=yes
IPADDR=192.168.100.1
PREFIX=24
```

1.랜카드 1개설정
2.랜카드 2개(본딩)
3.본딩 또는 랜카드가 1개일 경우 (고정 IP를 2개가 필요하다,서버에...)
  -DHCP 서버의 GATEWAY로 사용
  
  랜카드 2개면 첫번째는 네트워크 (외부) 연결 2번째 랜카드는 (내부 연결)


--------------------------------
실무상황일때      
회사에서 서버 설정 (DHCP Server 에 접속)   
 1) 리눅스 설치 (Network 사용 체크하지 않음)   
 2)
 ```
 #nmcli c modify bond0 autoconnect yes (자동으로 ip 할당)   
   참고) # cat /etc/sysconifg/netwokr-scripts/ens-* (내용중 ONBOOT=YES)   
		# nmcli c modify bond0 ipv4.method  (위의 파일에서 BOOTPROTO=dhcp)   
```
 3)IP/NETMASK/GATEWAY/DNS 자동으로 받으니 확인 가능   
회사에서 서버 설정(수동으로설정시) 회사에서 부여해준다.   
   

--------------------------------
cp 재설명   
   
cp -a(전부다,속성도 포함) -r(디렉토리 복사)   
cp 무엇을 어디로   
 ``` 
☆usermod -a -G 공유자 대상자 (적용받는자)   
usermod -a -G wheel roror (wheel 그룹에 roror그룹 추가)   
cat /etc/group | grep wheel   
   
# vi /etc/pam.d/su   
auth            sufficient      pam_wheel.so trust use_uid (주석해제)   
#usermod -a -G wheel roror (wheel 그룹에 추가하면,비번 없이 로그인)   
```

ens 35 / ens 160 물리적인 장치
bond0 /bond0:1 가상의 랜카드
bond0 : 192.168.123.200/24
bond0:1 : 192.168.100.1/24
-------------------------------
네트워크 설정 요약

```
1. 랜카드 추가
 -  # nmcli device (물리적인 장치)
 -  # nmcli connection (연결, 유틸리티, 접속 보조 프로그램)
1) # nmcli c add type ethernet con-name 'ens33' ifname ens33  (확인 : nmcli d 랜카드)
    # nmcli connection delete ens33 (삭제, UUID 명으로도 삭제가 가능)
2) # nmcli c add type bond con-name bond0 ifname bond0 mode active-backup
3) # nmcli c add type bond-slave ifname ens160 master bond0
4) # nmcli c add type bond-slave ifname ens33 master bond0
5) # nmcli c modify bond0 +bond.options primary=ens160 +bond.options miimon=100 +bond.options updelay=0 +bond.options downdelay=0
6) # nmcli c modify bond0 ipv4.addresses 192.168.123.200/24
7) # nmcli c modify bond0 ipv4.gateway 192.168.123.2
8) # nmcli c modify bond0 ipv4.dns 8.8.8.8,8.8.4.4
9) # nmcli c modify bond0 ipv4.method manual
10) # nmcli c modify bond0 autoconnect yes
11) # nmcli c down bond0
12) # nmcli c up bond0
13) # cd /etc/sysconfig/network-scripts/
14) # cp ifcfg-bond0 ./ifcfg-bond0:1 
15) # vi ./ifcfg-bond0:1
BONDING_OPTS="mode=active-backup downdelay=0 miimon=100 primary=ens160 updelay=0"
TYPE=Bond
BONDING_MASTER=yes
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=none
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
NAME=bond0:1
UUID=e8ddd477-d910-427f-91dd-fe8a28704171
DEVICE=bond0:1
ONBOOT=yes
IPADDR=192.168.100.1
PREFIX=24
```

## DHCP 서버
---------------------------
DHCP(서버)   
공유기/지하철/ --> wifi (IP)   
           --> IP 자동으로    
iptime --> 192.168.0.1 (gateway) --> http://192.168.0.1   
DHCP 설정 (사용,사용안함)   
 -wifi , 자동으로 IP 할당 받도록 해준다.   
    
kali network nat 확인후    
VM --> Network Editor --> Nat -> Use local DHCP  체크해제   
   
kali 에서 ifconfig 쳐서 확인해야함 IP 할당 못받아야한다.   
   
다시 Rocky 로   
```
# dnf install dhcp-server -y
# cp /etc/dhcp/dhcpd.conf ~
# cat /etc/dhcp/dhcpd.conf (내용참고)
# cp /usr/share/doc/dhcp-server/dhcpd.conf.example /etc/dhcp/dhcpd.conf
cp: overwrite '/etc/dhcp/dhcpd.conf'? y
# cd /etc/dhcp/
# ls
dhclient.d  dhcpd.conf  dhcpd6.conf
# cat ./dhcpd.conf | grep -Ev "^#|^$" (설정 내용만 참고)
#vi dhcpd.conf
:%s/^/#/
cp ./dhcpd.conf ./dhcpd.conf.old
# sed -i -e '/^#/d' ./dhcpd.conf (주석있는줄은 삭제)
 # vi /etc/dhcp/dhcpd.conf
option domain-name "dns.google.com";
option domain-name-servers 8.8.8.8, 8.8.4.4;
default-lease-time 600;
max-lease-time 7200;
authoritative;
subnet 192.168.100.0 netmask 255.255.255.0 {
  range 192.168.100.100 192.168.100.150;
  option routers 192.168.100.1;
  option broadcast-address 192.168.100.255;
}
 # sed -i -e '/^#/d' ./dhcpd.conf  (주석이 있는줄은 삭제)
 # systemctl restart dhcpd
 # systemctl enable dhcpd
 # firewall-cmd --add-service=dhcp
 # firewall-cmd --runtime-to-permanent

다시 kali 돌아가서
-Debian(kali ip 리로드)
 #systemctl restart networking
 #cat /etc/resolv.conf
 #route -n

kali dhcp ip할당받은거다

```

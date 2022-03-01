# week5-2

DHCP(서버)   
 -DHCP(서버)에서 Client 자동으로 ip 할당   
 -192.168.100.0/24   
 ```
# vi ifcfg-bond0:1
 IPADDR=192.168.123.1
```
-RedHat 계열 네트워크 카드 리로드
```
# /etc/init.d/network restart
# service network restart
# systemctl restart network(CentOs7)
# systemctl restart NetworkManger(CentOs8)
  -nmcli c donn 랜카드 / nmcli c up  랜카드
```
# DHCP 인터넷 연결 방법 2가지
-----------------------
1)DHCP 설정 및 인터넷 공유   
Rocky    
```
#firewall-cmd --permanent --add-masquerade (인터넷 공유 실행)
//#firewall-cmd --permanent --remove-masquerade (인터넷 공유 중지)
# firewall-cmd --reload
```
2)사용하고 있는 네트워크 대역으로 DHCP 설정
```
# vi /etc/dhcp/dhcpd.conf
option domain-name "dns.google.com";
option domain-name-servers 8.8.8.8, 8.8.4.4;
default-lease-time 600;
max-lease-time 7200;
authoritative;
subnet 192.168.123.0 netmask 255.255.255.0 {
  range 192.168.123.100 192.168.123.150;
  option routers 192.168.123.1;
  option broadcast-address 192.168.123.255;
}
```
## kali(debian) 한글 설치   
-------------------------
```
#apt update   
#apt install fonts-namum*   
```
## su/sudo  
-----------------

 
Redhat   
$su (sudo)   
$su -root   
$su -    
#visudo (# cat/etc/sudoers)   
   
Debian (root 패스워드를 사용하지 않는다)   
#sudo   
#sudo passwd  (kali)   
    
# LVM
-------------------------------------


Device 에서   
   
하드디스크 추가 이름같은거로   


하드디스크 명령어   
```
# lsblk
# df -h
# fdisk -l (page 74)
```
```
# ls -l /dev/nvme0n2 
brw-rw----. 1 root disk 259, 3  2월 27 02:53 /dev/nvme0n2
```
설정
```
# fdisk /dev/nvme0n2 (하드디스크 추가후 진행)
```
1) n 파티션 생성   
2) p (primary 설정)  -4개까지 가능   
3) Partition number:1   
4) First sector (용량 g,k,m) 엔터 두번   
   
5) t 파티션 타입 지정 (운영체제별)   
6) L 리스트   
7) Hex code: 8e     
   
8)w 치고 엔터 나가는거   
   
-LVM 추가
--------
```
# pvcreate /dev/nvme0n2p1(pv 볼륨생성)

#vgdisplay

# vgcreate vg_home /dev/nvme0n2p1
# vgchange -a y vg_home(볼륨 활성화)

# lvscan(logical volume 스캔)
 -Free PE/Size 참고
# lvcreate -l 2559 vg_home -n lv_home (lv 추가)
```
파티션 설정끝

-포맷
-----------
```
# mkfs -t xfs /dev/vg_home/lv_home (포맷)
 /mnt --> 마운트 포인터 (위치)
#df -h 장치가 없다. (장치가 아직 인식 되어있지 않다.)
 -마운트:장치를 활성화 시켜준(특정 디렉토리로 disk를 연결 시킨다)
# mkdir /mnt/home
# mount -t xfs /dev/vg_home/lv_home /mnt/home/
# df -h
/dev/mapper/vg_home-lv_home   10G  104M  9.9G   2% /mnt/home(확인가능하다)
# cp -a /home /mnt/home(홈에 복사 시켜놓는다)

# umount /mnt/home (사라진다)
# df -h (확인)
```
다음주에 쿼터 하고 서버구축함

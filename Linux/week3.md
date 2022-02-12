# Linux


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

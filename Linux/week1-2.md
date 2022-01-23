# week1-2 01/23   
### 1.리눅스 데스크톱 및 데스톱이란?   
### 2.리눅스 설치(Rocky)   
### 3.리눅스 에디터 사용법   
----------------------   

### 1.리눅스 데스크톱 및 데스톱이란?   

----------------------   
 -쉘 과 커넬   
 -터미널   
   

리눅스는 확장자 개념이 없다! .conf(구분하기위해)   
   
하드디스크 -> notepad.exe (프로그램)   
메모리    -> notepad.exe (프로세스)   
   
   
멀티 태스크 모드   
-Ctrl +Alt +F1 ~F7   
-Ctrl +Alt +F1 누르면 나가진다   
   
   
-kali linux (debian)   
 Ctrl +Alt +F2   
 Ctrl +Alt +F7   
   
   
shell (쉘) : 명령어 해석기,연결   
쉘이 커널로 전달해준다.   
커널은 리눅스이다.   

----------------------   

### 2.리눅스 설치(Rocky)   
   
----------------------
 -Rocky Linux   
 -파일시스템   
 -파티션 설정   
 순서
-----------------------   
File new Vitualmachine   
custom   
I will install the operating system later   
Linux CentOs 7 64bit   
processors :1 cores per processor:2   
4GB   
NATv
LSI Logic (Recommended)   
SCSI   
Create a new virtual disk   
disk size(GB):  20  Split Virtual   
   
Devices 에서 클릭해서    
CD/DVD (IDE) 에서   
Use Iso Image file: 이미지파일가져오기   
   
실행하고 드가자마자 마우스클릭 해서 F2 BIOS   
☆집에가져가고 싶을때 suppend 해서 export 해야한다   
   
yum install ibus-hangul 
-----------------------   
   
y 엔터하기   
/*오류가 뜨면 network checking 하고 systemctl restart network  NAT밑에 connect use 두개다 체킹하기   
100.100.100.0/24   
100.100.100.2   
Restore Defaults 클릭하기    
다시 100.100.100.0 으로설정 */   
   
전원버트 지역 및언어 에서 +   
한국어(Hangul) 추가   
shift + space 누르면 한영키 바뀜   
   
   
#yum install firefox -y 파이폭스 자동으로 깔린다   
파이어폭스열어서 google.com ( d2coding 검색)   
다운로드받고 압축풀기   
2018년도꺼 압축풀기   
풀어서 그폴더에서 터미널열기   
#ls #pwd    
#cp -r ./D2Coding /usr/share/fonts   
   
-리눅스에서 디렉토리 옵션은 주로 -r -R 을 사용한다.   
   
   


복사

#cp 무엇을 어디에   
#cp -r 무엇을 어디에 (-r 디렉토리 복사시 사용)   
   

터미널 편집 프로파일기본설정   
사용자 지정 글꼴 d2 D2Coding BOld 선택 v
   
위 순서로 의해 \\\\ 이게 써진다    
   
   
# 3.리눅스 에디터 사용법
-----------------------
 -VI   
v
[root@localhost roror]# echo "vi='vim'" >> ~/.bashrc   
[root@localhost roror]# source ~/.bashrc   
[root@localhost roror]# vi /etc/passwd   
   
:q 빠져나가기   
#vimtutor   
#cd   
#ls 해서 vimtest.txt 있는지 확인   
   
esc 누르면 노말 모드 빠져나가기 머안되면 esc   
ctl +v 노말 블록   
dd 한달락삭제   
★★★★:q ! (저장하지말고 강제로 나가라) ★★★★★★   
:w 저장   
:q 나가기   
:wq! (저장하고 강제로 나가라)   
:wq (저장하고 나가라)   
   
커서 이동하기 외워야하는것   
w ^ $ 0 G nG gg Ctrl+b Ctrl+f e b   
w: 워드단위   
b: w 반대   
set number: 소문자 g는 맨앞 1번으로 대문자 G 마지막 단락으로   
Ctrl +b:밑으로올라가고   
Ctrl +f: 위로올라가고   
$:개행 맨끝으로   
^:개행 맨앞으로   
   

입력모드 전환   
   
i a o  I A O    
i: 삽입   
a: 삽입하면서 입력전환   
o: 밑에쓰게   
   
복사 및 붙이기 & 삭제하기   
   
yy또는 y  : 그줄 복사   
p: 붙여넣기   
x 또는 dl   
dd: 지우기   
dw   
d& 또는 D   
shift +d :그뒤에꺼 숨기기   
   
찾기   
/ :찾기   
r: 한글자만 바꾼다   
j: 현재라인과 다음라인을 바꿔준다   

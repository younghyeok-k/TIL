# Linux-basic-command 01/24

## 리눅스 주요명령어
---------------------------------------------------


| 명령 | 설명 | 
|---------|---------|
| ls   | 디렉터리 내용의 목록을 표시  | 
| clear   | 화면을 지운다  | 
| echo  | 인수로 지정한 문자열을 출력한다  | 
| cp   | 파일을 복사한다  | 
| rm   | 파일을 삭제한다  | 
| mv   | 파일을 이동하고나 이름을 변경한다  | 
| ln   | 다른 파일을 가르키는 연결을 생성한다  | 
| cd  | 현재의 디렉터리를 이동한다  | 
| mkdir   | 디렉터리 생성한다  | 
| rmdir   | 비어있는 디렉터리를 삭제한다  | 
| pwd   | 현재 작업 중인 디렉터리의 경로를 표시한다  | 
| date   | 시스템에 설정된 현재의 시간과 날짜를 출력한다  | 
| dirs   | 디렉터리 스택에 저장된 내용을 표시한다  | 
| cat   | 파일 내용을 표시한다  | 
| more   | 파일의 내용을 페이지 단위로 표시한다  | 
| wc   | 문서 내에서 줄(단어,글자)의 수를 알려준다.  | 
| man   | 유틸리티나 API에 대한 도움말 메뉴얼을 보여준다  | 
| which   | 명령어의 위치하고 있는 경로를 표시한다.  | 
| find   | 시스템에서 파일이나 명령어를 찾는다.  | 
| grep   | 파일 내의 내용을 패턴을 이용해서 검색한다  | 
| adduser,useradd   | 시스템에 사용자를 추가한다  | 
| sudo   | 다른 사용자의 보안 권한으로 명령어를 수행한다.  | 
| su   | root나 다른 사용자로 변경한다  | 
| who   | 사용자에 대한 정보를 표시한다  | 
| wall   | 모든 사용자에게 메시지를 표시한다  | 
| logout   | 현재의 시스템에서 계정을 로그아웃한다  | 
| dmesg   | 커널의 부팅 로그 및 커널 로그를 출력한다.  | 
| chmod   | 파일의 접근 권한을 변경한다.  | 
| chown   | 파일의 소유자를 변경한다.  | 
| chgrp   | 파일과 관련된 그룹을 변경한다  | 
| passwd   | 사용자의 비밀번호를 변경한다.  | 
| du   | 사용자의 사용량을 검사한다.  | 
| df   | 디스크의 남은 공간을 표시한다.  | 
| free   | 시스템의 현재 남은 메모리의 양을 표시한다.  | 
| mount   | 디바이스 시스템에 연결한다.  | 
| ps   | 프로세스의 상태를 표시한다.  | 
| kill   | 프로세스에 시그널을 보내며.주로 프로세스를 죽이는데 사용  | 
| top   | 시스템에서의 현재 프로세스의 상태를 표시  | 
| fg   | 프로세스를 포그라운드 모드로 실행한다.  | 
| bg   | 프로세스를 백그라운드 모드로 실행한다.  | 
| sync   | 현재 캐시된 내용을 저장한다.  | 
| cal   | 달력을 보여준다  | 
| tar   | 여러개의 파일을 하나로 묶는다.  | 
| compress   | 파일을 압축하거나 압축을 해제한다.  | 
| halt   | 시스템을 종료한다  | 
| reboot   | 시스템을 재시작한다.  | 
| poweroff   | 시스템의 전원을 내린다.  | 
| startx   | X 윈도우를 시작한다.  | 
| talen   | 원격 서버에 터미널로 접속한다.  | 
| ftp   | ftp:서버에 접속한다  | 
| apt-cache   | 데비안 계열에서 소프트웨어 패키지를 검색하여 표시한다  | 
| apropos   | 해당 주제와 관련되 명령어들을 표시한다.  | 
| touch   | 크기가 0인 파일을 생성한다.  | 
| dirs   | 디렉터리 스택에 저장된 내용을 표시한다.  | 
| pushd   | 디렉터리 스택에 디렉터리를 저장한다.  | 
| popd   | 디렉터리 스택에서 마지막에 저장한 디렉터리 삭제후 이동   | 





### Linux 기초 명칭
---------------------------------------------------
| 명령 | 설명 | 
|---------|---------|
| CLI(Command Line Interface)| 명령어 기반의 텍스트 입출력 인터페이스  | 
| 터미널   | 서버의 로컬 또는 원격으로 접속할 수 있는 콘솔을 구현한 소프트웨어  | 
| 쉘   | 명령어를 해석하여 전달해주는 소프트웨어  | 
| 콘솔   | 서버의 로컬 장치에서 직접 명령어를 작성할 수 있는 입출력 장치  | 
| tty(Tele Type Writer)   | 콘솔 및 터미널 환경  | 
| pty(Pseudo-Terminal)   |  가상 터미널 환경 | 
| pts(Pseudo-Terminal Slave)   | 원격 터미널 환경  | 
| startx   | 아이템5  | 



### VI 명령어 
---------------------------------------------------
```
[root@localhost roror]# echo "vi='vim'" >> ~/.bashrc   
[root@localhost roror]# source ~/.bashrc   
[root@localhost roror]# vi /etc/passwd   
```
#### 커서 이동하기
| 명령 | 설명 | 명령 | 설명 |  
|---------|---------|---------|---------|
| h   | 커서를 왼쪽으로 이동  | }   | 다음 문단의 처음으로 이동  | 
| j   | 커서를 아래로 이동  | 	H   | 화면의 첫 줄로 이동  |  
| k   | 커서를 위로 이동  | M   | 화면의 중간으로 이동  | 
| l   | 커서를 오른쪽으로 이동  | L   | 화면의 끝 줄로 이동  |  
| w   | 다음 단어의 처음으로 이동  | Ctrl+b   | 한 화면 위로 이동  | 
| -   | 앞 줄의 첫 문자로 이동  | Ctrl+f    | 한 화면 아래로 이동  |  
| ^   | 줄의 첫 문자로 이동  | Ctrl+u   | 반 화면 위로 이동  | 
| $   | 줄의 맨 끝으로 이동  | Ctrl+d   | 반 화면 아래로 이동  |  
| +   | 다음 줄의 첫 문자로 이동  | e   | 다음 단어의 맨 뒤로 이동  | 
| 0   | 첫번째 열로 이동  | b   | 단어 맨 앞으로 이동  |  
| G   | 제일 끝줄로 이동  | z[Enter]   | 현재 커서가 위치한 줄을 화면의 첫줄로 이동  | 
| nG   | n번째 행으로 이동  | n%   | 입력한 n퍼센트에 해당하는 줄로 이동  |  
| gg   | 파일의 처음으로 이동  | 0   | 줄의 제일 처음으로 이동  | 
| (   | 문장의 처음으로 이동  | $   | 줄의 제일 끝으로 이동  |  
| )   | 다음 문장의 처음으로 이동  | 	Ctrl+Y   | 커서는 이동하지 않고 화면만 아래로 이동  | 
| {   | 문단의 처음으로 이동  | 	Ctrl+E   | 커서는 이동하지 않고 화면만 위로 이동  |  




#### 입력 모드 전환

| 명령 | 설명 |
|---------|---------|
| i   | 현재 커서 앞에 삽입하면서 입력 모드로 전환 (현재 커서 위치에서 입력 insert)  |
| a   | 현재 커서 뒤에 삽입하면서 입력 모드로 전환(다음 칸으로 커서이동후 끼워넣기 append)  | 
| o   | 현재 커서가 위치한 곳의 아랫줄에 삽입하면서 입력 모드로 전환  |
| I   | 현재 커서가 위치한 줄의 맨 앞에 삽입하면서 입력 모드로 전환  | 
| A   | 현재 커서가 위치한 줄의 맨 뒤에 삽입하면서 입력 모드로 전환  |
| O   | 현재 커서가 위치한 곳의 윗줄에 삽입하면서 입력 모드로 전환  | 
| s   | 현재 커서가 위치한 곳의 문자를 지우면서 입력 모드로 전환  |
| S   | 현재 커서가 위치한 줄을 지우면서 입력모드로 전환  | 
| ESC   | 명령 모드로 전환  | 




#### 복사 및 붙이기
| 명령 | 설명 |
|---------|---------|
| yy또는 y   | 현재 커서가 위치한 줄을 버퍼에 복사  |
| p   | 버퍼에 들어있는 내용을 현재 커서가 위치한 줄의 아래에 붙임  | 
| x   | 또는 dl: 현재 커서가 위치한 문자를 삭제  |
| dd   | 현재 커서가 위한 줄을 삭제  | 
| dw   | 현재 커서가 위한 단어를 삭제  |
| d$ 또는 D   | 현재 커서가 위치한 문자부터 줄의 끝까지 삭제  | 
| d0 shift d   | 커서의 왼쪽 문자부터 줄의 처음까지 삭제  |




#### 수정하기
| 명령 | 설명 |
|---------|---------|
| r,R   | 해당 단어에 r을 누르고 수정 R은 전체적인 수정  | 

#### 라인합치기
| 명령 | 설명 |
|---------|---------|
| J  |  현재라인과 다음라인을 합해준다  | 


#### 대소문자변경

| 명령 | 설명 |
|---------|---------|
| ~  |  3 ~ 3단어를 소문자는 대문자로 대문자는 소문자로 변경  | 


#### 찾기

| 명령 | 설명 |
|---------|---------|
| /  | 찾기  |
| r   | 한글자만 바꾼다  | 
| j   | 현재라인과 다음라인을 바꿔준다  |


#### ex 명령 모드
| 명령 | 설명 |
|---------|---------|
| ctl +v   | 노말 블록 모드  |
| :q !  | 변경된 내용이 있는 경우라도 저장하지 않고 무조건 종료한다  | 
| :w   |  작업 중인 내용을 저장한다  |
| :q   | 종료한다 수정된 사항이 있으면 종료되지 않는다  | 
| :wq!   | 무조건 저장하고 종료한다  |
| :wq   | 저장하고 종료한다  | 
| e   | 지정한 '파일명'으로 새롭게 편집한다  |

#### 정규표현식 기호

| 식 | 설명 |  식 | 설명 |
|---------|---------|---------|---------|
| ^  | 행의 첫문자  | 	$  | 행의끝  |
| .  | 아무 문자나 한 문자를 의미  | \  | 	이어지는 문자 그대로 해석  |
| []  | []사이의 문자 중하나	  | \|  | 	or을 의미  |
| [^]  | 묶어진 문자를 제외한 아무거나  | \{min,max\}  | min이상 max 이하 반복됨  |
| *  | 앞의 내용이 0번 이상 반복됨  | 	\+  | 앞의 내용이 1번 이상 반복됨  |
| \<  | 단어의 시작  | \>  | 단어의 끝  |
| \n  | 개행 문자  | \t  | 탭문자  |
| %  | 처음 행부터 끝 행까지  | [a~z]  | a~z 까지 모든 소문자  |
| [AB]  | A 또는 B  | [A-Z]  | A~Z 까지 모든 대문자  |
| [0~9]  | 0~9까지의 모든 정수  | p[aeiou]t  | pat,pet,pit,pot,put 중 한단어  |


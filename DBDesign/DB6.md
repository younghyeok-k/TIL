## 폼마법사
--------------------------
#### Form
- 사용자와 테이블(또는 질의) 간의 인터페이스
- 폼 마법사 또는 폼 디자인을 통해 생성
#### 폼 마법사를 이용한 폼 생성([회원관리] 테이블)
- 만들기 → 폼 마법사
![image](https://user-images.githubusercontent.com/97229292/166345232-388dec3d-e3ee-4f81-b2cb-c7f87a1296af.png)

#### 단일 테이블([회원관리])에 연결된 폼 생성(방법 1)
- 기존 필드 추가 이용
![image](https://user-images.githubusercontent.com/97229292/166345371-8fed3006-dfca-4066-bba0-0825146ca6a6.png)

![image](https://user-images.githubusercontent.com/97229292/166348106-0ee52957-3b86-4434-b652-53c4915dd211.png)

#### 단일 테이블([회원관리])에 연결된 폼 생성(방법 2)
- 속성 시트 이용
- 컨트롤 추가 → 폼의 레코드 원본 지정 → 컨트롤의 컨트롤 원본 지정
![image](https://user-images.githubusercontent.com/97229292/166348276-eb037b24-93cd-4777-8143-8d76b661a854.png)
![image](https://user-images.githubusercontent.com/97229292/166380592-ceb87302-2763-411e-9723-19e1c44a6991.png)
#### 여러 테이블에 연결된 폼 생성(방법 1)
- 예) [학생신상] : (학번, 학과, 이름), [성적관리] : (과목코드, 점수)
 - 기존 필드 추가 이용
![image](https://user-images.githubusercontent.com/97229292/166383126-5ace9e5a-dcee-471b-ace8-7892f2274da9.png)
간단하지만 두 테이블 간 연결 조건이 일치(=) 조건일 때만 사용 가능
![image](https://user-images.githubusercontent.com/97229292/166389883-c611a962-b08a-4a5b-ade7-57c93efa6b6d.png)

#### 여러 테이블에 연결된 폼 생성(방법 2)
- 여러 테이블을 연결하는 쿼리 먼저 설계 (쿼리_학생_성적)
![image](https://user-images.githubusercontent.com/97229292/166389897-d1835e8b-627e-4268-b4ae-6dd855554936.png)
 - 속성 시트에서 폼의 레코드 원본을 이미 만들어 둔 쿼리로 지정(쿼리_학생_성적)
 - 기존 필드 추가에서 필드 지정
![image](https://user-images.githubusercontent.com/97229292/166390646-01c74058-53d3-4e46-8565-69b4ea5f779b.png)
### 컨트롤
- 폼에서 데이터의 입력, 출력, 매크로 및 폼 실행 등에 사용되는 객체
![image](https://user-images.githubusercontent.com/97229292/166390661-ee72ec13-9ce6-411d-b69f-10cb58ada6d4.png)

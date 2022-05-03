## 폼마법사
--------------------------
#### Form
- 사용자와 테이블(또는 질의) 간의 인터페이스
- 폼 마법사 또는 폼 디자인을 통해 생성
#### 폼 마법사를 이용한 폼 생성([회원관리] 테이블)
- 만들기 → 폼 마법사
![image](https://user-images.githubusercontent.com/97229292/166390711-6a763304-5d23-4cc2-8182-2d50b5b8768d.png)

#### 단일 테이블([회원관리])에 연결된 폼 생성(방법 1)
- 기존 필드 추가 이용
![image](https://user-images.githubusercontent.com/97229292/166390713-eb276f21-d197-4334-b882-a5ce48f2e6a4.png)

![image](https://user-images.githubusercontent.com/97229292/166348106-0ee52957-3b86-4434-b652-53c4915dd211.png)

#### 단일 테이블([회원관리])에 연결된 폼 생성(방법 2)
- 속성 시트 이용
- 컨트롤 추가 → 폼의 레코드 원본 지정 → 컨트롤의 컨트롤 원본 지정
![image](https://user-images.githubusercontent.com/97229292/166390722-7beb37ba-cc22-4cfc-a89c-ee7e115316aa.png)
![image](https://user-images.githubusercontent.com/97229292/166380592-ceb87302-2763-411e-9723-19e1c44a6991.png)
#### 여러 테이블에 연결된 폼 생성(방법 1)
- 예) [학생신상] : (학번, 학과, 이름), [성적관리] : (과목코드, 점수)
 - 기존 필드 추가 이용
![image](https://user-images.githubusercontent.com/97229292/166390747-65416d56-4186-4df6-86ca-9165ac2e13dd.png)
간단하지만 두 테이블 간 연결 조건이 일치(=) 조건일 때만 사용 가능
![image](https://user-images.githubusercontent.com/97229292/166389883-c611a962-b08a-4a5b-ade7-57c93efa6b6d.png)

#### 여러 테이블에 연결된 폼 생성(방법 2)
- 여러 테이블을 연결하는 쿼리 먼저 설계 (쿼리_학생_성적)
![image](https://user-images.githubusercontent.com/97229292/166390758-c8e08f9a-22f3-485e-b733-a3e2ca1f33a8.png)
 - 속성 시트에서 폼의 레코드 원본을 이미 만들어 둔 쿼리로 지정(쿼리_학생_성적)
 - 기존 필드 추가에서 필드 지정
![image](https://user-images.githubusercontent.com/97229292/166390763-a55409f3-a9c3-4c53-a7ce-8421c94c5184.png)
### 컨트롤
- 폼에서 데이터의 입력, 출력, 매크로 및 폼 실행 등에 사용되는 객체
![image](https://user-images.githubusercontent.com/97229292/166390771-23106474-81ef-4fcf-acd7-68107393333c.png)

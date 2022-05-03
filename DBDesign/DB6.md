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

![image](https://user-images.githubusercontent.com/97229292/166391581-fb71eba5-bcf4-4694-a42a-8014d302718e.png)

![image](https://user-images.githubusercontent.com/97229292/166391586-1ef1125c-f927-43c7-9518-5b0518ce2037.png)
#### 체크 박스
- Yes / No 타입의 필드와 연결하여 사용
- 기존 필드 추가로 Yes / No 필드 추가 시 자동으로 체크 박스가 생성됨
- 예) [이력서] 테이블의 취업여부 필드
![image](https://user-images.githubusercontent.com/97229292/166391606-43a7b15f-9f2c-40c6-b518-ce407375472a.png)
#### 토글 버튼
- 체크 박스와 동일한 기능 수행
- Yes / No 필드와 연결하여 사용
- 예) [이력서] 테이블의 취업여부 필드
  - 폼의 레코드 원본을 [이력서]로 연결
  - 토글 버튼 컨트롤 추가
  - 컨트롤 원본으로 취업여부 필드 연결
  - 
![image](https://user-images.githubusercontent.com/97229292/166393106-d63cc369-f2a9-4002-94c5-c62f3cc80d83.png)

![image](https://user-images.githubusercontent.com/97229292/166391674-46e9a7b1-de62-4ecf-aef4-2261187e3757.png)
#### 옵션 버튼
- 여러 항목 중 하나의 항목만을 선택할 때 사용
- 무엇들 중 하나를 선택해야 하는지 범위 지정 필요
 - 옵션 그룹 생성 → 옵션
- 예) [이력서] 테이블의 성별 필드
  - 남자 = 0, 여자 = 1
  - 컨트롤 마법사를 사용하여 옵션 그룹 생성
![image](https://user-images.githubusercontent.com/97229292/166393720-8627f86b-a36e-4d6d-9fe5-37e8dca31bbe.png)


![image](https://user-images.githubusercontent.com/97229292/166393772-321d916c-dc45-43cd-88a3-78ed4e7ef8e5.png)

- [간략학생정보] 테이블에 대해 다음의 폼을 작성하시오.   
등록여부 : Yes / No   
학생구분 : 1(재학생), 2(졸업생), 3(휴학생)   


![image](https://user-images.githubusercontent.com/97229292/166393973-cbcaa882-e943-4ab5-9ce3-3c6471079a10.png)

#### 콤보 박스
- 리스트 박스 + 텍스트 박스의 형태
- 미리 정의된 리스트로부터 입력값을 선택하거나 직접 입력할 수 있는 컨트롤
- 리스트 정의
 - 기존의 테이블 또는 쿼리 사용 OR  컨트롤 생성 시 새로 지정
 - 예) [직종분류] 테이블의 직종 필드에서 값을 받아서 [이력서] 테이블의 직종분류 필드에 저장
![image](https://user-images.githubusercontent.com/97229292/166394019-b13d158b-3049-44a6-9a8d-b41549f9022f.png)



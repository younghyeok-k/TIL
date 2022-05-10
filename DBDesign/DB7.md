
### week7
----------------
### 첨부 파일
- 각 레코드에 이미지, PDF 등 다양한 파일 연결 가능
- 하나의 레코드에 다수의 첨부 파일을 연결할 수 있음
- 예) [학생신상] 테이블에 취미 필드 추가 → 축구, 야구, 농구 등 사진을 첨부 파일로 연결

![image](https://user-images.githubusercontent.com/97229292/167518053-4a829f5a-bbb1-4738-9c73-7cf70e242aba.png)

### 탭 컨트롤
- 업무상 관련된 여러 폼을 하나의 틀에서 관리
![image](https://user-images.githubusercontent.com/97229292/167518326-1a39a4f1-0cbf-4618-b740-58139aefa9d4.png)


### 언바운드 컨트롤(Unbound Control)
 - 테이블 / 쿼리의 필드와 연결되지 않은 컨트롤로, 값을 저장하지 않고 일시적으로 사용할 때 사용됨
 - 예) [가계부] 테이블에서 “증감“을 계산하여 저장없이 출력하는 경우
    - 속성 시트에서 컨트롤의 형식을 “통화＂로 지정
![image](https://user-images.githubusercontent.com/97229292/167518867-699106b8-53c9-4298-ac67-672b48b95740.png)

함수를 사용한 언바운드 컨트롤
- D. I. Y.) [가계부] 테이블과 연결하여 “규모” 필드를 추가한 폼을 생성하시오.
 - 수입 또는 지출의 금액이 5만원 초과인 경우 “고액“, 그렇지 않은 경우 “소액“ 출력
![image](https://user-images.githubusercontent.com/97229292/167519663-8c0810f1-067d-42a8-83fc-006ded40be20.png)


#### =IIf(Abs([지출]-[수입])>=50000,"고액","소액")


### Functions
![image](https://user-images.githubusercontent.com/97229292/167519757-56123f95-7496-4007-b80e-623ef6aea040.png)

### 컨트롤 배치
- 정렬 → 맞춤,  크기 / 공간 활용

![image](https://user-images.githubusercontent.com/97229292/167520356-44572fa1-fc93-477f-bbed-68955156f4b4.png)

![image](https://user-images.githubusercontent.com/97229292/167520318-f7fa2fc0-df32-4c62-ab18-8f6af84f8490.png)

### (D. I. Y.) [선수] 테이블에 대해 다음의 폼을 작성하시오.
- 배경 이미지, 특수 효과, 팝업 설정, 시작 폼 설정 등 적용 (뒷 페이지 참고)

![image](https://user-images.githubusercontent.com/97229292/167520555-2c9b39c1-eaf1-450f-b54d-490831636258.png)


![image](https://user-images.githubusercontent.com/97229292/167520943-6b19a42b-8158-4a3f-a615-b6a1d1075c9c.png)

![image](https://user-images.githubusercontent.com/97229292/167521072-d2ec4f35-c2d6-401a-bdd4-d3774eacc915.png)

### 기타 디자인 요소
- 배경 이미지
  - 형식 → 그림 → 파일 지정
  - 형식 → 그림 크기 조정 모드 → 원래 크기로
 
- 특수 효과
   - 각 컨트롤에 대해 마우스 우클릭

- 팝업 설정
     - 기타 → 팝업 → 예
     - 형식 → 탐색 단추 → 아니오(탐색 바 제거)

- 시작 폼 설정
     - 파일 → 옵션 → 현재 데이터베이스 → 폼 표시 → 폼 지정

### 분할 표시 폼
 - 폼과 테이블의 내용을 동시에 확인
 - 형식 → 기본 보기 → 분할 표시 폼
 - 형식 → 분할 표시 폼 방향

→ 데이터 시트를 아래쪽에


![image](https://user-images.githubusercontent.com/97229292/167521292-96f79364-95cf-4966-9e33-5a73bebecac9.png)
![image](https://user-images.githubusercontent.com/97229292/167521337-d28c05c6-1483-4c0d-849b-fbe49b6616d3.png)
![image](https://user-images.githubusercontent.com/97229292/167521390-f7614dfa-7247-455b-be1c-c455cb78fc04.png)

### 명령 단추의 기능
- 레코드 작업
  - Search, Insert, Delete 등
- 폼 작업
  - Open, Close, Relaod, Print 등
- 기타 작업
  - OpenQuery, MessageBox 등

- 이벤트 작성기를 통해 기능 정의 가능



 ### [이력서] 테이블로부터 [간략정보] 폼 생성
- “새 레코드 추가“ 버튼 생성 (컨트롤 마법사 사용)
- “레코드 삭제“ 버튼 생성 (컨트롤 마법사 사용)
![image](https://user-images.githubusercontent.com/97229292/167522541-34cc0795-8e28-428f-8fd3-8a967786d1df.png)
![image](https://user-images.githubusercontent.com/97229292/167522887-2d4661b0-4c91-4698-897e-2b8a6c7a1362.png)

### [학생신상폼] 에서 [성적관리폼] 열기
- [학생신상] 테이블로부터 [학생신상폼] 생성
- [성적관리] 테이블로부터 [성적관리폼] 생성
- [학생신상폼] 에서 [성적관리폼] 을 연결하는 명령 단추 생성

![image](https://user-images.githubusercontent.com/97229292/167523011-0620a020-acae-4e1c-a052-0fda5e1bb429.png)

![image](https://user-images.githubusercontent.com/97229292/167523121-bb1cce6b-3663-4457-b881-e67e136821d4.png)
![image](https://user-images.githubusercontent.com/97229292/167523125-d15e2bed-feed-43b8-812f-98108fa0926f.png)

### 매개변수를 이용한 폼 열기
- 간단한 방법 (Equal 조건만 적용 가능)

![image](https://user-images.githubusercontent.com/97229292/167524142-c4a8a214-1755-40d6-9162-9ab4d96f7cbd.png)

 - 복잡한 방법 (모든 조건 적용 가능 → 쿼리를 미리 생성함)
![image](https://user-images.githubusercontent.com/97229292/167524180-1427848d-f273-497b-aeb0-0ef1e80d61f4.png)
- [학번입력폼] 의 “신상조회“ 명령 단추 생성 (컨트롤 마법사 사용)
![image](https://user-images.githubusercontent.com/97229292/167524213-d9b79e7b-d87b-47ca-aded-c679661a04bd.png)

- 최종 결과
![image](https://user-images.githubusercontent.com/97229292/167524232-b11efc15-e878-47e7-933b-f961e2824b78.png)

### D. I. Y. – Very Difficult !!!
- 매개변수로 학번을 입력 받아서, 해당 학생보다, 같거나 늦게 태어난 모든 학생의 정보를 출력하시오
 ![image](https://user-images.githubusercontent.com/97229292/167525077-8825daf5-7b7a-430f-be64-74c22e769754.png)

### Hint) 다음의 순서로 생성
- 기준학번입력폼
 - 학번 입력 용 텍스트 상자 생성
- 생년월일조회쿼리
 - 해당 학번 학생의 생년월일 조회
- 신상조회쿼리
 - 위의 생년월일보다 같거나 이후 조회
- 학생조회폼
 -신상조회쿼리 연결
- 기준학번입력폼 수정

폼 열기 버튼으로 학생조회폼 연결
![image](https://user-images.githubusercontent.com/97229292/167527154-960301b3-3e87-40b8-9081-f17534e7d403.png)
### 하위 폼
- 연결된 폼을 새 폼이 아닌 기존 폼 내부에서 사용
- 예) [학생신상] 테이블의 하위 폼으로 [성적관리] 테이블을 연결
![image](https://user-images.githubusercontent.com/97229292/167527183-cf03dcb5-d91a-4bee-b26c-92bf4ede40aa.png)
### D. I. Y.
- [학생신상] 테이블과 [성적관리] 테이블을 활용하여 다음의 폼을 완성하시오.
![image](https://user-images.githubusercontent.com/97229292/167527201-a13f9e3b-3cc0-4e7f-b339-2b68079bb4a2.png)

### D. I. Y.
   - 학번과 점수를 입력 받아서, 해당 학생이 해당 점수 이상 취득한 과목을 조회하는 폼을 생성하시오.
   - [학생신상] 테이블과 [성적관리] 테이블을 활용
![image](https://user-images.githubusercontent.com/97229292/167527217-313799fb-a239-41d9-a8ae-aaacd639c453.png)
![image](https://user-images.githubusercontent.com/97229292/167528052-6ef63791-a18e-4751-a1db-70986ce61747.png)
### D. I. Y.
- 고객 ID와 대여 기간을 입력 받아서, 해당 고객이 해당 기간 중 대여한 DVD 의 내역을 조회하시오.
  - 대여 기간은 rent-Date 기준
- [tblCust] 테이블과 [tblRent] 테이블 활용
![image](https://user-images.githubusercontent.com/97229292/167528260-d961be39-002c-4105-bdcd-f6648aa33d3b.png)


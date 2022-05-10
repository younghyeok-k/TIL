
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
![image](https://user-images.githubusercontent.com/97229292/167523033-747b0ff4-36c9-40f5-8158-766b8f312f7f.png)
![image](https://user-images.githubusercontent.com/97229292/167523051-59e8bba6-60d5-4702-9a97-5b56be774442.png)




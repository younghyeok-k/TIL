# week5

## 매개변수 쿼리 ([도서목록관리] 테이블)
----------------------------------------
```
   - Q) 문자열을 입력받아, 해당 문자열이 저자명 또는 도서명에 포함된 도서를 출력하는 쿼리를 작성하시오.
      Like "*" & [키워드] & "*" or Like "*" & [키워드] & "*"
```

### 선택 쿼리
#### -단순조회 쿼리
       select
#### -요약 조회 쿼리
       집계함수(Group By)

### 실행 쿼리(수정or 갱신) 쿼리
#### -스키마 변경
       create TABLE
       Drop Table,Alter Tabler(다루지 않음)

#### -인스턴스 변경
     Insert,Update,Delete

## 테이블 생성
--------------------------

####  - 테이블 명은 전체 DB에서 유일해야 함
####  - 일반적으로 테이블은 [만들기] → [테이블] 에서 생성 가능
####  - 기존 테이블을 활용하여 새로운 테이블을 생성하는 경우 → 쿼리 사용




## 레코드 추가
----------------------
#### - 기존의 테이블에 새로운 레코드를 추가(삽입)
#### - 기본키가 중복되는 레코드는 추가 불가
 - Ex) [학생신상] 테이블에서 생년월일이 기준 날짜와 같거나 그 이후인 학생만 [학생신상_생년월일] 테이블에 추가

![image](https://user-images.githubusercontent.com/97229292/163900425-259c9375-6816-48cf-9862-08b8171a3c0e.png)
![image](https://user-images.githubusercontent.com/97229292/163900509-e211fcee-4708-424a-ade5-8f9cd97bfec4.png)

 ### 사용자 입력 + 기존 테이블 값의 추가
 #### - 사용자 일부 값을 입력하고, 이 값에 대응되는 다른 정보를 기존 테이블로부터 가져옴
 #### - Q) [장학생명단] 테이블에 새로운 값을 추가하는 쿼리를 작성하시오.
```
[장학생명단] 테이블의 필드는 다음과 같음
학번, 학과, 이름, 수혜연도, 수혜학기
[학번입력], [수혜연도입력], [수혜학기입력]만 매개변수로 입력받음
학과, 이름은 [학생신상] 테이블에서 가져옴 (학번을 조건으로 비교)
(필요시) 입력 순서는 매개변수 메뉴에서 편집 가능
Ex) 매개변수가 (02027, 2011, 2)인 경우, “전산”, “박희은＂은 자동으로 입력됨
```


![image](https://user-images.githubusercontent.com/97229292/163900214-3b654fca-1e78-49c7-8b17-e0a686d3a50c.png)
Ex) [비디오목록관리] 테이블에서 장르가 “호러” 또는 “스릴러“ 인 비디오의 등급을 “18세＂로 변경하시오.
![image](https://user-images.githubusercontent.com/97229292/163900291-fe0a4776-c772-4b64-a50a-ab1ac0a1eda4.png)

![image](https://user-images.githubusercontent.com/97229292/163900261-5f102028-89fc-49c0-8a33-a80b3482f36e.png)

Ex) [도서목록관리] 테이블에서 2007년 2월 1일부터 나온 모든 책의 소비자 가격을 10% 인상하시오
[소비자가격]=[소비자가격]*1.1
![image](https://user-images.githubusercontent.com/97229292/163900943-559b04d3-c5b8-47e0-a5ac-c014c507087c.png)

Ex) 과목 키워드와 교수명을 매개변수로 입력받아서, 해당 키워드를 포함하는 과목의 담당교수를 입력받은
![image](https://user-images.githubusercontent.com/97229292/163901596-f3e65766-ce65-4124-8442-d2b656075420.png)


## 레코드 삭제
------------------------
#### - 테이블에 존재하는 레코드를 삭제함
#### - 조건을 설정하지 않으면 전체 레코드가 삭제됨


Ex) [도서목록관리] 테이블에서 소비자 가격이 10,000원 미만인 모든 도서를 삭제함
![image](https://user-images.githubusercontent.com/97229292/163901851-79abd853-66af-40ee-928c-4190e352aba9.png)

Ex) [사용후기] 테이블에서 금칙어를 매개변수로 입력받아, 해당 카워드를 포함하는 제목의 글을 삭제하시오
![image](https://user-images.githubusercontent.com/97229292/163902045-665c1788-4da3-4941-a1f3-1a9216f234a2.png)



## 요약 쿼리
------------------------------------------------
#### - 합계, 평균, 최대, 최소, 개수 등의 통계치 생성
#### - SQL의 GROUP BY 명령어에 해당

Ex) [학생신상], [성적관리] 테이블에서 학과별 / 학사상태별 중간고사 평균 조회
![image](https://user-images.githubusercontent.com/97229292/163902851-426b6895-fb54-4fbd-8245-06ecdf1eae07.png)

## Sub-Query
------------------------------------------------
#### - 다른 쿼리의 내부에 포함된 쿼리
![image](https://user-images.githubusercontent.com/97229292/163902898-dd50be78-517f-44fb-be8f-5c5e7cc6753b.png)


##### Motivating Example ([학생신상] 테이블)

Ex) 학번이 “05454” 인 학생보다 이후에 태어난 학생의 학번, 이름, 생일을 출력하시오.
학번이 “05454” 인 학생의 생년월일은? → “1986-02-01”
“1986-02-01” 이후에 태어난 학생의 학번, 이름, 생일은?


![image](https://user-images.githubusercontent.com/97229292/163903314-737b0cf0-028b-4005-bebf-bb3dcf53f390.png)

![image](https://user-images.githubusercontent.com/97229292/163903718-bb58d1ee-569c-494a-8253-74f65ffed331.png)


#####  - Sub-Query를 이용하여 하나의 쿼리로 구성하는 경우
##### - Sub-Query 를 먼저 생성한 후, 이를 포함하여 Main Query를 생성함
- 
![image](https://user-images.githubusercontent.com/97229292/163903936-4ea525ec-225a-42aa-9988-084a0c3998ca.png)

![image](https://user-images.githubusercontent.com/97229292/163904500-04b395d8-4563-4bb9-8d2a-c4d2f7189df2.png)


Ex) [학생신상], [성적관리] 테이블을 이용하여, 중간고사의 평균을 소수점 둘째자라까지 나타내시오.

중간요약: Round([중간평균]![중간고사의평균],2)
![image](https://user-images.githubusercontent.com/97229292/163905831-3d4befad-6691-4481-8e8b-187d162f1a4b.png)


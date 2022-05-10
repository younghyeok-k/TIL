
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

### 기타 디자인 요소
-배경 이미지
 - 형식 → 그림 → 파일 지정
 - 형식 → 그림 크기 조정 모드 → 원래 크기로
 
- 특수 효과
 - 각 컨트롤에 대해 마우스 우클릭

- 팝업 설정
    - 기타 → 팝업 → 예
    - 형식 → 탐색 단추 → 아니오(탐색 바 제거)

- 시작 폼 설정
    - 파일 → 옵션 → 현재 데이터베이스 → 폼 표시 → 폼 지정





관계형 데이터 모델

table  :행과 열의 2차원 구조를 가진 데이터 저장 객체
    -관계형 데이터모델에서는 relation 릴레이션과 대응된다

Column :테이블에서 세로방향으로 이루어진 개별 속성
   -관계형 데이터모델에서는 Attribute 애트리뷰트 와 대응된다

row:테이블에서 가로방향으로 이루어진 연결된 데이터
  -관계형 데이터모델에서는 Tuples 튜플 과 대응된다


관계형 데이터모델 제약조건

1) 도메인 제약
-속성 값은 원자성을 가지며,도메인에서 정의된 값이어야 한다
-Composite Attribute(복합 속성)와 Multivalued Attribute(다중)는 허용되지 않는다
- Null 값은 허용됨

2) 키제약 
-릴레이션의 모든 튜블은 서로 식별이가능해야한다

3)개체 무결성 제약
-기본키 (PK) 는 UNIQUE & NOT NULL 이어야 함


4) 참조 무결성 제약
외래키 (FK:Forign Key)
 - 릴레이션 R1 이 릴레이션 R2를 참조하는 경우 ,R2의 기본키는 R1에서 외래키로 사용됨
   -NULL 이거나
   -아닌경우R 2에 실제로 존재하는 값으로 구성되야한다


ER – to – Relational Model 변환 규칙

     - step 1 : Mapping of Strong Entity Types

     - step 2 : Mapping of Weak Entity Types

     - step 3 : Mapping of Binary 1:N Relationship Types

     - step 4 : Mapping of Binary 1:1 Relationship Types

     - step 5 : Mapping of Binary M:N Relationship Types

     - step 6 : Mapping of N-ary Relationship Types

     - step 7 : Mapping of Multivalued Attributes

-------------------------------------
      Mapping of Strong Entity Types(독자적으로 존재 → 강한 개체 타입)
      -    각   strong entity E에 대응되는 릴레이션 R을 생성함
      - E의 키 속성 중 하나를 선택하여 R의 기본키(Primary Key)로 정함
	
     Mapping of Weak Entity Types(조직에서 부양가족 : 직원의 존재에 의존 → 약한 개체 타입)
      ER 모델에서 약한 개체는 독립적으로 존재할 수 없고 Owner Entity Type에 종속적입니다.
     그런데 관계 모델로 변환할 때는 약한 개체를 독립된 Relation으로서 작성해야 합니다.
     
     Mapping of Binary 1:N Relationship Types    
     각 Binary 1:N Relationship RS에 대해, 
     이 Relationship에 참여하는 두 entity를 각각 S(N-side)와 T(1-side)라고 하면
      T의 기본키를 S의 외래키로 포함  RS에 속한 모든 simple attributes를 S에 포함시킴
      이렇게해야 null 이 덜생긴다


     Mapping of Binary 1:1 Relationship Types
     Relation Type에 해당하는 릴레이션을 생성하지 않는다.
     원래 Relation Type에 있어야 할 Attribute들을 관계를 맺는 두 릴레이션 중 한쪽으로 합쳐버립니다.
     합칠 때 null이 적게 생기는 경우를 선택하여 합칩니다.
     그냥 둘다 외래키로 만들어서 하나로 합쳐서  attributes 를 넣는다

   
     Mapping of Binary M:N Relationship Types
    각 M:N 관계 RR에 대해서 새로운 relation U를 만든다.
    U에 참여하는 entity type들의 PK를 U의 FK로 넣는다.
     FK의 모음이 U의 PK가 된다. 그리고 U에 M:N 관계의 atribute를 추가하면 된다.
    
    N-ary Relationship Types
    새로운 relation U를 만들어서 관계에 참여하는 relation들의 PK를 FK로 두고
    N-ary 관계의 attribute를 추가한다.

    Mapping of Multivalued Attributes
   각 multivalued attribute A에 대해 새 relation U를 생성하고, 
   A의 attibute와 U를 소유하는 entity type의 PK를 FK로 넣는다. U의 PK는 {A, FK}{A,FK}가 된다


-----------------------------------------

일반화(generalization) 계층

- A ISA B 라고 선언하면, A개체는 모두 B개체로도 볼 수 있다.

문제점 
  Redundant Information in Tuples(중복정보)
    - update후에 중복 값이 서로 다른 값을 갖을 수 있다

    속성들을 관계 스키마로 그룹핑한다. : 저장 공간에 의미있는 영향을 미친다.

 - update anomalies에 따라서 기본 관계의 자연 조인을 저장한다.
 - update anomalies의 타입 : 삽입, 삭제, 수정 ( 공간낭비 + 이상현상 발생 )
 - 관계에서 업데이트 이상현상이 없도록 하기 위한 base relation schemas를 디자인 해라.
 - 어쩔 수 없이 생긴다면 명확하게 note해야 한다. (de-normalization 할 때)


이런한 문제점으로 해결하기위해

3NF Normaliztion (제3 정규화)
한 테이블을 쪼개 각각 따로 관리하여 이상현상의 영향도를 줄이는 것이라 생각하면 될 것 같습니다.


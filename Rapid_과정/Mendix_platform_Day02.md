

## 1. 마이크로플로우 

- Commit
  - 데이터베이스에 저장한다.
- Refresh
  - 
- Retrieve







## 2. Object EventHandler

- Object Events
  - Created
  - Committed
  - Deleted
  - Rolled Back(저장하기 전으로 취소한다는 의미)
- Event Handler
  - before
  - after
- 설정위치
  - 엔티티에서 설정(도메인모델)
- Micorflow Naming
  - Prefix_Entity_Operation
  - Prefix
    - Create
      - ACR(만든 후 상태로)
      - BCR(만들기 전 상태로)
    - Commit
    - RollBack
    - Delete



## 3. Security(보안)

- 유저의 권한에 따라서 액세스 할 수 있고 없고를 정하기 위한 보안사항
- End User
  - User Role
  - Module Role

1. App Security에서
   - Production 모드로 전환하고 UserRole 정리/생성
2. UserManager Module Security에서
   - Module Role을 정리/생성
   - Module Role 별 페이지, 마이크로프로우, 나노플로우 액세스 체크
   - 엔티티 액세스 관리
3. App Security에서
   - User Role 탭에서 User Role과 Module Role이 연결돼야하는지를 지정할수 있다
4. 세부 사항 조정
   - 버튼이나 텍스트 창같은 경우는 Role based 조건을 사용하여 Visibillity를 통해서 세부 사항 조정 가능



## 4. XPath 

- 왜 XPath를 사용하는가
  - Mendix가 데이터와 상호작용할 때 도메인 모델을 탐색하는데 사용
  - 상호작용할 때 데이터베이스의 데이터흐름을 제어하는데 사용
  - 데이터의 양을 조절하기 위해 (원하는 데이터만 사용할 수 있게)

- XPath vs Microflow, Expression
- Expression
  - 코딩할때 처럼 문장을 작성하는 작업



- XPath를 사용하는 곳
  - XPath Constraint라는 레이블이 지정된 창
    - 페이지
      - Data Saurce
    - 참조 선택기
      - Reference Selector
      - Reference Set Selector
    - 마이크로플로우
      - Retrieve
    - 보안
      - Access to Entity



- 사용 방법
  - 참조 문법
    - //모듈.엔티티/속성
    - //모듈.엔티티/Association/엔티티
    - 연결 안된 엔티티는 가져올 수 없다.
  - 토큰
    - // : 시작
    - [] : 제약조건
    - / : 엔티티 다음, Association 다음
    - () : 우선순위



- Tab Container
  - 데이터가 어떻게 컨트롤이 되는지 보기위한 위젯



## 4. 앱 빌드

1. 사용자 스토리를 살펴보고 우선 순위를 지정하여 시작하는데 가장 유용한 것이 무엇인지 확인한다.

2. 사용자 스토리를 완료하려면 다음 작업이 필요

   1. 정보를 볼 수 있는 페이지에 액세스할 수 잇는 홈페이지가 있어야 한다

   2. 홈페이지 레이아웃을 조정한다

   3. 버튼을 추가한다

   4. 버튼에 링크될 페이지를 추가한다

   5. 시스템의 정보를 표시하는 이 페이지에 버튼을 연결한다.

      

- 열 만들기
  - Navigation Layout
  - 레이아웃 그리드
    - 페이지의 구조 또는 레이아웃을 구축하는데 사용하는 위젯
    - 행은 세로로 표시되고 각 행은 행에서 가장 큰 열만큼 세로 공간을 차지한다
  - 컨테이너 및 위젯
    - 다양한 종류의 위젯을 추가하여 페이지 콘텐츠를 구축할 수 있다.
    - 위젯을 컨테이너 안에 배치한다
      - 위젯을 그룹화 할 수 있다.
      - 일관된 스타일을 지정할 수 있다.
      - 페이지에서 간격 및 정렬을 할 수 있다.



- 페이지 만들기

  - 버튼을 만들고 실제로 어딘가로 연결되도록 한다.

  - 루트 데이터에 대한 페이지를 만들고 버튼을 해당 페이지에 연결한다.

  - 페이지 제목

    - 각 단어는 대문자로 시작해야한다.
    - 여러 단어는 밑줄로 구분한다. (공백을 사용하면 오류)

    

- 일관성 오류 분석
  - 검사 상태를 보고 오류가 뜨면 화면 하단의 패널에 해결해야할 오류에 대한 정보가 표시된다
  - 오류 메시지를 읽고 오류의 원인을 찾아가고 싶으면 오류글을 더블클릭 하면 된다.



## 5. 엔티티 

- 앱에 데이터를 표시하려면 목록 보기를 엔티티에 연결해야한다.
- 속성
  - 엔티티에 대한 정보의 종류를 결정한다
  - 데이터 유형을 정한다.
  - 종류
    - AutoNumber
      - 자동으로 생성된 양수 또는 음수인 정수
    - Binary
      - 바이너리 데이터
    - Boolean
      - 참 or 거짓
    - Decimal
      - 소수점 이하 자릿수를 가질 수 있는 양수 또는 음수
    - DateTime
      - 날짜 및 시간 구성 요소로 구성된 특정 시점으로 밀리초까지 정확
    - Enumeration
      - 미리 정의된 값 목록
    - HashString
      - 암호화 되어 저장된 문자열 
    - Integer
      - 정수
    - Long
      - 범위가 큰 정수
    - String
      - 문자, 공백, 숫자 및 기타 문자가 포함된 텍스트
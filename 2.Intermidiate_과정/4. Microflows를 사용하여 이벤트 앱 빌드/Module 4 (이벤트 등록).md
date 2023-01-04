# Module 4 (이벤트 등록)



### 익명 사용자 (Anonymous user)

- 온라인 상점과같은 로그인이 필요하지 않은 콘텐츠를 보여주기 위해 사용
- App security의 Anonymous user탭에서 설정할 수 있다.
  - 여기서 익명을 사용할건지와 user role을 정해줄 수 있다.
- 익명 사용자를 활성화 할 경우 익명 사용자 역할에 대한 역할 기반 홈페이지를 추가해줘야한다.



### 변수 (Variables)

- 마이크로플로우를 만들 때 여러 변수를 사용하게 된다
- 단일 객체, 객체 목록, 기본 값으로 존재할 수 있다.
  - 단일 객체
    - 도메인 모델의 엔티티에 의해 정의된 엔티티의 단일 인스턴스
    - 생성, 변경, 삭제
    - 목적 - 데이터 저장
  - 객체 List
    - 특정 엔티티의 객체 List
    - 생성, 변경(설정, 추가)
    - List 기능
      - List 집계(sum, average, count, minimum, maximum)
      - List 연산(union, intersect, subtract, contains, equals, sort, filter, find, head, tail)
    - 목적 - 객체 List로 작업 수행
  - 기본 변수
    - 다른 value type일 수 있다 : Boolean, date and time, decimal, enumeration, integer/long, string
    - 목적 - 마이크로플로우 로직 내에서 사용하기 위한 값의 임시 저장
- 마이크로플로우의 변수는 달러기호($)로 표시되고 변수이름이 그 뒤에 온다.
- 변수는 마이크로플로우의 반환 값으로 사용될 수도 있다.



### 토큰 (Tokens)

- 특별한 type의 변수이다.
- Exclusive Splits 또는 XPath Constraints에서처럼 마이크로플로우에서도 사용할 수 있는 시스템 생성 값이다.
- 사용할 수 있는 토큰이 여러 개 있고 대부분이 DateTime과 관련됐다.
- DateTime과 관련 없는 유일한 토큰은 Current User 토큰이다. 
  - 이 토큰에는 현재 사용자 객체의 ID가 포함되어 있다.
  - ex) [%CurrentDateTime%]'를 사용하여 현재 순간(밀리초 단위)을 식별할 수 있으며, '[%CurrentUser%]'를 사용하여 현재 사용자 ID에 액세스할 수 있다.



### 마이크로플로우 표현식 및 함수

- Decision의 표현식에 boolean 뿐만 아니라 enumeration를 사용하여 enumeration 값에 따라 조건 수가 다양해 진다.

- 마이크로플로우 표현식 사용하는 곳

  - Split conditions

  - Create and change object actions

  - Create and change of variables

  - Output of end events

  - Arguments for parameters (Java Actions, sub-microflow calls, etc.)

    

- Functions

  - Arithmetic Expressions
    - \* div + -
  - Relational Expressions
    - < > = !=
  - Special Checks
    - empty, isNew
  - Boolean Expressions
    - and, or, not
  - Differentiation
    - if, then, else
  - Mathematical
    - max, min, round, etc.
  - String
    - toUpperCase, find, substring, etc.
  - Date/Time
    - dateTime, addDays, etc.
  - Parse/Format
    - parseFloat, formatDateTime, etc.



### Formatting and Parsing

- DateTime 입력이 Mendix에서 사용하는 것과 다른 형식인 경우 Formatting and Parsing을 사용할 수 있다.
- Formatting은 날짜를 텍스트로 변환하고 Parsing은 텍스트를 날짜로 변환한다.
  - formatDateTime과 parseDateTime이라는 함수를 사용한다.





### 익명 User Roles 생성

1. App Security에서 Anonymous라는 User Role을 만든다.
2. 익명 사용자 택으로 이동하여 허용을 예로 설정하고 User Role를 선택해준다.
3. 익명이 사용할 사용자 정의 홈페이지가 없어서 자동으로 기본 홈으로 대체되어 보안에서 허용되지 않아서 오류가 발생하기 때문에 권한을 주어야한다.
4. 익명에 관한 페이지들을 만들어주고 보안을 설정해준다.



### 마이크로플로우 디버깅

- Studio Pro에는 기술적 오류가 있는지 확인하는 consistency checker가 내장되어 있다.
- 앱이 기능적으로 예상대로 작동하는지 확인하기 위해 Mendix는 디버거 도구를 제공한다.
- 디버거란?
  - 디버거를 사용하면 애플리케이션 실행을 일시중지하고 앱 변수의 상태와 마이크로플로우가 변수에 대해 작동하는 방식을 검사할 수 있다.
  - 디버거를 사용하면 Mendix 클라우드나 다른 원격 서버에서 실행되는 애플리케이션을 원격으로 디버그할 수도 있다.



### 객체 롤백


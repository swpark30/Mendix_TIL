# Module 4 (더 복잡한 제약 조건 사용)



### UserRole 시스템 변수

- UserRole을 사용하여 계정을 제한할 때는 토큰에 대한 XPath 변수와 열거형으로 XPath를 구성할 때 플랫폼이 제공할 수 있는 지원이라는 두 기술을 결합한다
- 보안 탭에서 UserRole을 생성 하면 플랫폼은 XPath를 구성할 때 사용할 수 있는 System Variable을 자동으로 생성한다.
- 이 변수에는 [%UserRole_Manager%]와 같이 UserRole의 이름이 포함된다.
- 변수는 XPath가 시스템 모듈 연결이 System.UserRole에서 끝나는 경우에만 자동 완성으로 나타난다.



### XPath 함수

- 플랫폼에는 XPath 내에서 여러 함수들이 있다.
- String manipulation (문자열 조작)
  - contains(), string-length(), end-with()와 같은 함수를 사용
  - ex) [contains(Description, 'emergency')]는 설명 속성에 'emergency' 문자열이 포함된 모든 VacationRequests 목록을 반환한다.
- DateTime manipulation (DateTime 조작)
  - year-from-dateTime()이나 weekday-from-dateTime()을 사용
  - ex) [year-from-dateTime(StartDate)=2020]은 2020에 StartDate가 발생한 모든 VacationRequests 목록을 반환한다.
-  Boolean expressions (Boolean 표현식)
  - true()나 false()에 대한 
  - ex) [IsLocalUser=true()]는 Boolean 속성인 IsLocalUser가 true로 설정된 모든 계정 목록을 반환 한다.



### 함수와 연산자를 사용한 제약

- 1단계 : 관리자용 승인 워크플로우 추가

  1. VacationRequest_NewEdit 페이지를 열고 저장 버튼 옆에 마우스 오른쪽 클릭하여 위젯 추가를 선택한다.
  2. call microflow를 누르고 이름이 ACT_VacationRequest_Approve인 새로운 마이크로플로우를 만든다.
  3. 버튼이 생성되면 더블클릭하여 속성창을 열고 이름을 Approve로 바꾼다.
  4. 마이크로플로우 창으로 넘어가서 Change Object activity를 사용하여 vacationRequest의 status를 Approved상태로 바꿔준다
  5. Close page activity를 추가해준다.
  6. 마이크로플로우 창에서 오른쪽클릭하여 속성을 선택한다.
  7. Security 섹션에서 Allowed roles를 manager로 설정하여 액세스 권한을 준다.

- 2단계: 홈 페이지에 새 탭 추가

  - 승인된 휴가 요청이 표시될 탭을 추가한다.

  1. Home_web을 연다.
  2. 기존에 있는 Submitted 탭을 마우스 오른쪽 클릭하여 오른쪽 탭 페이즈 추가를 선택한다.
  3. 새 탭을 더블 클릭하여 이름을 Approved this year로 바꿔준다.

- 3단계: 열거형, 변수 및 연산자를 사용하여 데이터 제한

  - 사용자가 올해 승인된 휴가 요청을 보고 싶을때

  1. 데이터 그리드의 데이터 소스를 XPath로 설정하고 XPath를 작성한다.
  2. New 와 Edit 버튼에 대한 오류 수정하기
     1. New 버튼을 삭제한다.
     2. Edit 버튼의 페이지를 VacationRequest_NewEdit으로 설정한다.



### empty values 확인

- 지금까지 특정필드의 값을 확인하여 XPath 제약 조건을 걸었지만 값이 할당되지 않은 엔티티를 찾을 때는 더 복잡해진다.
- empty
  - 속성이나 연결에 값이 없는 경우 플랫폼은 여전히 비어 있는 값을 사용하여 이를 확인할 수 있다.
  - ex) VacationManagement.VacationRequest[Status=empty]
  - 이 XPath는 상태에 할당된 값이 없는 목록을 반환한다.
- not()
  - empty 체크 외에도 플랫폼에는 조건이 충족되지 않는지 확인하는 메커니즘이 있고 not() 함수가 그것이다.
  - 이 함수는 연산자와 속성을 사용하여 생성된 표현식을 평가하는데 사용할 수 있다.
  - ex) VacationManagement.VacationRequest[not(StartDate>'[%BeginOfCurrentDay%]')]
  - 이 XPath는 시작 날짜가 오늘 이후가 아닌 모든 목록을 반환한다. 즉, 오늘 이전에 발생한 모든 휴가 날짜를 의미
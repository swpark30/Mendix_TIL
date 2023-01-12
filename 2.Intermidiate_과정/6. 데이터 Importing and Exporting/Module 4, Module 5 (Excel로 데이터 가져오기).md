## 4. Excel로 데이터 가져오기



- Excel Importer 모듈을 Marketplace에서 다운받아서 넣는다.
- 그러면 오류가 많이 생기는데 
- Marketplace에서 Mx Model Reflection을 다운 받아서 넣어주면 오류가 사라진다.
- 두 모듈에 대해 보안 적용을 해준다.





## 5. 데이터를 REST 서비스로 가져오기



- 사용하려면 새로운 개념을 도입

  - JSON 구조
    - JSON 조각을 저장하고 Import 매핑 및 Export 매핑에서 사용할 수 있는 스키마 구조로 변환하여 JSON 콘텐츠를 Mendix 객체나 그 반대로 변환한다.
  - Import 매핑
    - 들어오는 XML 또는 JSON이 특정 XML 스키마 또는 JSON 구조에 따라 Mendix 객체로 변환되는 방식을 정하는데 사용
    - 다른 시스템에서 받은 데이터를 해석하는데 필요
  - HTTP 헤더
    - REST 호출에서 메타 데이터를 전달하는데 사용된다.
    - 입증
      - 사용자 이름 + 비밀번호
    - 기타 HTTP 헤더
  - REST 서비스 활동 호출
    - REST 엔드포인트를 호출하는데 사용
    - 일반적으로 Import 매핑을 사용하여 REST 호출의 응답을 처리해야 하는 위치와 방법을 지정할 수 있다.

  

- REST 서비스를 사용하여 데이터 가져오기

  1. JSON 구조 만들기
  2. Import 매핑 생성
  3. REST 가져올 주소를 상수로 만들어 준다.
  4. REST 호출을 실행하고 데이터를 가져오기 위한 마이크로플로우 작성
     1. REST 호출을 만든다.
     2. REST 호출 General 탭에서 Location에 상수를 적용해준다.
     3. HTTP 헤더 탭에서 HTTP 인증 사용을 체크해준다.
     4. User name과 Password를 정해준다.
     5. Response 탭에서 Apply import mapping을 선택한다.
     6. Mapping을 선택한다.
     7. 확인을 누르고 REST 창을 닫는다
  5. 마이크로플로우 보안을 정해준다.
  6. 데이터그리드에 마이크로플로우를 부를 버튼을 생성하고 연결해준다.




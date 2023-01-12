## 6. REST 서비스로 데이터 노출



- Mendix에서 REST 서비스를 게시하려면 새로운 개념이 필요
  - Message Definitions
    - 앱과 주고받는 메시지를 정의한다.
    - 메시지를 정의하면 해당 메시지에 대한 Import 및 Export 매핑을 만들 수 있다.
  - Export 매핑
    - 도메인 모델 엔티티에 저장된 Mendix 객체를 XML 또는 JSON문서로 변환하는데 사용된다.





- Published REST 서비스 추가 
  1. Published REST Service를 추가한다.
  2. REST Service를 열고 Connector창에서 원하는 엔티티를 찾아서 Resource 섹션에 넣는다
  3. 창이 하나 뜨고 원하는 속성을 정해주고 확인을 누르면 자동으로 필요한 리소스를 모두 생성한다.
  4. 서비스 설명 페이지를 열고 싶으면 만들었던 Published REST Service에 들어가면 위에 주소가 있다.



## 7. Excel로 데이터 내보내기



- Excel을 사용하여 데이터를 내보내는 가장 간단한 방법은 데이터 그리드에서 (Excel로 내보내기 버튼)을 사용하는 것
  - 제한사항
    - 데이터 그리드에 액세스 할 수 있는 데이터만 내보낼 수 있다.
    - 내보낼 데이터를 조작할 수 없다.
    - 데이터 그리드에 XPath 데이터 소스가 있는 경우에만 Excel로 내보내기 버튼을 사용할 수 있다.
  - 사용방법
    1. 데이터 그리드 소스를 XPath로 변경한다.
    2. 그리드 컨트롤 바를 오른쪽 클릭하고 Export to Excel 버튼을 추가한다.
    3. 웹에서 버튼을 클릭하여 다운이 되는지 확인한다.
- Excel Exporter module 사용
  - 사용해야하는 상황
    - 데이터 그리드에 XPath 이외의 데이터 소스를 사용할 때
    - List view 또는 template grid가 있는 페이지에 Excel로 Export 버튼을 만들고 싶을 때
    - Export하기 전에데이터를 조작하고 싶을 때
    - 더 복잡한 방식으로 데이터를 내보내고 싶을 때
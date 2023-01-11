# Module 4 (추가 사용자 추가)



### Cross Module Associations

- 멘딕스에서 일반적으로 기능레벨에서 수행되는 여러 모듈로 앱을 나눌 수 있다.
- 앱을 만들때 이미 System, Administration, MyFirstModule 세가지 모듈은 항상 있다.
  - System 모듈
    - 앱을 실행하게 하는 것으로 모든 앱이 필요로 하는 기본 데이터 구조 (사용자, 파일, 세션 등)을 포함한다.
    - 이 모듈은 액세스되지 않는다.
  - Administration 모듈
    - 사용자가 계정을 갖고 관리할 수 있도록 하는 모듈
  - MyFirstModule  모듈
    - 앱 빌드를 시작하는 모듈
- 모듈 간 연결을 생성하여 다른 모듈의 데이터를 연결할 수 있다.
- 플레이어가 계정을 가지길 원할때 Player엔티티에서 Account로 교차 모듈 연결을 만들면 가능하다.
  - 사용 방법
    - 교차모듈연결을 사용할 엔티티의 속성창을 열고 Associations 탭을 연다
    - New를 눌러 Marketplace modules의 Administration의 Account를 클릭하여 연결을 추가한다.
    - 연결을 오른쪽 클릭하면  Go to other side라는 옵션이 나오고 그걸 누르면 Account가 있는 도메인 모델로 이동한다.
- 다른 모듈과 연결 하는 또 다른 방법은 하나의 엔티티가 다른 모듈의 엔티티에 상속되도록 하는 것인데 이건 Advenced 난이도에서 배울 예정이다.



### System Members

- 데이터베이스에 저장할 수 있는 객체에 대한 정보
- 저장할 수 있는 4가지 System Members
  - createdDate (만든 날짜)
    - 객체가 생성된 날짜 및 시간
  - changedDate (수정 날짜)
    - 객체가 마지막으로 변경된 날짜 및 시간
  - owner (소유자)
    - 객체를 만든 사용자
  - changedBy (변경자)
    - 마지막으로 객체를 변경한 사용자
- 기본적으로 이 정보들은 데이터베이스에 저장되지 않는다.
  - 객체가 많으면 이 정보가 실제로 필요하지 않고 데이터베이스를 복잡하게 만들 필요가 없기 때문에
- 엔티티 속성창에서 System Members 중 하나 이상을 저장하도록 선택이 가능하다.
- 보안 적용을 하지 않아도 owner System Members를 사용하여 객체를 만든 사용자만 객체의 세부 정보들을 변경할 수 있도록 할 수 있다.


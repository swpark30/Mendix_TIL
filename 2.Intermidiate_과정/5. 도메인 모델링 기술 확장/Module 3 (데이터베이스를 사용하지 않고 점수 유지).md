# Module 3 (데이터베이스를 사용하지 않고 점수 유지)



- 목표 - 경기중에 점수를 유지하고 나중에 데이터베이스에 저장할 수 있도록 하는 기능을 구축
  - 이 기능을 구축하기 위해 non-persistable entity를 사용할 것이다.



### Persistable Entities

- 지속가능한 엔티티로 객체를 데이터베이스에 저장할 수 있는지 여부를 정한다.
- 엔티티가 지속 가능하다고 선언되면 이 엔티티에 대한 데이터베이스 테이블이 생성된다. 이러한 엔티티의 인스턴스를 커밋하면 테이블에 행이 추가된다. 이 인스턴스에 저장된 속성 및 연관 정보도 데이터베이스에 저장된다.
  - (지금까지 항상 Persistable Entities를 사용하여 저장할 수 있는 정보로 작업했다.)



### Non-Persistable Entities

- 데이터베이스에 저장할 수 없으므로 연결된 데이터베이스 테이블이 없다.

- 커밋하는 것은 가능하지만 현재 속성 값과 연결 값만 데이터베이스가 아닌 메모리에 저장한다. 세션이 끝나면 정보는 삭제된다.

- ##### Transient objects

  - 객체가 생성되면 메모리에만 존재하고 이것을 일시적 객체라고 한다.
  - 객체가 생성되면 AutoNumber 유형의 속성이 있는 경우의 정보 검색을 제외하고 데이터베이스에 액세스할 수 없다.
  - Non-Persistable Entities에는 데이터베이스 테이블이 없으므로 AutoNumber  특성도 가질 수 없다.

- ##### Non-persistable associations

  - Non-Persistable Entities와 Persistable Entities간에 연결을 만들 때 연결의 소유권은 항상 Non-Persistable Entities쪽에만 있어야 한다.

- Persistable Entities의 색상은 파란색이고 Non-Persistable Entities의 색상은 주황색이여서 여부를 쉽게 인식 가능하다.



- 제한 사항

  - 도메인 모델에 대한 유효성 검사 규칙을 가질 수 없다.
  - 인덱스를 가질 수 없다. 
    - (둘다 데이터베이스 기능이므로)

  

- 사용하는 이유

  - 트랜잭션에 연결된 프로세스 데이터이거나 법적으로 저장할 수 없는 민감한 정보를 데이터베이스에 커밋할 수 없어야 하기 때문이다.
  - Persistable Entities로도 커밋을 안하면 되는데 이렇게 하면 잊어버리기 쉬워 문제가 될 수 있고 데이터베이스에 불필요한 테이블을 만들어서 데이터베이스가 더러워지기 때문이다.

  

- 사용 방법

  - 똑같이 엔티티를 만들고 Persistable만 no로 바꿔주면 된다.



### calculated attribute

- 도메인 모델에서 정하고 액세스하는 순간 값을 얻는다.
- 속성 값은 선택한 마이크로플로우를 사용하여 결정한다.
- 이 값은 데이터베이스에 존재하지 않기 때문에 데이터베이스를 쿼리할 때 직접 사용할 수 없다.
- 모든 retrieve나 List retrieve의 행별로 실행되므로 calculated attribute의 사용을 최소화하는 것이 좋다.
  - 정보가 사용자에게 표시되거나 마이크로플로우에서 사용될 때마다 마이크로플로우가 값을 계산하기 위해 트리거 되기 때문이다.
  - List view에 calculated attribute를 표시할 때 앱의 성능이 저하될 수 있다.
- derived 값이 변경될 때 이벤트핸들러를 사용하여 새 derived 값을 자동으로 커밋하여 최대한 데이터베이스에 저장하려고 해야한다.
- 값이 자주 변경이 된다면 calculated attribute을 사용하는게 좋다.
- 도메인 모델에서 calculated attribute은 이름 뒤에 작은 마이크로플로우 아이콘으로 식별할 수 있다.
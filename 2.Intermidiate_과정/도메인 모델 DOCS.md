# 도메인 모델 DOCS



- Mendix 앱은 모듈로 구성되어 있다.
- 모듈은 앱의 기능을 별도의 부분으로 나누는 단위 (자바의 class같은 느낌)
- 각 모듈에는 고유의 도메인 모델이 있다.
- 도메인 모델은 애플리케이션 도메인의 정보를 추상적인 방식으로 설명하는 데이터 모델이다. (애플리케이션 아키텍쳐의 핵심)



### 구성 요소

- Studio의 도메인 모델은 2가지로 구성된다

  - Entity
    - 실제 객체의 클래스를 나타낸다.
    - 엔티티는 속성을 가질 수 있다.
      - 속성 - 엔티티를 설명 및 식별한다.
  - associations
    - 엔티티 간의 관계를 설명한다.

- 다양한 유형의 엔티티

  - 이미지 엔티티

    - 이미지를 저장할 수 있는 특수한 엔티티
    - 사용자는 이미지를 보고 업로드할 수 있다.

  - 파일 엔티티

    - 파일을 저장할 수 있는 특수한 엔티티
    - 사용자는 텍스트문서나 pdf같은 파일들을 업로드나 다운로드를 할 수 있다.

  - 외부 엔티티

    - 조직에 대해 Data Hub 기능이 활성화된 경우에만 사용할 수 있다.

    

| Element                | Displays                                                     |
| ---------------------- | ------------------------------------------------------------ |
| Annotation             | 도메인 모델을 설명하는 주석                                  |
| Entity Name            | 엔티티가 데이터베이스에서 참조되는 이름                      |
| Event Handler(s)       |                                                              |
| Image                  | An image which helps to identify the entity                  |
| Validation Rule(s)     | An indication that one or more [validation rules](https://docs.mendix.com/refguide/validation-rules/) have been set up for this attribute |
| Calculated Value       | An indication that the value of this [attribute](https://docs.mendix.com/refguide/attributes/) is calculated |
| One                    | Indicates that one of this entity relates to the quantity of the entity at the other end of the association |
| Association Name       | How the [association](https://docs.mendix.com/refguide/associations/) will be referred to in the database |
| Many                   | Indicates that many of these entities relate to the quantity of the entity at the other end of the association |
| Association Owner      | An end of an association without an arrow indicates that this entity [owns](https://docs.mendix.com/refguide/associations/#ownership) the association (it is also possible for both entities to own the association) |
| Attribute Name         | How this attribute will be referred to in the database       |
| Attribute Type         | The [type](https://docs.mendix.com/refguide/attributes/#type) of data stored in this attribute |
| Non-persistable Entity | 데이터베이스에 저장되지 않고 앱 내에서 일시적으로만 저장되는 엔티티입니다. |



### 엔티티 유형 

-  external entity
  - 데이터 허브를 통해 다른 애플리케이션의 데이터를 사용할 수도 있다.
  - 도메인 모델에서 보라색 엔티티 컨테이너로 표시된다.

- Persistable entity
  - 엔티티에 대한 데이터베이스 테이블이 생성된다.
  - 엔티티는 파란색으로 표시된다.
- Non-persistable entity
  - 런타임 메모리에 저장되고 데이터베이스에 커밋되지 않는다.
  - 엔티티는 주황색으로 표시된다.



### 엔티티 속성

- Access rules
- Documentation
  - 앱 내에서 엔티티를 사용할 때 본인 또는 다른 구성원에게 유용한 엔티티의 측면을 설명할 수 있다.
- General
  - name
    - 엔티티의 이름을 정한다
    - 모듈 도메인 모델 내에서만 고유해야한다.
    - 서로 다른 모듈의 도메인 모델에 있는 경우 이름이 같은 엔티티를 가질 수 있다.
  - Export Level
    - 추가 기능 및 솔루션 모듈에만 사용할 수 있다.
    - 엔티티가 Hidden으로 설정된 경우 속성이 표시되지 않고 숨겨져 Usable로 설정할 수 없다.
    - 추가 모듈 또는 솔루션을 개발할 때 소비자 측에서 이 문서에 대한 액세스 레벨을 정할 수 있다.
  - Generalization (일반화)
    - 특정 엔티티가 속성을 파생하는 엔티티를 지정하는 것이다.
    - 객체 지향 프로그래밍(OOP)에서는 이런 일반화를 상속이라고 부른다.
    - 이 기능의 중요한 용도 중 하나는 시스템 모듈에서 기능을 파생시키는 것이다.
  - Image
    - 이미지 속성을 사용하여 엔티티를 이미지와 연결할 수 있다.
    - 도메인 모델에서 이미지는 엔티티의 오른쪽 상단 모서리에 시각화 된다.
  - Persistable
    - 엔티티의 인스턴스를 데이터베이스에 저장할 수 있는지 여부를 정의한다.
- System members
  - Store createdDate 
    - 엔티티에 시스템 속성 createdDate가 포함되어 있는지 여부를 정한다.
    - 객체를 생성할 때 서버에 의해 자동으로 생성된다.
  - Store changedDate
    - 객체가 변경된 가장 최근 날짜와 시간을 저장
  - Store owner
    - 객체를 생성한 사용자에 대한 참조를 저장하는 시스템 엔티티 User에 대한 연결이다.
  - Store changedBy



### Persistable

- 엔티티의 지속 가능 속성을 나타내며 객체를 데이터베이스에 커밋할 수 있는지 여부를 정하는 것이다.
- 엔티티에 대한 데이터베이스 테이블이 생성된다.
- 객체를 커밋하면 테이블에 행이 삽입되고 객체의 속성 및 연결 값도 데이터베이스에 저장된다.
- 자동 커밋된 객체
  - 롤백은 마지막 커밋 이후의 메모리 변경 사항을 되돌린다.
  - 지속 가능한 자동 커밋 객체 또는 상태가 "NEW"인 객체에 대해 롤백을 수행하면 연결된 엔티티의 데이터베이스에서 이 객체의 행을 삭제한다.



### Non-Persistable

- 런타임 메모리에 저장되고 데이터베이스에는 커밋되지 않는다.
- 데이터베이스에 테이블이 없고 이러한 유형을 검색하는 유일한 방법은 연결을 통한 것이다.
- 이 엔티티를 커밋하면 현재 속성 값과 연결 값이 메모리에 기록되고 롤백이 이러한 값으로 되돌아갈 수 있다.



### Generalizations

- 일반화 엔티티의 특수화인 엔티티를 사용하는 경우 데이터베이스 유니크 유효성 검사를 사용할 수 없다.



### navigatability (탐색 가능성)

- Reference 세트의 Owner 속성에 해당한다.
- 연결을 추가하거나 변경할 때만 중요하다.
- 하나의 객체 소유자를 연결로 지정해도 소유자가 아닌 쪽에서 연결을 읽는 것을 방지할 수는 없다.
- 단방향 탐색 가능한 연결
  - 부모에서 자식으로의 한 방향으로만 연결된 엔티티에 대한 탐색을 허용하는 연결
  - 이런 연결은 일반적으로 외부 공급자 또는 Mendix Data Hub를 통해 외부 엔티티에서 OData 서비스 통합에 의해 도입된다.
  - 단방향 탐색 가능성의 주요 의미는 제약 조건 및 쿼리와 같은 XPath 사용 사례와 관련 있다.
  - 도메인 모델 편집기에서 점선 화살표로 표시된다.
  - 양방향인 다른 도메인 모델 연결에서 데이터를 검색할 수 있다.


































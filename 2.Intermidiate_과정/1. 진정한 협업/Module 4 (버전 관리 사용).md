# Module 4 (버전 관리 사용)

- Mendix가 사용하는 버전 관리 도구는 TortoiseSVN이다.
- 이 도구를 사용하면 특정 이전 버전으로 되돌릴 수 있다.



### 버전 제어 레포지토리에 앱 업로드

- Mendix에서 새 앱을 시작하면 시스템에서 자동으로 앱용 레포지토리 생성을 제안한다.
- 아직 버전 제어를 받지 않은 앱은 나중에 버전 제어 레포지토리에 연결할 수 있다.
  - 이 경우 Mendix의 메뉴중 Version Control 아래에 있는 Upload to Version Control Server를 클릭하면 업로드 된다.



### History

- 앱 히스토리에서는 지금까지 앱에 적용된 변경 사항을 볼 수 있다.
- Mendix 개발자 포털에서 Team Server로 이동하면 4가지 유형의 이벤트를 볼 수 있다.
  - commit
  - Created tags
  - Created branch lines
  - Deleted branch lines
- Studio Pro내에서 Version Control > History... 로 이동하면 2가지 유형의 이벤트가 있다.
  - The revision number
  - A symbol, indicating the type of change



### Snapshots 포함

- 멘딕스에는 로컬 배포에 사용할 수 있는 자체 기본 데이터베이스가 있다.
- Studio Pro를 통해 데이터 스냅샷을 만들려면 버전 제어 메뉴(Version Control >  Add a snapshot of your data)로  이동해야한다.
- 이렇게 하면 데이터의 스냅샷이 생성되고 zip 파일 (data-snapshot.zip)이 앱의 배포 디렉토리에 추가 된다.
- 다음에 커밋할 때 지정된 배포 폴더에서 이 데이터베이스의 압축을 풀어 전체 팀이 이 데이터베이스를 사용할 수 있다.



### Conflicts and Resolve (충돌과 해결)

- 팀원이 동일한 문서에서 작업한 경우 Studio Pro는 다운로드한 문서 버전과 로컬에 저장된 문서 버전간에 충돌을 식별한다.
- Pro는 충돌 없이 변경 사항을 커밋하기 때문에 커밋하기 전에 충돌을 해결해야 한다.
  - 처음에는 새로 업데이트된 버전과 로컬 앱 버전 간의 차이점을 식별한다.
  - 충돌하는 문서를 변경한 팀원과 연결하고 어떤 버전을 사용해야 하는지 결정한다.
  - 충돌하는 문서의 두 버전을 모두 보려면 Studio Pro에서 자체 문서 사본을 만들고 'Resolve using theirs'를 선택하면 된다.
- 충돌을 일으킬 수 있는 변경 유형
  - 수정 - 수정 충돌
    - 본인과 다른 팀원이 정확히 동일한 문서를 수정했을 때 발생한다.
  - 수정 - 삭제 충돌
    - 누군가 제거한 요소를 변경할 때 발생한다.
  - 이 외에도 동일한 이름의 문서를 추가, 동일한 AppStore 모듈을 가져올 때 충돌이 발생할 수 있다.
- 충돌을 방지할 수 있는 방법
  - 팀 구성원과 합의하는 것
  - 정기적인 업데이트 및 커밋을 수행
  - 작업을 분리한다.
  - 모든 스프린트에서 도메인 모델 기반을 마련



### 이전 버전 열기

- 모델의 두 개정 사이의 차이점을 식별하기 위해, 라이브 환경에서 게시된 개정을 디버그하기 위해 이전 버전을 열 필요가 있다.
- 이전 버전을 열려면 해당 버전에서 branch를 생성해야 한다.
- 보거나 분석 목적으로만 이 branch를 사용하고 이 branch이후에 많은 커밋이 있으므로 변경하면 안된다.



### 브랜치 사용

- 브랜치를 사용하면 실행 중인 앱에 영향을 주지 않고 기능 개발을 계속할 수 있다.
- branch를 사용하여 얻을 수 있는 가능성

  - branch 만들기
  - 변경 사항 Merge
    - 포트 수정 
      - branch 라인 중 하나에서 메인 라인으로 특정 부분을 이동할 수 있는 옵션을 제공한다.
    - Merge feature branch (병합 기능 브랜치)
      - 전체 branch를 메인라인에 병합하는데 사용되며 메인라인에서만 사용할 수 있다.
      - 이 병합 작업을 시작하려면 Pro 메인라인을 열고 메뉴의 Version Control > Merge Changes Here을 누른다.
        - 병합하기 전에 메인라인에서 모든 변경 사항을 커밋해야 한다.
    - Advanced merge 
      - 고급 병합 옵션을 사용하면 메인 라인 또는 branch라인의 다양한 개정을 각각 선택한 유형의 라인에 병합할 수 있다.
  - Reverse merge changes (역병합 변경)
    - 경우에 따라 이전 버전의 앱으로 돌아가 변경 사항을 되돌려야 한다.
    - 변경 사항을 되돌리는데 사용할 시작 버전과 종료 버전을 지정해야 한다.
    - 한 번에 여러 커밋을 롤백할 수도 있지만 단일 커밋만 되돌리도록 선택할 수도 있다.
  - Delete a branch 
    - branch가 병합된 후 지정된 branch라인을 삭제할 수 있다.



### 자체 SVN 서버 사용

- 멘딕스는 팀 서버를 활성화할 때 SVN 환경의 프로비저닝을 관리한다.
- 앱 배포 디렉터리를 저장할 수 있다.
  - 이렇게 하려면 먼저 자체 SVN 서버를 설정해야한다.
  - 메뉴에서 Edit > Preferences > Version Control > Enable private version control에서 개인 버전 제어를 활성화 해야 한다.




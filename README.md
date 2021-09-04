## 01. Git 이 무엇인가..?!   
  - **버전 관리를 도와주는 시스템**이다.
  - **Git의 동작 방식**
    - 커밋에서 발생하는 차이들만 저장하는 것이 아니라, 커밋된 파일 전체인 스냅샷을 저장한다.
    - 바뀌지 않은 파일은 이전 파일의 링크만 저장하기 때문에, 용량을 많이 잡아먹지 않고, 계산도 필요 없다.
  - **.git 파일 내부에 저장되어 있는 정보**
    - 원격저장소의 주소
    - 버전 관리한 데이터 등..

## 02. Git 상태/공간 뜯어보기

![git_4status](https://user-images.githubusercontent.com/59442344/110064253-154cc180-7db0-11eb-8eb8-78387c2dc354.jpg)

  - **Git/GitHub으로 구분되는 4가지 공간.**
    - **작업 공간(WorkSpace)**
    - **로컬저장소(.git) 스테이지(stage**)
    - **로컬저장소(.git) commit저장소**
    - **원격저장소(GitHub)**   
 
  - **Git으로 관리하는 파일의 4가지 상태**
    - **추적 안됨 (untracked)** / 로컬저장소에 올라간 적 없음 : WorkSpace에서 작업 중인 파일.
    - **추적 됨 (tracked)** / 로컬저장소에 올라간 적 있음
      - **스테이지됨 (staged)** : WorkSpace에서 Stage로 올라온 파일. (선택된 파일)
      - **수정없음 (unmodified)** : commit된 내용과 WorkSpace에 존재하는 내용에 차이가 없는 파일
      - **수정함 (modified)** : staged되지 않고, commit된 내용과 WorkSpace에 존재하는 내용에 차이가 존재하는 파일

## 03. Git file (System/Global/Local file) 
  - **System 설정 파일** : 전체 system 사용자에게 적용된다.
    - git config --system 명령어
  - **Global 설정 파일** : 한 사용자의 전체 git 저장소에 적용된다.
    - git config --global 명령어
  - **Local 설정 파일** : 하나의 저장소에만 적용된다.
    - git config --local 명령어

## 04. Git 협업


## 05. Git 용어   

  - **원격 저장소 (repository)** : GitHub에서 협업할 공간. (다른 개발자들과 같이 버전관리할 공간.)
  - **로컬 저장소** : 내 컴퓨터에서 Git으로 버전관리 중인 공간
    - 특정 폴더 내의 숨겨진 .git 폴더가 바로 로컬 저장소 이다.
    - CLI 환경에서는 git init 이라는 명령어를 통해서 .git 폴더 생성됨
    - GUI 환경에서는 +create 이라는 아이콘을 통해서 .git 폴더 생성됨 
    - .git 폴더에 원격저장소의 주소, 버전 관리 데이터 등의 필요한 정보를 저장.
  - **Git** : 버전 관리 시스템
  - **GitHub** : Git을 통해 관리하는 프로젝트를 올려두는 공간
  - **GUI** : Graphic User Interface, 마우스로 명령 입력
  - **CLI** : Command Line Interface, 커멘드 라인으로 명령어 입력
  - **Git Bash** : CLI 방식으로 Git을 이용하게 해주는 환경
  - **commit** : 버전을 갱신하는 것, 새로운 버전으로 생성된 파일
  - **log** : 모든 commit 확인
  - **checkout** : 원하는 지점의 버전으로 파일을 되돌릴 수 있다.
  - **push** : 로컬 저장소 -> 원격 저장소로 commit을 올리는 것.
  - **pull** : 원격 저장소 -> 로컬 저장소로 commit을 내려받는 것.
  - **branch** : 특정 버전 위치를 가리키는 포인터이다.
  - **master** : Git이 제공하는 기본적인 branch 이름, 보통 로컬저장소의 버전 상태를 가리킨다.
  - **origin** : 원격 저장소의 닉네임.
    - $git remote add **origin** " ... " : 원격 저장소의 닉네임을 origin으로 저장하라는 git 명령.
    - **origin / master** : 보통 원격저장소의 버전 상태를 가리킨다.
  - **head** : 커밋들을 자유롭게 가리킬수 있는 포인터이다. head 포인터를 통해서, branch를 넘나들 수 있다.


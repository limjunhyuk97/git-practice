# Let's study Git, GitHub!

## Git 이 무엇인가..?!   
  - **버전 관리를 도와주는 시스템**이다.
  - **Git의 동작 방식**
    - 커밋에서 발생하는 차이들만 저장하는 것이 아니라, 커밋된 파일 전체인 스냅샷을 저장한다.
    - 바뀌지 않은 파일은 이전 파일의 링크만 저장하기 때문에, 용량을 많이 잡아먹지 않고, 계산도 필요 없다.

## Git 작업 뜯어보기

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

## Git 용어   

  - **원격 저장소 (repository)** : GitHub에서 협업할 공간. (다른 개발자들과 같이 버전관리할 공간.)
  - **로컬 저장소** : 내 컴퓨터에서 git으로 버전관리 중인 공간
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

## CLI Git Command

 - **$ git init**
   - git 로컬 저장소 생성
   - .git 폴더 생성
   - git으로 버전관리를 시작할 폴더를 지정

  - **$ git config --global user.email "...@....com"**
    - 버전관리를 위한 내 이메일정보 등록

  - **$ git config --global user.name "jun hyuk lim"**
    - 버전관리를 위한 내 이름 정보 등록

  - **$ git add ...**
    - ... 파일을 커밋에 추가

  - **$ git commit -m " ... "**
    - add한 파일에 ...의 설명을 추가해서 commit
    - commit은 버전의 생성
    - -m 은 message를 의미함
    - -m 을 통해서 설명을 잘 적어두어야 후에 버전 관리 (수정, 개선)에 용이함

  - **$ git log**
    - log 명령어는 최신 커밋부터, 여태까지의 커밋 내용을 보여준다

  - **$ git checkout (특정 버전의 커밋 아이디)**
    - 특정 버전의 커밋 아이디는 log 명령어를 통해서 확인할 수 있다.

  - **$ git checkout -b  " ... "**
    - 현재 커밋(버전)에서 새로운 " ... "설명 브랜치를 생성한다.

  - **$ git checkout -**
    - 가장 상위 버전으로 head를 이동시킨다.
    - 가장 상위 버전에 head가 위치할때는 바로 이전 버전으로 head를 이동시킨다.

  - **$ git remote add origin " ...(GitHub 리포지토리 주소) "**
    - 로컬 저장소에 원격 저장소(GitHub)의 주소를 알려준다.

  - **$ git push origin master** -> GitHub 계정 입력 후 동기화
    - 원격 저장소로 git으로 관리한 버전내용(commit)들을 push 함

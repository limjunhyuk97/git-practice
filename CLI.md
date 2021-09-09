# Git with CLI

## CLI Git Command

### git init

 - **$ git init**
   - git 로컬 저장소 생성 (또는 초기화)
   - .git 폴더 생성
   - git으로 버전관리를 시작할 폴더를 지정

### git config
  - 깃에 대한 설정을 추가, 변경, 삭제하는 명령어 이다.

  - **$ git config --global user.email "...@....com"**
    - 버전관리를 위한 내 이메일정보 등록

  - **$ git config --global user.name "jun hyuk lim"**
    - 버전관리를 위한 내 이름 정보 등록

### git add

  - **$ git add ...**
    - ... 파일의 커밋을 위해 변경된 사항을 반영하여 stage에 추가
    - git add -A : 모든 tracked, untracked change 들을 stage로 올린다.

### git commit   

  - **$ git commit -m " ... "**
    - add 명령어로 stage로 올린 파일에 대해서, 로컬 저장소의 commit 저장소에 저장
    - commit은 버전의 생성
    - -m 은 message를 의미함
    - -m 을 통해서 설명을 잘 적어두어야 후에 버전 관리 (수정, 개선)에 용이함

  - **$ git commit -a**
    - 변경된 사항들에 대해서 전부 commit 저장소에 저장

### git log
  - 이전 commit들을 모두 둘러볼 수 있게 해준다.

  - **$ git log**
    - log 명령어는 최신 커밋부터, 여태까지의 커밋 내용을 보여준다

### git checkout
  - 이전 commit으로의 버전 변경을 가능하게 한다.

  - **$ git checkout (특정 버전의 커밋 아이디)**
    - 특정 버전의 커밋 아이디는 log 명령어를 통해서 확인할 수 있다.

  - **$ git checkout -b  " ... "**
    - 현재 커밋(버전)에서 새로운 " ... "설명 브랜치를 생성한다.

  - **$ git checkout -**
    - 가장 상위 버전으로 head를 이동시킨다.
    - 가장 상위 버전에 head가 위치할때는 바로 이전 버전으로 head를 이동시킨다.

### git push

  - **$ git push origin master** -> GitHub 계정 입력 후 동기화   
    - 원격 저장소로 git으로 관리한 버전내용(commit)들을 push 함

### git pull / fetch
  - 'git init' -> 'git remote add origin ...' 를 수행한 다음에 원격 저장소의 내용을 끌어올 수 있다.
  - pull : 원격저장소의 소스를 가져오고, 해당 저장소의 소스가 더 최신버전이라면 지금의 버전을 해당 버전에 맞춰 올린다.
  - fetch : 단지 소스를 가져올 뿐 merge 하지는 않는다

  - **$ git pull origin<원격 저장소명> master<branch명>**
    - 원격저장소에서 fetch 명령어로 가져온 뒤, merge까지 한번에 수행하여 실제 파일의 내용이 변경되는 명령어
  - **$ git fetch origin<원격 저장소명>**
    - fetch 명령어를 통해서 변경된 내용을 가져온다.


### git diff
  
  - **$ git diff HEAD origin/master**
    - git fetch 수행 후에, 원격 저장소에서 받아온 상태와 로컬 저장소의 상태가 어디서 다른지 확인할 수 있다.

### git clone

  - **$ git clone (리포지토리 주소)**   
    - 원격 저장소의 리포지토리에 있는 내용들을 로컬 저장소(워킹 디렉토리)로 끌어온다.
    - mac 환경에서, clone하여 저장할 로컬저장소에서의 위치를 먼저 지정해주어야 한다.
    - clone하면 자동으로 origin이라는 이름이 원격 저장소의 별칭으로 생성된다.

### git remote 

  - **git remote -v**
    - 해당 로컬 리포지토리와 연결되어있는 remote 저장소의 단축이름과 주소URL을 알 수 있다.

  - **$ git remote add origin ...(GitHub 리포지토리 주소)**
    - 로컬 저장소에 원격 저장소(GitHub)의 주소를 알려준다.
    - 즉, 로컬 저장소(워킹 디렉토리)에 새로운 원격 저장소를 추가한다.
# Source Tree

## Source Tree란?
  - Git을 통한 버전관리를 GUI 환경에서 도와주는 프로그램

## Source Tree 사용
  - Visual Studio Code에서 편집, 생성, 수정한 항목들을 git bash의 CLI 환경에서 관리하는 것처럼, source tree를 통해서 GUI 환경으로 관리할 수 있다.

![History](https://user-images.githubusercontent.com/59442344/110058817-6e175c80-7da6-11eb-96ea-088c9c463357.jpg)

  - **History** : branch에 commit한 내용들을 GUI 환경에서 깔끔하게 보여줌
  - **origin** : origin은 원격 저장소의 닉네임.
    - $git remote add **origin** " ... " : 원격 저장소의 닉네임을 origin으로 저장하라는 git 명령.
  - **origin / master** : origin / master은 원격저장소의 버전
  - **master** : master은 현재 내 로컬저장소에서의 버전, 우리가 commit 올리는 줄기의 이름.

![clone_add_create](https://user-images.githubusercontent.com/59442344/110057915-cb121300-7da4-11eb-824e-3a2f34ba0d71.jpg)

  - **Clone** : 원격 저장소를 내 컴퓨터에 받아오고(로컬 저장소 자동으로 생성, .git 파일의 자동 생성), 소스트리에도 추가함.
  - **Add** : 로컬 저장소를 소스트리에 추가
  - **Create** : 내 컴퓨터의 특정 파일에 로컬 저장소 생성(.git 파일의 생성, git init 과 동일)

![commit_before_add](https://user-images.githubusercontent.com/59442344/110058581-e9c4d980-7da5-11eb-8def-f99a70133f59.jpg)
![commit](https://user-images.githubusercontent.com/59442344/110057828-9f8f2880-7da4-11eb-9ba9-6f61b3fa3f67.jpg)

  - **스테이지에 올라가지 않는 파일 [+]** : git add ... 의 특정 파일 선택과 동일, (스테이지에 올라가지 않은 파일 -> 스테이지 올라간 파일)로 파일 선택.
  - **밑에 메시지 작성 박스** :  git commit -m  " ... " 의 메시지 작성과 같다.
  - **커밋** : 로컬 리포지토리(master branch)에 커밋함

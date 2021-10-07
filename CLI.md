# Git with CLI

## CLI Git Command

- 새로운 로컬 저장소의 생성 : git init
- 로컬 저장소의 설정 변경 : git config
- 로컬 저장소에 commit : git add, git commit
- 원격 저장소로 push : git push
- 로컬 저장소로 pull : git pull
- 브랜치 이동 : git checkout
- 브랜치 생성 : git checkout, git branch
- 브랜치 합치지 : git merge
- 커밋 히스토리들 확인 : git log
- 커밋 사이 HEAD 이동 : git checkout
- 커밋 사이 Branch 이동 : git reset, git rebase, git revert




### git init

- **$ git init**

  - git 로컬 저장소 생성 (또는 초기화)
  - .git 폴더 생성
  - git으로 버전관리를 시작할 폴더를 지정




### git config

- 깃에 대한 설정을 추가, 변경, 삭제하는 명령어 이다.

- **--global, --local, --system**
  - --global : 전역 옵션을 설정한다.(현재 사용자를 위한 옵션), 일반적인 개인 컴퓨터에서 사용
  - --local : 지역 옵션을 설정한다.(현재 Git 저장소에만 유용한 옵션), 잠시 다른 컴휴터에서 git 사용시 사용 가능.
  - --system : 시스템 환경 옵션을 설정한다.(PC 사용자 전체를 위한 옵션)
  - 우선순위 : 지역 > 전역 > 시스템
  - **지역에 대한 옵션을 따로 제공하지 않으면**, **local 옵션으로 받아들인다.**

- **--unset**
  - 설정한 내용을 제거한다.

- **$git config --global \<옵션 명>**
  - 전역 옵션에 어떤 값이 들어갔는 지 살펴본다.

- **$git config --global \<옵션 명> \<새로운 값>**
  - 전역 옵션에 어떤 값을 넣는다.
  - **$ git config --global user.email "...@....com"** : 버전관리를 위한 내 이메일정보 등록
  - **$ git config --global user.name "jun hyuk lim"** : 버전관리를 위한 내 이름 정보 등록
  - **$ git config --**

- **$git config --global --unset \<옵션명>**
  - 전역 옵션으로 설정한 어떤 값을 제거한다.

- **$git config --local \<옵션 명>**
  - 지역 옵션에 어떤 값이 들어갔는 지 살펴본다.

- **$git config --local \<옵션 명> \<새로운 값>**
  - 지역 옵션에 어떤 값을 넣는다.

- **$git config --local --unset \<옵션명>**
  - 지역 옵션으로 설정한 어떤 값을 제거한다.

- **$git config --system \<옵션 명>**
  - 시스템 옵션에 어떤 값이 들어갔는 지 살펴본다.

- **$git config --system \<옵션 명> \<새로운 값>**
  - 시스템 옵션에 어떤 값을 넣는다.

- **$git config --system --unset \<옵션명>**
  - 시스템 옵션으로 설정한 어떤 값을 제거한다.




### git add

- **$ git add \<파일명1> \<파일명 2>**
  - 여러개의 파일들을 지정하여, stage에 올린다.

- **$ git add \***
  - 수정된 전체 파일을 stage에 올린다.

- **$ git add .**
  - 수정된 전체 파일 중 .gitignore로 지정한 무시하고자 하는 파일을 제외하고 stage에 올린다.

- **git add -A**
    -모든 tracked, untracked change 들을 stage로 올린다.




### git reset

- soft, mixed, hard 옵션을 사용할 수 있다.

- **$ git reset <\파일명>**
  - modify된 어떤 파일의 변경사항을 다시 unstage 시킨다.
  - **별다른 조건 없이** 사용하면 **mixed reset**으로 동작한다.




### git commit

- **$ git commit -m "...커밋 메세지..."**
  - add 명령어로 stage로 올린 파일에 대해서, 로컬 저장소의 commit 저장소에 저장
  - commit은 버전의 생성
  - -m 은 message를 의미함
  - -m 을 통해서 설명을 잘 적어두어야 후에 버전 관리 (수정, 개선)에 용이함

- **$ git commit -a**
  - **add 명령을 생략**하고, **변경된 사항들에 대해서 전부 commit 저장소에 저장**
  - untracked된 파일들은 commit 되지 않는다.(.gitignore로 무시하고자 하는 파일들에 대해서는 commit 일어나지 않는다.)

- **$ git commit --amend -m "...변경할 커밋 메시지..."**
  - 가장 최근의 commit message를 변경한다.



### git log

- 이전 commit들을 모두 둘러볼 수 있게 해준다.
- **--oneline** : 커밋 메시지를 한줄로 요약해서 보여준다.
- **--graph** : 커밋 옆에 브랜치의 흐름을 그래프로 보여준다.
- **--decorate** : 브랜치와 태그 등의 참조를 간결히 표시한다.
- **--all** : 모든 브랜치들을 확인하고 싶을 때 사용할 수 있다.

- **$ git log**
  - log 명령어는 최신 커밋부터, 여태까지의 커밋 내용을 보여준다

- **$ git log -n <숫자>**
  - log 기록을 위에서부터 특정 숫자만큼 확인한다.

- **$ git log --oneline**
  - 커밋들을 간단하게 한 줄 단위로 보고 싶을 때 사용한다.

- **$ git log --oneline --graph --decorate**
  - HEAD와 관련된 커밋들을 자세히 보고 싶을 때 사용한다.

- **$ git log --oneline --graph --all --decorate**
  - 모든 브랜치의 커밋 이력을 조회한다.




### git checkout

- 이전 commit으로의 버전 변경을 가능하게 한다.
- 다른 branch로 이동할 수 있게 해준다.

- **$ git checkout <커밋 아이디>**

  - 특정 버전의 커밋 아이디는 log 명령어를 통해서 확인할 수 있다.
  - 특정 버전의 커밋으로 HEAD가 이동한다.

- **$ git checkout <브랜치 이름>**
  - 현재 branch에서 다른 branch로 이동한다.

- **$ git checkout -b  <브랜치 이름> <커밋 아이디>**
  - [커밋 아이디]를 명시하지 않을 경우, 현재 커밋(버전)에서 새로운 [브랜치 이름] 브랜치를 생성한다.
  - [커밋 아이디]를 명시한 경우, [커밋 아이디] 위치에서 새로운 [브랜치 이름] 브랜치를 생성한다.

- **$ git checkout -**
  - 가장 상위 버전으로 HEAD를 이동시킨다.
  - 가장 상위 버전에 head가 위치할때는 바로 이전 버전으로 HEAD를 이동시킨다.

- **$ git checkout ~n**
  - 현재 브랜치에서 n개 만큼 아래의 자식 커밋으로 HEAD를 내려보낸다.

- **$ git checkout <브랜치 이름>^**
  - 현재 브랜치에서 ^의 갯수 만큼 아래의 자식 커밋으로 HEAD를 내려보낸다.




### git push

- **$ git push [origin(원격 저장소)] [master(로컬 저장소 브랜치)]** -> GitHub 계정 입력 후 동기화
  - 원격 저장소로 git으로 관리한 버전내용(commit)들을 push 함

- **$ git push -u origin [로컬 브랜치 이름] --force**
  - rebase를 사용하여 강제 push가 필요한 경우 사용한다.

- **$ git push -u origin [로컬 브랜치 이름]**
  - **현재 로컬 브랜치**에서 생성된 커밋들을 **원격저장소로** 올린다.
  - -u 옵션으로 업스트림 등록할 수 있다.

- **$ git push --set-upstream [origin] [원격 저장소 이름]**
  - **현재 로컬 브랜치**에서 생성된 커밋들을 새롭게 지정한 upstream **원격저장소 branch**로 올린다.


### git pull / fetch

- 'git init' -> 'git remote add origin ...' 를 수행한 다음에 원격 저장소의 내용을 끌어올 수 있다.
- pull : 원격저장소의 소스를 가져오고(fetch), 해당 저장소의 소스가 더 최신버전이라면 지금의 버전을 해당 버전에 맞춰 올린다(merge).
- fetch : 단지 소스를 가져올 뿐 merge 하지는 않는다

- **$ git pull**
  - git fetch + git merge 의 명령이다.
  - 즉, **원격의 내용을 가져오고(fetch), 원격의 내용을 반영하여 로컬의 버전을 맞춰 올린다.(merge)**

- **$ git pull \<원격 저장소명(origin)> \<branch명(master)>**
  - 원격저장소에서 fetch 명령어로 가져온 뒤, merge까지 한번에 수행하여 실제 파일의 내용이 변경되는 명령어

- **$ git fetch \<원격 저장소명(origin)>**
  - fetch 명령어를 통해서 변경된 내용을 가져온다.
 



## git merge

- **$ git merge 브랜치이름**
  - 지정한 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영한다.
 



### git diff

- **$ git diff**
  - commit된 파일 상태와 modified된 파일 상태를 비교한다.
  
- **$ git diff HEAD origin/master**
  - git fetch 수행 후에, 원격 저장소에서 받아온 상태와 로컬 저장소의 상태가 어디서 다른지 확인할 수 있다.

- **$ git diff --staged**
  - stage된 변경사항에 대해서 확인한다.

- **$ git diff \<branch1> \<branch2>**
  - brach1과 branch2의 내용에 대해서 비교한다.




### git clone

- **$ git clone \<리포지토리 주소> [새로운 폴더 명]]**
  - **원격 저장소의 리포지토리에 있는 내용들을 내가 지정한 위치에 끌고와서 "폴더를 만들고," 그안에 워크스페이스와 로컬저장소를 만들어 준다.**
  - mac 환경에서, clone하여 저장할 로컬저장소에서의 위치를 먼저 지정해주어야 한다.
  - clone하면 자동으로 origin이라는 이름이 원격 저장소의 별칭으로 생성된다.
  - **fatal: destination path '...' already exists and is not empty directory.**
    - clone을 할 경우, 새로운 폴더명을 지정해주지 않으면, 원격 이름과 동일한 폴더를 새로 만든다.
    - 이때, 원격 이름과 동일한 폴더가 있는 경우 오류가 발생한다. 그때 위와 같은 오류가 발생.




### git remote

- **$ git remote -v**
  - 해당 로컬 리포지토리와 연결되어있는 remote 저장소의 단축이름과 주소URL을 알 수 있다.

- **$ git remote add origin \<원격 저장소 이름>**
  - 로컬 저장소에 원격 저장소(GitHub)의 주소를 알려준다.
  - 즉, 로컬 저장소(워킹 디렉토리)에 새로운 원격 저장소를 추가한다.




### git status

- git 워킹트리의 상태를 보는 명령이다.
- 워킹트리의 변경사항을 확인할 수 있다.

- **$ git status -s**
  - git status 명령보다 짧게 요약해서 상태를 보여준다. 변경된 파일이 많을 때 유용하다. (변경된 상태를 보여줌)




### git help

- **$ git help <명령어>**
  - 특정 명령어에 대한 도움말을 확인할 수 있다.




### git branch

- **$ git branch**
  - 현재 로컬에 존재하는 branch들을 확인한다.
  - 현재 브랜치를 확인할 수 있다.

- **$ git branch [-f] <브랜치 이름> [커밋 체크섬]**
  - **$ git branch <브랜치 이름>** : 현재 브랜치에 새로운 <브랜치 이름>을 갖는 브랜치를 생성한다.
  - ****

- **$ git branch -d <브랜치 이름>**
  - 브랜치를 삭제한다.
  - HEAD 브랜치나, 병합되지 않은 브랜치를 삭제할 수 없다.

- **$ git branch -D <브랜치 이름>**
  - 브랜치를 강제로 삭제한다.

- **$ git branch -m <OLD_BRANCH> <NEW_BRANCH>**
  - OLD_BRANCH의 이전 로컬 브랜치 명을 NEW_BRANCH의 새로운 로컬 브랜치 명으로 변경한다.
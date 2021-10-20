## 01. Git 이 무엇인가..?

- **버전 관리를 도와주는 시스템**이다.
- **Git의 동작 방식**
  - 커밋에서 발생하는 차이들만 저장하는 것이 아니라, 커밋된 파일 전체인 스냅샷을 저장한다.
  - 바뀌지 않은 파일은 이전 파일의 링크만 저장하기 때문에, 용량을 많이 잡아먹지 않고, 계산도 필요 없다.
- **.git 파일 내부에 저장되어 있는 정보**
  - 원격저장소의 주소
  - 버전 관리한 데이터 등..
  - 커밋 객체 : 부모 커밋에 대한 참조정보, 실제 커밋 으로 구성
- **git으로 관리하는 원격/로컬 저장소 만들기**
  - 존재하는 원격 저장소를 **clone하여 로컬에 git을 생성**한다.
  - 로컬에서 git을 생성하고, 존재하는 원격 저장소를 **git remote add origin .. 을 통해 로컬에 연결**한다.





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

- **force push는 나만 사용하는 브랜치에서 하자!! (history가 꼬일 수 있다.)**
- **Branch** : 여러 명의 협업자들이 줄기를 나누어 프로젝트를 작업할 수 있게 도와주는 기능
  - **여러 명**이 **작업의 갈래를 나누지 않은 상태**라면
    - **먼저 푸시**한 커밋은 **정상**적으로 올라간다
    - **나중에 푸시**한 커밋은 **'낡은 커밋에 푸시하지 말라'는 오류가 발생**한다.
  - **Branch**는 단순한 포인터이다.
    - **[master] pointer** : Git이 제공하는 기본 브랜치(포인터)
    - **[HEAD] pointer** : 브랜치 사이를 넘나들 수 있게 해주는 포인터
      - detached HEAD 상태 : master 포인터에서 HEAD 포인터가 분리된 상태
  - **Branch**를 만들 때에는 base를 잘 설정해야 한다. (어떤 시점에서 브랜치를 뻗어나갈 것인가?)
  - **[master] pointer**를 기준으로 branch를 생성한 후에, 협업한 내용들을 다시 **merge** 한다.
- **Merge** : 병렬로 뻗어나간 가지들간의 합집합을 구하는 기능이다.
- **Merge의 3가지 경우**
  - **Merge commit** : 충돌은 없고, 합쳐서 새로운 commit을 생성
    - 어떤 브랜치를 기준으로 병합할지를 선택하는 과정이 요구된다.
  - **Fast-Forward** : 충돌은 없고, 한 commit가 다른 commit을 포함하고 있을 때의 commit 생성
  - **Conflict** : 충돌이 발생한 상황
    - Conflict가 발생하면 충돌이 난 부분을 확인하여, 어떤 것을 남길지를 수동으로 택하고 병합하는 과정이 요구된다.
- **Pull Request**
  - master branch에 merge해도 되는지에 대해서 협력자에게 허락을 요청하는 과정!
  - pull request를 보내기 전에는 원본 저장소의 README.md 파일의 contribution guideline에 대한 내용이 있는지 확인하는 것이 좋다.
  - **fork나, branch**를 통해서 원본 저장소에 pull request를 보낼 수 있다.
  - **pull request 보내기**
    - **base branch / compare branch**
      - **base branch** : 병합 결과물이 올라갈 기준이 되는 브랜치
      - **compare branch** : base branch와 비교대상이 되는 브랜치
    - **Compare & pull request** : 원격 저장소에 커밋을 수행한 경우, 협력자에게 pull request를 보낸다.
    - **new pull request** : 다른 branch로 pull request를 직접 보내거나, 직접 설정을 변경하고 싶은 경우 사용.
  - **pull request 받기**
    - **[File changed] : 파일 변경사항을 확인할 수 있다.**
    - **[Comment] : 명시적 승인 없이 코멘트만 남긴다.**
    - **[Approve] : 코멘트를 남기고 merge를 승인한다.**
    - **[Request changes] : 코멘트를 남기고 수정을 요청한다.**
- **Tag** : 특정 커밋, 상태에 버전을 붙여주거나, 별칭을 붙여주는 역할을 한다.
  - branch와 마찬가지로 커밋을 가리키는 포인터이다.
  - push해주어야 원격저장소에서도 확인할 수 있다.
  - Tag 탭에서 확인할 수 있고, Release 탭에서 다운받을 수 있다.
- **fork** : 브랜치를 포함한 원본 저장소의 모든 커밋 이력을 원격 저장소로 통째로 옮긴다. 다른 이의 원격저장소 내 계정에 통째로 복사.
  - 원격 저장소에서는 fork할 시점의 원본 저장소의 히스토리만 알 수 있다.
  - 오픈소스를 다룰 때, 원본 저장소로의 pull request에서 발생가능한 conflict를 피하기 위해서 원본 저장소의 **history** 또한 고려할 필요가 있다.
    - source tree에서, **로컬에 연결된 원격**으로 **'upstream'이라는 관용적인 이름을 사용**하는 **원본 리포지토리를 추가**할 수 있다!
- **rebase(재배치), fetch(새로고침)**
  - 예전 코드를 기준으로 갱신한 사항을, **마치 원본의 최신코드를 기준으로 갱신한 것처럼 이력을 조작**하는 것.
    - **내가 여태까지 수정한 것이 마치! 최신 원본 저장소의 커밋 뒤에 붙어있는 양 만들어버리는것!**
    - 실제로 rebase한 내용은 새로운 커밋이 되어 붙는다. (커밋 체크섬의 값이 다르다.)
  - rebase를 사용하면, 원본의 변경을 가져와 merge하고, 그것을 다시 원본에 pull request할 때 발생하는 **불필요한 merge가 생성되는 것을 방지**할 수 있다.
  - rebase를 수행하면 히스토리가 강제조작되기 때문에, 다른 사람이 히스토리를 보고있다면 완전히 꼬이게 된다. 그러므로, **혼자 쓰는 브랜치에서 수행해야 함**
    - **원본 저장소의 이력을 fetch해서 가져온다.**
    - **내가 수정한 내용을 원본 저장소의 끝에 재배치**
    - **충돌이 일어난 경우**
      - 발생하는 충돌들이 모두 해결될 때까지 계속 '재배치 계속'
      - 모든 재배치가 완료되면 **master branch가 원본의 최신 branch 앞으로 재배치** 됨
    - **rebase할만한 commit이 없는 경우** : 아무 작업도 수행하지 않음
    - **fast-forward 가능한 경우** : fast-forward로 rebase 수행
  - **원격 저장소에 push한 브랜치는 rebase하지 않는 것이 원칙이다!**
    - 원격 저장소에 push한 브랜치를 다른 곳 앞으로 rebase하면, 내용이 유지되면서 위에 더 추가되는 양상이 아니라, 아상하게 꼬여버리는 수가 있다.

<img src="https://user-images.githubusercontent.com/59442344/136898606-222c1156-7a87-4a92-a3c3-62223553abe3.png" width="70%" height="23%">


- **amend** : 새로운 커밋 없이 마지막 커밋 내용 혹은 커밋 메세지를 변경하는 방법이다.
  - 커밋 옵션에서 **Amend last commit**을 사용하면, 로컬에서의 가장 최근의 기존 커밋을 덮어 씌울 수 있다.
  - 커밋 옵션에서 **Amend last commit**을 사용하여 변경된 로컬에서의 최근 커밋을, **강제 push**를 통해서 원격 저장소로 보낼 수 있다.
- **cherry-pick** : 다른 브랜치의 커밋 하나만 골라서 현재 브랜치에 반영하는 방식이다.
  - cherry-pick의 주체 branch를 선택
  - cherry-pick의 대상 commit을 선택하여 그 commit만 골라서 주체 branch 끝에 붙일 수 있다.
  - **cherry-pick**은 다른 것을 내쪽에 갔다 붙이는 것, **rebase**는 내것을 다른 쪽에 갔다 붙이는 것.
- **reset(초기화)** : 특정 커밋으로 현재 브랜치를 이동시키는 작업이다.
  - **soft reset** : 원하는 커밋위치로 상태를 돌리지만, 변경 이전 이력을 uncommited change로 남기고, stage에 변경사항 올리지 않음
  - **mixed reset** : 원하는 커밋으로 상태를 돌리지만, 변경 이전 이력을 uncommited change로 남기고, stage에 변경사항을 올려놓음
  - **hard reset** : 원하는 커밋으로 상태를 돌리고, 변경 이전 이력들을 폐기한다.
- **revert(되돌리기)** : 커밋을 이전 커밋으로 되돌리고 싶을 떄 사용한다.
  - c1, f1, c2, f2, c3 (master) 순서대로 commit들이 이뤄졌고 f1, f2를 취소해야 할 때
  - 최신 커밋부터 취소를 한 결과로 c1, f1, c2, f2 ,c3, rf2, rf1 (master)처럼 **rf2와 rf1이라는 취소 결과 commit을 master branch에 추가하는 방식으로 수정할 수 있다.**
- **stash(임시저장)** : 아직 커밋하지 않은 변경사항을 잠시 저장해두는 기능이다.
  - stash에는 **추적되는 파일들 만 올라간다.**
  - **stash 올리기** : stash 항목에서 현재 tracking 되는 변경사항들에 대해서 stash 하라고 설정
  - **stash 가져오기 / 제거하기** : stashes에서 stash 항목들에 대해서 '스태시 적용' / '스태시 제거' 선택.

<img src="https://user-images.githubusercontent.com/59442344/133256000-c7342404-060c-448d-a1ca-885f37d82545.png">





## 05. Git / GitHub 용어

- **원격 저장소 (repository)** : GitHub에서 협업할 공간. 로컬 저장소를 업로드 하는 공간. (다른 개발자들과 같이 버전관리할 공간.)
- **로컬 저장소** : .git 폴더. 커밋이 들어있는 공간.
  - 특정 폴더 내의 숨겨진 .git 폴더가 바로 로컬 저장소 이다.
  - CLI 환경에서는 git init 이라는 명령어를 통해서 .git 폴더 생성됨
  - GUI 환경에서는 +create 이라는 아이콘을 통해서 .git 폴더 생성됨
  - .git 폴더에 원격저장소의 주소, 버전 관리 데이터 등의 필요한 정보를 저장.
- **Git** : 버전 관리 시스템
- **GitHub** : Git을 통해 관리하는 프로젝트를 올려두는 공간
- **GUI** : Graphic User Interface, 마우스로 명령 입력
- **CLI** : Command Line Interface, 커멘드 라인으로 명령어 입력
- **Git Bash** : CLI 방식으로 Git을 이용하게 해주는 터미널 환경
- **commit** : 버전을 갱신하는 것, 새로운 버전으로 생성된 파일
- **log** : 모든 commit 확인
- **checkout** : 원하는 지점의 버전으로 파일을 되돌릴 수 있다.
- **push** : 로컬 저장소 -> 원격 저장소로 commit을 올리는 것.
- **pull** : 원격 저장소 -> 로컬 저장소로 commit을 내려받는 것.
- **pull request** : 다른 브랜치에서, 혹은 다른 원격 저장소에서, 원본 저장소의 소유자에게 commit을 통한 병합을 요청하는 것.
- **branch** : 특정 버전 위치를 가리키는 포인터이다. 커밋에서 일어난 분기, 혹은 코드 분기점을 만드는 것.
  - 새로운 기능 추가, 버그 수정, 병합과 리베이스 테스트, 이전 코드 개선, 특정 커밋으로 돌아가고 싶을 때 등의 경우에 브렌치 기능을 사용한다.
- **fork** : 브랜치를 포함한 원본 저장소의 모든 커밋 이력을 원격 저장소로 통째로 옮긴다. 다른 이의 원격저장소 내 계정에 통째로 복사.
  
 |branch|fork|
 |:---:|:---:|
 |하나의 원본 저장소에서 분기 나눔|여러 원격 저장소로 분기|
 |하나의 원본 저장소에서 커밋 이력 확인 가능|원본 저장소에 영향을 미치지 않고, fork한 저장소에서 자유롭게 코드 수정 가능|
 |다수의 사용자의 커밋을 관리하기에 불편하다|원본 저장소의 커밋확인을 위한 주소 추가가 필요하다|

- **master** : Git이 제공하는 기본적인 branch 이름, 보통 로컬저장소의 버전 상태를 가리키며, 새로운 commit을 master 위에 올린다.
- **origin** : 원격 저장소의 닉네임이며, 다른 이름으로 변경 가능. 원격 저장소의 현재상태를 사리키는 꼬리표.
  - $git remote add **origin** " ... " : 원격 저장소의 닉네임을 origin으로 저장하라는 git 명령.
  - **git push origin master** : master의 모든 새로운 commit들을 origin위에 올리는 명령.
  - **origin / master** : 보통 원격저장소의 버전 상태를 가리킨다.
- **HEAD** : 커밋들을 자유롭게 가리킬수 있는 포인터이다. head 포인터를 통해서, branch를 넘나들 수 있다. **현재 작업 중인 브랜치 또는 커밋**. **항상 작업 트리의 가장 최근의 커밋을 가리킨다.**
  - **detached HEAD** : HEAD를 branch 대신에 커밋에 붙이는 것을 의미한다.
    - 예를 들어 C1 에 main branch가 있다면 : C1 <- main <- HEAD
    - 만약, 현재 branch에서 checkout을 통해서 최신 커밋이 아닌 다른 커밋으로 이동했다면 : C1 <- main , Cn <- HEAD
- **OAuth** : 비밀번호 제공 없이 다른 웹사이트 상의 자신의 정보에 대해, 웹사이트나, 애플리케이션에 접근권한을 부여하는 접근위임응 위한 개방형 표준.
- **fetch** : '새로고침' 기능으로, 원본저장소 혹은 원격 저장소의 이력을 업데이트 하되, 코드에 영향을 주지 않는다. (pull은 코드까지 변경시킨다)
- **amend** : 새로운 커밋 없이 마지막 커밋 내용 혹은 커밋 메세지를 변경하는 방법이다.
- **cherry-pick** : 다른 브랜치의 커밋 하나만 골라서 특정 브랜치에 반영하는 방식이다.
- **rebase(재배치)** : 예전 코드를 기준으로 갱신한 사항을, **마치 원본의 최신코드를 기준으로 갱신한 것처럼 이력을 조작**하는 것. 
- **reset(초기화)** : 특정 커밋으로 현재 브랜치를 이동시키는 작업이다.
- **revert(되돌리기)** : 커밋을 이전 커밋으로 되돌리고 싶을 떄 사용한다.
- **working tree(워킹트리)** : 일반적인 작업이 이뤄지고 있는 .git이 있는 폴더내의 .git 폴더를 제외한 부분들이 워킹트리. 커밋을 체크아웃하면 생성되는 파일과 디렉토리.
- **commit tree(커밋 트리)** : 커밋, 브랜치 등으로 이루어져 있는 프로젝트 내에 존재하는 전체 커밋 양태.
- **작업 폴더** : 워킹트리 + 로컬 저장소
- **commit cheksum(커밋 체크섬, 커밋 아이디) / SHA1 해시 체크섬** : 커밋마다 부여되어 있는 고유한 값이다.
- **upstream brach(업스트림)** : 로컬 저장소와 연결된 원격 저장소의 branch를 일컫는 단어이다.
- **relative ref(상대 참조)** : commit checksum(SHA1)이라는 절대값을 통해서 commit 사이를 이동하는 것이 아니라, 현재 commit 위치에서 상대적인 위치값을 바탕으로 이동한다. (HEAD가 이동)
- **Tag(태그)** : 특정 커밋, 상태에 버전을 붙여주거나, 별칭을 붙여주는 역할을 한다.
- **3-way merge** : 특정 조상 commit에서 분기한 두개의 브랜치를 다시 merge하는 것을 말한다.
  - rebase, merge에서 발생할 수 있는 conflict를 해결하고 merge하면 된다. (물론 문제가 없어서 fast-forwarded 되거나, 그냥 merge 될 수도 있다.)

 ||3-way merge|rebase|
 |:---:|:---:|:---:|
 |특징|merge commit 생성|현재 commit 수정해서 대상 위로 재배치|
 |장점|충돌이 한번만 발생|히스토리가 깔끔함|
 |단점|트리가 지저분해짐|여러번 충돌이 발생 가능함|

- **upstream/downstream/origin**
  - **upstream** : fork의 맥락에서 내가 fork 해서 가져온 오리지널 레포지토리.
  - **downstream** : 내가 변경하고 있는 내 로컬 리포지토리.
  - **origin** : fork해서 내 원격으로 끌고 온 원격 리포지토리.
  - downstream, upstream은 상대적인 개념이다.





## 06. Open Source와 License

### 1. MIT License

- 소스를 가공하여 재배포 가능
  - 상업적 이용 OK
  - 변경 OK
  - 배포 OK
  - 사적 이용 OK
  - 저자 책임, 보증 NO
  - 저작권 표시 및, 해당 허가 표시를 소프트 웨어의 모든 복제물, 또는 중요 부분에 기재하여야 함.





## 07. Git Tips

- **current branch has no upstream 오류의 해결**
  - push할 원격 저장소가 지정되어있지 않아서 문제가 발생한다.

```git
git push -u <원격저장소 지정 (origin)> <로컬저장소 지정(master)>
```

- **fatal: destination path '...' already exists and is not empty directory.**
  - clone을 할 경우, 새로운 폴더명을 지정해주지 않으면, 원격 이름과 동일한 폴더를 새로 만든다.
  - 이때, 원격 이름과 동일한 폴더가 있는 경우 오류가 발생한다. 그때 위와 같은 오류가 발생.
  - 내가 겪었던 문제 : .git 폴더 상위 디렉토리로 이동시켜야 함 -> .git mv 써서 옮기려 했는데 이미 있다고 안 옮겨짐 -> (상위 디렉토리에 있던 .git 폴더를 rm -rf 로 지우고 옮겼으면 끝났을 문제) -> 원격을 clone하려고 시도 -> 원격을 clone 하는 것은 .git 폴더를 만드는 것이 아닌데, .git 폴더가 안만들어지자 다시 clone 시도 -> 'destination path ... already exist' 문제 발생 (clone하는 것은 원격 리포지토리를 옮기는 것이지 .git 폴더를 만드는 게 아니다!)

- **Authentication 오류의 해결..**
  - CLI 환경
    - 2021.8.13 부로 Git에서 Basic 로그인 방식을 제공하지 않기에, personal token을 만들어 사용하여야 함.
    - 아래의 방식으로 원격 저장소 URL다시 설정
    - 그 후, 비밀번호 작성하라 할때, 발급한 토큰을 입력하면 재연결 가능.

```git
git remote set-url origin https://YOURUSERNAME@github.com/USERNAME/REPOSITORY.git 
```

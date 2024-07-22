# CLI, 버전관리

1. 버전 관리가 무엇인가?<br>
 다른 파일을 만들지 않고 동일한 파일명에 진행 과정 기록
2. CLI(Command Line Interface)를 왜 배워야 하는가?<br>
 GUI에 비해 자원을 덜 잡아먹고 더 빠르다<br>
 반복적인 작업을 자동으로 처리할 수 있다 (파일명 1000개 바꾸기 등)<br>
 해야 할 작업을 명확하게 전달할 수 있다 (documentation)

# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?<br>
git - 로컬에 설치하는 버전 관리 툴, 오픈소스 소프트웨어<br>
github - git repository를 호스팅하는 웹 플랫폼, 로컬이 아닌 레포지토리에 접근 가능

# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?<br>
git init - 새로운 git repository 생성 및 초기화<br>
git clone - 존재하던 repository의 복사본 생성, 주로 서버에 있던 걸 로컬로 가져올 때 사용
2. git clone하는 절차와 명령어를 적어주세요.<br>
1-새로운 repository 생성 및 초기화<br>
2-명령어에 주어진 주소로 remote origin 설정<br>
3-remote repository의 모든 데이터 가져오기<br>
4-기본적으로 main branch로 체크아웃<br>
/$ git clone https://github.com/someuser/somerepo.git
3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?<br>
버전 관리에 필요한 정보가 들어 있음<br>
hooks/ - commit, push 등 특정 행동이 일어날 때 실행해야 하는 스크립트<br>
info/ - exclude 파일: repository에 무시할 파일 설정<br>
objects/ - 모든 objects (commits, trees, blobs(files), tags)<br>
refs/ - commit objects에 대한 포인터<br>
HEAD - 현재 branch<br>
config - repository-specific 설정 파일<br>
description - 설명<br>
index - staging area<br><br>
삭제 시 모든 버전에 대한 기록 삭제, git 명령어 사용이 불가능해짐

# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.<br>
working tree - 프로젝트의 실제 파일이 들어있는 공간<br>
staging area - commit에 어떤 내용이 들어갈지를 저장하는 공간, repo에 실제로 버전을 기록하기 전에 변경 사항을 확인할 수 있음<br>
repository - 프로젝트의 모든 버전을 저장하는 데이터베이스
2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)
```bash
 ...
 Working Tree -> [git add]-> Staging Area -> [git commit] -> Repository
 ...
```
3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?<br>
git log

# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?<br>
tracked file - 이전 commit에 들어 있었던 파일<br>
(unmodified - 이전 commit에서 달라지지 않은 파일<br>
modified - 이전 commit에서 달라졌지만 staged되지 않은 파일<br>
staged - 이전 commit에서 달라졌고 staged된 파일)<br>
untracked file - 이전 commit에 들어 있지 않았고, 다음 commit에 staged되지 않은 파일

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?<br>
1 - 새로 생성된 파일은 기본적으로 untracked 상태임<br>
2 - .gitignore에 있는 파일은 의도적으로 추적하지 않음 (임시 파일, 보안이 필요한 파일 등)<br>

3. 항상 무엇을 생활화하자?<br>
정기적 commit
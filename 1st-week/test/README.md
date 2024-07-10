# CLI, 버전관리

1. 버전 관리가 무엇인가?
- 동일한 파일명에 진행과정 기록하는 것


2. CLI(Command Line Interface)를 왜 배워야 하는가?
- 버전관리, 백업 협업을 하기위해 git을 사용하는데 CLI는 git을 더 잘 활용하기 위해 사용한다.





# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?
- 깃은 분산버전관리 시스템으로 깃이 소프트웨어이고 깃허브가 서비스라는 점이다. 
깃은 개발자의 로컬 컴퓨터에서 동작하며 소스코드의 버전관리를 담당한다
- 깃허브는 깃 리포지토리를 호스팅하는 웹서비스로 협업을 위한 다양한 도구를 제공한다.








# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?
- git init : 빈 git저장소를 만들거나 기존 저장소를 초기화 하는 명령어이다
- git clone: 해당하는 저장소를 복제해 새 디렉터리로 가져오는 명령어이다. 
- 즉 git init은 프로젝트 자체를 처음부터 시작하는 것이고 clone은 프로젝트 내에 중간에 투입가능.





2. git clone하는 절차와 명령어를 적어주세요.
- 깃헙에서 레포지토리에 있는 데이터를 가져오기 위해서 code의 url을 복사한다.
- 그 뒤 git bash에서 clone을 하고 싶은 디렉토리로 이동하고 git clone url을 하면 된다. 





3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?
- hook: git에서 지원하는 commit push등이 정의
- logs: head 각각의 브랜치 별로 작업목록이 로그로 기록된다. 
- HEAD: 현재 로컬저장소가 가르키고 있는 브랜치를 참조한다.
- refs: git 에서 관리하는 branch들의 정보가 들어있다. 
- config: 저장소의 설정 정보를 포함.
- description: 저장소에 대한 설명을 포함하며 주로 Gitosis나 GitWeb 같은 툴에서 사용.

- 삭제시 버전 관리 손실: 모든 커밋, 브랜치, 태그 등 버전 관리 기록이 사라진다.
추적 손실: Git이 파일 변화를 추적할 수 없음.
복구 불가: 삭제된 .git 폴더는 복구할 수 없기 때문에 이전의 커밋 내역을 복구하는 것이 불가능함.
협업 문제: 다른 사람들과 협업 중이었다면 변경 사항을 푸시하거나 풀 할 수 없음.


# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.
- working tree: 현재 사용자가 작업중인 프로젝트 디렉토리와 그안에 있는 파일 상태를 나타낸다. (git에 의해 추적되지 않는다.)

- staging area: commit될 파일들을 임시로 저장하는 곳 (수정한 파일을 git에게 수정완료 했으니 working tree랑 분리한다 여기서부터는 수정하기 어렵다.)

- repository : 만들어진 버전이 존재는 하지만 github에는 가있지 않는다. 






2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)
```bash
 ...
   code 
    git add 파일명 # workingtree에서 staging 영역으로 추가
    git commit -m 파일명 # 스테이징 영역에서 로컬저장소로 커밋
    git push origin # 로컬저장소에서 원격저장소로 push origin은 기본원격저장소 이름

 ...
```
3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?
- git status


# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?

- tracked file: git이 이미 버전관리를 하고 있는 파일(commit 된 후)

- untracked file : git이 아직 버전관리를 하지 않는 파일(commit 된적이 없음)

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?

- 버전 관리 시스템이 효율적으로 작동하도록 하고 불필요한 파일을 제외 시키기 위해서이다. 

3. 항상 무엇을 생활화하자?
- git 백업..
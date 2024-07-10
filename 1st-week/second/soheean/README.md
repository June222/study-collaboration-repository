# CLI, 버전관리

1. 버전 관리가 무엇인가?
- 버전 관리 시스템은 파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템이다.
2. CLI(Command Line Interface)를 왜 배워야 하는가?
- 입출력 만으로 컴퓨터와 소통할 수 있어 작업의 효율을 높일 수 있다. 직접 서버 컴퓨터에 찾아갈 필요 없고 효율적으로 접속하고 데이터를 활용할 수 있다.

# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?
- *git*은 본인의 코드와 수정내역을 기록하고 관리하도록 돕는 버전 관리 **프로그램**이다. *github*은 git 저장소를 관리하는 클라우드 기반 호스팅 **서비스**이다. 

# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?
-  clone은 저장소를 복제해 내 로컬 디렉터리로 가져온다. init은 내 로컬에서 빈 깃 저장소를 만들거나 기존 저장소를 다시 초기화한다
2. git clone하는 절차와 명령어를 적어주세요.
- 1. github에서 원하는 레포지토리를 눌러서 주소 복사
- 2. 저장소 복제하기 : git clone [url] 
3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?
- .git 파일은 git에서 변경된 모든 사항을 저장하는 파일이다. 삭제하면 해당 디렉토리의 버전 관리 기록이 모두 사라지고 일반 디렉토리가 된다

# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.
- Working tree: 현재 작업 중인 파일들이 있는 디렉토리
- Staging area: 커밋할 준비가 된 변경사항들을 임시로 저장하는 영역
- Repository: 모든 버전과 변경 이력이 저장되는 곳

2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)
```bash
git add <file>  # Working tree에서 Staging area로 파일 추가
git commit -m "message"  # Staging area에서 Repository로 변경사항 커밋
git push origin master
```
3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?
```bash
git log # 커밋 히스토리 확인
```
# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?
- Tracked file은 git이 관리하고 있는 파일이고 untracked file은 git이 관리하고 있지 않은 파일
2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?
- 불필요한 파일을 관리하지 않음으로써 저장소를 효율적으로 관리하기 위해
3. 항상 무엇을 생활화하자?
- git status 명령어를 자주 사용하여 현재 저장소의 상태를 확인하는 것을 생활화하자
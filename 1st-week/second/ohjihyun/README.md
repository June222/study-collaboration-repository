# CLI, 버전관리
# HOMEWORK 
1. 버전 관리가 무엇인가?
  동일한 파일명에 진행 과정들을 기록을 하는 것. (깃발 느낌으로)
2. CLI(Command Line Interface)를 왜 배워야 하는가?
  텍스트 명령으로 파일을 작업할 수 있기 때문. 


# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?
  Git은 버전 관리 도구이고, Git을 사용하는 웹 서비스가 Github이다. 


# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?
  init을 사용하면 GUI로 쓸 때 일어나는 일들을 명령어를 사용해서 일어날 수 있게 해주고, clone은 온라인에서 가져와서 생성하는 것이다. 

2. git clone하는 절차와 명령어를 적어주세요.
  [1] Git 설치 
  [2] cd 명렁어로 작업 폴더로 이동
  [3] git clone [project URL] 를 작성해서 clone을 완료한다. 

3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?
  프로젝트의 모든 버전 관리 정보가 들어있으며, 삭제 시 버전 관리 기능이 사라진다. 

# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.

  [1] Working Tree 
    아직 버전으로 만들기 전 단계를 의미한다. (수정 중인 상태)
  [2] Staging Area 
    여러개의 파일 중 특정 파일만 업데이트한 버전을 만들고 싶을 때, 버전으로 만들어지게 될 파일의 묶음을 의미한다. (만들어질 것 보관)
  [3] Repository 
    만들어진 버전이 존재하는 곳을 의미함. 

2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)
```bash
 git add # 변경 사항 추가 (staging Area에)
 git status # 상태 확인 
 git commit -m " " # commit 메시지 추가. 
 git status 
 git push origin # 
 ...
```
3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?
  git log -p : 각 커밋의 변경된 부분을 보여준다. (그냥 출력하면 내용이 너무 많기 때문에 명령어 필요)

# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?
  버전 관리 유무에 따른 차이점이 존재한다. 
  Staging Area로 넘겨지지 않은 파일은 untracked file이다. 

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?
  개발 속도 및 효율성을 향상하기 위해서이다. 

3. 항상 무엇을 생활화하자?
  git status !!
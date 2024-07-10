# CLI, 버전관리

1. 버전 관리가 무엇인가?  
다른 파일을 만들지 않고, 동일한 파일명에 진행과정을 기록하는 것.

2. CLI(Command Line Interface)를 왜 배워야 하는가?  
cli는 GUI가 없는(백엔드) 환경에서는 github desktop등을 사용할 수 없기 때문에 cmd창에서 할 수 있는 CLI를 배워야 한다.

# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?  
git은 버전과 백업, 협업 등을 관리할 수 있게 도와주는 도구이고,  
github는 git을 기반으로 한 웹 서비스이다.

# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?  
init은 새롭게 repository를 local에 만드는 것이고,  
clone은 github에 올라가있는 repository를 local에 복사해서 가져오는 것이다.  

2. git clone하는 절차와 명령어를 적어주세요.  
    1. cd명령어를 통해 repository를 불러올 폴더로 이동한다.
    2. github에서 불러올 repository의 주소를 복사한다.
    3. `git clone [주소]` 명령어를 사용해서 clone한다. (명령어엔 [ ] 제거)


3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?  
.git 폴더에는 working tree와 staging area, repository의 정보가 저장되어 있다. local에서 commit한 내용도 들어가 있다.  
이 폴더를 삭제할 경우 local에 commit한 내용이 다 사라지므로 상당히 안좋은 상황을 겪게 될 것이다.


# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.  
working tree는 버전으로 만들어지기 전단계로 아직 수정중인 단계이다.  
staging area는 버전으로 만들어질 파일이 들어가야하는 단계이다.  
repository는 만들어진 버전들이 저장되는 곳이다. 하지만 아직 origin에 베포가 되지않은 단계이다.  

2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)  

**working tree -> staging area**
```bash
 ...
 # 
 git add "파일명" # 특정 파일을 working tree에서 staging area로 옮기는 코드
 git add . # working tree에 있는 모든 파일을 staging area로 옮기는 코드
 ...
```
**staging area -> local repository**
```bash
 ...
 # staging area -> local repository
 git commit -m "커밋 제목" # staging area에서 local repsitory로 commit해주는 코드
 ...
```
**local repository -> remote repository**
```bash
 ...
 # local repository -> remote repository
 git push origin # local에 있는 commit내용을 remote(github) repository에 올려주는 코드
 ...
```
3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?  
`git log`를 사용하면 commit된 내용을 확인 할 수 있다.  
`git log -p`를 사용한다면 좀더 자세한 정보를 확인 할 수 있다.


# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?  
tracked file은 현재 commit된 내용이 있으며 추가적으로 수정된 파일이다.  
untracked file은 현재 commit된 내용이 없으며 새로 추가된 파일이다.

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?  
commit할 내용 즉, 백업할 파일만 추적하기 때문이다.  

3. 항상 무엇을 생활화하자?  
저장 및 백업
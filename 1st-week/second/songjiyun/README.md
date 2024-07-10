# CLI, 버전관리<br><br>

1. 버전 관리가 무엇인가?<br>
   파일 명을 바꾸지 않고 동일한 파일 명에 진행 상황을 기록해두는 것<br>
2. CLI(Command Line Interface)를 왜 배워야 하는가?<br>
   CLI를 사용하면 GUI가 없는 서버 환경에서도 명령어로 깃을 다룰 수 있으며 익숙해진다면 간편하게 다룰 수 있기 때문에 CLI를 배워야한다.<br><br><br>


# git != GitHub<br><br>

1. git 과 github는 다릅니다. 어떻게 다른가요?<br>
   git은 버전관리를 가능하게 해주는 도구 또는 버전관리 프로그램이고<br>
   github는 git을 기반으로 하는 웹 사이트이다.<br><br><br>


# init, clone<br><br>

1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?<br>
   init는 생성하면서 초기화를 시키는 것이고<br>
   clone은 온라인 상에서의 파일을 내 로컬로 가져오는 것(생성)이다.<br><br>

2. git clone하는 절차와 명령어를 적어주세요.<br>
   git clone 이라는 명령어를 입력한 뒤, 그 뒤에 github에서의 code의 주소를 입력한 후 엔터키를 누른다.<br>
   -> 온라인 상에서의 파일이 나의 로컬로 clone 된다.<br><br>

3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?<br>
   각종 파일들의 정보가 담겨있다. 삭제 시, 파일 전체나 파일의 내용이 사라지므로 삭제에 유의해야한다.<br><br><br>


# Workflow **중요<br><br>

1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.<br>
   working tree : 저장, commit 둘 다 이뤄지지 않은 작업 중인 파일이 위치하는 곳<br>
   staging area : 저장이 완료되었고 새로운 버전(history)을 만들고자하는 파일이 위치하는 곳(working tree에서 넘어왔음)<br>
   repository : 저장, commit 둘 다 완료되어 만들어진 버전(해당 버전은 이미 배포되었거나 배포될 예정임)이 존재하는 곳(온라인 상의 repository에는 저장되었을 수도 있고 안 되었을 수도 있음)<br><br>

2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)<br><br>
<br>-working tree -> staging area
```bash
 ...
 add content(파일명) #파일을 버전으로 만들기 위해 staging area로 이동시킴
 ...
```
<br>-staging area -> repository
```bash
 ...
 git commit content(버전명)) #파일을 commit하여 버전을 생성함
 ...
```
<br><br>

3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?<br>
   git log<br><br><br>


# 여러 파일로 하나의 버전<br><br>

1. tracked file, untracked file의 차이는 무엇인가요?<br>
   tracked file은 git이 관리하는 파일이고<br>
   untracked file은 git이 관리하지 않는 파일이다.<br><br>

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?<br>
   수많은 파일들을 모두 관리할 수는 없기 때문이다.<br>
   (untracked가 기본 값이라 git에게 관리를 하라고 명령을 내려야한다.)<br><br>

3. 항상 무엇을 생활화하자?<br>
   버전관리를 생활화하자...
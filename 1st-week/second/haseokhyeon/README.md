# CLI, 버전관리

1. 버전 관리가 무엇인가?

   동일한 파일의 진행과정, 수정과정을 기록하고 변경사항을 원하는 만큼 적용하는 것.

2. CLI(Command Line Interface)를 왜 배워야 하는가?

   CLI는 많은 컴퓨터 자원을 필요로 하는 환경에서 사용해야 할 상황이 있을 수 있다. github 환경을 사용할 수 없을 수 있기 때문에 CLI를 배워야 하는 것이다.


# git != GitHub
1. git 과 github는 다릅니다. 어떻게 다른가요?

git은 버전 관리를 위한 시스템이고, github는 이런 git을 기반으로 하는 웹 호스팅 서비스이다.

# init, clone
1. Repository를 local에 생성하는 방법은 init, clone 두 가지가 있습니다. 이 두 가지가 무엇이 다른가요?

init는 아예 빈 저장소를 만들고, clone은 기존에 있던 저장소를 가져오는 기능의 차이가 있다.

2. git clone하는 절차와 명령어를 적어주세요.

clone하려는 directory로 이동한 뒤에
'git clone 가져오려는 repository의 사이트'를 실행하면 된다.

3. .git 폴더에는 어떤 내용이 들어가있나요? 삭제하면 어떻게 되나요?

버전 관리를 할때 사용되는 history등 중요한 정보를 담고 있다. 삭제하면 해당 폴더는 사용할 수 없는 상태가 되어버린다.....

# Workflow **중요
1. git workflow는 working tree, staging area, repository 3가지가 있습니다. 어떻게 다른 지 정리해보세요.

working tree : 버전으로 만들기 전, 수정 중인 단계
staging area : 버전으로 만들어지기 위해서 업데이트된 파일 모음
Repository : 만들어진 버전이 존재

2. 각 단계를 넘어가는 명령어는 무엇인지 적어주세요.(아래를 복사해서 코드를 쓰시면 이쁘게 나옵니다.)

```bash
git add 파일이름 (working tree -> staging area)
git commit -m 버전 이름 (staging area -> Repository)
git push (remote repository로 변경사항 올리기)
```

3. repository에 저장된 버전을 확인하려면 어떤 명령어를 써야하나요?

git log

# 여러 파일로 하나의 버전
1. tracked file, untracked file의 차이는 무엇인가요?

tracked file : git이 관리하는 파일, 커밋을 한번이라도 한 이후 git이 수정 여부를 계속 추적하는 파일이다.
untracked file : git이 관리하지 않는 파일, 한번도 버전관리가 이루어지지 않아서 git이 수정 여부를 추적하지 않는 파일이다.

2. git은 모든 파일을 항상 track(추적)하지 않는데 왜 그럴까요?

효율적으로 저장소를 관리하기 위해

3. 항상 무엇을 생활화하자?

git status 자주 확인하기
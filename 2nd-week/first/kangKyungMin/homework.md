# CLI 버전관리
1. CLI 버전관리란 무엇인가?<br>
- CLI를 사용해서 깃허브 데스크탑/웹페이지에서 했던 작업을 콘솔에서 제어하는 것<br>
-파일의 변경 사항 중 의미있는 지점을 기록하는 것
2. git log를 치면 나오는 HEAD는 어떤 의미가 있나요?<br>
-현재 체크아웃된 브랜치 혹은 커밋을 가리키는 포인터

3. 아래 그림(fig. 1)에서 최신 버전에서 두번째 버전으로 돌아가려면 어떤 명령어를 써야하나요(커밋 메세지가 "message 1"인 버전)
```bash
...
git checkout 009fae8d
...
```
![git log 시 결과](./sources/commit_log1.png)*fig 1. git log 시 결과* <br>

4. main branch의 최신 버전으로 돌아가려면 어떤 명령어를 써야하나요?<br>
git checkout main
5. HEAD, HEAD -> main(혹은 master)는 어떤 차이가 있나요?<br>
-HEAD - Detached HEAD 상태, 특정 커밋을 가리키고 있으며 브랜치와 연결되지 않았음<br>
-HEAD -> main - main 브랜치를 가리키고 있음

# add 옵션, Editor
1. `git commit -am "message"` 에서 -am은 -a, -m 옵션이 합쳐진 것입니다. 각각은 어떤 의미를 가지는 옵션인지 말해보세요.<br>
-a - add: tracked 파일을 자동적으로 staging area로 옮김<br>
-m - message: 커밋 메시지 "message"를 작성할 수 있음
2. `git commit -am "message"`에서 -a 옵션은 실수를 방지하기 위한 조건이 있습니다. 조건이 무엇인가요?<br>
-untracked file을 자동적으로 staging하지 않음
3. `git config --global core.editor "vim"`의 뜻을 설명해보세요.<br>
git config - git 환경설정 세팅하기<br>
--global - 해당 유저의 모든 레포지토리에 변경사항 적용 (없으면 명령을 입력한 해당 레포지토리에만 적용)<br>
core.editor "vim" - 텍스트 에디터를 vim으로 변경

# git reset, revert
1. 위 그림(fig. 1)에서 `git reset --hard 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?<br>
최신 커밋을 삭제하고 구 버전(009fae8d)으로 되돌림
2. `git revert 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?<br>
최신 커밋 위에 새로 구 버전을 커밋함
3. `git reset ...`과 `git revert ...`는 의미가 비슷한데, 용도에 차이를 두고 사용한다면 어떤 차이가 있나요?<br>
git reset - 로컬에서 버전 되돌리기<br>
git revert - 공유된 레포지토리에서 버전 되돌리기

# tag, branch
1. tag는 왜 쓰이고 무엇을 대신하는 건가요?<br>
- commit ID를 대신해서 특정 커밋을 가리키는 tag를 생성할 수 있음<br>
- 기억하기 더 쉬우므로 특정 버전으로 체크아웃하는 데 도움을 줌

2. branch는 생성한다는 것은 어떤 의미인가요?<br>
- 특정 커밋으로부터 새롭고 독립적인 개발 라인을 만듦

# branch
1. branch는 왜 필요한가요?<br>
메인 코드베이스를 건드리지 않고 독립적으로 파일을 수정할 수 있게 해 줌

2. 아래 fig 2.와 fig 3.의 그림과 커밋을 순서대로 각각 대응 시켰을 때, 두 번째 그림에서 새로운 그림을 그리기 위해 분기(branch)를 생성하려면 어떻게 해야하는 지 코드를 작성해주세요 (HEAD는 맨 위 그림 즉, 최신 버전을 가르치고 있음.) 

![alt text](./sources/log_visualization.png) *fig 2.*<br>
![alt text](./sources/commit_log2.png) *fig 3.*<br>
git branch new-branch 72974ff7


3. 각자의 main branch의 최신 버전에서 `dev-{이름} (예: dev-junwoo)`이라는 브랜치를 만들고 (branch가 고장난 것 같으면 `dev-junwoo_1`처럼 만들어도 됩니다.)
4. 이 과제를 작성하고 본인의 remote repository로 push 한 뒤
5. 강준우 repository에 `dev`라는 branch에 PR을 날려보세요. (push가 안될 경우 `git push --set-upstream dev-{이름}`로 push 해보세요.)
6. 다했으면 하는 과정 각각을 스크린샷해서 여기에 올려주세요. 드래그앤 드랍으로 하면 됩니다.

### Advanced
1. HEAD 옆 origin/main, origin/dev, origin/HEAD는 무슨 뜻일지 추측해보세요.<br>
로컬 HEAD와 origin (원격 레포지토리) 사이의 관계를 알려줌<br>
origin/main - 로컬 HEAD가 origin의 main 브랜치와 같은 커밋을 가리킴<br>
origin/main, origin/dev, origin/HEAD - 로컬 HEAD가 main, dev 브랜치의 공통된 커밋을 가리키며, origin HEAD와 같은 커밋을 가리킴
2. `git checkout -b {branch_name}`에서 -b 옵션은 '{branch_name}라는 이름으로 새로운 브랜치를 만든다.' 이 명령어 결과와 같은 결과를 만드는 명령어를 찾아보세요.<br>
git switch -c {branch_name}<br>
switch : 브랜치 변경 커맨드<br>
-c : 새 브랜치를 만들고 해당 브랜치로 변경함
3. `git config ...`에서 바꿀 수 있는 다른 명령어들은 무엇이 있나요? 맘에 드는 설정을 바꾼 뒤 알려주세요.<br>
user.name - 커밋 시 어떤 사용자 이름으로 남길지 설정<br>
user.email - 사용자 이메일 설정<br>
init.defaultBranch - 기본 브랜치명 설정
4. `git reset --hard ...`처럼 `git reset`에는 `--hard` `--mixed` `--soft`등 옵션이 있는데 이 옵션이 어떤 차이가 있는지 알려주세요.<br>
--hard - HEAD 위치 변경, staging area와 작업 영역을 전부 구버전 커밋으로 초기화<br>
--mixed - HEAD 위치 변경, staging area를 구버전 커밋으로 초기화, 작업 영역은 변함 없음<br>
--soft - HEAD 위치만 변경

5. 자주 사용되는 branch의 이름들이 몇 가지가 있습니다. 어떤 것들이 있고 무슨 이유로 그 branch를 사용하는지 2가지만 알려주세요.<br>
release branch - 출시 버전 준비<br>
hotfix branch - 출시 버전에서 발생한 버그 수정
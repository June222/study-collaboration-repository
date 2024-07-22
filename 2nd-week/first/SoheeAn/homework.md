# CLI 버전관리
1. CLI 버전관리란 무엇인가?
- 명령어를 통해 자동화가 가능하고 GUI를 제어할 수 없는 서버환경에서도 사용 가능
2. git log를 치면 나오는 HEAD는 어떤 의미가 있나요?
- HEAD가 특정 커밋에 찍혀 있을 경우 해당 브랜치의 마지막 커밋이 해당 부분이라는 것을 알 수 있게 된다. 즉, HEAD는 특정 브랜치의 마지막 커밋에 대한 포인터
3. 아래 그림(fig. 1)에서 최신 버전에서 두번째 버전으로 돌아가려면 어떤 명령어를 써야하나요(커밋 메세지가 "message 1"인 버전)
```bash
...
git checkout 009fae8d 
...
```
![git log 시 결과](./sources/commit_log1.png)*fig 1. git log 시 결과* <br>

4. main branch의 최신 버전으로 돌아가려면 어떤 명령어를 써야하나요?
```bash
...
git checkout main 
...
```
5. HEAD, HEAD -> main(혹은 master)는 어떤 차이가 있나요?
- *HEAD*는 단순히 현재 작업 중인 커밋을 가리킨다. *HEAD -> main*은 main 브랜치의 최신 커밋을 가리키고 있음을 명시적으로 나타냄. 

# add 옵션, Editor
1. `git commit -am "message"` 에서 -am은 -a, -m 옵션이 합쳐진 것입니다. 각각은 어떤 의미를 가지는 옵션인지 말해보세요.
- `-a`: add 명령어를 사용하지 않고 수정된 파일에 대해 add,commit기능을 한번에 수행
- `-m`: vim에서 별도의 메세지를 작성할 필요없이 인라인 형식으로 바로 커밋 메세지 작성
2. `git commit -am "message"`에서 -a 옵션은 실수를 방지하기 위한 조건이 있습니다. 조건이 무엇인가요?
- git이 이미 추적중인 파일에 대해서만 작동한다. untracked file은 자동으로 추가가 안됨
3. `git config --global core.editor "vim"`의 뜻을 설명해보세요.
- 전역 git 설정에서 기본 텍스트 편집기를 vim으로 설정

# git reset, revert
1. 위 그림(fig. 1)에서 `git reset --hard 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?
- "message 1" 커밋으로 돌아가고 이후의 커밋들은 삭제된다. 
2. `git revert 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?
- "message 1"의 커밋 직전으로 돌아가는 새로운 커밋을 생성한다. 이때 commit history는 유지
3. `git reset ...`과 `git revert ...`는 의미가 비슷한데, 용도에 차이를 두고 사용한다면 어떤 차이가 있나요?
- `reset` : commit history들을 삭제하고 특정 시점의 커밋으로 되돌아감.
- `revert` : 이전 commit history들은 그대로 두고, 되돌리고 싶은 커밋 복원
# tag, branch
1. tag는 왜 쓰이고 무엇을 대신하는 건가요?
- 특정 커밋을 쉽게 참조할 수 있게 이름을 제공한다. 
2. branch는 생성한다는 것은 어떤 의미인가요?
- 독립적인 작업 line을 만들어서 main에 영향을 주지 않고 새로운 기능을 개발할 수 있게 함.

# branch
1. branch는 왜 필요한가요?
- 병렬개발 가능
- main의 안정적인 코드와 개발중인 코드를 분리할 수 있다
2. 아래 fig 2.와 fig 3.의 그림과 커밋을 순서대로 각각 대응 시켰을 때, 두 번째 그림에서 새로운 그림을 그리기 위해 분기(branch)를 생성하려면 어떻게 해야하는 지 코드를 작성해주세요 (HEAD는 맨 위 그림 즉, 최신 버전을 가르치고 있음.) 
![alt text](./sources/log_visualization.png) *fig 2.*<br>
![alt text](./sources/commit_log2.png) *fig 3.*<br>
```bash
...
git checkout 72974ff # git checkout commit number 해서 과거로 가서
git branch dev # dev라는 branch 생성
git checkout dev # dev로 이동
...
```
3. 각자의 main branch의 최신 버전에서 `dev-{이름} (예: dev-junwoo)`이라는 브랜치를 만들고 (branch가 고장난 것 같으면 `dev-junwoo_1`처럼 만들어도 됩니다.)
4. 이 과제를 작성하고 본인의 remote repository로 push 한 뒤
5. 강준우 repository에 `dev`라는 branch에 PR을 날려보세요. (push가 안될 경우 `git push --set-upstream dev-{이름}`로 push 해보세요.)
6. 다했으면 하는 과정 각각을 스크린샷해서 여기에 올려주세요. 드래그앤 드랍으로 하면 됩니다.
![alt text](./sources/screenshot1.png)
![alt text](./sources/screenshot2.png)

### Advanced
1. HEAD 옆 origin/main, origin/dev, origin/HEAD는 무슨 뜻일지 추측해보세요.
- 각각의 branch 들을 가리킴 
2. `git checkout -b {branch_name}`에서 -b 옵션은 '{branch_name}라는 이름으로 새로운 브랜치를 만든다.' 이 명령어 결과와 같은 결과를 만드는 명령어를 찾아보세요.
```bash
...
git branch {branch_name}
git checkout {branch_name}
...
```
3. `git config ...`에서 바꿀 수 있는 다른 명령어들은 무엇이 있나요? 맘에 드는 설정을 바꾼 뒤 알려주세요.
- git config user.name sohee 했더니 커밋 시 사용되는 사용자 이름이 sohee가 되었다
4. `git reset --hard ...`처럼 `git reset`에는 `--hard` `--mixed` `--soft`등 옵션이 있는데 이 옵션이 어떤 차이가 있는지 알려주세요.
- `hard` : 로컬,커밋, 스테이징 모두 reset 된다
- `mixed` : 기본옵션. 로컬은 유지가 되고 커밋과 스테이징이 reset 된다
- `soft` : 스테이징은 유지가 되고 커밋만 reset이 된다
5. 자주 사용되는 branch의 이름들이 몇 가지가 있습니다. 어떤 것들이 있고 무슨 이유로 그 branch를 사용하는지 2가지만 알려주세요.
- develop(dev): 다음 버전 출시 개발 브랜치
- feature : 새로운 기능 개발 및 버그 수정이 필요할때마다 dev 브랜치로 부터 분기

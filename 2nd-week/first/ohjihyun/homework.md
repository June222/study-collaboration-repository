# CLI 버전관리
1. CLI 버전관리란 무엇인가?  
  - 명령어를 통해서 깃허브 데스크탑이나 웹페이지에서 했던 작업을 콘솔에서 제어하는 것. / 코드의 변경 사항 중 의미있는 지점을 기록하는 것. 
2. git log를 치면 나오는 HEAD는 어떤 의미가 있나요?  
  - 현재 위치한 버전을 의미함. 
3. 아래 그림(fig. 1)에서 최신 버전에서 두번째 버전으로 돌아가려면 어떤 명령어를 써야하나요(커밋 메세지가 "message 1"인 버전)
```bash
...
git checkout 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e
...
```
![git log 시 결과](./sources/commit_log1.png)*fig 1. git log 시 결과* <br>

4. main branch의 최신 버전으로 돌아가려면 어떤 명령어를 써야하나요?  
- git checkout main
5. HEAD, HEAD -> main(혹은 master)는 어떤 차이가 있나요?  
- HEAD는 현재 작업 중인 커밋.  
HEAD -> main 은 HEAD가 현재 branch를 가리키고 있다는 의미.   
: "현재의 버전이 가장 최신의 버전임. "

# add 옵션, Editor
1. `git commit -am "message"` 에서 -am은 -a, -m 옵션이 합쳐진 것입니다. 각각은 어떤 의미를 가지는 옵션인지 말해보세요.  
- add, commit 의미. 
2. `git commit -am "message"`에서 -a 옵션은 실수를 방지하기 위한 조건이 있습니다. 조건이 무엇인가요?  
- 최초 한 번은 add가 되어서 tracked 상태가 되어야 함. (그렇지 않으면 자동 add X)
3. `git config --global core.editor "vim"`의 뜻을 설명해보세요.
- git의 설정 중 이 컴퓨터 전체의 설정을 바꿀건데, 에디터를 "vim"으로 바꿈을 의미함. 

# git reset, revert
1. 위 그림(fig. 1)에서 `git reset --hard 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?
- message 1의 버전으로 리셋됨, 현재 branch의 head가 message 1의 커밋을 가리키게 됨. 
2. `git revert 009fae8d669b3bc7eadb5558d2f6f16b50fa7e6e`을 하면 결과가 어떻게 되나요?
- message 1 커밋의 변경 사항으로 되돌려져, 새로운 커밋으로 기록된다. (기존의 커밋 히스토리는 그대로 유지됨. )
3. `git reset ...`과 `git revert ...`는 의미가 비슷한데, 용도에 차이를 두고 사용한다면 어떤 차이가 있나요?  
- git reset은 과거로 돌아가는 것이고, git revert는 과거의 상태를 현재에 반영하는 것이다. reset은 remote repository에 변경 사항들이 반영되어 있다면, push를 허용하지 않는다. (git이 충돌을 막는 것.) 하지만 revert는 remote와 local 둘 다 문제없이 작용한다. 

# tag, branch
1. tag는 왜 쓰이고 무엇을 대신하는 건가요?  
- commit ID를 대신하여 버전을 식별하기 위해 쓰임. 
2. branch는 생성한다는 것은 어떤 의미인가요?  
- Git 저장소에서 저장소를 여러가지 상태로 공존할 수 있게 하는 것. 

# branch
1. branch는 왜 필요한가요?  
- 저장소의 이름을 여러번 변겅하지 않은 채로 하나의 저장소에서 다양한 작업을 진행할 수 있음. 
2. 아래 fig 2.와 fig 3.의 그림과 커밋을 순서대로 각각 대응 시켰을 때, 두 번째 그림에서 새로운 그림을 그리기 위해 분기(branch)를 생성하려면 어떻게 해야하는 지 코드를 작성해주세요 (HEAD는 맨 위 그림 즉, 최신 버전을 가르치고 있음.) 

![alt text](./sources/log_visualization.png) *fig 2.*<br>
![alt text](./sources/commit_log2.png) *fig 3.*<br>

3. 각자의 main branch의 최신 버전에서 `dev-{이름} (예: dev-junwoo)`이라는 브랜치를 만들고 (branch가 고장난 것 같으면 `dev-junwoo_1`처럼 만들어도 됩니다.)
4. 이 과제를 작성하고 본인의 remote repository로 push 한 뒤
5. 강준우 repository에 `dev`라는 branch에 PR을 날려보세요. (push가 안될 경우 `git push --set-upstream dev-{이름}`로 push 해보세요.)
6. 다했으면 하는 과정 각각을 스크린샷해서 여기에 올려주세요. 드래그앤 드랍으로 하면 됩니다.

### Advanced
1. HEAD 옆 origin/main, origin/dev, origin/HEAD는 무슨 뜻일지 추측해보세요.
2. `git checkout -b {branch_name}`에서 -b 옵션은 '{branch_name}라는 이름으로 새로운 브랜치를 만든다.' 이 명령어 결과와 같은 결과를 만드는 명령어를 찾아보세요.  
- branch 생성 `git branch {name}`
- branch 전환 `git checkout {name}`

3. `git config ...`에서 바꿀 수 있는 다른 명령어들은 무엇이 있나요? 맘에 드는 설정을 바꾼 뒤 알려주세요.
- 사용자 이름을 설정할 수 있음.  
`git config --global user.name "JHyun" 

4. `git reset --hard ...`처럼 `git reset`에는 `--hard` `--mixed` `--soft`등 옵션이 있는데 이 옵션이 어떤 차이가 있는지 알려주세요.  
- `--hard`는 모든 변경사항을 삭제한다. 
- `--mixed`는 기본 옵션으로, 변경사항은 작업 디렉토리에 그대로 남아 있게 된다.  
- `--soft`는 인덱스와 작업 디렉토리는 변경하지 않고, HEAD 만 지정된 커밋으로 이동한다. 

5. 자주 사용되는 branch의 이름들이 몇 가지가 있습니다. 어떤 것들이 있고 무슨 이유로 그 branch를 사용하는지 2가지만 알려주세요.

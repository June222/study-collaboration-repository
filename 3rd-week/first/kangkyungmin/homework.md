## 1. 각자 폴더 만들기
## 2. 각자 폴더에 붙여넣기
## 3. `dev`로 브랜치 변경 후 `git pull`
## 4. `dev-{이름}-3rd`브랜치 생성 이후 `checkout`하고 작업하기


# Branch & Merge
1. base는 무엇을 의미하나요?<br>
두 브랜치/커밋의 공통 조상
2. branch, merge, confilct가 각각 무엇을 의미하는지 알려주세요.<br>
branch - 레포지토리의 한 버전, 각각의 브랜치는 서로 독립적임<br>
merge - 두 브랜치를 병합하여 새 버전을 만듦<br>
conflict - 두 브랜치에서 같은 파일의 같은 부분이 서로 다를 때 발생

3. merge를 왜 사용해야 하나요?<br>
여러 개발자가 서로 다른 기능을 개발했을 때, merge함으로써 main branch로 모든 기능을 병합 가능
4. 두 개의 branch를 병합(merge)할 때, 병합되는 쪽이 아닌 병합받는 쪽에 checkout을 해야하는 이유를 history와 관련지어 설명해주세요. (ppt p.6 참조)<br>
병합받는 쪽(main)에 checkout하고 merge하면 main branch의 history가 선형적이고, 따라가기 쉬움

# Merge & Conflict
1. `Auto-merging`이 무엇인지 알려주세요.<br>
merge 시 conflict이 발생하는 조건이 아니면, git에서 유저의 개입 없이 자동으로 두 브랜치의 변경사항을 합치는 기능
2. 스터디 시간에 배운 `conflict`는 무엇을 의미하는 지 알려주세요.<br>
같은 파일의 같은 부분이 병합될 때, git이 자동적으로 병합할 수 없을 경우 발생하는 것

3. 다음 세가지 `서로 다른 파일 병합`, `같은 파일 다른 부분 병합`, `같은 파일 같은 부분 병합` 중 `auto-merging` 기능이 제공되는 것을 구분하고 제공되지 않는 것은 왜 제공되지 않는 지 알려주세요.<br>
[서로 다른 파일 병합] 제공 O<br>
[같은 파일 다른 부분 병합] 제공 O<br>
[같은 파일 같은 부분 병합] 제공 X (두 가지 서로 다른 수정사항 중 어떤 것을 적용해야할 지 알 수 없으므로)
4. `fig.1`은 `conflict` 발생을 유도한 후 명령창입니다. 입력한 명령어는 다음과 같을 때, 이후 `conflict`를 해결하는 방법을 알려주세요.
```bash
git checkout master
git log --all --graph --oneline
git branch
git merge o2
git status
```
![alt text](/sources/conflict-1.png)*fig.1*
- work.txt를 수동으로 수정, conflict marker 제거
- git add work.txt -> conflict 해결된 파일을 staging area로 옮김
- git commit

# Cherry-pick & rebase
1. `cherry-pick`와 `rebase`는 어떤 기능의 명령어이고 왜 필요한지 알려주세요.<br>
cherry-pick - 한 브랜치에서 특정 커밋의 변경사항만을 다른 브랜치에 적용할 때 사용<br>
rebase - 병렬적인 작업 흐름을 직렬로 바꾸어 히스토리를 읽기 쉽게 할 때 사용
2. `fig.2`을 직접 구현한 결과가 `fig.3`입니다. `fig.2`의 결과와 같게 만들려면 어떻게 해야하는 지 알려주세요. 
![alt text](/sources/cherry-pick-1.png)*fig.2*
![alt text](/sources/rebase-merge-log.png)*fig.3*<br>
git cherry-pick 41a0109

3. `fig.3`을 `fig.4`의 결과와 같게 만들고 싶다면 어떤 명령어를 쳐야하는지 알려주세요(HEAD는 HEAD->master에 있음.)
![alt text](/sources/rebase-1.png)*fig.4*<br>
git rebase master
4. `rebase`의 조건이 있는데 어떤 것일 지 추측해보세요.(정답이 되는 조건은 설명한 적 있음.)<br>
rebase를 적용할 버전이 원격 저장소로 push되지 않았을 때에만 rebase 가능

# Advanced
1. *fig.5* 에서 `HEAD`가 `master`의 최신 버전이 아닌 `dc9d3c7`에 checkout 되어 `git merge topic`하게 된다면 어떻게 될지 추측해보세요.
![alt text](/sources/rebase-merge-log.png)*fig.5*<br>
m1 커밋과 topic branch의 변경사항을 병합, m2 커밋은 포함하지 않음

2. *fig.5* 에서 `git commit --amend`로 최신 버전(`33763e0`, `HEAD->master`)의 커밋 메세지를 수정할 수 있었습니다. 만약 최신 버전의 __커밋 내용__ 즉, 파일 안의 코드를 한 줄 수정하고 싶을 때는 히스토리를 아예 삭제하는 `git reset --hard dc9d3c7` 대신 어떤 명령어를 사용해야 하는지 알려주세요.
- git add [file] -> 수정한 파일 스테이징
- git commit --amend -> 최신 커밋에 수정사항 반영

3. `cherry-pick`에서도 `conflict`가 발생할 수 있습니다. 충돌 원인을 예상해보고 해결 방법을 알려주세요.
4. 터미널에 `git merge --help`를 쳐보면 merge에도 굉장히 많은 옵션이 있음을 알 수 있습니다. 이미 실행한 merge를 취소하는 옵션을 포함해서 세 가지의 옵션을 임의로 골라 알려주세요.<br>
--ff - 현 브랜치와 merge 대상 브랜치가 fast-forward 관계에 있을 경우 fast-forward merge 사용, 아닐 경우 merge commit 생성 (git merge의 기본값)<br>
--no-ff - fast-forward 관계에 있더라도 merge commit 생성<br>
--abort - merge conflict 발생 시, --abort하면 conflict 해결 과정을 취소하고 merge 전 상태로 되돌림
5. 정말 만약에... merge 한 브랜치를 push하고 pr이 승락된 브랜치를 되돌려야한다면 어떻게 되돌릴 수 있을 지 알려주세요.....
6. branch간에 merge를 진행할 때 새로운 commit이 생겨날 수도 있고 아닐 수도 있습니다. 이 관점에서 `fast-forward merge`, `3-way merge`를 비교하여 알려주세요.<br>
fast-forward merge - 기준 브랜치에는 새 커밋이 없고 새 브랜치에 새 커밋이 있을 때 발생<br>
ex) master 브랜치에서 hotfix 브랜치 생성 -> hotfix 브랜치에서 파일 변경(master 브랜치는 변함 없음) -> master에서 hotfix merge -> master 브랜치의 HEAD만 hotfix 브랜치로 이동<br><br>
3-way merge - 두 브랜치 모두 새 커밋이 있을 때 발생<br>
ex) master 브랜치 커밋 C1에서 feature 브랜치 생성 -> master에서 커밋 C2 진행, feature에서 커밋 D1 진행 -> master에서 feature merge -> 두 브랜치의 코드를 합쳐서 새 커밋을 만듦
## 1. 각자 폴더 만들기 -> ok
## 2. 각자 폴더에 붙여넣기 -> ok
## 3. `dev`로 브랜치 변경 후 `git pull` -> ok
## 4. `dev-{이름}-3rd`브랜치 생성 이후 `checkout`하고 작업하기 -> ok


# Branch & Merge
1. base는 무엇을 의미하나요?<br>
merge 하려 하는 branch들의 공통 조상 branch<br><br>

2. branch, merge, confilct가 각각 무엇을 의미하는지 알려주세요.<br>
branch : 마치 평행우주처럼 우리의 저장소를 여러가지 상태로 공존할 수 있게 해주는 것<br>
merge : 병합하다, 합치다<br>
conflict : 두 개의 branch가 같은 이름의 파일에서 같은 부분을 수정했을 때 git은 자동으로 해당 수정사항들을 병합하지 못함. 이때 생기는 현상이 conflict(충돌)임<br><br>

3. merge를 왜 사용해야 하나요?<br>
어떤 branch에서의 작업이 다른 branch에서도 유용할 것 같으면 ‘merge’를 해서 작업의 효율성을 높일 수 있음<br><br>

4. 두 개의 branch를 병합(merge)할 때, 병합되는 쪽이 아닌 병합받는 쪽에 checkout을 해야하는 이유를 history와 관련지어 설명해주세요. (ppt p.6 참조)<br>
병합이 되는 쪽은 새로운 버전이 생기지 않기 때문임<br><br>


# Merge & Conflict
1. `Auto-merging`이 무엇인지 알려주세요.<br>
conflict(충돌)이 일어나지 않는 경우, git이 자동으로 merge(병합)해주는 것<br><br>

2. 스터디 시간에 배운 `conflict`는 무엇을 의미하는 지 알려주세요.<br>
두 개의 branch가 같은 이름의 파일에서 같은 부분을 수정했을 때 git이 자동으로 해당 수정사항들을 병합하지 못하는 현상이 발생하는 데 이것을 conflict(충돌)이라고 함<br><br>

3. 다음 세가지 `서로 다른 파일 병합`, `같은 파일 다른 부분 병합`, `같은 파일 같은 부분 병합` 중 `auto-merging` 기능이 제공되는 것을 구분하고 제공되지 않는 것은 왜 제공되지 않는 지 알려주세요.<br>
서로 다른 파일 병합 : auto-merging 기능 제공됨<br>
같은 파일 다른 부분 병합 : auto-merging 기능 제공됨<br>
같은 파일 같은 부분 병합 : auto-merging 기능 제공되지 않음/양쪽 다 동시에 수정한 것이므로 git이 처리할 수 없어 사용자가 처리해야 함<br><br>

4. `fig.1`은 `conflict` 발생을 유도한 후 명령창입니다. 입력한 명령어는 다음과 같을 때, 이후 `conflict`를 해결하는 방법을 알려주세요.<br>
```bash
git checkout master
git log --all --graph --oneline
git branch
git merge o2
git status
```
![alt text](/sources/conflict-1.png)*fig.1*
<br>
```bash
nano work.txt #파일을 열어 편집할 수 있게 됨/구분자 등 git이 우리를 위해 제공한 내용을 지우고, 변경할 최종 사항만을 입력하기
git add work.txt #사용자가 충돌을 해결했음을 git에게 알림
git commit #commit까지 완료해줘서 파일을 수정된 상태로 저장하기
```
<br><br>

# Cherry-pick & rebase
1. `cherry-pick`와 `rebase`는 어떤 기능의 명령어이고 왜 필요한지 알려주세요.<br>
CHERRY-PICK : 특정한 commit(버전) 하나만 픽업하여 다른 commit(버전) 뒤에 붙일 수 있는 기능<br>
REBASE : 병렬적으로 나타나는 작업의 진행 흐름을 한 작업이 끝난 후 다른 작업이 진행된 것으로 나타내는 것(직렬로 나타냄)/훨씬 더 직관적으로 작업의 진행 흐름을 파악할 수 있게 함<br><br>

2. `fig.2`을 직접 구현한 결과가 `fig.3`입니다. `fig.2`의 결과와 같게 만들려면 어떻게 해야하는 지 알려주세요.<br>
```bash
git checkout master #현재 위치한 branch를 topic에서 master로 변경하기
git cherry-pick daa4 #t2 가져오기(cherry-pick)
```
<br>
![alt text](/sources/cherry-pick-1.png)*fig.2*
![alt text](/sources/rebase-merge-log.png)*fig.3*<br><br>

3. `fig.3`을 `fig.4`의 결과와 같게 만들고 싶다면 어떤 명령어를 쳐야하는지 알려주세요(HEAD는 HEAD->master에 있음.)<br>
```bash
git checkout master #이동시키려는 branch로 이동하기
git rebase topic #topic branch가 가리키고 있는 commit(버전)인 t3으로 base를 옮기기
```
<br>
![alt text](/sources/rebase-1.png)*fig.4*<br><br>

4. `rebase`의 조건이 있는데 어떤 것일 지 추측해보세요.(정답이 되는 조건은 설명한 적 있음.)<br>
버전들이 원격 저장소로 push 되기 전까지만 rebase 가능(push 후에는 rebase 불가)/내 컴퓨터(나의 local)에서만 rebase 가능<br><br>


# Advanced
1. *fig.5* 에서 `HEAD`가 `master`의 최신 버전이 아닌 `dc9d3c7`에 checkout 되어 `git merge topic`하게 된다면 어떻게 될지 추측해보세요.<br>
topic branch의 최신 commit인 e4b8d17이 포함된 새로 병합되어 만들어진 commit이 생성됨/병합 후 HEAD는 새로 병합되어 만들어진 commit을 가리키게 됨<br>
![alt text](/sources/rebase-merge-log.png)*fig.5*<br><br>

2. *fig.5* 에서 `git commit --amend`로 최신 버전(`33763e0`, `HEAD->master`)의 커밋 메세지를 수정할 수 있었습니다. 만약 최신 버전의 __커밋 내용__ 즉, 파일 안의 코드를 한 줄 수정하고 싶을 때는 히스토리를 아예 삭제하는 `git reset --hard dc9d3c7` 대신 어떤 명령어를 사용해야 하는지 알려주세요.<br>
```bash
nano work.txt #파일을 열고 수정하기
git add work.txt 
git commit --amend #commit message를 수정할 수 있는 editor가 열리므로 commit 내용을 수정할 수 있게 됨
```
<br><br>

3. `cherry-pick`에서도 `conflict`가 발생할 수 있습니다. 충돌 원인을 예상해보고 해결 방법을 알려주세요.<br>
-충돌 원인 : 두 branch에서 같은 파일, 같은 부분을 수정하면 conflict 발생할 수 있음<br>
-해결 : 
```bash
git status #충돌이 발생한 파일을 알아내기
nano work.txt #충돌이 발생한 파일을 열어 수정하여 충돌 해결하기
git add work.txt #git에게 충돌을 해결했음을 알리기
```
<br><br>

4. 터미널에 `git merge --help`를 쳐보면 merge에도 굉장히 많은 옵션이 있음을 알 수 있습니다. 이미 실행한 merge를 취소하는 옵션을 포함해서 세 가지의 옵션을 임의로 골라 알려주세요.<br>
* --abort : 현재 진행 중인 병합을 중단하고, 병합 시도 전의 상태로 되돌림/병합 도중 충돌이 발생했거나 병합을 계속할 수 없는 경우에 유용함<br>
```bash
git merge --abort
```
<br>
* --squash : merge하는 commit들을 하나의 commit으로 합침/병합된 branch들의 모든 변경 사항이 현재 branch에 적용되지만, merge된 commit 자체는 생성되지 않으므로 수동으로 commit 해줘야 함<br>
```bash
git merge --squash [branch name]
git commit
```
<br>
* --no-ff : Fast-forward merge을 방지하고, 항상 새로운 merge commit을 생성하므로 merge의 history가 명확하게 남음/Fast-forward merge은 history를 단순화할 수 있지만, merge commit을 만들지 않기 때문에 merge 작업의 명시적 기록이 남지 않음<br>
```bash
git merge --no-ff [branch name]
```
<br><br>

5. 정말 만약에... merge 한 브랜치를 push하고 pr이 승락된 브랜치를 되돌려야한다면 어떻게 되돌릴 수 있을 지 알려주세요.....<br>
되돌리기 작업을 새로운 버전(commit)으로 기록하기 때문에 history를 보존할 수 있는 revert를 사용하면 됨<br>
```bash
git log #현재 branch의 상태와 commit history 체크하기
git revert "commit ID" #revert를 사용해서 되돌리기
```
<br><br>

6. branch간에 merge를 진행할 때 새로운 commit이 생겨날 수도 있고 아닐 수도 있습니다. 이 관점에서 `fast-forward merge`, `3-way merge`를 비교하여 알려주세요.<br>

-Fast-Forward Merge<br>
 +merge 시 새로운 commit이 생겨나지 않음<br>
 +branch를 merge하려는 branch의 최신 commit으로 이동함<br>
 +merge하려는 branch가 대상 branch의 직후 커밋이어야 함(즉, 대상 branch에서 다른 commit이 없어야 함)<br>
 +branch merge의 흔적이 남지 않으므로 나중에 history를 볼 때 언제 merge되었는 지 알 수 없음<br>

-3-Way Merge<br>
 +merge 시 새로운 commit이 생겨남<br>
 +세 개의 commit을 사용하여 merge함(현재 branch, merge하려는 branch, 공통 조상 commit)<br>
 +대상 branch와 merge하려는 branch 사이에 다른 commit들이 존재할 수 있음<br>
 +merge commit이 생성되므로 나중에 history를 볼 때 언제 merge되었는 지 알 수 있음
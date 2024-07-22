## 1. 각자 폴더 만들기
## 2. 각자 폴더에 붙여넣기
## 3. `dev`로 브랜치 변경 후 `git pull`
## 4. `dev-{이름}-3rd`브랜치 생성 이후 `checkout`하고 작업하기


# Branch & Merge
1. base는 무엇을 의미하나요?
- 브랜치가 나뉘기 전의 기준점이 되는 커밋
2. branch, merge, confilct가 각각 무엇을 의미하는지 알려주세요.
- **branch** : 독립적인 작업 공간을 만드는 기능
- **merge** : 서로 다른 브랜치의 내용을 하나로 합치는 작업
- **conflict** : 병합시 같으 부분이 서로 다르게 수정되어 충돌이 발생한 상태
3. merge를 왜 사용해야 하나요?
- 여러 개발이 완료된 브랜치들을 메인 브랜치에 통합하기 위해

4. 두 개의 branch를 병합(merge)할 때, 병합되는 쪽이 아닌 병합받는 쪽에 checkout을 해야하는 이유를 history와 관련지어 설명해주세요. (ppt p.6 참조)
- 병합 결과가 현재 작업중인 브랜치(checkout된 브랜치)에 반영이 되기 때문. 그래야 병합 히스토리가 일관성있게 유지가 된다

# Merge & Conflict
1. `Auto-merging`이 무엇인지 알려주세요.
- git이 자동으로 충돌없이 병합을 수행하는 기능
2. 스터디 시간에 배운 `conflict`는 무엇을 의미하는 지 알려주세요.
- merge시 같은 파일의 같은 부분이 다르게 수정되어 병합 할 수 없는 상황
3. 다음 세가지 `서로 다른 파일 병합`, `같은 파일 다른 부분 병합`, `같은 파일 같은 부분 병합` 중 `auto-merging` 기능이 제공되는 것을 구분하고 제공되지 않는 것은 왜 제공되지 않는 지 알려주세요.
- 서로 다른 파일 병합, 같은 파일 다른 부분 병합 : auto merging 가능
- 같은 파일 같은 부분 병합 : auto merging 불가능 (충돌 발생)
    - git이 어느 쪽의 변경사항을 선택해야 할지 결정 할 수 없기 때문
4. `fig.1`은 `conflict` 발생을 유도한 후 명령창입니다. 입력한 명령어는 다음과 같을 때, 이후 `conflict`를 해결하는 방법을 알려주세요.
```bash
git checkout master
git log --all --graph --oneline
git branch
git merge o2
git status
```
![alt text](/sources/conflict-1.png)*fig.1*
- 충돌이 발생한 파일을 열어서 충돌이 발생한 부분을 수동으로 수정한다. 그리고 git add, commit해서 병합커밋 생성
# Cherry-pick & rebase
1. `cherry-pick`와 `rebase`는 어떤 기능의 명령어이고 왜 필요한지 알려주세요.
- **cherry-pick** : 특정 커밋만을 선택적으로 현재 브랜치에 적용하는 기능(특정 변경사항만 적용하고 싶을때)
- **rebase** : 브랜치의 base를 다른 지점으로 옮기는 기능 (히스토리를 깔끔하게 하기 위해)
2. `fig.2`을 직접 구현한 결과가 `fig.3`입니다. `fig.2`의 결과와 같게 만들려면 어떻게 해야하는 지 알려주세요. 
![alt text](/sources/cherry-pick-1.png)*fig.2*
![alt text](/sources/rebase-merge-log.png)*fig.3*
```bash
git cherry-pick 41a0109
```
3. `fig.3`을 `fig.4`의 결과와 같게 만들고 싶다면 어떤 명령어를 쳐야하는지 알려주세요(HEAD는 HEAD->master에 있음.)
![alt text](/sources/rebase-1.png)*fig.4*
```bash
git checkout master
git rebase topic
```
4. `rebase`의 조건이 있는데 어떤 것일 지 추측해보세요.(정답이 되는 조건은 설명한 적 있음.)
- rebase의 조건은 아직 push되지않은 로컬 커밋에 대해서만 수행해야한다..?

# Advanced
1. *fig.5* 에서 `HEAD`가 `master`의 최신 버전이 아닌 `dc9d3c7`에 checkout 되어 `git merge topic`하게 된다면 어떻게 될지 추측해보세요.
![alt text](/sources/rebase-merge-log.png)*fig.5*
2. *fig.5* 에서 `git commit --amend`로 최신 버전(`33763e0`, `HEAD->master`)의 커밋 메세지를 수정할 수 있었습니다. 만약 최신 버전의 __커밋 내용__ 즉, 파일 안의 코드를 한 줄 수정하고 싶을 때는 히스토리를 아예 삭제하는 `git reset --hard dc9d3c7` 대신 어떤 명령어를 사용해야 하는지 알려주세요.
3. `cherry-pick`에서도 `conflict`가 발생할 수 있습니다. 충돌 원인을 예상해보고 해결 방법을 알려주세요.
4. 터미널에 `git merge --help`를 쳐보면 merge에도 굉장히 많은 옵션이 있음을 알 수 있습니다. 이미 실행한 merge를 취소하는 옵션을 포함해서 세 가지의 옵션을 임의로 골라 알려주세요.
5. 정말 만약에... merge 한 브랜치를 push하고 pr이 승락된 브랜치를 되돌려야한다면 어떻게 되돌릴 수 있을 지 알려주세요.....
6. branch간에 merge를 진행할 때 새로운 commit이 생겨날 수도 있고 아닐 수도 있습니다. 이 관점에서 `fast-forward merge`, `3-way merge`를 비교하여 알려주세요.
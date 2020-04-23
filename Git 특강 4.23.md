# Git 특강 4/23

## 참고 git 사이트

- 개발자 기술 면접
  - https://github.com/JaeYeopHan/Interview_Question_for_Beginner
- 주니어 개발자 채용 정보
  - https://github.com/jojoldu/junior-recruit-scheduler
- 원격 근무 회사
  - https://github.com/milooy/remote-or-flexible-work-company-in-korea
- .gitignore 파일 생성 사이트
  - http://gitignore.io/
- emoji 사이트
  - https://emojipedia.org/
- vim 연습 게임
  - https://vim-adventures.com/
- commit 메시지 참고
  - https://blog.ull.im/engineering/2019/03/10/logs-on-git.html
- 노션앱(notion)
- github student pack
  - https://education.github.com/pack
- 아이콘 
  - https://fontawesome.com/
- bootstrap
  - https://startbootstrap.com/themes/resume/
- 

## Git

- DVCS (분상형 버전 관리 시스템)

- 개발 : 리누스 토르발스

- 중요 명령어 : git status

  배쉬화면 CLI(command line interface)

  window화면 GUI(graphic user interface)

[![image-20200423101429247]()](https://github.com/sjjam/TIL/blob/master/git 특강/Git 특강 423.md)

- 구조

  - working directory

    |add

  - staging area

    |commit

  - commits

  [![image-20200423102139343]()](https://github.com/sjjam/TIL/blob/master/git 특강/Git 특강 423.md)

  세 개 모두 비어있음을 의미

## Git status를 통해 정리하기

### CLI 기초 명령어

```
# list (파일 목록)
$ ls
# change directory(디렉토리 변경)
$ cd
# 빈 파일 생성
$ touch <파일명>
```

### 상황

#### 1. add

```
$ touch a.txt
$ git status

No commits yet
# 트래킹X. 새로 생성된 파일.
Untracked files:
  # 커밋을 하기 위한 곳에 포함시키려면
  # Staging area로 이동시키려면, git add
  (use "git add <file>..." to include in what will be committed)
        a.txt
# WD O, Staging area X
nothing added to commit but untracked files present (use "git add" to track)
$ git add a.txt
$ git status
On branch master

No commits yet
# 커밋될 변경사항들(staging area O)
Changes to be committed:
  # unstage를 위해서 활용할 명령어(add 취소)
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```

#### 2. commit

```
$ git commit -m 'Create a.txt'
[master (root-commit) 376d250] Create a.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt

$ git status
On branch master
nothing to commit, working tree clean
```

- 커밋 내역 확인

```
$ git log
commit 376d25047ba5305a87f8d3fae794210a39d8e839 (HEAD -> master)
Author: sjjam <shimjm21@gmail.com>
Date:   Thu Apr 23 10:34:14 2020 +0900

    Create a.txt
    
$ git log --oneline
376d250 (HEAD -> master) Create a.txt
```

#### 3. 추가파일 변경 상태

```
$ touch b.txt
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

no changes added to commit (use "git add" and/or "git commit -a")
$ git add a.txt
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   a.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt
```

#### 4. 커밋 메시지 변경

> **주의!!** 커밋 메시지 변경시 해시값 자체가 변경되어,
>
> 이미 원격저장소에 push 한 이력에 대해선느 메시지
>
> 변경을 하면 안된다.

```
$ git commit --amend
```

- vim 텍스트 편집기가 실행된다.

  - `i`: 편집 모드

  - ```
    esc
    ```

     

    편집 모드를 종료하고, 명령 모드에서

    - :wq
      - write + quit

```
[master f260885] a.txt 추가
 Date: Thu Apr 23 10:45:10 2020 +0900
 1 file changed, 22 insertions(+), 1 deletion(-)
```

##### 4-1. 특정 파일을 빼놓고 커밋 했을 때

```
$ git add <omit_file>
$ git commit --amend
```

- 빠뜨린 파일을 add 한 이후에 commit --amend를 하면, 해당 파일까지 포함하여 재커밋이 이뤄진다.

#### 5. 작업 내용을 이전 버전으로 되돌리기

- a.k.a. 작업 하던 내용 버리기

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  # WD 변경사항들을 버리기 위해서는 restore
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git restore a.txt
$ git status
On branch master
nothing to commit, working tree clean
```

#### 6. 특정 파일/폴더 삭제 커밋

> 해당 명령어는 실제 파일이 삭제되는 것은 아니지만, git에서 삭제되었다는 이력을 남기는 것

```
$ git rm --cached b.txt
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.txt

# 주의!! 해당 파일이 물리적으로 삭제 되는 것은 아니다.
```

- 일반적으로는 .gitignore와 함께 활용한다.

  1. .gitignore 에 해당 파일 등록
  2. git rm --cached를 통해 삭제 커밋

  - 이렇게 작업을 하면, 실제 파일은 삭제되지 않지만 이후로 git으로 전혀 관리되지 않는다.

## gitignore

- git으로 관리하고 싶지 않는 파일을 등록하여 활용할 수 있다.
- 일반적으로 프로젝트 환경(IDE, OS 등)에 관련된 정보나 추가적으로 공개되면 안되는 데이터 파일 등을 설정한다.
- 일반 프로젝트 환경에 대한 정보는 우선 [gitignore.io](https://gitignore.io/)에서 프로젝트 시작할 때마다 정의하는 습관을 가지자.

```
# 특정 파일
secret.csv
# 특정 폴더
idea/
# 특정 확장자
*.csv
# 특정 폴더에서 특정 파일 빼고
!idea/a.txt
```
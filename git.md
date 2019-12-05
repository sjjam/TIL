## Git

> Git은 분산형버전관리시스템(DVCS)이다.
>
> 소스코드 형상 관리 도구로써, 작성되는 코드의 이력을 관리한다.

## 0. 기본 설정

아래의 설정은 이력 작성자(author)를 설정하는 것으로, 컴퓨터에서 최초에 한번만 설정하면 된다.



```bash
$ git config --global user.name sjjam<<본인 github 계정으로 변경
$ git config --global user.email shimjm21@gmail.com<<github 가입 이메일로 변경
```

## 1. 로컬 저장소(repository) 활용

### 1. 저장소 초기화

``` bash

```

* (master) 는 현재 있는 브랜치 위치를 뜻하며, .git 폴더가 생성된다.
* 해당 폴더를 삭제하게 되면 모든 git 과 관련된 이력이 삭제된다.

### 2. add

이력을 확정하기 위해서는 add 명령어를 통하여 staging area에 stage 시킨다.

``` bash
$ git add                      # 현재 디렉토리를 stage
$ git add README.md            # 특정 파일을 stage
$ git add images/              # 특정 폴더를 stage
```

`add`를 한 한 이후에는 항상 status 명령어를 통해 원하는 대로 되었는지 확인한다.

```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git.md
        new file:   "images/\353\257\270\354\206\214\342\223\222\354\202\264\354\260\220-\353\263\264\353\205\270\353\263\264\353\205\270.png"
        new file:   markdown.md

```

### 3. commit

`git`은 `commit` 을 통해 이력을 남긴다. 

커밋 시에는 항상 메시지를 통해 해당 이력의 정보를 나타내야 한다.

```bash
$ git commit -m 'Init'
[master (root-commit) ca4900a] Init
 3 files changed, 82 insertions(+)
 create mode 100644 git.md
 create mode 100644 "images/\353\257\270\354\206\214\342\223\222\354\202\264\354\260\220-\353\263\264\353\205\270\353\263\264\353\205\270.png"
 create mode 100644 markdown.md

```

커밋 목록은 아래의 명령어를 통해 확인 가능하다.

```bash
$ git log
commit ca4900a34ea7727d7f648466d18e83a3fe827ee0 (HEAD -> master)
Author: sjjam <shimjm21@gmail.com>
Date:   Thu Dec 5 16:53:31 2019 +0900

    Init

```


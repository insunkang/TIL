# Git 

> Git은 분산형버전관리시스템(DVCS)이다.
>
> 소스코드 형상 관리 도구로써, 작성되는 코드의 이력을 관리한다.

## 0. 기본설정

아래의 설정은 이력 작성자(author)를 설정하는 것으로, 컴퓨터에서 최초에 한번만 설정하면 된다.

```bash
$ git config --global user.name insunkang
$ git config --global user.email cactus2378@naver.com
```

## 1.로컬 저장소(repository) 활용

### 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/TIL/.git/
(master) $
```

* (master) 는 현재 있는 브랜치 위치를 뜻하며 .git 폴더가 생선된다.
* 해당 폴더를 삭제하게 되면 모든 git과 관련된 이력이 삭제된다.

### 2. add

이력(history)을 확정하기 위해서는 add 명령어를 통하여 staging area에 stage 시킨다.

```bash
$ git add .            # 현재 디렉토리를 stage
$ git add README.md    # 특정 파일을 stage
$ git add images/      # 특정 폴더를 stage
```

add를 한 이후에는 항상 status 명령어를 통해 원하는 대로 되었는지 확인한ㄷ.

```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   "git.PNG"
        new file:   git.md
        new file:   "images/.jpg"
        new file:   markdown.md

```

### 3. commit

`git` 은 `commit` 을 통해 이력을 남긴다.

커밋 시에는 항상 메시지를 통해 해당 이력의 정보를 나타내야 한다.

```bash
$ git commit -m 'Init'
[master (root-commit) 7dbc5e5] Init
 4 files changed, 104 insertions(+)
 create mode 100644 "git \354\264\210\352\270\260\354\204\244\354\240\225.PNG"
 create mode 100644 git.md
 create mode 100644 "images/\353\263\264\353\205\270\353\263\264\353\205\270.jpg"
 create mode 100644 markdown.md

```

커밋 목록은 아래의 명령어를 통해 확인 가능하다.

```bash
$ git log
commit 7dbc5e51124757b4f14d5dc02df34dd5e29ce62b (HEAD -> master)
Author: insunkang <cactus2378@naver.com>
Date:   Thu Dec 5 16:51:58 2019 +0900

    Init

```



## 2. 원격 저장소(remote repository) 활용

> 원격 저장소는 다양한 서비스를 통해 제공 받을수 있다.
>
> github, gitlab, bitbucket

### 1. 원격 저장소 등록

```bash
$ git remote add origin https~
```

원격 저장소(remote)를 origin 이라는 이름으로 해당 url로 설정한다.

등록된 원격 저장소는 아래의 명령어로 확인할 수 있다.

등록은 한번만 실행하면 된다.

```bash
![새로고침 하고 새로운거 저장하는 과정](../새로고침 하고 새로운거 저장하는 과정.PNG$ git remote -v
origin  https://github.com/insunkang/TIL.git (fetch)
origin  https://github.com/insunkang/TIL.git (push)

```

### 2.원격 저장소 push

```bash
$ git push origin master
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (10/10), 62.51 KiB | 10.42 MiB/s, done.
Total 10 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/insunkang/TIL.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```

origin 원격 저장소에 push 하게 되며, github에서 확인할 수 있다.

이후 작업 과정에서는 add -> commit 이력을 남기고 push로 업로드 하면 된다.![새로고침 하고 새로운거 저장하는 과정](images/새로고침 하고 새로운거 저장하는 과정-1575535640242.PNG)
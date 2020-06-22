```bash
git pull https://github.com/sjjam/django_form.git master --allow-unrelated-histories
git pull https://github.com/sjjam/django_url.git master --allow-unrelated-histories
git pull https://github.com/sjjam/django_mysite.git master --allow-unrelated-histories
```



```bash
student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git pull https://github.com/sjjam/django_form.git master --allow-unrelated-histories
warning: no common commits
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 24 (delta 0), reused 24 (delta 0), pack-reused 0
Unpacking objects: 100% (24/24), done.
From https://github.com/sjjam/django_form
 * branch            master     -> FETCH_HEAD
CONFLICT (add/add): Merge conflict in README.md
Auto-merging README.md
Automatic merge failed; fix conflicts and then commit the result.

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   .gitignore
        new file:   mysite/manage.py
        new file:   mysite/mysite/__init__.py
        new file:   mysite/mysite/settings.py
        new file:   mysite/mysite/urls.py
        new file:   mysite/mysite/wsgi.py
        new file:   mysite/pages/__init__.py
        new file:   mysite/pages/admin.py
        new file:   mysite/pages/apps.py
        new file:   mysite/pages/migrations/__init__.py
        new file:   mysite/pages/models.py
        new file:   mysite/pages/templates/catch.html
        new file:   mysite/pages/templates/loop.html
        new file:   mysite/pages/templates/throw.html
        new file:   mysite/pages/tests.py
        new file:   mysite/pages/views.py

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both added:      README.md


student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git log --oneline
43a2a7c (HEAD -> master, origin/master) first commit

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git add .

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git commit
[master 5578bfe] Merge branch 'master' of https://github.com/sjjam/django_form

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git log
commit 5578bfeb4792a925bea90d386132bd02167ec4bb (HEAD -> master)
Merge: 43a2a7c 457626f
Author: sjjam <shimjm21@gmail.com>
Date:   Mon Jun 15 16:54:47 2020 +0900

    Merge branch 'master' of https://github.com/sjjam/django_form

commit 43a2a7c49d3fcbe649f3cdfbff7fb44aa50ac138 (origin/master)
Author: sjjam <shimjm21@gmail.com>
Date:   Mon Jun 15 11:47:42 2020 +0900

    first commit

commit 457626f5e730b4788662252336ce94cb68d911c7
Author: sjjam <shimjm21@gmail.com>
Date:   Fri Jun 12 17:23:51 2020 +0900

    06/12 form

commit c87c25dfef63d76bdcc3811778960b23ece8ff54
Author: sjjam <shimjm21@gmail.com>
Date:   Fri Jun 12 09:23:24 2020 +0900


student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git pull https://github.com/sjjam/django_url.git master --allow-unrelated-histories

warning: no common commits
remote: Enumerating objects: 73, done.
remote: Counting objects: 100% (73/73), done.
remote: Compressing objects: 100% (53/53), done.
remote: Total 73 (delta 10), reused 73 (delta 10), pack-reused 0
Unpacking objects: 100% (73/73), done.
From https://github.com/sjjam/django_url
 * branch            master     -> FETCH_HEAD
CONFLICT (add/add): Merge conflict in mysite/pages/views.py
Auto-merging mysite/pages/views.py
CONFLICT (add/add): Merge conflict in mysite/mysite/urls.py
Auto-merging mysite/mysite/urls.py
CONFLICT (add/add): Merge conflict in mysite/mysite/settings.py
Auto-merging mysite/mysite/settings.py
CONFLICT (add/add): Merge conflict in README.md
Auto-merging README.md
Automatic merge failed; fix conflicts and then commit the result.

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   mysite/db.sqlite3
        new file:   mysite/mysite/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/settings.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/urls.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/wsgi.cpython-37.pyc
        new file:   mysite/mysite/templates/base.html
        new file:   mysite/pages/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/__pycache__/admin.cpython-37.pyc
        new file:   mysite/pages/__pycache__/models.cpython-37.pyc
        new file:   mysite/pages/__pycache__/urls.cpython-37.pyc
        new file:   mysite/pages/__pycache__/views.cpython-37.pyc
        new file:   mysite/pages/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/templates/pages/artii.html
        new file:   mysite/pages/templates/pages/catch.html
        new file:   mysite/pages/templates/pages/food.html
        new file:   mysite/pages/templates/pages/index.html
        new file:   mysite/pages/templates/pages/lotto.html
        new file:   mysite/pages/templates/pages/lotto_result.html
        new file:   mysite/pages/templates/pages/result.html
        new file:   mysite/pages/templates/pages/throw.html
        new file:   mysite/pages/urls.py
        new file:   mysite/secondapp/__init__.py
        new file:   mysite/secondapp/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/admin.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/models.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/urls.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/views.cpython-37.pyc
        new file:   mysite/secondapp/admin.py
        new file:   mysite/secondapp/apps.py
        new file:   mysite/secondapp/migrations/__init__.py
        new file:   mysite/secondapp/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/models.py
        new file:   mysite/secondapp/static/secondapp/images/bono.png
        new file:   mysite/secondapp/templates/secondapp/index.html
        new file:   mysite/secondapp/templates/secondapp/static_example.html
        new file:   mysite/secondapp/tests.py
        new file:   mysite/secondapp/urls.py
        new file:   mysite/secondapp/views.py

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both added:      README.md
        both added:      mysite/mysite/settings.py
        both added:      mysite/mysite/urls.py
        both added:      mysite/pages/views.py


student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git merge --abort

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ ls
mysite/  README.md

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ ls
mysite/  README.md

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ mkdir django_form

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ mv mysite/ django_form/mysite/

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ ls
django_form/  README.md

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    mysite/manage.py
        deleted:    mysite/mysite/__init__.py
        deleted:    mysite/mysite/settings.py
        deleted:    mysite/mysite/urls.py
        deleted:    mysite/mysite/wsgi.py
        deleted:    mysite/pages/__init__.py
        deleted:    mysite/pages/admin.py
        deleted:    mysite/pages/apps.py
        deleted:    mysite/pages/migrations/__init__.py
        deleted:    mysite/pages/models.py
        deleted:    mysite/pages/templates/catch.html
        deleted:    mysite/pages/templates/loop.html
        deleted:    mysite/pages/templates/throw.html
        deleted:    mysite/pages/tests.py
        deleted:    mysite/pages/views.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        django_form/

no changes added to commit (use "git add" and/or "git commit -a")

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git add .

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git commit -m 'move files'
[master d25ec68] move files
 15 files changed, 0 insertions(+), 0 deletions(-)
 rename {mysite => django_form/mysite}/manage.py (100%)
 rename {mysite => django_form/mysite}/mysite/__init__.py (100%)
 rename {mysite => django_form/mysite}/mysite/settings.py (100%)
 rename {mysite => django_form/mysite}/mysite/urls.py (100%)
 rename {mysite => django_form/mysite}/mysite/wsgi.py (100%)
 rename {mysite => django_form/mysite}/pages/__init__.py (100%)
 rename {mysite => django_form/mysite}/pages/admin.py (100%)
 rename {mysite => django_form/mysite}/pages/apps.py (100%)
 rename {mysite => django_form/mysite}/pages/migrations/__init__.py (100%)
 rename {mysite => django_form/mysite}/pages/models.py (100%)
 rename {mysite => django_form/mysite}/pages/templates/catch.html (100%)
 rename {mysite => django_form/mysite}/pages/templates/loop.html (100%)
 rename {mysite => django_form/mysite}/pages/templates/throw.html (100%)
 rename {mysite => django_form/mysite}/pages/tests.py (100%)
 rename {mysite => django_form/mysite}/pages/views.py (100%)

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git pull https://github.com/sjjam/django_url.git master --allow-unrelated-histories
From https://github.com/sjjam/django_url
 * branch            master     -> FETCH_HEAD
CONFLICT (add/add): Merge conflict in README.md
Auto-merging README.md
Automatic merge failed; fix conflicts and then commit the result.

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   mysite/db.sqlite3
        new file:   mysite/manage.py
        new file:   mysite/mysite/__init__.py
        new file:   mysite/mysite/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/settings.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/urls.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/wsgi.cpython-37.pyc
        new file:   mysite/mysite/settings.py
        new file:   mysite/mysite/templates/base.html
        new file:   mysite/mysite/urls.py
        new file:   mysite/mysite/wsgi.py
        new file:   mysite/pages/__init__.py
        new file:   mysite/pages/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/__pycache__/admin.cpython-37.pyc
        new file:   mysite/pages/__pycache__/models.cpython-37.pyc
        new file:   mysite/pages/__pycache__/urls.cpython-37.pyc
        new file:   mysite/pages/__pycache__/views.cpython-37.pyc
        new file:   mysite/pages/admin.py
        new file:   mysite/pages/apps.py
        new file:   mysite/pages/migrations/__init__.py
        new file:   mysite/pages/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/models.py
        new file:   mysite/pages/templates/pages/artii.html
        new file:   mysite/pages/templates/pages/catch.html
        new file:   mysite/pages/templates/pages/food.html
        new file:   mysite/pages/templates/pages/index.html
        new file:   mysite/pages/templates/pages/lotto.html
        new file:   mysite/pages/templates/pages/lotto_result.html
        new file:   mysite/pages/templates/pages/result.html
        new file:   mysite/pages/templates/pages/throw.html
        new file:   mysite/pages/tests.py
        new file:   mysite/pages/urls.py
        new file:   mysite/pages/views.py
        new file:   mysite/secondapp/__init__.py
        new file:   mysite/secondapp/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/admin.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/models.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/urls.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/views.cpython-37.pyc
        new file:   mysite/secondapp/admin.py
        new file:   mysite/secondapp/apps.py
        new file:   mysite/secondapp/migrations/__init__.py
        new file:   mysite/secondapp/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/models.py
        new file:   mysite/secondapp/static/secondapp/images/bono.png
        new file:   mysite/secondapp/templates/secondapp/index.html
        new file:   mysite/secondapp/templates/secondapp/static_example.html
        new file:   mysite/secondapp/tests.py
        new file:   mysite/secondapp/urls.py
        new file:   mysite/secondapp/views.py

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both added:      README.md


student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 4 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   mysite/db.sqlite3
        new file:   mysite/manage.py
        new file:   mysite/mysite/__init__.py
        new file:   mysite/mysite/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/settings.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/urls.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/wsgi.cpython-37.pyc
        new file:   mysite/mysite/settings.py
        new file:   mysite/mysite/templates/base.html
        new file:   mysite/mysite/urls.py
        new file:   mysite/mysite/wsgi.py
        new file:   mysite/pages/__init__.py
        new file:   mysite/pages/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/__pycache__/admin.cpython-37.pyc
        new file:   mysite/pages/__pycache__/models.cpython-37.pyc
        new file:   mysite/pages/__pycache__/urls.cpython-37.pyc
        new file:   mysite/pages/__pycache__/views.cpython-37.pyc
        new file:   mysite/pages/admin.py
        new file:   mysite/pages/apps.py
        new file:   mysite/pages/migrations/__init__.py
        new file:   mysite/pages/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/models.py
        new file:   mysite/pages/templates/pages/artii.html
        new file:   mysite/pages/templates/pages/catch.html
        new file:   mysite/pages/templates/pages/food.html
        new file:   mysite/pages/templates/pages/index.html
        new file:   mysite/pages/templates/pages/lotto.html
        new file:   mysite/pages/templates/pages/lotto_result.html
        new file:   mysite/pages/templates/pages/result.html
        new file:   mysite/pages/templates/pages/throw.html
        new file:   mysite/pages/tests.py
        new file:   mysite/pages/urls.py
        new file:   mysite/pages/views.py
        new file:   mysite/secondapp/__init__.py
        new file:   mysite/secondapp/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/admin.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/models.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/urls.cpython-37.pyc
        new file:   mysite/secondapp/__pycache__/views.cpython-37.pyc
        new file:   mysite/secondapp/admin.py
        new file:   mysite/secondapp/apps.py
        new file:   mysite/secondapp/migrations/__init__.py
        new file:   mysite/secondapp/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/secondapp/models.py
        new file:   mysite/secondapp/static/secondapp/images/bono.png
        new file:   mysite/secondapp/templates/secondapp/index.html
        new file:   mysite/secondapp/templates/secondapp/static_example.html
        new file:   mysite/secondapp/tests.py
        new file:   mysite/secondapp/urls.py
        new file:   mysite/secondapp/views.py

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both added:      README.md


student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ ls
django_form/  mysite/  README.md

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ mkdir django_url

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ mv mysite/ django_url/mysite/

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git add .

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git commit
[master 94f3e37] Merge branch 'master' of https://github.com/sjjam/django_url

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git log --oneline
94f3e37 (HEAD -> master) Merge branch 'master' of https://github.com/sjjam/django_url
d25ec68 move files
5578bfe Merge branch 'master' of https://github.com/sjjam/django_form
43a2a7c (origin/master) first commit
5d56a8f 06/15 appname <EC><B6><94><EA><B0><80>
11790c3 06/13 url, <EC><95><B1> <EB><B6><84><EB><A6><AC>
abded89 first commit
457626f 06/12 form
c87c25d first commit

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git pull https://github.com/sjjam/django_mysite.git master --allow-unrelated-histories
warning: no common commits
remote: Enumerating objects: 43, done.
remote: Counting objects: 100% (43/43), done.
remote: Compressing objects: 100% (33/33), done.
remote: Total 43 (delta 1), reused 43 (delta 1), pack-reused 0
Unpacking objects: 100% (43/43), done.
From https://github.com/sjjam/django_mysite
 * branch            master     -> FETCH_HEAD
CONFLICT (add/add): Merge conflict in README.md
Auto-merging README.md
Automatic merge failed; fix conflicts and then commit the result.

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ ls
django_form/  django_url/  mysite/  README.md

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 8 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        new file:   mysite/db.sqlite3
        new file:   mysite/manage.py
        new file:   mysite/mysite/__init__.py
        new file:   mysite/mysite/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/settings.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/urls.cpython-37.pyc
        new file:   mysite/mysite/__pycache__/wsgi.cpython-37.pyc
        new file:   mysite/mysite/settings.py
        new file:   mysite/mysite/urls.py
        new file:   mysite/mysite/wsgi.py
        new file:   mysite/pages/__init__.py
        new file:   mysite/pages/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/__pycache__/admin.cpython-37.pyc
        new file:   mysite/pages/__pycache__/models.cpython-37.pyc
        new file:   mysite/pages/__pycache__/views.cpython-37.pyc
        new file:   mysite/pages/admin.py
        new file:   mysite/pages/apps.py
        new file:   mysite/pages/migrations/__init__.py
        new file:   mysite/pages/migrations/__pycache__/__init__.cpython-37.pyc
        new file:   mysite/pages/models.py
        new file:   mysite/pages/templates/class_name.html
        new file:   mysite/pages/templates/dtl.html
        new file:   mysite/pages/templates/forif.html
        new file:   mysite/pages/templates/gugu.html
        new file:   mysite/pages/templates/hello.html
        new file:   mysite/pages/templates/index.html
        new file:   mysite/pages/templates/introduce.html
        new file:   mysite/pages/templates/name.html
        new file:   mysite/pages/templates/times.html
        new file:   mysite/pages/templates/yourinfo.html
        new file:   mysite/pages/templates/yourname.html
        new file:   mysite/pages/tests.py
        new file:   mysite/pages/views.py

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both added:      README.md


student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ mkdir django_mysite

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ mv django_mysite/ django_mysite/mysite
mv: cannot move 'django_mysite/' to a subdirectory of itself, 'django_mysite/mysite'

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ mv mysite/ django_mysite/mysite

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git add .

student@M16014 MINGW64 ~/Desktop/tmp/django (master|MERGING)
$ git commit
[master 7defab3] Merge branch 'master' of https://github.com/sjjam/django_mysite

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 11 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git remote
origin

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git remote -v
origin  https://github.com/sjjam/django.git (fetch)
origin  https://github.com/sjjam/django.git (push)

student@M16014 MINGW64 ~/Desktop/tmp/django (master)
$ git push origin master
Enumerating objects: 148, done.
Counting objects: 100% (148/148), done.
Delta compression using up to 8 threads
Compressing objects: 100% (119/119), done.
Writing objects: 100% (146/146), 34.28 KiB | 1.43 MiB/s, done.
Total 146 (delta 27), reused 0 (delta 0)
remote: Resolving deltas: 100% (27/27), done.
To https://github.com/sjjam/django.git
   43a2a7c..7defab3  master -> master


```


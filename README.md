# git-sami

### git requirments

- Track everything
- Os independent
- Uniuq id  
- No content change  

### git objects

- blob => file
- tree => dir
- commit => snapshot

### two tier arch

![alt text](image.png)

### three tier arch

![alt text](image-1.png)

### example for creating a file

![alt text](image-2.png)

### untracked then tracked

![alt text](image-3.png)

## install
>
> apt install git

### Identity
>
> git config --global user.name "John Doe"
> git config --global user.email <johndoe@example.com>

### Configurations
>
> git config --list

> git config --global # User (global) -> ~/.gitconfig

> git config --system # System -> /etc/gitconfig

> git config  # Project -> /.git/conifg

### Text Editor
>
> git config --global core.editor vi [or code 🙂]

### Color Output
>
> git config --global color.ui true

# LAB01

```bash
mkdir gitwork
cd gitwork
ls
echo "Hello, Git" >> file.txt
cat file.txt
ls al
ls -al
git init
ls -al
cd .git
ls .git
ls
ls -al
ls -al objects
git status
cd ..
git status

root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# git add *
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file.txt

cd .git/
cd objects/b7/
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork/.git/objects/b7# git cat-file -t b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
blob

root@Haytham:/mnt/d/HandsOn/git-sami/gitwork/.git/objects/b7# git cat-file -s b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
11

root@Haytham:/mnt/d/HandsOn/git-sami/gitwork/.git/objects/b7# git cat-file -p b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
Hello, Git

## to commit 
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# git commit -m "Initial commit"
[master (root-commit) 4207fd4] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# git status
On branch master
nothing to commit, working tree clean
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# 

### you will find three objects
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork# cd .git/objects/
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork/.git/objects# ls
15  42  b7  info  pack
root@Haytham:/mnt/d/HandsOn/git-sami/gitwork/.git/objects# 
```

### LAB02
```bash
haytham@server:~/git-sami$ vim file.txt
haytham@server:~/git-sami$ cat file.txt 
Hello, Git
haytham@server:~/git-sami$ git status 
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        file.txt

nothing added to commit but untracked files present (use "git add" to track)
haytham@server:~/git-sami$ git status -s
?? file.txt
haytham@server:~/git-sami$ git add file.txt 
haytham@server:~/git-sami$ git status -s
A  file.txt
haytham@server:~/git-sami$ git commit -m "Added file.txt"
[main 33ca0b3] Added file.txt
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
haytham@server:~/git-sami$ git log
commit 33ca0b34963ecd89db14227a477ed93fe2c916f8 (HEAD -> main)
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:01:12 2026 +0300

    Added file.txt

commit a0147301319dd4751004b5fef3cce6f4cc3a6614 (origin/main, origin/HEAD)
Author: Haytham <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 21:49:10 2026 +0300

    added  steps

commit 151d67d49f1a31993515286eccbb5f1fdea49860
Author: haythammohamd <71211485+HaythamMohamd@users.noreply.github.com>
Date:   Tue Jun 16 19:18:10 2026 +0300

    Initial commit
haytham@server:~/git-sami$ find .git/objects/ -type f
.git/objects/pack/pack-9ce473bfff77765fd8aa15ecbaec5fba4268875c.pack
.git/objects/pack/pack-9ce473bfff77765fd8aa15ecbaec5fba4268875c.rev
.git/objects/pack/pack-9ce473bfff77765fd8aa15ecbaec5fba4268875c.idx
.git/objects/b7/aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
.git/objects/c7/a67c32b3307681733613dc013f7c532b094886
.git/objects/33/ca0b34963ecd89db14227a477ed93fe2c916f8
haytham@server:~/git-sami$ git cat-file -p b7ae
Hello, Git
haytham@server:~/git-sami$ git cat-file -p c7a6
100644 blob 69b537a942d9aec17971d0ad1c48c54d6f0b7252    README.md
100644 blob b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e    file.txt
160000 commit 4207fd46da9cee8fd8a31f179e7bb7e926bd2ce1  gitwork
100644 blob 16000abd9a2251fd921aa3917e1a3f1f32886747    image-1.png
100644 blob ad9cafa081f16e1f4f222cbf73b97817b3bc0826    image-2.png
100644 blob 82bc437851ca3e4bb6f8a67073a9a03b90b7f332    image-3.png
100644 blob 16000abd9a2251fd921aa3917e1a3f1f32886747    image.png
```

### git is working as linked list
<img width="727" height="282" alt="image" src="https://github.com/user-attachments/assets/4cf6f1ee-2cac-4456-8403-a7536d267117" />

### LAB03
```bash
haytham@server:~/git-sami$ vim file.txt 
haytham@server:~/git-sami$ git status -s
 M file.txt
haytham@server:~/git-sami$ cat file.txt 
Hello, Git
Second line in file.txt
Third line in file.txt
haytham@server:~/git-sami$ git status -s
 M file.txt
haytham@server:~/git-sami$ 
haytham@server:~/git-sami$ ### to know the diff
haytham@server:~/git-sami$ git diff
diff --git a/file.txt b/file.txt
index b7aec52..8481662 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 Hello, Git
+Second line in file.txt
+Third line in file.txt


haytham@server:~/git-sami$ ## if you make git add ., there is no difference
haytham@server:~/git-sami$ git status 
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   file.txt

no changes added to commit (use "git add" and/or "git commit -a")
haytham@server:~/git-sami$ git add .
haytham@server:~/git-sami$ git diff
haytham@server:~/git-sami$

haytham@server:~/git-sami$ ## to get difference between working dir and staging
haytham@server:~/git-sami$ git diff --staged
diff --git a/file.txt b/file.txt
index b7aec52..8481662 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 Hello, Git
+Second line in file.txt
+Third line in file.txt
haytham@server:~/git-sami$


haytham@server:~/git-sami$ ## to make the commit open with vim
haytham@server:~/git-sami$ git config --global core.edior vim 
haytham@server:~/git-sami$ git commit
[main f470813] Third line added
 1 file changed, 2 insertions(+)
haytham@server:~/git-sami$ git log 
commit f4708131848cae95c640b9ce73b75676d1598b88 (HEAD -> main)
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:12:20 2026 +0300

    Third line added

commit 33ca0b34963ecd89db14227a477ed93fe2c916f8
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:01:12 2026 +0300

    Added file.txt

commit a0147301319dd4751004b5fef3cce6f4cc3a6614 (origin/main, origin/HEAD)
Author: Haytham <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 21:49:10 2026 +0300

    added  steps

commit 151d67d49f1a31993515286eccbb5f1fdea49860
Author: haythammohamd <71211485+HaythamMohamd@users.noreply.github.com>
Date:   Tue Jun 16 19:18:10 2026 +0300

    Initial commit


haytham@server:~/git-sami$ ## to make the commit open with vim
haytham@server:~/git-sami$ git config --global core.edior vim 
haytham@server:~/git-sami$ git commit
[main f470813] Third line added
 1 file changed, 2 insertions(+)
haytham@server:~/git-sami$ git log 
commit f4708131848cae95c640b9ce73b75676d1598b88 (HEAD -> main)
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:12:20 2026 +0300

    Third line added

commit 33ca0b34963ecd89db14227a477ed93fe2c916f8
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:01:12 2026 +0300

    Added file.txt

commit a0147301319dd4751004b5fef3cce6f4cc3a6614 (origin/main, origin/HEAD)
Author: Haytham <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 21:49:10 2026 +0300

    added  steps

commit 151d67d49f1a31993515286eccbb5f1fdea49860
Author: haythammohamd <71211485+HaythamMohamd@users.noreply.github.com>
Date:   Tue Jun 16 19:18:10 2026 +0300

    Initial commit
haytham@server:~/git-sami$ 
haytham@server:~/git-sami$ ### git log
haytham@server:~/git-sami$ git log
commit f4708131848cae95c640b9ce73b75676d1598b88 (HEAD -> main)
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:12:20 2026 +0300

    Third line added

commit 33ca0b34963ecd89db14227a477ed93fe2c916f8
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:01:12 2026 +0300

    Added file.txt

commit a0147301319dd4751004b5fef3cce6f4cc3a6614 (origin/main, origin/HEAD)
Author: Haytham <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 21:49:10 2026 +0300

    added  steps

commit 151d67d49f1a31993515286eccbb5f1fdea49860
Author: haythammohamd <71211485+HaythamMohamd@users.noreply.github.com>
Date:   Tue Jun 16 19:18:10 2026 +0300

    Initial commit
haytham@server:~/git-sami$ git log --oneline
f470813 (HEAD -> main) Third line added
33ca0b3 Added file.txt
a014730 (origin/main, origin/HEAD) added  steps
151d67d Initial commit
haytham@server:~/git-sami$ git log --oneline file.txt
f470813 (HEAD -> main) Third line added
33ca0b3 Added file.txt
haytham@server:~/git-sami$ git log --oneline -2
f470813 (HEAD -> main) Third line added
33ca0b3 Added file.txt
haytham@server:~/git-sami$ git show f470813
commit f4708131848cae95c640b9ce73b75676d1598b88 (HEAD -> main)
Author: haytham.mo7amed <haytham.mo7amed@gmail.com>
Date:   Tue Jun 16 22:12:20 2026 +0300

    Third line added

diff --git a/file.txt b/file.txt
index b7aec52..8481662 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 Hello, Git
+Second line in file.txt
+Third line in file.txt
haytham@server:~/git-sami$ git log --oneline --graph
* f470813 (HEAD -> main) Third line added
* 33ca0b3 Added file.txt
* a014730 (origin/main, origin/HEAD) added  steps
* 151d67d Initial commit
haytham@server:~/git-sami$ git diff 33ca0b3..f470813
diff --git a/file.txt b/file.txt
index b7aec52..8481662 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1,3 @@
 Hello, Git
+Second line in file.txt
+Third line in file.txt




haytham@server:~/git-sami$ ## if you forget add file or missed up the commit msg
haytham@server:~/git-sami$ git commit --amend
[main 79def9a] Third line added - edited with 'git commit --amend'
 Date: Tue Jun 16 22:12:20 2026 +0300
 1 file changed, 2 insertions(+)
haytham@server:~/git-sami$ git log --oneline 
79def9a (HEAD -> main) Third line added - edited with 'git commit --amend'
33ca0b3 Added file.txt
a014730 (origin/main, origin/HEAD) added  steps
151d67d Initial commit
haytham@server:~/git-sami$ 
```

### restore from working dir
```bash
haytham@server:~/git-sami$ echo "First line in file" >> file.txt 
haytham@server:~/git-sami$ 
haytham@server:~/git-sami$ cat file.txt 
Hello, Git
First line in file
haytham@server:~/git-sami$ 
haytham@server:~/git-sami$ git status 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   file.txt

no changes added to commit (use "git add" and/or "git commit -a")
haytham@server:~/git-sami$ 
haytham@server:~/git-sami$ ## el file dah f el working dir, need to restore it
haytham@server:~/git-sami$ git restore file.txt 
haytham@server:~/git-sami$ git status 
On branch master
nothing to commit, working tree clean
haytham@server:~/git-sami$ 
```

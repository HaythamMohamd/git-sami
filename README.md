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

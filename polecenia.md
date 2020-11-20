git init 

git config --global user.name "Mateusz Kulesza"
git config --global user.email "mateusz@placki.com"

code C:/Użytkownicy/<moj user>/.gitconfig
code ~/.gitconfig
code .git/config

git status
git add readme.txt
git commit 

git commit -m "Opis zmian"
git commit --amend

# VIM
a - WPROWADZANIE TEKSTU
ESC - Wyłacz wprowadzanie
:q! - Przerwij commit
:wq - Zapisz komunikat i utwórz commit 

# Add move remove
git add .
git mv index.html strona/index.html
git rm readme.txt

# Checkout 
git checkout <file>
git checkout <rev> <file>


# Internals -  DO NOT USE!
https://git-scm.com/book/en/v2/Git-Internals-Git-Objects
git hash-object test.txt
git hash-object -w test.txt
.git/objects/32/19ed06858e627c54e3272d7a260509b63d83a7

# Remove dangling objects
git prune 

git cat-file -p <hash>
git update-index --add --cacheinfo 100644 3219ed06858e627c54e3272d7a260509b63d83a7 test.txt

git write-tree
58a93b5cc43c5a6d3135420cb6d72cac0d2dfa26 

git update-index --add --cacheinfo 100644 a69c0feac9815fe47cecb849931d858109a5a0c9 child.txt
git write-tree
b2b2f5acab4847a899634ccaee04b947679723dd

git read-tree 85f68134798c7fa0e3e4a6ba29ddcfffd7917df6
git read-tree --prefix=katalog b2b2f5acab4847a899634ccaee04b947679723dd

git write-tree
81824d89a5cd013fce300b105fa1ebea75bb61d1

git cat-file -p 81824d89a5cd013fce300b105fa1ebea75bb61d1
040000 tree b2b2f5acab4847a899634ccaee04b947679723dd    katalog
100644 blob 3219ed06858e627c54e3272d7a260509b63d83a7    test.txt
100644 blob 30d74d258442c7c65512eafab474568dd706c430    test2.txt

git commit-tree 81824d89a5cd013fce300b105fa1ebea75bb61d1 -m "Self made commit" -p master
dcd446dcb6cc08fe7a76b094ec926f06e3d39f31

git cat-file -p dcd446dcb6cc08fe7a76b094ec926f06e3d39f31

# Git show
git show b64ee9b06
git show master
git show v12

# Git log 
git log -1
git log -5
git log b64ee9..c926f0

git log --before "2 hours ago" --after "3 hours ago" --author "Mateusz" --grep "plik"

git log -- strona/
git log -- index.html



git log --format="short" 
git log --format="full" 
git log --format="oneline" 
git log --oneline
git log --format="%h %s"

# Git Diff
git diff
git diff HEAD
git diff b64ee9
git diff HEAD~3
git diff HEAD~1..HEAD~2
git diff HEAD~3 sciezka/do/pliku
git diff HEAD~1..HEAD~2 sciezka/do/pliku

git diff --cached


# Tag
git tag
git tag v1.1
git tag v1.1 -a 
git tag v1.1 -a -m "Opis"

git tag -l
git tag -l -n

# Branch
git branch
git branch nowy_branch <commitRef>

git checkout nowy_branch
git switch nowy_branch

git checkout -b nowy_branch
git switch -c nowy_branch

git branch -d do_usuniecia
git branch -D do_usuniecia

git branch -d wip-demo-x
error: The branch 'wip-demo-x' is not fully merged.
If you are sure you want to delete it, run 'git branch -D wip-demo-x'.


# Merge
git merge inny_branch
git merge inny_branch --no-ff

# Remote
git clone zrodlo lokalny_katalog
git remote 
git remote show origin
git remote add nazwa_serwera lokalizacja_na_serwerze

git fetch origin/master
git merge FETCH_HEAD

git pull origin master:master
git pull origin zdalny_branch:moj_branch
git pull 

git remote add kopia C:/Projects/altkom/git-open-listopad-clone
git push kopia master:master 
git push kopia master

// Set remote branch and track in local
git push -u origin branch

// Set local branch to track remote branch
git checkout -b <branch>
git branch -u <remote>/<branch>


## SSH Key
ssh-keygen

Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/<USER>/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/ev45i/.ssh/id_rsa
Your public key has been saved in /c/Users/ev45i/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:APz9YssGCmtYEw0Ld2Ih2wlTv4YqrHtF/twf5C4BehM ev45i@DESKTOP-10PBE5H
The key's randomart image is:
+---[RSA 3072]----+
|+.oo.            |
|.*=oo.           |
|.+o*....         |
|  o.o.E..        |
|  .+o. oS..      |
|..+.+ + +o.      |
|o+ = = * +o      |
|+ + . o *. .     |
|o+     . oo      |
+----[SHA256]-----+

// GET PUBLIC KEY
cat ~/.ssh/id_rsa.pub

# Praca zdalna
git checkout -b <nazwa_brancha>
// tworzym plik autorzy/<imie_litera>.html
git add .
git commit -m "O autorze - Mateusz K."
git push -u origin <nazwa_brancha>


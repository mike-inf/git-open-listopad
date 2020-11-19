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
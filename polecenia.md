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
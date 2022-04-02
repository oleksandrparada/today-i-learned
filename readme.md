* git config --list - деталі конфігу
* touch NAME (e.g. foo.txt) - створити файл
* mkdir NAME (e.g. bar) - створити директорію
* cp NAME_FILE NEW_NAME (cp ./foo.txt ./bar.txt) - скопіювати файл
* mv NAME NEW NAME (mv foo.txt ../foo-3.txt) - перенести файл
* cat FILE_NAME (cat first-file.txt) - вивести що є в файлі
* ls - виводить файли в директорії
* ls -a - виводить файли в директорії разом з прихованими afqkfvb
* cd NAME(e.g. ~/Desktop/module-git) - переходить до директорії, яку вказуєм
* cd .. - на рівень вище по директорії

* git log - історія змін
* git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short - формат простий для змін

* git init - створення .git репозиторія
* tree.com //a //f - показати директорію гіт
* git status - статус репозиторія, файлик які змінили, створили, т.д.

* git add NAME (e.g. first-file.txt) - додати файл, щоб протрекувати зміни
* git add . - додати всі файли
* git restore --staged foo.txt - забрати файл foo.txt з трекінгу

* git commit -m "comment" - коміт змін з коментарем
* git branch NAME - створити гілку
* git checkout NAME - перейти на гілку
* git checkout -b NAME - створити гілку + перейти на неї

**З'єднання гілок**:
* git merge - з'єднати дві гілки, кожна з яких містить унікальний коміт, відповідна жодна з них не містить повного набору "робочої інфи" в цьому репозиторії. Окремо checkout + merge до іншої. 

* git rebase SECONDARY_BRANCH_NAME- перемістити зміни з другорядної гілки до змін з гілки main. Тоді це буде виглядати наче ці зміни були додані одна за одною, хоча насправді вони були додані одночасно
* git rebase MAIN_BRANCH_NAME - просунути посилання гілки main вперед в історії до додаткової гілки

**Пересування**:
* HEAD - вказівник. місце, де зараз знаходишся
* hash - унікальний код коміта
* git checkout HASH_NAME (e.g. f2de) - пересуватись по хешам
* git checkout HEAD^ - пересуватись вище HEAD. 
* git checkout HEAD^^ - пересуватись вверх по гілці на 2 кроки
* git checkout HEAD~3 - пересуватись вверх на 3 коміти
* git branch -f BRANCH_NAME PLACE (BRANCH_NAME - e.g. main, bugFix) (PLACE - e.g. HEAD^, HEAD~3, hash) - переспрямувати бранч на якийсь конкретний коміт
* git reset PLACE (e.g. HEAD^, HEAD~3, hash) - відміняє зміни переміщуючи вказівник гілки назад в історії на старіший коміт (для локальних бранчів на власному комп’ютері). вона спричиняє "переписування історії", її не можна використовувати в ситуації коли кілька користувачів працюють з цим бранчем
* git revert HEAD - відкотити зміни й потім поділитися цими відкоченими змінами з друзями через push. Створює новий коміт (e.g. C2')

**Псевдоніми**
* git config --global alias.co checkout
* git config --global alias.ci commit
* git config --global alias.st status
* git config --global alias.br branch
* git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
* git config --global alias.type 'cat-file -t'
* git config --global alias.dump 'cat-file -p'
* alias gs='git status '
* alias ga='git add '
* alias gb='git branch '
* alias gc='git commit'
* alias gd='git diff'
* alias gco='git checkout '
* alias gk='gitk --all&'
* alias gx='gitx --all'

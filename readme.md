**Каталог .git**
* ls -C .git - каталог, в якому зберігаються всі «матеріали» git
* ls -C .git/objects - база даних об'єктів. Каталог, імена яких складаються з 2 символів. Імена каталогів є першими двома буквами хеша об'єкта, що зберігається в git.
* git cat-file - Надає вміст або інформацію про тип і розмір для об'єктів сховища
* git cat-file -p hash - pretty-print вміст об'єкта

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

* git tag NAME - тег для коміта
* git tag - показати всі теги
* git hist master --all - лог з тегами

* git init - створення .git репозиторія
* tree.com //a //f - показати директорію гіт
* git status - статус репозиторія, файлик які змінили, створили, т.д.

* git add NAME (e.g. first-file.txt) - додати файл, щоб протрекувати зміни
* git add . - додати всі файли
* git restore --staged foo.txt - забрати файл foo.txt з трекінгу

**Перенести файл в новий каталог libco**
1
* mkdir lib
* git mv hello.html lib

2
* mkdir lib
* mv hello.html lib
* git add lib/hello.html
* git rm hello.html

**Коміт/Зміна коміту**
1
* git commit -m "comment" - коміт змін з коментарем
* git commit --amend -m "" - змінити попередній коміт

2
* git add Fine_Name
* git commit -m "Wrong commit"
* git revert HEAD --no-edit
* git commit -m ""

**Гілка/Перехід по гілці**
* git branch NAME - створити гілку
* git branch - виводить локальну гілку
* git branch -a - виводить усі гілки (+ віддалені)
* git checkout NAME - перейти на гілку
* git checkout -b NAME - створити гілку + перейти на неї

**Додайте локальну гілку, котра відстежує віддалену гілку**
git branch --track style origin/style
git branch -a
git hist --max-count=2

**Створити чистий репозиторій**
git clone --bare hello hello.git (Current_REPO_NAME CLEAN_REPO_NAME) - Чисті репозиторії (без робочих каталогів) зазвичай використовуються для розшарювання

git remote add shared ../hello.git - Додати чистий репозиторій в якості віддаленого репозиторію до нашого оригінального репозиторію

**З'єднання гілок**:
* git merge - з'єднати дві гілки, кожна з яких містить унікальний коміт, відповідна жодна з них не містить повного набору "робочої інфи" в цьому репозиторії. Окремо checkout + merge до іншої. 
* git rebase SECONDARY_BRANCH_NAME- перемістити зміни з другорядної гілки до змін з гілки main. Тоді це буде виглядати наче ці зміни були додані одна за одною, хоча насправді вони були додані одночасно
* git rebase MAIN_BRANCH_NAME - просунути посилання гілки main вперед в історії до додаткової гілки
* git fetch - витягує зміни з віддаленого репозиторію, але не зливає їх з напрацьованим в локальних гілках
* git pull - еквівалент командам git fetch => git merge original/master

**Пересування**:
* HEAD - вказівник. місце, де зараз знаходишся
* hash - унікальний код коміта
* git checkout HASH_NAME (e.g. f2de) - пересуватись по хешам
* git checkout HEAD^ - пересуватись вище HEAD. 
* git checkout HEAD^^ - пересуватись вверх по гілці на 2 кроки
* git checkout HEAD~3 - пересуватись вверх на 3 коміти
* git branch -f BRANCH_NAME PLACE (BRANCH_NAME - e.g. main, bugFix) (PLACE - e.g. HEAD^, HEAD~3, hash) - переспрямувати бранч на якийсь конкретний коміт
* git reset PLACE (e.g. HEAD^, HEAD~3, hash) - відміняє зміни переміщуючи вказівник гілки назад в історії на старіший коміт (для локальних бранчів на власному комп’ютері). вона спричиняє "переписування історії", її не можна використовувати в ситуації коли кілька користувачів працюють з цим бранчем
* git reset --hard hash/tag - видалення коміту з гілки
* git revert HEAD - відкотити зміни й потім поділитися цими відкоченими змінами з друзями через push. Створює новий коміт (e.g. C2')

**Забрати з трекінгу файл**
* git add FILE_NAME - додати трекінг файлу
* git reset HEAD FILE_NAME - скидає буферну зону до HEAD. Це очищає буферну зону від змін, які ми щойно проіндексували.
* git checkout - видалити зміни в робочому каталозі.



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

## Основные "повседневные" команды GIT

- git status
- git add .
- git commit -m "GeekBrains > Yii2 > Lesson 4 > Complete"
- git push
- git pull
- git log
- git config --list

- git config --global user.email "email@gmail.com"
- git config --global user.name "Alexander Shatalov"

### Добавить каталог в индекс
- git add folder_name/

### Клонирование репозитория в текущий каталог
- git clone https://gitlab.com/test/ .

### Решение проблемы "Filename too long" для Windows

- git config --system core.longpaths true

### Обновить GIT

- Linux: git update
- Windows: git update-git-for-windows

### Create a new repository on the command line
- echo "# converter" >> README.md
- git init
- git add README.md
- git commit -m "first commit"
- git remote add origin https://github.com/avshatalov48/converter.git
- git push -u origin master

### Push an existing repository from the command line
- git remote add origin https://github.com/avshatalov48/converter.git
- git push -u origin master

### Создание новой ветки
#### https://githowto.com/ru/creating_a_branch
- git checkout -b <имяветки> (является шорткатом для git branch <имяветки> за которым идет  git checkout <имяветки>)
- git checkout <имяветки> (переключиться на ветку)

### Операции отмены
#### https://git-scm.com/book/ru/v2/Основы-Git-Операции-отмены
Например, если вы фиксируете изменения, и понимаете, что забыли проиндексировать изменения в файле, который хотели включить в коммит, можно сделать примерно так:

- git commit -m 'initial commit'
- git add forgotten_file
- git commit --amend -m 'initial commit'

В итоге получится единый коммит — второй коммит заменит результаты первого.

### Переименование последнего коммита
#### https://ru.stackoverflow.com/questions/741280/как-переименовать-коммит-в-github
- git commit --amend -m 'Новое сообщение'
- git push --force origin <имя ветки на удаленном репозитории>

### Удаление последнего коммита (который ещё не запушен)
- git reset --hard HEAD~1
- HEAD~1 означает фиксацию перед головой

### Удаление последнего коммита (который уже запушен)
- Переключаемся на ветку
- Hard Reset на нужный коммит (git reset --hard cb6fa7f62ac546602dc3dc6bb566f5a0e30985b9)
- git push -f origin название-ветки (git push -f origin master)

### Объединить несколько коммитов (изменений) в один
- Переключаемся на ветку
- Вариант 1:
  - Soft Hard Reset на нужный коммит
- Вариант 2:
  - git reset --hard HEAD~12 (Reset the current branch to the commit just before the last 12)
  - git merge --squash HEAD@{1} (HEAD@{1} is where the branch was just before the previous command)
- git push -f origin название-ветки (чтобы удалить предыдущие коммиты, иначе появится новый и останутся прежние)
- git commit (фиксируем все изменения в новом коммите)

### Перенос коммитов из одной ветки, в новую. Например, когда напушил в master
- Создаем новую ветку, мержим с веткой-источником
- Пушим её
- ветка-источник - Hard Reset на нужный коммит
- git push -f origin название-ветки-источника

### Reset
- git reset --hard (отменить все незакоммиченное)
- git reset --hard HEAD~n (отменить все незакоммиченное и откатиться на n-коммитов)

### Удаление Git репозитория
Статья: http://gearmobile.github.io/git/github-how-to-delete-repository/
- Переходим в нужный репозиторий
- Копируем его имя
- Settings > Danger Zone (внизу страницы) > Delete this repository
- Вводим имя удаляемого репозитория
- Вводим пароль GiHub

### Stash
- Сохранения изменений: git stash
- Применение сохраненных изменений: git stash pop

### Убрать файл из отслеживания
- git rm <название файла> --cached

- сделать git rm <название файла>, предварительно скопировав его, чтобы не потерять
- добавить файл в .gitignore
- закоммитить изменения

Если файл уже под контролем (был ранее добавлен в репозиторий), то .gitignore на нем работать не будет. Что, собственно, и логично. Есть два варианта:
- удалить файл -> закомитить -> добавить в .gitignore -> вернуть файл
- удалить из индекса (git update-index --assume-unchanged your-file) -> добавить в .gitignore

### Подробнее о файле .gitignore, наглядный пример:
```
# Игнор-лист файлов проекта
# Игнорировать ВСЕ файлы и директории, включая поддиректории и файлы в них
*
# ---- ФАЙЛЫ ----
# Игнорирование по типу файла, будут игнорироваться в АБСОЛЮТНО всех директориях
# Например /files/data.zip, /server.log, /uploads/users/data/info.xls
*.zip
*.log
*.pdf
*.xls
# Игнорирование файла во ВСЕХ директориях
# Например /params/db/config.php, /config.php
config.php
# Игнорирование конкретного файла ТОЛЬКО в корне проекта
# (корнём считается расположение файла .gitignore)
# Например НЕ БУДЕТ проигнорирован файл /db/config.php
/config.php
# Игнорирование конкретного файла ТОЛЬКО в указанной директории
# Например НЕ БУДЕТ проигнорирован файл /prod/params/config.php
/params/config.php
# ---- ДИРЕКТОРИИ ----
# Игнорирование всех файлов и папок ТОЛЬКО в конкретной директории(включая поддиректории и файлы в них)
# Например /images/user.jpg, /images/company/logo.png
# НЕ БУДУТ проигнорированы файлы и папки /prod/images/user.jpg
/images/*
# Игнорирование всех файлов и папок в ЛЮБЫХ директориях с указанным именем
# Например /images/user.jpg, /core/images/user.jpg
images/*
# Игнорирование ВСЕХ html-файлов в ОДНОЙ КОНКРЕТНОЙ директории(НЕ ВКЛЮЧАЯ поддиректории)
# Например /private/index.html
# НЕ БУДУТ проигнорированы файлы в /private/ivan/index.html
/private/*.html
# Игнорирование ВСЕХ html-файлов в КОНКРЕТНОЙ директории ВКЛЮЧАЯ поддиректории
# Например /private/info.html, /private/users/ivan/info.html
/private/**/*.html
# ---- РАЗНОЕ ----
# Исключение из игнорирования
# Игнорирование ВСЕХ файлов и папок внутри директории /secret,
# за исключением файла /secret/free.txt, он не будет проигнорирован
/secret/*
!/secret/free.txt
# Игнорирование файла с именем, содержащим спецсимволы
# Например !readme!.txt
\!readme!.txt
# Игнорирование всех JPG и JPEG файлов внутри директорий,
# которые начинаются на "h" и МОГУТ содержать ещё один символ после
# Например /images/h4/user.jpg, /images/h/company.jpeg
/images/h?/*.jp?g
```

### Перенос репозитория из GitLab на GitHub

#### Утилиты, скрипты
- https://github.com/piceaTech/node-gitlab-2-github
- https://github.com/wollzelle/gitlab-github-migrate
- https://github.com/mahmalsami/migrate-github-gitlab/blob/master/migrate.sh
- https://github.com/cybertk/git-copy

#### Через меню GitHub "Import repository" (Public)
- Официальный мануал - https://docs.github.com/en/free-pro-team@latest/github/importing-your-projects-to-github
- GitHub > Меню > "+" > "Import your project to GitHub"
- Для private-репозиториев, необходимо добавлять токены: https://gitlab.com/profile/personal_access_tokens

#### Для любых репозиториев
- Чтобы передались все созданные ветки, необходимо их создать и отслеживать локально. Можно всё сделать вручную, а можно и с помощью Bash-скрипта: https://gist.github.com/avshatalov48/f9ba2cba93ec1c274ca7fa4627287c97
- создаём пустой репозиторий на GitHub
- $ git remote add github https://yourLogin@github.com/yourLogin/yourRepoName.git
- $ git push --mirror github

### Переименование репозитория
- GitHub > Меню > Settings > Options > Repository name > Rename
- Проект локально: $ git remote set-url origin https://github.com/<ваш-логин>/<новое-имя-репозитория>.git

### Вывод списка названий коммитов с датой и хэшем
- $ git log --pretty="- %ad | %h | %s" --no-merges --date=format:"%Y-%m-%d %H:%M:%S" >commites.txt
- https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History

### Отключение проверки SSL
- $ git config --global http.sslVerify false

### Fix Git Self Signed Certificate in Certificate Chain on Windows
https://mattferderer.com/fix-git-self-signed-certificate-in-certificate-chain-on-windows

### Полезные ссылки:
- Ой, блин, гит! (https://ru.hexlet.io/blog/posts/oh-shit-git)
- Как сделать свой первый Pull Request (https://rustycrate.ru/руководства/2016/03/07/contributing.html)
- Подробнее о файле .gitignore (http://orlov.io/ru/articles/podrobnee-o-faile-gitignore)
#

- `git log 'origin/main'` - проверка изменений на удаленном репозитории (ветка main)
  git log 'origin/branch' - проверка изменений на удаленном репозитории (ветка branch)

- `git fetch` — только загружает изменения с удалённого репозитория, но не сливает их. После этого вы можете просмотреть изменения и выполнить слияние вручную с помощью `git merge`.

- `git pull` — загружает изменения с удалённого репозитория и автоматически сливает их с вашей текущей веткой.

**Пример:**

1. Быстрая загрузка и слияние:

   ```
   git pull
   ```

2. Поэтапная загрузка и слияние:
   ```
   git fetch
   git merge origin/main
   ```
   (где `main` — имя вашей ветки)

git pull

- `git pull` — загружает изменения с удалённого репозитория и автоматически сливает их с вашей текущей веткой.
  x
  **Пример:**

1. Быстрая загрузка и слияние:

   ```
   git pull
   ```

2. Поэтапная загрузка и слияние:

   ```
   git fetch
   git merge origin/main
   ```

   (где `main` — имя вашей ветки)

   # Git - система контроля версий

## Основные команды Git

- `git init` — инициализация нового репозитория.
- `git clone <url>` — клонирование удалённого репозитория.
- `git status` — просмотр состояния файлов в рабочей директории.
- `git add <файл>` — добавление файла в индекс (staging area).
- `git commit -m "сообщение"` — создание коммита с описанием изменений.
- `git log` — просмотр истории коммитов.
- `git diff` — просмотр различий между версиями файлов.
- `git branch` — просмотр и управление ветками.
- `git checkout <ветка>` — переключение между ветками.
- `git merge <ветка>` — слияние ветки с текущей.
- `git pull` — получение изменений из удалённого репозитория и слияние.
- `git push` — отправка изменений в удалённый репозиторий.

## Пример базового рабочего процесса

1. `git clone <url>`
2. Внесите изменения в файлы.
3. `git status`
4. `git add <файл>`
5. `git commit -m "описание изменений"`
6. `git push`

git log --author Iryna

git show - изменения самый последний коммит

git show 5fac1040b8386228c4bead0a05c14d4a9580e01f

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..0323d61
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+# testing-portfolio

git blame GitTutorial.md - какие и кто изменения проводились в файле построчно

git blame GitTutorial.md | grep **Пример:** - кто изменил строку **Пример:**

git blame GitTutorial.md | grep Iryna -

git diff

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ echo "3line" >> newfile.txt

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ git checkout newfile.txt
Updated 1 path from the index

cat: conflickt.tx: No such file or directory

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ cat conflickt.txt

3line

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ git checkout .
Updated 2 paths from the index

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ echo "3line" >> conflickt.txt

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ git stash
warning: in the working copy of 'conflickt.txt', LF will be replaced by CRLF the next time Git touches it
Saved working directory and index state WIP on main: 6493f4d gitTutorial modif

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ cat conflickt.txt

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)
$ git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: conflickt.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (7ae2889aee2ec0b82ada3d01c2704a1257ba5a33)

Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (main)


stash - временное хранилище
stash - временное хранилище
stash - временное хранилище
git stash скрыть изминения
git stash pop проверить/вернуть скрытые изминения
git stash clear полностью  удалить изминения


### переименование
git branch name - создание ветки
git branch -m name new-name  - переименование этой ветки
touch second.name.txt - создание нового файла

### переименование ветки с файлами на удаленном репозитории
git push origin :feature - пуш файлов на удаленный перозиторий с переименованной ветки на локальном репозитоири - feature - старая ветка на удаленном репозитории
```git bash
Ирина Елькина@Iryna-Ielkina MINGW64 /d/Work/Testing/testing-portfolio (test-branch)
$ git push origin :feature
To https://github.com/ielkina/testing-portfolio.git
 - [deleted]         feature
```

### удалить ветку

git branch -d test-branch - удаление ветки test-branch 
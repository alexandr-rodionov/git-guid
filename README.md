# Git. Инструкция для начинающих.
Git — это система контроля версий, которая помогает отслеживать изменения в проекте. Этот инструмент можно использовать как для индивидуальной, так и для командной работы.
Git позволяет сохранять изменения локально и при необходимости возвращаться к предыдущим версиям проекта. Также можно создать удалённую копию на хостинг-платформе, которая работает с Git, и поделиться результатом с другими.

В этой инструкции собраны базовые вещи, которые помогут в начале пути освоения инструмента.

## Оглавление

1. [Установка](#установка)
    - [Windows](#windows)
    - [macOS](#macos)
    - [Linux](#linux)
2. [Настройка](#настройка)
3. [Шпаргалка (базовые команды в консоли)](#шпаргалка-базовые-команды-в-консоли)
    - [Навигация](#навигация)
    - [Работа с файлами и папками](#работа-с-файлами-и-папками)
        - [Создание](#создание)
        - [Копирование и перемещение](#копирование-и-перемещение)
        - [Чтение](#чтение)
        - [Удаление](#удаление)
    - [Полезные возможности](#полезные-возможности)
4. [Инициализация репозитория](#инициализация-репозитория)
    - [Делаем папку репозиторием  - `git init`](#делаем-папку-репозиторием)
    - [«Разгитить» - `rm -rf .git`](#разгитить)
    - [Cостояние репозитория - `git status`](#cостояние-репозитория)
5. [Добавляем файлы в репозиторий - `git add`](#добавляем-файлы-в-репозиторий)

## Установка
### Windows
1. Перейдите на страницу официального сайта [Git](https://git-scm.com/download/win).
2. Скачайте одну из двух версий (32-bit или 64-bit) из категории Standalone Installer (англ. «автономный установщик»), в зависимости от типа вашей операционной системы Windows.
3. Запустите программу установки. Обратите внимание, куда будет установлен Git. Обычно это директория `C:\Program Files\Git`.
4. Проверьте, что в списке устанавливаемых программ стоит галочка напротив пункта Git Bash Here — это позволит открывать консоль с Git в любой папке.
5. Далее установщик предложит много опций. Выберите все необходимое или оставьье все настройки по умолчанию. Несколько раз нажмите Next (англ. «далее»), пока не начнётся процесс установки.
6. После окончания установки нажмите Finish (англ. «завершить»).

Проверьте установку. Для этого откройте терминал и введите эту команду: :point_down:
```bash
git version
```
Если Git установлен правильно, консоль выведет его текущую версию. 

### macOS
Для установки Git на macOS существует два способа.

1. Откройте консоль и выполните команду `/usr/bin/git`. Она запустит установщик. Нажмите Install (англ. «установить») и дождитесь окончания установки.
Когда установка завершится, для проверки выполните эту команду: :point_down:
```bash
git version
``` 
Если на экран выводится текущая версия Git, значит, установка прошла успешно.	

2. Используйте Homebrew.
    - Установите менеджер пакетов Homebrew:
        - Перейдите на официальный сайт [Homebrew](https://brew.sh/).
        - Скопируйте команду для установки — справа от неё есть символ для копирования. Нажмите на него, чтобы команда попала в буфер обмена.
        - Найдите программу Terminal в поиске Spotlight или в списке программ. Вставьте скопированный текст в окно терминала и нажмите Enter.
    - Установите Git с помощью Homebrew. Скопируйте и введите в терминал следующую команду: :point_down:
    ```bash
    brew install git
    ```

Проверьте установку. Для этого откройте терминал и введите эту команду: :point_down:
```bash
git version
```
Если на экран выводится текущая версия Git, значит, установка прошла успешно.

### Linux
Для установки Git на Linux нужно использовать терминал. 
1. Найдите программу Terminal в поиске или в списке программ.
2. Перейдите на официальный сайт [Git](https://git-scm.com/download/linux) и выберите команду установки для своей версии Linux.
3. Скопируйте её в программу Terminal и нажмите Enter. 

После успешной установки введите команду для проверки: :point_down:
```bash
git version
```` 
Если вы видите в консоли текущую версию Git, всё прошло успешно.

Поздравляем, Git установлен! :clap: :thumbsup:
____
[:arrow_up:Оглавление](#Оглавление)
____
## Настройка
Для настройки Git можно использовать командную строку. Если у вас macOS или Linux, запустите программу Terminal. Если Windows — Git Bash.

### Работа с файлом настройки `.gitconfig`
Сейчас вы работаете в одиночку, но в дальнейшем вам может понадобиться использовать Git в команде. Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.

Вы можете указать любую электронную почту и любое имя. Сделать это можно с помощью команды `git config` (от англ. configuration — «конфигурация», «настройка») с ключом `--global` (англ. «глобальный»). При этом не имеет значения, в какой директории вы находитесь прямо сейчас: вызов `git config --global` сработает везде.

В качестве значения `user.name` нужно указать своё имя или никнейм. Для настройки параметра `user.email` указывают электронную почту.
```bash
git config --global user.name "Ivan Ivanov" 
# имя или ник нужно написать латиницей и в кавычках

git config --global user.email ivanov@ivan.ru
# здесь нужно указать свой настоящий email
``` 
Все глобальные настройки Git хранит в файле `.gitconfig` в домашней директории. Команда запишет в этот файл указанные имя и почту. Чтобы убедиться в этом, можно вызвать команду для чтения файлов: :point_down:
```bash
cat ~/.gitconfig
``` 
Другой способ проверки — вывести содержимое файла конфигурации Git той же командой `git config` с флагом `--list` (англ. «список»): :point_down:
```bash
git config --list
``` 
В ответ командная строка покажет текущие значения настроек: :point_down:
```bash 
user.name=Username
user.email=username@yandex.ru 
```
Готово! :thumbsup:
____
[:arrow_up:Оглавление](#Оглавление)
____
## Шпаргалка (базовые команды в консоли)
### Навигация
- `pwd` (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
- `ls` (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
- `ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа `.`;
- `cd first-project` (от англ. change directory, «сменить директорию») — перейди в папку `first-project`;
- `cd first-project/html` — перейди в папку `html`, которая находится в папке `first-project`;
- `cd ..` — перейди на уровень выше, в родительскую папку;
- `cd ~` — перейди в домашнюю директорию (`/Users/Username`);
- `cd /` — перейди в корневую директорию.

### Работа с файлами и папками
#### Создание
- `touch index.html` (англ. touch, «коснуться») — создай файл `index.html` в текущей папке;
- `touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
- `mkdir second-project` (от англ. make directory, «создать директорию») — создай папку с именем `second-project` в текущей папке.

#### Копирование и перемещение
- `cp file.txt ~/my-dir` (от англ. copy, «копировать») — скопируй файл в другое место;
- `mv file.txt ~/my-dir` (от англ. move, «переместить») — перемести файл или папку в другое место. Кроме того, команду `mv` можно использовать, чтобы переименовать файл или папку если указать ту же директорию где находится объект, например, `mv file.txt file1.txt`.

#### Чтение
- `cat file.txt` (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

#### Удаление
- `rm about.html` (от англ. remove, «удалить») — удали файл `about.html`;
- `rmdir images` (от англ. remove directory, «удалить директорию») — удали папку `images`;
- `rm -r second-project` (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку `second-project` и всё, что она содержит.

### Полезные возможности
- Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (`&&`).
- У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (`↑`) и вниз (`↓`).
- Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать `Tab`. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке `dev`. Начните вводить `cd first` и дважды нажмите `Tab`. Если папка `first-project` есть внутри `dev`, командная строка автоматически подставит её имя. Останется только нажать `Enter`.
____
[:arrow_up:Оглавление](#Оглавление)
____
## Инициализация репозитория
Инициализация Git-репозитория и проверка, что всё прошло успешно.

### Делаем папку репозиторием
Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать Git-репозиторием (от англ. repository — «хранилище»). Для этого следует переместиться в неё и ввести команду `git init` (от англ. initialize — «инициализировать»).
Например, создайте папку `first-project` и сделайте её Git-репозиторием: перейдите в неё с помощью команды `cd` и выполните `git init`. :point_down:
```bash
cd ~/dev/first-project
# перешли в нужную папку

git init
# создали репозиторий
```
Можно создать папку в любом месте на компьютере. Но в этом случае нужно поменять путь `~/dev/first-project` на тот, который ведёт к вашей папке. Помните, что не рекомендуется создавать репозиторий Git внутри другого Git-репозитория. Это может вызывать проблемы с отслеживанием изменений.
В некоторых случаях при инициализации репозитория Git может показать объёмное сообщение, которое начинается со слов `Using 'master' as the name…`. Не пугайтесь: это не ошибка.

Также `git init` выведет сообщение вида `Initialized empty Git repository in <*ваша папка с проектом*>/.git/` (англ. «инициализирован пустой Git-репозиторий в `<*ваша папка*>/.git/`»). В подпапке `.git` Git будет хранить всю служебную информацию.

Команда `git init` — одна из редко применяемых, ведь репозиторий создаётся один раз, а пользоваться им можно сколько угодно долго.

### «Разгитить»
Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку `.git`. :point_down:
```bash
cd <папка с репозиторием> 
# перешли в папку

rm -rf .git 
# удалили подпапку .git 
```
Разберём подробнее, что такое `-rf`:
- ключ `-r` (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;
- ключ `-f` (от англ. force — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».

:heavy_exclamation_mark: Будьте осторожны: в подпапке `.git` хранится история изменений. Если удалить `.git`, то вся история проекта будет стёрта без возможности восстановления — останется только последняя версия файлов.


### Cостояние репозитория
После инициализации репозитория `first-project` запустите команду `git status` (от англ. status — «статус», «состояние») — она показывает текущее состояние репозитория.

Команда `git status` выведет:
- название текущей ветки: `On branch master` или `On branch main`;
- сообщение о том, что в репозитории ещё нет коммитов: `No commits yet`;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — `nothing to commit (create/copy files and use "git add" to track)`.

В отличие от git init, команду git status используют часто. В любой непонятной ситуации стоит посмотреть состояние (статус) репозитория, а потом решить, что делать дальше.
____
[:arrow_up:Оглавление](#Оглавление)
____
## Добавляем файлы в репозиторий
После инициализации Git-репозитория необходимо добавить туда файлы.

### Подготовить файлы к сохранению
Добавим в репозиторий два файла. Например, файл `todo.txt`, в котором будет список дел, и `readme.txt` для информации о проекте.
Создайте файлы `todo.txt` и `readme.txt` в папке `first-project` и запустите `git status`, чтобы посмотреть, что изменилось. :point_down:
```bash
touch todo.txt
touch readme.txt
# создали файлы todo.txt и readme.txt

git status
# проверили статус
``` 
Git сообщит, что в папке `first-project` есть `untracked files` (от англ. track — «следить», untracked — «неотслеженный», «неотслеживаемый») — ещё не отслеживаемые файлы `readme.txt` и `todo.txt`.

Состояние `untracked` значит, что Git ещё не хранит информацию о версиях файла и не может отследить, как он изменялся.

Сейчас в `first-project` два файла. Мы хотим отслеживать состояние обоих, поэтому можем использовать команду `git add --all` (от англ. add — «добавить» + от англ. all — «всё»). Ключ, или флаг, `--all` позволяет подготовить к сохранению все файлы в репозитории. :point_down:
```bash
git add --all
# подготовили к сохранению все файлы в репозитории

git status
# проверили статус 
```
Добавлять файлы можно и по одному, без ключа `--all`. :point_down:
```bash
git add todo.txt
git add readme.txt
git status 
```
Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (`.`). :point_down:
```bash
git add .
# добавить всю текущую папку

git status 
```
Вы можете использовать любой из этих вариантов — результат будет одинаковый.

Получилось! :muscle: Файлы, которые отмечены зелёным, теперь отслеживаются и готовы к сохранению. Но сохранения пока не произошло, потому что команда `git add` только запоминает текущее содержимое (контент) файла.

Если сейчас отредактировать любой из «зелёных» файлов в папке first-project, он перейдёт в состояние modified (англ. «изменённый») и будет и в «зелёном», и в «красном» списках.

Например, откройте файл todo.txt в любом редакторе (подойдёт даже блокнот) и напишите в нём: `1. Привет Мир.`.

Сохраните изменения, а затем снова вызовите команду `git status` в консоли.

Файл `todo.txt` теперь есть и в «зелёном», и в «красном» списках:
- зелёным отмечена пустая версия файла — в таком виде он был во время последнего запуска команды `git add`;
- красным отмечена версия с текстом `1. Привет Мир.`.

Чтобы запомнить новое состояние файла, нужно снова ввести команду git add и передать в качестве параметра имя изменённого файла или ключ `--all`. :point_down:
```bash
git add todo.txt
# или
$ git add --all 
```
Теперь файл `todo.txt` снова готов к сохранению! Будет сохранена последняя добавленная версия с текстом `1. Привет Мир.`.
____
[:arrow_up:Оглавление](#Оглавление)
____

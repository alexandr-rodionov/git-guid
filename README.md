## Оглавление

1. [Установка](#Установка)
    - [Windows](#Windows)
    - [macOS](#macOS)
    - [Linux](#Linux)
2. [Далее](#)

## Установка

### Windows
1. Перейдите на страницу официального сайта [Git](https://git-scm.com/download/win).
2. Скачайте одну из двух версий (32-bit или 64-bit) из категории Standalone Installer (англ. «автономный установщик»), в зависимости от типа вашей операционной системы Windows.
3. Запустите программу установки. Обратите внимание, куда будет установлен Git. Обычно это директория C:\Program Files\Git.
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

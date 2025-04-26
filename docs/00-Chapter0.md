## Начало работы: Настройка Окружения

Прежде чем мы погрузимся в мир Computer Science и разработки на Go, необходимо подготовить наше рабочее окружение. Нам понадобятся инструменты для написания, компиляции, сборки и запуска кода на Go, C, NASM, а также для работы с Git, Docker и другими технологиями курса.

Это руководство поможет настроить всё необходимое на разных операционных системах: Linux (Ubuntu/Debian, Arch), macOS и Windows.

**Общие Рекомендации:**

1.  **Терминал (Командная строка):** Бэкенд-разработка тесно связана с использованием терминала. Научитесь комфортно работать в нем на вашей ОС.
    *   **Linux/macOS:** Используйте встроенный Terminal, iTerm2, Konsole, Tilix или другие.
    *   **Windows:** PowerShell, Windows Terminal или терминал внутри WSL (рекомендуется).
2.  **Текстовый редактор / IDE:** Вам нужен инструмент для написания кода.
    *   **[Visual Studio Code (VS Code)](https://code.visualstudio.com/):** Бесплатный, мощный, кроссплатформенный редактор с отличной поддержкой Go, C, Docker, Git и множества других языков и инструментов через расширения. **Рекомендуется для этого курса.**
    *   **[GoLand](https://www.jetbrains.com/go/):** Платная, но очень мощная IDE от JetBrains, специально для Go. Есть бесплатная лицензия для студентов.
    *   **Vim / Neovim:** Мощные текстовые редакторы для любителей консоли (им посвящен бонусный раздел).
3.  **Система контроля версий Git:** Необходима для работы с проектами и кодом.

**Установка по Операционным Системам:**

---

### Linux (Ubuntu / Debian)

Откройте терминал и выполните следующие команды:

1.  **Обновление пакетов:**
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
2.  **Установка компилятора C (GCC) и утилит для сборки:**
    ```bash
    sudo apt install build-essential -y
    # Проверка:
    gcc --version
    ```
3.  **Установка Go:**
    *   Скачайте последнюю версию с [официального сайта Go](https://go.dev/dl/).
    *   Распакуйте архив (например, в `/usr/local/go`).
    *   Добавьте `/usr/local/go/bin` в ваш `PATH`. Инструкции есть на сайте Go.
    *   *Альтернатива (может быть не самая свежая версия):* `sudo apt install golang-go -y`
    *   **Проверка:**
        ```bash
        go version
        ```
4.  **Установка NASM:**
    ```bash
    sudo apt install nasm -y
    # Проверка:
    nasm -v
    ```
5.  **Установка Git:**
    ```bash
    sudo apt install git -y
    # Проверка:
    git --version
    ```
6.  **Установка Docker:** Следуйте [официальной инструкции для Ubuntu/Debian](https://docs.docker.com/engine/install/ubuntu/). Обычно включает добавление репозитория Docker и установку `docker-ce`. **Не рекомендуется** ставить Docker из стандартных репозиториев Ubuntu (`docker.io`), он может быть устаревшим.
    ```bash
    # Примерные шаги (обязательно сверьтесь с официальной документацией!)
    # ... команды для добавления репозитория Docker ...
    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
    # Добавление пользователя в группу docker (чтобы не использовать sudo)
    sudo usermod -aG docker $USER
    # Перелогиньтесь или выполните newgrp docker для применения изменений
    # Проверка:
    docker --version
    ```

---

### Linux (Arch Linux / Manjaro)

Откройте терминал и выполните:

1.  **Обновление системы:**
    ```bash
    sudo pacman -Syu
    ```
2.  **Установка компилятора C (GCC) и утилит для сборки:**
    ```bash
    sudo pacman -S base-devel --needed
    # Проверка:
    gcc --version
    ```
3.  **Установка Go:**
    ```bash
    sudo pacman -S go
    # Проверка:
    go version
    ```
4.  **Установка NASM:**
    ```bash
    sudo pacman -S nasm
    # Проверка:
    nasm -v
    ```
5.  **Установка Git:**
    ```bash
    sudo pacman -S git
    # Проверка:
    git --version
    ```
6.  **Установка Docker:**
    ```bash
    sudo pacman -S docker docker-compose
    # Запуск и добавление в автозагрузку службы Docker
    sudo systemctl enable --now docker.service
    # Добавление пользователя в группу docker
    sudo usermod -aG docker $USER
    # Перелогиньтесь или выполните newgrp docker
    # Проверка:
    docker --version
    ```

---

### macOS

1.  **Установка Homebrew (если еще не установлен):**
    Следуйте инструкциям на [официальном сайте Homebrew](https://brew.sh/).
2.  **Обновление Homebrew:**
    ```bash
    brew update && brew upgrade
    ```
3.  **Установка Command Line Tools (включает Git и компилятор Clang/GCC):**
    ```bash
    xcode-select --install
    # Примите лицензию, если потребуется
    # Проверка:
    gcc --version
    git --version
    ```
4.  **Установка Go:**
    ```bash
    brew install go
    # Проверка:
    go version
    ```
5.  **Установка NASM:**
    ```bash
    brew install nasm
    # Проверка:
    nasm -v
    ```
6.  **Установка Docker Desktop:**
    Скачайте и установите [Docker Desktop для Mac](https://docs.docker.com/desktop/install/mac-install/) с официального сайта Docker. Запустите приложение.
    ```bash
    # Проверка (в терминале):
    docker --version
    ```

---

### Windows

Для разработки на Go, C, Docker под Windows **настоятельно рекомендуется** использовать **[Windows Subsystem for Linux (WSL 2)](https://learn.microsoft.com/ru-ru/windows/wsl/install)**. Это обеспечит вам полноценное окружение Linux внутри Windows, что значительно упростит работу со многими инструментами курса.

**Вариант 1: Использование WSL 2 (Рекомендуемый)**

1.  **Установите WSL 2:** Следуйте [официальной инструкции Microsoft](https://learn.microsoft.com/ru-ru/windows/wsl/install). Самый простой способ в современных Windows - открыть PowerShell от имени администратора и выполнить:
    ```powershell
    wsl --install
    ```
    По умолчанию установится Ubuntu. Перезагрузите компьютер. После перезагрузки настройте имя пользователя и пароль для вашего Linux-дистрибутива.
2.  **Установите [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701)** (опционально, но удобно).
3.  **Запустите ваш дистрибутив Linux** (например, Ubuntu) из меню "Пуск" или через Windows Terminal.
4.  **Далее следуйте инструкциям для Linux (Ubuntu / Debian)** внутри терминала WSL для установки `build-essential`, `golang-go` (или с сайта), `nasm`, `git`.
5.  **Установите [Docker Desktop для Windows](https://docs.docker.com/desktop/install/windows-install/):** Скачайте и установите с официального сайта. Во время установки убедитесь, что выбрана опция интеграции с WSL 2. Docker Desktop будет управлять Docker Engine внутри WSL.
    ```bash
    # Проверка Docker (в терминале WSL):
    docker --version
    ```
6.  **Работа с кодом:** Установите VS Code на Windows. При первом открытии папки проекта, расположенной внутри WSL (например, `/home/username/myproject`), VS Code предложит установить расширение "WSL" - сделайте это. Оно позволит VS Code работать напрямую с файлами и терминалом внутри WSL.

**Вариант 2: Без WSL (Менее предпочтительный)**

Если вы по каким-то причинам не можете использовать WSL:

1.  **Установка Go:** Скачайте и установите MSI-инсталлятор с [официального сайта Go](https://go.dev/dl/). Он добавит Go в PATH.
    ```cmd
    # Проверка (в cmd или PowerShell):
    go version
    ```
2.  **Установка компилятора C (MinGW-w64):** Установите набор инструментов MinGW-w64 (например, через [MSYS2](https://www.msys2.org/) или другие дистрибутивы). Добавьте путь к `gcc.exe` в системный PATH.
    ```cmd
    # Проверка:
    gcc --version
    ```
3.  **Установка NASM:** Скачайте Windows-инсталлятор с [официального сайта NASM](https://www.nasm.us/). Добавьте путь к `nasm.exe` в PATH.
    ```cmd
    # Проверка:
    nasm -v
    ```
4.  **Установка Git:** Скачайте и установите [Git для Windows](https://git-scm.com/download/win). Выберите опции для интеграции с Command Prompt и/или PowerShell.
    ```cmd
    # Проверка:
    git --version
    ```
5.  **Установка Docker Desktop:** Скачайте и установите [Docker Desktop для Windows](https://docs.docker.com/desktop/install/windows-install/). Он использует Hyper-V или WSL 2 (даже если вы не используете WSL для других инструментов, Docker Desktop может его установить).
    ```cmd
    # Проверка:
    docker --version
    ```

---

**HTML/CSS:** Для работы с HTML/CSS не требуется отдельная установка, кроме текстового редактора (VS Code отлично подойдет) и любого современного веб-браузера (Chrome, Firefox, Edge).

**Проверка Установки (Пример):**

1.  **Go:** Создайте файл `hello.go`:
    ```go
    package main
    import "fmt"
    func main() {
        fmt.Println("Hello, Go!")
    }
    ```
    В терминале: `go run hello.go`
2.  **C:** Создайте файл `hello.c`:
    ```c
    #include <stdio.h>
    int main() {
       printf("Hello, C!\n");
       return 0;
    }
    ```
    В терминале: `gcc hello.c -o hello_c && ./hello_c` (На Windows без WSL может быть `./hello_c.exe`)
3.  **NASM (Очень простой пример):** Создайте `hello.asm` (синтаксис для Linux x86-64):
    ```nasm
    section .data
        msg db "Hello, NASM!", 0xa ; Сообщение и перевод строки
        len equ $ - msg         ; Длина сообщения

    section .text
        global _start

    _start:
        ; write(1, msg, len)
        mov rax, 1      ; Системный вызов write
        mov rdi, 1      ; Файловый дескриптор 1 (stdout)
        mov rsi, msg    ; Адрес сообщения
        mov rdx, len    ; Длина сообщения
        syscall         ; Вызвать ядро

        ; exit(0)
        mov rax, 60     ; Системный вызов exit
        xor rdi, rdi    ; Код возврата 0
        syscall         ; Вызвать ядро
    ```
    В терминале (Linux/WSL/macOS):
    ```bash
    nasm -f elf64 hello.asm -o hello.o
    ld hello.o -o hello_nasm
    ./hello_nasm
    ```    (На Windows без WSL потребуется другой синтаксис и линковщик)

**Заключение:**

Теперь ваше рабочее окружение готово к изучению курса. Убедитесь, что все основные команды (`go`, `gcc`, `nasm`, `git`, `docker`) выполняются в вашем терминале и показывают версии установленных программ. Если возникли проблемы — обратитесь к официальной документации по установке соответствующего инструмента для вашей ОС.

Можно приступать к первой главе!


# Notes for the book "Tools and Skills for .NET 8" by Mark J. Price 

# Команды в Linux

## Toolbox

1. Создание именного toolbox с определенным image

```bash
toolbox create -d ubuntu -r 24.04 net8
```

2. Вход в контейнер

```bash
toolbox enter net8
```

3. Если при входе в toolbox ошибка

```text
Error: terminfo entry not found for foot
```

Надо поставить `foot-terminfo`

```bash
sudo apt-get update
sudo apt-get install foot-terminfo
```

## Установка .NET8 в ubuntu

**Источник: https://learn.microsoft.com/ru-ru/dotnet/core/install/linux-ubuntu-install?tabs=dotnet8&pivots=os-linux-ubuntu-2404**

После захода в toolbox выполнить:

```bash
sudo apt-get update
sudo apt-get install -y dotnet-sdk-8.0
```

Проверка:

```bash
dotnet --version
dotnet --list-sdks
```

## Установка .NET8 в ubuntu через менеджер пакетов

**Источник: https://code.visualstudio.com/docs/setup/linux**

1. Выполнить:

```bash
sudo apt-get install wget gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -D -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/microsoft.gpg
rm -f microsoft.gpg
```

2. Создать файл `/etc/apt/sources.list.d/vscode.sources`:

```text
Types: deb
URIs: https://packages.microsoft.com/repos/code
Suites: stable
Components: main
Architectures: amd64,arm64,armhf
Signed-By: /usr/share/keyrings/microsoft.gpg
```

3. Lastly, update the package cache and install the package:

(Ставить `code`)

```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code # or code-insiders
```

## Git

1. Конфигурация git

В консоли:

```bash
git config --global user.name "Artem Agafonov"
git config --global user.email agart@mail.ru
git config --global core.editor gedit
git config --global init.defaultBranch main
```

Посмотреть настройки:

```bash
git config --list
```

Показать значение определенной настройки:

```bash
git config user.name
git config user.email
```

2. Создать файл `.gitignore`

При помощи `dotnet` (CLI):

```bash
dotnet new gitignore
```


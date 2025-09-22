# Notes for the book "Tools and Skills for .NET 8" by Mark J. Price 

## Команды в Linux

### Toolbox

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

### Установка .NET8 в ubuntu

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

### Установка VSCode в ubuntu через менеджер пакетов

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

### Git

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

3. Установка token для push изменений

```bash
git remote set-url origin https://artag:{token}@github.com/artag/tools-skills-net8-notes.git
```

где вместо `{token}` вставить живой token. Если все сделано правильно, то должен пройти

```bash
git push
```

## Chapter 1

### VSCode. Расширения

Из книги:

- `C# Dev Kit` (`ms-dotnettools.csdevkit`)

- `C#` (`ms-dotnettools.csharp`)

- `IntelliCode for C# Dev Kit` (`ms-dotnettools.vscodeintellicode-csharp`)

- `MSBuild project tools` (`tintoy.msbuild-project-tools`/`tintoy`)

- `SQL Server (mssql) for Visual Studio Code` (`ms-mssql.mssql`)

- `REST Client` (`humao.rest-client`)

- `ilspy-vscode` (`icsharpcode.ilspy-vscode`)

Мои:

- `Error lens` (`usernamehw.errorlens`)

- `Markdown All in One` (`yzhang.markdown-all-in-one`)

- `markdownlint` (`davidanson.vscode-markdownlint`)

#### Управление расширениями в терминале

- `code --list-extensions` - Перечисление установленных расширений

- `code --install-extension <идентификатор>` - Установка расширения с указанным идентификатором

- `code --uninstall-extension <идентификатор>` - Удаление расширения с указанным идентификатором

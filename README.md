# LM Tube

## Content
- <a href="#installation">Installation</a>
    - <a href="#global_dependencies">Global dependencies</a>
    - <a href="#ides">IDEs and tools</a>
- <a href="#setup_and_running">Setup and running</a>
    - [Environment config](#envconfig)
    - [SSH](#ssh)
    - [Install project dependencies](#projectdeps)
    - [Running](#run)
    - [Debugging](#debug)
- <a href="#settings_and_commands">Useful settings and commands</a>
- <a href="#contributing">Contributing</a>
- <a href="https://confluence.lmru.tech/display/NDP/Coding+style+and+standards">Coding style and standards</a> (link to Confluence)

<h1 id="installation">Installation</h1>
The installation consists of the following software you will need to install on your local machine. It is necessary to install appropriate versions from the list to get evetything at work.
(Tested on 18 may 2020, Windows 10)


| Necessary software                        | Version                                                    |
| ----------------------------------------- | ---------------------------------------------------------- |
| Node.js                                   | 12.16.3                                                    |
| npm                                       | 6.14.4                                                     |
| Git with git bash command prompt          | any                                                        |
| IDE (WebStorm or Visual Studio Code)      | any                                                        |


<h2 id="global_dependencies">Global dependencies</h2>
### Node.js

- #### Ubuntu
    ```
    $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
    $ command -v nvm
    $ nvm install 12.16.3
    ```

- #### Windows

1. Open the page: [https://nodejs.org/download/release/v12.16.3/](https://nodejs.org/download/release/v12.16.3/).
2. Download the suitable installer (e.g. `node-v12.16.3-x64.msi`) and install it.
3. Make sure the npm directory (e.g. `C:\Users\user\AppData\Roaming\npm`) is added to `PATH`.
4. Check the avaliability of node.js: open command prompt(cmd) and type ```node -v```, the result should be ```v12.16.3```

- #### Mac OS

> Install [Homebrew Package Manager](https://brew.sh/index_ru) if you don't have it.

1. [Install nvm with Brew](http://dev.topheman.com/install-nvm-with-homebrew-to-use-multiple-versions-of-node-and-iojs-easily/)
2. Install the suitable version of node:
    ```
    nvm install 12.16.3
    ```

### NPM
```
$ npm install -g npm@6.14.4
```

check it after installation:

```
$ npm -v
```

### Git

- #### Ubuntu
    ```
    $ sudo apt-get install git
    ```

- #### Windows

    Download from [the official site](https://git-scm.com/downloads) and install it.

    It is worth to select the "Checkout as-is, commit Unix-style line endings" option while installing Git
    or clone the repository with `--config core.autocrlf=input`
    (otherwise there will be trouble with  the `linebreak-style` ESLint rule).
    Alternatively you can follow [the rule docs](http://eslint.org/docs/rules/linebreak-style#using-this-rule-with-version-control-systems).

    Some build scrips may require `bash`. Git install Bash with itself so the simplest way to provide `bash`
    is to add `C:\Program Files\Git\bin` to `PATH`.

- #### Mac OS
    ```
    brew install git
    ```
> #### Clone the project
> [How to clone a repository from Gitlab](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html#clone-a-repository)


<h2 id="ides">IDEs and tools</h2>

### VSCode
1. Download from [here](https://code.visualstudio.com/)

### JetBrains Webstorm

1. Download from [here](https://www.jetbrains.com/)

<h1 id="setup_and_running">Setup and running</h1>

<a name="projectdeps"></a>

## Install project dependencies

```
$ npm i
```

<a name="run"></a>

## Running:

Necessary applications:

| App name                                                     |
| ------------------------------------------------------------ |
| cmd or git bash window (or command prompt from IDE terminal) |

First, start the virtual device from the Android Studio. Then, execute your application:

- 1st terminal - dev server:

    ```bash
    $ npm run browser:build
    ```

    or, if you want to clear cache from previous launches, execute the following command:

    ```bash
    $ npm run native:dev -- --reset-cache
    ```

    > Note: if you are facing errors with the first script, relating to access rights, etc., please, try those steps to clear and reset android build BEFORE you start ```npm run native:dev```:
    >
    > 1. Change your directory to ./android:
    >
    > ```bash
    > $ cd ./android
    > ```
    >
    > 2. run *gradlew* script with *clean* flag:
    >
    > ```bash
    > $ ./gradlew clean 
    > ```
    >
    > ​	or:
    >
    > ```powershell
    > > gradlew clean
    > ```
    >
    > depending on your operation system and command-line interface.

    

- 2nd terminal - build native android app wrapper for development:
(emulator should be started or device should be connected via USB. In order to check run in cmd `adb devices`)

    ```
    $ npm run native:android
    ```



<a name="debug"></a>

## Debugging:

Necessary applications:

| App name                                                     |
| ------------------------------------------------------------ |
| Android Studio                                               |
| cmd or git bash window (or command prompt from IDE terminal) |
| React Native Debugger                                        |

First, start the virtual device from the Android Studio. Then, open RN Debugger and execute your application from command line (as said in point "Running" above)

When runninig on a mobile device, press Ctrl+m hot key and select **Debug JS Remotely**

#### <a name="useful"></a>

<h1 id="settings_and_commands">Useful settings and commands</h1>
Console log network activity:

- From React Native Debugger, select **Debugger**->**Open Config File**, then change

  ```defaultNetworkInspect: false``` to ```true```

Running dev script with clear cache:

```
$ npm run native:dev -- --reset-cache
```

Running android virtual device with command prompt (you can also use automated scripts located in ./local folder):

(See [here](./local/readme.md) for the possibility to run automated script)

```
$ emulator -list-avds
```

​	then copy device name to the next command and execute it:

```
$ emulator '@<device_name>'
```

> Note: This command will work if you [set path to your android emulator](./local/readme.md) in **Path** (system environment variable), otherwise just replace "emulator" word with path-to-android-emulator which is located on your local machine next to Sdk folder that you settled (e.g. C:\Users\CurrentUser\AppData\Local\Android\Sdk\emulator)

Killing all flow proceses (Windows)

```
taskkill /IM "flow.exe" /F
```

> Sometimes there are unexpected errors in application that disappear when you remove **/build** and **/node_modules** directory and reassemble the project (```npm i``` and run scripts)

<h1 id="contributing">Contributing</h1>
## branch name
**[type]/[JIRA-TASK]-[short-description]**

- feature/LFRONT-3801-added-btn-to-entity-view-form
- bugfix/LFRONT-1022-fixed-navigation-panel
- docs/updated-installation-section

## commit message
**[JIRA-TASK] [Module] - [work description]**

- LFRONT-3801 App - added btn to entity view form
- LFRONT-1022 Catalog - fixed navigation panel
- README - updated installation section

## MR title
**[type]/[JIRA-TASK] [app change description]**

- feature/LFRONT-3801 Добавлена кнопка на форму просмотра сущности
- bugfix/LFRONT-1022 Исправлен деффект отображения панели навигации
- docs Обновлена секция руководства по установке зависимостей

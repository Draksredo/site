# LM Tube

## Content
- <a href="#installation">Installation</a>
    - <a href="#global_dependencies">Global dependencies</a>
    - <a href="#ides">IDEs and tools</a>
- <a href="#setup_and_running">Setup and running</a>
    - [Install project dependencies](#projectdeps)
    - [Running](#run)
- <a href="https://confluence.lmru.tech/display/LOCDEV/LM+Tube">Tested on 18 may 2020, Windows 10</a> (link to Confluence)

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

First, execute your application:

- 1st terminal - To build a project, run the following command:

    ```bash
    $ npm run browser:build
    $ npm run browser:build:serve
    ```

- 2nd terminal - build the application shell for development:

    ```
    $ npm run browser:build:dev
    ```


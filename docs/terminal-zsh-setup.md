# Zsh Terminal

![Zsh](../assets/oh-my-zsh-logo.png?raw=true)

The Z shell ([Zsh](https://www.zsh.org)) is a Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting.

Zsh is an extended Bourne shell with many improvements, including some features of Bash, Korn shell (ksh), and tcsh.

## Terminal theme - Oh My Zsh + Powerlevel9k + Nerd font

The standard macOS Terminal appearance is just boring. Apple included a few nice preset themes too, but to really make your terminal appearance stand out you need to customize it yourself.

Below is the Terminal using my personal theme and `.zshrc` configuration. Feel free to copy and use it.

![macOS Zsh theme](../assets/terminal-zsh.png?raw=true)

## Update and select Zsh as the default shell

1. Update zsh:

    ```bash
    brew install zsh
    ```

2. Add the new shell to the list of allowed shells:

    ```bash
    if $(grep -Fxq "/usr/local/bin/zsh" /etc/shells); then
        echo "The list of shells is already updated"
    else
        sudo echo "/usr/local/bin/zsh" >> /etc/shells
    fi
    ```

3. Change to the new shell:

    ```bash
    chsh -s /usr/local/bin/zsh
    ```

4. Check the ZSH version:

    ```bash
    zsh --version

    # zsh 5.7.1 (x86_64-apple-darwin18.2.0)
    ```

## Install Oh My Zsh

[Oh My Zsh](https://ohmyz.sh/) is an open source, community-driven framework for managing your zsh configuration.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

You can upgrade it to get the latest features it offers:

```bash
upgrade_oh_my_zsh
```

## Install Fonts

You will want to check out the [Nerd-Fonts](https://github.com/ryanoasis/nerd-fonts) repo, which contains a ton of fonts which support all the awesome symbols you want to use.

To install the fonts, use Homebrew Cask Fonts:

1. Add Homebrew Cask Fonts:

    ```bash
    brew tap homebrew/cask-fonts
    ```

2. Install Nerd Font:

    ```bash
    brew cask install font-hack-nerd-font
    ```

## Install Powerlevel9k theme

[Powerlevel9k](https://github.com/Powerlevel9k/powerlevel9k) is the most awesome Powerline theme for ZSH around!

Run on the terminal:

```bash
URL="https://github.com/bhilburn/powerlevel9k.git"
DIR="${HOME}/.oh-my-zsh/custom/themes/powerlevel9k"
git clone "${URL}" "${DIR}"
```

## Install Plugins

### Install zsh-completions

Clone the repository inside your oh-my-zsh repo:

```bash
URL="https://github.com/zsh-users/zsh-completions"
DIR="${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-completions"
git clone "${URL}" "${DIR}"
```

### Install syntax highlighting

[Syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) package provides syntax highlighting for the shell zsh.

Clone the repository inside your oh-my-zsh repo:

```bash
URL="https://github.com/zsh-users/zsh-syntax-highlighting.git"
DIR="${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting"
git clone "${URL}" "${DIR}"
```

## Install exa (optional)

[exa](https://the.exa.website) is a replacement for ls written in Rust.

```bash
brew install exa
```

### Update `.zshrc`

1. Backup the current `.zshrc` file:

    ```bash
    if [[ -f "${HOME}/.zshrc" ]]; then
        cp "${HOME}/.zshrc" "${HOME}/.zshrc.bkp"
    fi
    ```

2. Update the `.zshrc`. Paste that in the terminal:

    ```bash
    read -r -d '' ZSH_PROFILE <<"EOF"
    #!/bin/bash
    # Zsh Profile for macOS
    # Copyright (c) Marcos Gomes-Borges
    # https://github.com/mgomesborges/mac-dev-setup

    # POWERLEVEL THEME SETTINGS
    ############################################################
    # Must have a nerd font installed
    POWERLEVEL9K_MODE="nerdfont-complete"

    # POWERLEVEL9K_COLOR_SCHEME="dark"
    POWERLEVEL9K_PROMPT_ON_NEWLINE=true
    POWERLEVEL9K_MULTILINE_FIRST_PROMPT_PREFIX=""
    POWERLEVEL9K_MULTILINE_LAST_PROMPT_PREFIX="%# "

    POWERLEVEL9K_ALWAYS_SHOW_USER=true
    POWERLEVEL9K_ALWAYS_SHOW_CONTEXT=true
    POWERLEVEL9K_CONTEXT_TEMPLATE="mgomesborges" # "%n@%m"

    POWERLEVEL9K_CONTEXT_DEFAULT_BACKGROUND="white"
    POWERLEVEL9K_CONTEXT_DEFAULT_FOREGROUND="black"

    # Long paths truncation strategy
    POWERLEVEL9K_SHORTEN_STRATEGY=""
    POWERLEVEL9K_SHORTEN_DIR_LENGTH=2

    # Dir home foreground and background
    POWERLEVEL9K_HOME_ICON=""
    POWERLEVEL9K_HOME_SUB_ICON=""
    POWERLEVEL9K_FOLDER_ICON=""
    POWERLEVEL9K_ETC_ICON=""

    POWERLEVEL9K_DIR_DEFAULT_BACKGROUND="025"
    POWERLEVEL9K_DIR_DEFAULT_FOREGROUND="white"
    POWERLEVEL9K_DIR_HOME_BACKGROUND="025"
    POWERLEVEL9K_DIR_HOME_FOREGROUND="white"
    POWERLEVEL9K_DIR_HOME_SUBFOLDER_BACKGROUND="025"
    POWERLEVEL9K_DIR_HOME_SUBFOLDER_FOREGROUND="white"

    # Displays a lock icon if you do not have write permissions on the folder
    POWERLEVEL9K_DIR_WRITABLE_FORBIDDEN_BACKGROUND="white"
    POWERLEVEL9K_DIR_WRITABLE_FORBIDDEN_FOREGROUND="red"

    # Time
    POWERLEVEL9K_TIME_FORMAT="%D{%d/%m %H:%M:%S}"

    # Current Python virtual environment
    POWERLEVEL9K_VIRTUALENV_BACKGROUND="220"
    POWERLEVEL9K_VIRTUALENV_FOREGROUND="black"

    # Current Python version
    POWERLEVEL9K_CUSTOM_PYTHON_VERSION="zsh_python_version"
    POWERLEVEL9K_CUSTOM_PYTHON_VERSION_BACKGROUND="024"
    POWERLEVEL9K_CUSTOM_PYTHON_VERSION_FOREGROUND="white"

    zsh_python_version(){
        local virtualenv_path="$VIRTUAL_ENV"
        # Early exit; $virtualenv_path must always be set
        [[ -z "$virtualenv_path" ]] && return
        python_version=$(python --version 2>&1)
        echo ${python_version/"Python"/""}
    }

    # Prompt elements
    POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
        context
        dir
        dir_writable
        virtualenv
        custom_python_version
        rbenv
    )
    POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
        background_jobs
        rvm
        vcs
        time
    )

    # OH MY ZSH SETTINGS
    ############################################################
    # Path to oh-my-zsh installation
    export ZSH="${HOME}/.oh-my-zsh"

    # ZSH Terminal title
    DISABLE_AUTO_TITLE=true
    # echo -ne "\e]1;TERMINAL_TITLE\a"

    # Username which by default will not be shown
    export DEFAULT_USER="$USER"

    # Set name of the theme to load
    ZSH_THEME="powerlevel9k/powerlevel9k"

    # Disable Oh My Zsh automatic update
    DISABLE_UPDATE_PROMPT="true"

    # Plugins
    plugins=(
        git
        gitfast
        python
        pip
        pipenv
        virtualenv
        docker
        docker-compose
        kubectl
        zsh-completions
        zsh-syntax-highlighting
    )

    # Reload for zsh-completions
    autoload -U compinit && compinit
    source $ZSH/oh-my-zsh.sh

    # User configuration
    ############################################################

    # exa is a replacement for ls https://github.com/ogham/exa
    if command -v exa 1>/dev/null 2>&1; then
        alias ls="exa --group-directories-first --classify"
    fi

    # Python virtual environment
    # Allow pip only for active virtual environment
    # Use 'gpip' for global environment
    export PIP_REQUIRE_VIRTUALENV=true
    gpip(){
        PIP_REQUIRE_VIRTUALENV="" pip "${@}"
    }

    # Pyenv Python version management
    if command -v pyenv 1>/dev/null 2>&1; then
        eval "$(pyenv init -)"
        pyenv virtualenvwrapper
    fi
    EOF

    echo "${ZSH_PROFILE}" > "${HOME}/.zshrc"
    ```

## Enable Antialias text, Bold Fonts, ANSI Colors, and Bright Colors

1. Open the macOS Terminal
2. In the top menu bar, select `Terminal` then `Preferences...` (⌘,)
3. Select the `Profiles` tab
4. Choose the **Basic** or **Pro** profile/theme from the left side list
5. Press the `Default` button near the bottom of the window
6. Under the `Font` tab change the font:

    * `Hack Regular Nerd Font Complete 14 pt`

7. Under the `Text` tab check the boxes:

   * `Antialias text`
   * `Use bold fonts`
   * `Display ANSI colors`
   * `Use bright colors for bold text`

![Terminal Profiles - Text](../assets/terminal-profiles-text-zsh.png?raw=true)
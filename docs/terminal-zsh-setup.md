# Zsh Terminal

![Zsh](../assets/oh-my-zsh-logo.png?raw=true)

The Z shell ([Zsh](https://www.zsh.org)) is a Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting.

Zsh is an extended Bourne shell with many improvements, including some features of Bash, Korn shell (ksh), and tcsh.

## Terminal theme - Oh My Zsh + Powerlevel9k + Nerd font

The standard macOS Terminal appearance is just boring. Apple included a few nice preset themes too, but to really make your terminal appearance stand out you need to customize it yourself.

Below is the Terminal using my personal theme and `.zshrc` configuration. Feel free to copy and use it.

You can set up Zsh following this tutorial or using the mac-dev-setup install script:

```bash
bash <(curl -fsSL raw.githubusercontent.com/mgomesborges/mac-dev-setup/master/install) zsh
```

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

    # zsh 5.8 (x86_64-apple-darwin20.1.0)
    ```

## Install Oh My Zsh

[Oh My Zsh](https://ohmyz.sh/) is an open source, community-driven framework for managing your zsh configuration.

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

You can upgrade it to get the latest features it offers:

```bash
omz update
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
    brew install font-hack-nerd-font
    ```

## Install Powerlevel10k theme

[Powerlevel10k](https://github.com/romkatv/powerlevel10k) is the most awesome Powerline theme for ZSH around!

Run on the terminal:

```bash
URL="https://github.com/romkatv/powerlevel10k.git"
DIR="${HOME}/.oh-my-zsh/custom/themes/powerlevel10k"
git clone "${URL}" "${DIR}"
```

## Install Plugins

### Install zsh-autosuggestions

Clone the repository inside your oh-my-zsh repo:

```bash
URL="https://github.com/zsh-users/zsh-autosuggestions"
DIR="${HOME}/.oh-my-zsh/custom/plugins/zsh-autosuggestions"
git clone "${URL}" "${DIR}"
```

### Install syntax highlighting

[Syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) package provides syntax highlighting for the shell zsh.

Clone the repository inside your oh-my-zsh repo:

```bash
URL="https://github.com/zsh-users/zsh-syntax-highlighting.git"
DIR="${ZSH_CUSTOM:-${HOME}/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting"
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
    # Zsh Profile for macOS
    # Copyright (c) Marcos Gomes-Borges
    # https://github.com/mgomesborges/mac-dev-setup

    # Homebrew
    export PATH="/usr/local/sbin:$PATH"

    # POWERLEVEL 10K THEME SETTINGS
    ############################################################
    POWERLEVEL9K_MODE="nerdfont-complete"

    # Current directory
    POWERLEVEL9K_DIR_FOREGROUND=254
    POWERLEVEL9K_DIR_BACKGROUND=237

    # OS identifier color
    POWERLEVEL9K_OS_ICON_FOREGROUND=232
    POWERLEVEL9K_OS_ICON_BACKGROUND=7

    # Time
    POWERLEVEL9K_TIME_FOREGROUND=0
    POWERLEVEL9K_TIME_BACKGROUND=7
    POWERLEVEL9K_TIME_FORMAT="%D{%d/%m %H:%M:%S}"

    # Current Python virtual environment
    POWERLEVEL9K_VIRTUALENV_FOREGROUND=0
    POWERLEVEL9K_VIRTUALENV_BACKGROUND=220

    # Pyenv
    POWERLEVEL9K_PYENV_FOREGROUND=255
    POWERLEVEL9K_PYENV_BACKGROUND=24

    POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
        os_icon
        dir
        vcs
        newline
        prompt_char
    )
    POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
        status
        command_execution_time
        background_jobs
        direnv
        asdf
        virtualenv
        pyenv
        vim_shell
        time
        newline
    )

    # OH MY ZSH SETTINGS
    ############################################################
    # Path to oh-my-zsh installation
    export ZSH="${HOME}/.oh-my-zsh"

    # ZSH Terminal title
    DISABLE_AUTO_TITLE=true

    # Set name of the theme to load
    ZSH_THEME="powerlevel10k/powerlevel10k"

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
        colorize
        compleat
        zsh-autosuggestions
        zsh-syntax-highlighting
        colored-man-pages
        command-not-found
    )

    # Update ZSH settings
    source $ZSH/oh-my-zsh.sh

    # User configuration
    ############################################################

    # exa is a replacement for ls https://github.com/ogham/exa
    if command -v exa 1>/dev/null 2>&1; then
        alias ls="exa --icons --group-directories-first --classify"
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
        eval "$(pyenv init --path)"
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

    * `Hack Regular Nerd Font Complete 18 pt`

7. Under the `Text` tab check the boxes:

   * `Antialias text`
   * `Use bold fonts`
   * `Display ANSI colors`
   * `Use bright colors for bold text`

8. Update the **ANSI Colours** table: click on the colour, select the colour picker tool and use the colours from the palette below as a reference.

![Terminal Profiles - Text](../assets/terminal-profiles-text-zsh.png?raw=true)

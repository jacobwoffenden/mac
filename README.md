# mac

1. Determine Architecture

    ```bash
    if [[ "$( uname -m )" == "arm64" ]]; then
      export APPLE_SILICON="true"
      export BREW_BINARY="/opt/homebrew/bin/brew"
    else
      export APPLE_SILICON="false"
      export BREW_BINARY="brew"
    fi
    ```

1. Install Xcode Tools

    ```bash
    xcode-select --install
    ```

1. Install Rosetta 2

    ```bash
    if [[ "${APPLE_SILICON}" == "true" ]]; then
      softwareupdate --install-rosetta --agree-to-license
    fi
    ```

1. Install Homebrew

    ```bash
    /bin/bash -c "$( curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh )"
    ```

1. Install Oh My Zsh

    ```bash
    /bin/bash -c "$( curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh )"
    ```

1. Create Directory

    ```bash
    mkdir -p ${HOME}/Developer/github.com/jacobwoffenden
    ```

1. Clone Repository

    ```bash
    git clone https://github.com/jacobwoffenden/mac.git ${HOME}/Developer/github.com/jacobwoffenden/mac
    ```

1. Install Brew Packages

    ```bash
    ${BREW_BINARY} bundle --file ${HOME}/Developer/github.com/jacobwoffenden/mac/Brewfile

    # ${BREW_BINARY} bundle --file ${HOME}/Developer/github.com/jacobwoffenden/mac/Brewfile.moj
    ```

1. Create ZSH Configuration

    ```bash
    cp ${HOME}/Developer/github.com/jacobwoffenden/mac/zsh/zshrc ${HOME}/.zshrc
    ```

1. Create Git Configuration

    ```bash
    cp ${HOME}/Developer/github.com/jacobwoffenden/mac/git/gitconfig ${HOME}/.gitconfig

    # cp ${HOME}/Developer/github.com/jacobwoffenden/mac/git/gitconfig.moj ${HOME}/.gitconfig
    ```

1. Create Hyper Configuration

    ```bash
    cp ${HOME}/Developer/github.com/jacobwoffenden/mac/hyper/hyper.js ${HOME}/.hyper.js
    ```

1. Create GPG Configuration

    ```bash
    cp ${HOME}/Developer/github.com/jacobwoffenden/mac/gnupg/gpg.conf ${HOME}/.gnupg/gpg.conf
    cp ${HOME}/Developer/github.com/jacobwoffenden/mac/gnupg/gpg-agent.conf ${HOME}/.gnupg/gpg-agent.conf
    ```

1. Import and Trust GPG Public Key

    ```bash
    gpg --import ${HOME}/Developer/github.com/jacobwoffenden/mac/gnupg/jacob@woffenden.io.asc
    gpg --edit-key jacob@woffenden.io
    trust
    5
    y
    ```

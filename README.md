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

2. Install Xcode Tools

```bash
xcode-select --install
```

3. Install Rosetta 2

```bash
if [[ "${APPLE_SILICON}" == "true" ]]; then
  softwareupdate --install-rosetta --agree-to-license
fi
```

4. Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

5. Install Oh My Zsh

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

6. Create Directory

```bash
mkdir -p ${HOME}/git/github.com/jacobwoffenden
```

7. Clone Mac Repository

```bash

git clone https://github.com/jacobwoffenden/mac.git ${HOME}/git/github.com/jacobwoffenden/mac
```

8. Install Brew Packages

```bash
${BREW_BINARY} bundle --file ${HOME}/git/github.com/jacobwoffenden/mac/Brewfile
```

9. Create ZSH Configuration

```bash
cp ${HOME}/git/github.com/jacobwoffenden/mac/zsh/zshrc ${HOME}/.zshrc
```

10. Create Git Configuration

```bash
cp ${HOME}/git/github.com/jacobwoffenden/mac/git/gitconfig ${HOME}/.gitconfig
```

11. Create GPG Configuration

```bash
cp ${HOME}/git/github.com/jacobwoffenden/mac/gnupg/gpg.conf ${HOME}/.gnupg/gpg.conf
cp ${HOME}/git/github.com/jacobwoffenden/mac/gnupg/gpg-agent.conf ${HOME}/.gnupg/gpg-agent.conf
```

12. Import and Trust GPG Public Key

```bash
gpg --import ${HOME}/git/github.com/jacobwoffenden/mac/gnupg/jacob@woffenden.io.asc
gpg --edit-key jacob@woffenden.io
trust
5
y
```

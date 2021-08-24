# mac

Things to do when getting a Mac

1. Install Xcode Tools

```
xcode-select --install
```

2. Install Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

3. Install OhMyZSH

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

4. Clone Repository

```
git clone https://github.com/jacobwoffenden/mac.git
```

5. Import and Trust GPG Public Key

```
gpg --import mac/gnupg/jacob@woffenden.io.asc
gpg --edit-key jacob@woffenden.io
trust
5
y
```

6. Run Brew Bundle

```
brew bundle --file mac/Brewfile
```

7. Create Directories

```
mkdir -p ${HOME}/.kube
mkdir -p ${HOME}/.ssh
chmod 700 ${HOME}/.ssh
```

8. Copy Configurations

```
# ZSH
cp mac/zsh/zshrc ${HOME}/.zshrc

# GPG
cp mac/gnupg/gpg.conf ${HOME}/.gnupg/gpg.conf
cp mac/gnupg/gpg-agent.conf ${HOME}/.gnupg/gpg-agent.conf

# Git Configuration
cp mac/git/gitconfig ${HOME}/.gitconfig
```
# mac

```
# Determime system architecture
if [[ "$( uname -m )" == "arm64" ]]; then
  export APPLE_SILICON="true"
  export BREW_BINARY="/opt/homebrew/bin/brew"
else
  export APPLE_SILICON="false"
  export BREW_BINARY="brew"
fi

# Install Xcode
xcode-select --install

# Install Rosetta 2
if [[ "${APPLE_SILICON}" == "true" ]]; then
  softwareupdate --install-rosetta --agree-to-license
fi

# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Oh My ZSH
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Clone mac repo
git clone https://github.com/jacobwoffenden/mac.git

# Run Brew
${BREW_BINARY} bundle --file mac/Brewfile.{personal|work}

# Import and Trust GPG Public Key
gpg --import mac/gnupg/jacob@woffenden.io.asc
gpg --edit-key jacob@woffenden.io
trust
5
y

# Create ZSH Configuration
cp mac/zsh/zshrc ${HOME}/.zshrc

# Create GPG Configuration
cp mac/gnupg/gpg.conf ${HOME}/.gnupg/gpg.conf
cp mac/gnupg/gpg-agent.conf ${HOME}/.gnupg/gpg-agent.conf

# Create Git Configuration
cp mac/git/gitconfig ${HOME}/.gitconfig
```
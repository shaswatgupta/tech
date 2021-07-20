---
title: "Macbook Pro setup"
date: 2021-01-30T15:29:00-08:00
draft: false
toc: false
comments: true
twitterImage:
categories:
- SRE
- MACBOOK
---

Last year around march i lost by Macbook to water.
Here I am back again setting up my Macbook Pro 2019 model.

1. Guide to follow for first time Macbook setup:
Open: https://sourabhbajaj.com/mac-setup/ on safari.

2. Install xcode and homebrew
```$xslt
sudo xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)”
```

3. Some of tools i use on day to day basis.
```$xslt
brew install lastpass-cli vim git wget telnet stormssh tmuxinator telegram-cli go scala sbt openjdk@11 wireguard-tools wireguard-go gh hugo kubectx kube-ps1 helm nmap ipcalc jq youtube-dl ffmpeg luarocks
```

4. Installations with cask.
```$xslt
brew install --cask android-file-transfer appcleaner caffeine cheatsheet docker doubletwist dropbox google-chrome flux rectangle transmission lastpass microsoft-office intellij-idea google-backup-and-sync iterm2 flock telegram tunnelblick authy hammerspoon lens bitwarden obs \mysql qemu libvirt
```

5. Font installation
```$xslt
brew tap homebrew/cask-fonts && brew install --cask font-source-code-pro
```

6. Hashicorp tools installation
```$xslt
brew tap hashicorp/tap
brew install hashicorp/tap/vault && brew upgrade hashicorp/tap/vault
brew install hashicorp-boundary-desktop
brew install hashicorp/tap/boundary
brew install consul
brew cask install vagrant
brew cask install vagrant-manager
vagrant plugin install vagrant-libvirt
```

7. Visual Studio Code installation and customizations.
Use the following link to configure VS Code.
https://sourabhbajaj.com/mac-setup/VisualStudioCode/
```$xslt
brew install --cask visual-studio-code
```

8. Appstore installations
 - Wireguard.
 - Pocket.
 - Microsoft Remote Desktop.

9. Dotfiles requirements.
```$xslt
brew install fzf
$(brew --prefix)/opt/fzf/install
brew install diff-so-fancy
```

10. Dotfiles setup.
My dotfiles are fork of https://github.com/caarlos0/dotfiles because dotfiles are meant to be forked.
https://carlosbecker.com/posts/dotfiles-are-meant-to-be-forked
```$xslt
cd ~
git clone https://github.com/shaswatgupta/.dotfiles
```
Post cloning follow the instructions on repo.

11. Completion setup in iterm2.
```$xslt
brew search completion
brew install bash-completion brew-cask-completion docker-completion vagrant-completion bash-completion docker-compose-completion gradle-completion launchctl-completion packer-completion ruby-completion stormssh-completion docker-machine-completion maven-completion pip-completion tmuxinator-completion
```

12. Cloud Providers cli setups.
```$xslt
GCP: https://cloud.google.com/sdk/docs/quickstart
AWS: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html
```

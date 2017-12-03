# macOS Setup

## Java

The brew version of Java is 9, which has some compatibility issue with macOS High Sierra (10.13).

If you have already installed JDK9 using the JDK package, you should uninstall it using the following commands:

``` bash
$ sudo rm -fr /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
$ sudo rm -fr /Library/PreferencePanes/JavaControlPanel.prefPane
$ sudo rm -fr /Library/Java/JavaVirtualMachines/jdk-9.jdk
```

 There are two ways to install JDK8:

1. Download and install JDK8 from Java website.

2. Install from brew

   ``` bash
   $ brew cask install caskroom/versions/java8
   ```

## Basic Components

1. brew

   ``` bash
   $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

2. proxychains-ng

   ``` bash
   $ brew install proxychains-ng
   # then configure /usr/local/etc/proxychains.conf
   socks5 127.0.0.1 8887
   ```

3. source code pro fonts

   ``` bash
   # source code pro fonts
   $ brew tap caskroom/fonts
   $ brew cask install font-source-code-pro
   ```

4. vimrc

   ``` bash
   # vimrc
   $ git clone https://github.com/mapleaph/vim
   $ cp vim/vimrc ~/.vimrc
   ```

5. iterm2

   ``` bash
   # iterm2
   $ brew cask install iterm2
   # download color schemes, "Afterglow" is preferred
   $ git clone https://github.com/mbadolato/iTerm2-Color-Schemes.git
   # then set font to Source Code Pro, preferred size is 12
   ```

6. ohmyzsh

   ``` bash
   # ohmyzsh
   $ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
   # exit zsh back to bash
   $ chsh -s $(which zsh); exit
   # then edit $HOME/.zshrc file, change the ZSH_THEME to "agnoster"
   ```

7. Surge or ShadowsocksX

   ``` bash
   # install surge or shadowsocksx
   $ brew cask install surge
   $ brew cask install shadowsocksx
   ```

## Basic Package/Version Managers

1. pip

   ```bash
   $ sudo easy_install pip
   # install package locally, preferred.
   $ pip install --user PACKAGENAME
   # install package globally
   $ pip install PACKAGENAME
   ```

2. pyenv

   ```bash
   $ brew install pyenv
   $ echo "eval \"\$(pyenv init -)\"" >> $HOME/.zshrc
   $ source $HOME/.zshrc
   # list all available python versions
   $ pyenv versions
   # install python 3.6.2
   $ CFLAGS="-I$(brew --prefix openssl)/include" \
   LDFLAGS="-L$(brew --prefix openssl)/lib" \
   pyenv install 3.6.2
   ```

3. nvm (node version manager)

   ```bash
   $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.5/install.sh | bash
   $ echo "export NVM_DIR=\"\$HOME/.nvm\"" >> $HOME/.zshrc
   $ echo "[ -s \"\$NVM_DIR/nvm.sh\" ] && . \"\$NVM_DIR/nvm.sh\"  # This loads nvm" >> $HOME/.zshrc
   $ echo "[ -s \"\$NVM_DIR/bash_completion\" ] && . \"\$NVM_DIR/bash_completion\"  # This loads nvm bash_completion" >> $HOME/.zshrc
   $ source $HOME/.zshrc
   # list installed versions
   $ nvm ls version
   # list currently used versions
   $ nvm current
   # list available remote versions
   $ nvm ls-remote
   ```

4. npm (node package manager)

   ```bash
   # After nodejs was installed, npm is available
   # install package locally
   $ npm install PACKAGENAME
   # install package globally, preferred.
   $ npm install -g PACKAGENAME
   ```

## Common Components

``` bash
$ brew install archey thefuck m-cli magic-wormhole mas progress tldr you-get youtube-dl tig rg trash wget zsh-syntax-highlighting ffmpeg ccat entr fzf gnuplot lolcat pandoc screenfetch openssl harfbuzz dnsmasq ispell coreutils crosstool-ng tmux

$ brew cask install appcleaner youdaodict unetbootin etcher firefox google-chrome arduino mpv xld kindle xiami neteasemusic iina lyricsx android-file-transfer handshaker gpg-suite aliwangwang qq vlc ichm namechanger grammarly cyberduck thunder baidunetdisk spotify typora sourcetree keka veracrypt go2shell oversight coconutbattery google-backup-and-sync dropbox artpip vagrant virtualbox virtualbox-extension-pack wireshark telegram disk-inventory-x jdownloader karabiner-elements nutstore vnc-viewer youdaonote yu-writer 115browser tftpserver burn

# android development
$ brew cask install android-sdk

# flash player for safari, chrome and firefox, no good to install it, power/resource consuming.
$ brew cask install flash-player flash-npapi

# quick look plugins
$ brew cask install webpquicklook qlcolorcode qlimagesize qlmarkdown qlprettypatch qlstephen qlvideo quicklook-csv quicklook-json quicklookase suspicious-package

# imgcat (not the iterm2 plugin)
$ brew tap eddieantonio/eddieantonio
$ brew install imgcat

# visual studio code insiders
$ brew tap caskroom/versions
$ brew install caskroom/versions/visual-studio-code-insiders
# vscode plugins
# 1. vscode-icons
# 2. one monokai theme

# spacemacs
$ brew tap d12frosted/emacs-plus
$ brew install emacs-plus
$ git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d

# paid software
$ brew cask install flume daisydisk beyond-compare manuscripts pdfexpert tripmode commander-one devonthink dash moom contexts istat-menus bartender 1password alfred
iexplorer vmware-fusion paragon-ntfs waltr adobe-creative-cloud screens

# software download directly from the website due to size problem
# 1. paralles
# 2. microsoft-office
# 3. toast titanium

# using npm
$ npm install -g vtop

# using pip
$ pip install --user howdoi powerline-status gfwlist2pac
# export PATH
$ export PATH="$HOME/Library/Python/2.7/bin:$PATH"
```

## Safari Extensions

Double click extensions from old ~/Library/Safari/Extensions folder to install, directly paste the folder into the new place dose not take effect (Still don't know why).

### Useful Extensions

1. 1Password
2. Adblock Plus (should update list from options after installation)
3. Grammarly
4. NoMoreiTunes
5. "Open In" button for Internet Explorer
6. Push for Kindle
7. Sessions
8. Stylish
   1. baidu lite
   2. flat zhihu
   3. weibo v6
   4. YouTube - Nyan Cat progress bar video player theme
9. sVim
10. Thunder Extension (installed from Thunder app)
11. Translate
12. 惠惠购物助手
13. Polyglot
14. Clip to DEVONthink


## Enable Anywhere APPs

``` bash
$ sudo spctl --master-disable
```

## Dictionaries

Copy all files under then old ~/Library/Dictionaries to the new place.

## Karabiner Elements

Copy old file ~/.config/karabiner/karabiner.json to the new place.
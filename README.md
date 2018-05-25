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
   $ git clone https://github.com/mapleaph/vim ~/.vim
   $ cd ~/.vim
   $ git submodule update --init --recursive
   ```

5. iterm2

   ``` bash
   # iterm2
   $ brew cask install iterm2
   # download color schemes, "Afterglow" or "Dracula" is preferred
   $ git clone https://github.com/mbadolato/iTerm2-Color-Schemes.git
   # then set font to Source Code Pro, preferred size is 12
   ```

6. ohmyzsh

   ``` bash
   # ohmyzsh
   $ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
   # exit zsh back to bash
   $ exit
   # change the default shell to zsh
   $ chsh -s $(which zsh); exit
   # then edit $HOME/.zshrc file, change the ZSH_THEME to "agnoster"
   # or use a third-party theme like this one called jovial, copy the jovial.zsh-theme to .oh-my-zsh/themes folder
   $ git clone https://github.com/zthxxx/jovial $HOME/; cd $HOME; cp jovial/jovial.zsh-theme $HOME/.oh-my-zsh/themes/; rm -rf jovial
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
   # for example, install python 3.6.5
   $ CFLAGS="-I$(brew --prefix openssl)/include" \
   LDFLAGS="-L$(brew --prefix openssl)/lib" \
   pyenv install 3.6.5
   # path for pyenv's python
   # $HOME/Library/Python/x.y/bin
   # path for brew's python
   # /usr/local/Cellar/python/3.6.5/bin
   # /usr/local/Cellar/python@2/2.7.14_3/bin

   # switch between different python versions globally
   $ pyenv global <version>
   # or locally
   $ pyenv local <version>
   # or only for shell
   $ pyenv shell <version>
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
$ brew install archey thefuck m-cli magic-wormhole mas progress tldr you-get youtube-dl tig rg trash wget zsh-syntax-highlighting ffmpeg ccat entr fzf gnuplot lolcat pandoc screenfetch openssl harfbuzz dnsmasq ispell coreutils crosstool-ng tmux graphviz ctags cmake wakeonlan cscope valgrind pandoc tesseract ripgrep mosh

$ brew cask install appcleaner youdaodict etcher firefox google-chrome arduino mpv xld kindle xiami neteasemusic iina lyricsx android-file-transfer handshaker gpg-suite aliwangwang qq vlc ichm namechanger grammarly cyberduck thunder baidunetdisk typora sourcetree keka veracrypt go2shell oversight coconutbattery google-backup-and-sync dropbox artpip vagrant virtualbox virtualbox-extension-pack wireshark telegram disk-inventory-x karabiner-elements nutstore vnc-viewer youdaonote yu-writer 115browser tftpserver burn aerial fliqlo applepi-baker lepton mactex doxygen steam xquartz qqmusic macvim vimr calibre sqlpro-studio

# android development
$ brew cask install android-sdk

# flash player for safari, chrome and firefox, no good to install it, power/resource consuming.
$ brew cask install flash-player flash-npapi

# quick look plugins
$ brew cask install webpquicklook qlcolorcode qlimagesize qlmarkdown qlprettypatch qlstephen qlvideo quicklook-csv quicklook-json quicklookase suspicious-package

# imgcat (not the iterm2 plugin)
$ brew tap eddieantonio/eddieantonio
$ brew install imgcat

# visual studio code
$ brew install visual-studio-code
# visual studio code insiders
$ brew tap caskroom/versions
$ brew install caskroom/versions/visual-studio-code-insiders
# vscode plugins
# 1. vscode-icons
# 2. one monokai theme
# 3. ftp-kr
# 4. vscode-pdf
# 5. markdownlint
# 6. Markdown PDF
# 7. C/C++
# 8. C/C++ Clang Command Adapter
# 9. C++ Intellisense
# 10. Chinese (Simplified) Language Pack for Visual Studio Code

# spacemacs
$ brew tap d12frosted/emacs-plus
$ brew install emacs-plus
$ git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d

# paid software
$ brew cask install flume daisydisk beyond-compare manuscripts pdfexpert tripmode commander-one devonthink-pro dash moom contexts istat-menus bartender 1password alfred
iexplorer vmware-fusion paragon-ntfs waltr adobe-creative-cloud screens timing pagico crossover expressions gitfinder imazing

# software download directly from the website due to size problem
# 1. paralles
# 2. microsoft-office
# 3. toast titanium

# using npm
$ npm install -g vtop

# using pip
$ pip install --user howdoi powerline-status gfwlist2pac ici ydcv
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
9. sVim（启用这个插件后，无法使用左右键控制视频进度）
10. vimari
11. Thunder Extension (installed from Thunder app)
12. Translate
13. 惠惠购物助手
14. Polyglot
15. Clip to DEVONthink
16. OneNote Web Clipper
17. Tampermonkey 系列脚本
    1. Simple YouTube MP3 Button
    2. Youtube Best Video Downloader 2
    3. Download YouTube
    4. 视频网页全屏
    5. YouTube +（目前和新版 Youtube 网页冲突，需要改为旧版）
    6. 视频站启用html5播放器
    7. 新浪微博之我要看大图
    8. MiniblogImgPop - 微博浮图
    9. Mouseover Popup Image Viewer
    10. 右键在新标签中打开图片时显示最优化图像质量
    11. DownAlbum
    12. 百度云插件+APIKey
    13. Github New Feed Filter
    14. Userscript+ : 显示当前网站所有可用的UserJS脚本 Jaeger


## Enable Anywhere APPs

``` bash
$ sudo spctl --master-disable
```

## Dictionaries

Copy all files under then old ~/Library/Dictionaries to the new place.

## Karabiner Elements

Copy old file ~/.config/karabiner/karabiner.json to the new place.
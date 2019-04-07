# macOS Setup

## Internet

```bash
# brew cask install surge
# install surge from local backup is a better choice
brew cask install shadowsocksx
brew tap v2ray/v2ray
brew install v2ray-core
sudo brew services start v2ray-core
```

## Xcode

Install Xcode from App Store or just install the neccessary tools when installing homebrew.

## Basic Components

1. homebrew

   ```bash
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

2. proxychains-ng

   ```bash
   $ brew install proxychains-ng
   # then configure /usr/local/etc/proxychains.conf
   socks5 127.0.0.1 8887
   ```

3. fonts

   ```bash
   brew tap caskroom/fonts
   brew cask install font-source-code-pro font-hanamina
   ```

4. iterm2

   ```bash
   # iterm2
   brew cask install iterm2
   # download color schemes, "Afterglow" or "Dracula" is preferred
   git clone https://github.com/mbadolato/iTerm2-Color-Schemes.git
   # then set font to Source Code Pro, preferred size is 13
   ```

5. ohmyzsh

   ```bash
   # ohmyzsh
   sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

   cd ~; git clone https://github.com/mapleaph/zshrc ~/.zshrcgit; rm -r .zshrc; ln -s .zshrcgit/zshrc .zshrc
   # then edit $HOME/.zshrc file, change the ZSH_THEME to "agnoster"
   # third-party themes
   ## ZSH_THEME="jovial/jovial"
   git clone https://github.com/zthxxx/jovial.git ~/.oh-my-zsh/custom/themes/jovial
   ## ZSH_THEME="zeta-zsh-theme/zeta"
   git clone https://github.com/skyerlee/zeta-zsh-theme.git ~/.oh-my-zsh/custom/themes/zeta-zsh-theme
   ## ZSH_THEME="spaceship-prompt/spaceship"
   git clone https://github.com/denysdovhan/spaceship-prompt.git ~/.oh-my-zsh/custom/themes/spaceship-prompt
   ## ZSH_THEME="powerlevel9k/powerlevel9k"
   git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
   # exit zsh back to bash
   exit
   # change the default shell to zsh
   chsh -s $(which zsh); exit
   ```

6. vim and vimrc

   First you should install vim from Homebrew, because vim shipped with macOS does not enable the clipboard functionality.

   ```bash
   brew install vim
   # then export PATH to pick up Homebrew version of vim instead of the system version.
   # add this line to bashrc or zshrc file
   export PATH=/usr/local/bin:$PATH

   # vimrc
   git clone https://github.com/mapleaph/vim ~/.vim
   cd ~/.vim; git submodule update --init --recursive

   # for YouCompleteMe plugin
   cd bundle/YouCompleteMe; ./install.py --clang-completer --js-completer
   ```

6. zsh-completion

   ```bash
   brew install zsh-completion

   # then add the following to .zshrc
   fpath=(path/to/zsh-completions/src $fpath)

   # then execute following commands
   rm -f ~/.zcompdump; compinit
   chmod go-w '/usr/local/share'
   ```

## Basic Package/Version Managers

1. pip

   ```bash
   sudo easy_install pip
   # install package locally, preferred.
   pip install --user PACKAGENAME
   # install package globally
   pip install PACKAGENAME
   ```

2. pyenv

   ```bash
   brew install pyenv
   echo "eval \"\$(pyenv init -)\"" >> $HOME/.zshrc
   source $HOME/.zshrc
   # list all available python versions
   pyenv versions
   # for example, install python 3.7.0
   CFLAGS="-I$(xcrun --show-sdk-path)/usr/include" pyenv install -v 3.7.0
   # path for pyenv's python
   # $HOME/Library/Python/x.y/bin
   # path for brew's python
   # /usr/local/Cellar/python/3.7.0/bin
   # /usr/local/Cellar/python@2/2.7.14_3/bin

   # switch between different python versions globally
   pyenv global <version>
   # or locally
   pyenv local <version>
   # or only for shell
   pyenv shell <version>
   ```

3. nvm (node version manager)

   ```bash
   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.5/install.sh | bash
   echo "export NVM_DIR=\"\$HOME/.nvm\"" >> $HOME/.zshrc
   echo "[ -s \"\$NVM_DIR/nvm.sh\" ] && . \"\$NVM_DIR/nvm.sh\"  # This loads nvm" >> $HOME/.zshrc
   echo "[ -s \"\$NVM_DIR/bash_completion\" ] && . \"\$NVM_DIR/bash_completion\"  # This loads nvm bash_completion" >> $HOME/.zshrc
   source $HOME/.zshrc
   # list installed versions
   nvm ls version
   # list currently used versions
   nvm current
   # list available remote versions
   nvm ls-remote
   ```

4. npm (node package manager)

   ```bash
   # After nodejs was installed, npm is available
   # install package locally
   npm install PACKAGENAME
   # install package globally, preferred.
   npm install -g PACKAGENAME
   ```

## Common Components

```bash
brew install adwaita-icon-theme \
             aom \
             archey \
             aria2 \
             atk \
             autoconf \
             autogen \
             autojump \
             automake \
             bash \
             bdw-gc \
             binutils \
             boost \
             cairo \
             ccat \
             cdrtools \
             check \
             cmake \
             cocoapods \
             coreutils \
             cscope \
             ctags \
             dbus \
             dnsmasq \
             elinks \
             emacs \
             entr \
             faac \
             faad2 \
             ffmpeg \
             flac \
             flex \
             fontconfig \
             freetype \
             frei0r \
             fribidi \
             fzf \
             gawk \
             gd \
             gdbm \
             gdk-pixbuf \
             gettext \
             ghostscript \
             giflib \
             git-flow \
             git-lfs \
             glib \
             glib-networking \
             gmp \
             gnu-sed \
             gnuplot \
             gnutls \
             go \
             gobject-introspection \
             gotop \
             graphite2 \
             graphviz \
             grep \
             gsasl \
             gsettings-desktop-schemas \
             gst-libav \
             gst-plugins-bad \
             gst-plugins-base \
             gst-plugins-good \
             gst-plugins-ugly \
             gstreamer \
             gtk+3 \
             gtk-vnc \
             gts \
             guile \
             harfbuzz \
             help2man \
             hicolor-icon-theme \
             highlight \
             htop \
             icarus-verilog \
             icu4c \
             ideviceinstaller \
             imagemagick@6 \
             intltool \
             ios-deploy \
             ipcalc \
             iperf \
             iperf3 \
             iproute2mac \
             ispell \
             jasper \
             jpeg \
             json-glib \
             lame \
             leptonica \
             libarchive \
             libass \
             libbluray \
             libcerf \
             libcroco \
             libepoxy \
             libevent \
             libffi \
             libgcrypt \
             libgpg-error \
             libidn2 \
             libimobiledevice \
             libmms \
             libogg \
             libosinfo \
             libplist \
             libpng \
             libpsl \
             librsvg \
             libsamplerate \
             libshout \
             libsndfile \
             libsodium \
             libsoup \
             libsoxr \
             libssh2 \
             libtasn1 \
             libtiff \
             libtool \
             libunistring \
             libusb \
             libvirt \
             libvirt-glib \
             libvorbis \
             libvpx \
             libxml2 \
             libyaml \
             libzip \
             little-cms2 \
             lolcat \
             lua \
             lua@5.1 \
             lz4 \
             m-cli \
             m4 \
             magic-wormhole \
             mailutils \
             mas \
             meson \
             mpfr \
             nasm \
             ncurses \
             netpbm \
             netperf \
             nettle \
             ngrep \
             ninja \
             nmap \
             nnn \
             node \
             opencore-amr \
             openjpeg \
             openssl \
             opus \
             orc \
             osinfo-db \
             osinfo-db-tools \
             p11-kit \
             pandoc \
             pango \
             pcre \
             pcre2 \
             perl \
             pixman \
             pkg-config \
             progress \
             pstree \
             py2cairo \
             py3cairo \
             pygobject3 \
             python \
             python@2 \
             qemu \
             readline \
             ripgrep \
             rtmpdump \
             rubberband \
             ruby \
             sc-im \
             screenfetch \
             sdl2 \
             shared-mime-info \
             snappy \
             socat \
             speex \
             sphinx-doc \
             spice-gtk \
             spice-protocol \
             sqlite \
             squirrel \
             taglib \
             telnet \
             tesseract \
             texi2html \
             texinfo \
             thefuck \
             theora \
             tig \
             tldr \
             tmux \
             trash \
             tree \
             unbound \
             usbmuxd \
             usbredir \
             vala \
             vde \
             virt-manager \
             virt-viewer \
             vte3 \
             wakeonlan \
             webp \
             wget \
             wireguard-go \
             wireguard-tools \
             x264 \
             x265 \
             xvid \
             xz \
             yajl \
             yarn \
             you-get \
             youtube-dl \
             zsh-syntax-highlighting

brew cask install aerial \
             aliwangwang \
             android-file-transfer \
             anydesk \
             appcleaner \
             applepi-baker \
             arduino \
             baidunetdisk \
             boxcryptor \
             burn \
             calibre \
             clipy \
             commandq \
             cyberduck \
             dingtalk \
             doxygen \
             dupeguru \
             fantastical \
             firefox \
             fliqlo \
             go2shell \
             google-chrome \
             gpg-suite \
             gpodder \
             grammarly \
             gtkwave \
             handshaker \
             helium \
             ichm \
             iina \
             java \
             karabiner-elements \
             keka \
             keyboardcleantool \
             kindle \
             lepton \
             losslesscut \
             lrtimelapse \
             lyricsx \
             macdown \
             macvim \
             michaelvillar-timer \
             microsoft-remote-desktop-beta \
             mpv \
             mysqlworkbench \
             namechanger \
             neteasemusic \
             nightowl \
             omnifocus \
             omnigraffle \
             onedrive \
             open-in-code \
             osxfuse \
             oversight \
             qq \
             sequel-pro \
             snipaste \
             sourcetree \
             spotify \
             sqlpro-studio \
             squirrel \
             steam \
             switchhosts \
             teamviewer \
             telegram-desktop \
             tftpserver \
             thunder \
             tuntap \
             typora \
             unetbootin \
             vagrant \
             veracrypt \
             vlc \
             vnc-viewer \
             wireshark \
             xiami \
             xld \
             xnconvert \
             xquartz


# android development
brew cask install android-sdk

# flash player for safari, chrome and firefox, no good to install it, power/resource consuming.
brew cask install flash-player flash-npapi

# quick look plugins
brew cask install webpquicklook qlcolorcode qlimagesize qlmarkdown qlprettypatch qlstephen qlvideo quicklook-csv quicklook-json quicklookase suspicious-package

# imgcat (not the iterm2 plugin)
brew tap eddieantonio/eddieantonio
brew install imgcat

# visual studio code
brew cask install visual-studio-code
# visual studio code insiders
brew tap caskroom/versions
brew cask install caskroom/versions/visual-studio-code-insiders
# Finder plugin for visual studio code
brew cask install open-in-code
# vscode plugins
# 1. C/C++
# 2. C/C++ Clang Command Adapter
# 3. C++ Intellisense
# 4. Chinese (Simplified) Language Pack for Visual Studio Code
# 5. Code Outline
# 6. Debugger for Java
# 7. Dracula Official
# 8. ftp-kr
# 9. Git History
# 10. Git Project Manager
# 11. GitLens -- Git supercharged
# 12. Go
# 13. Java Extension Pack
# 14. Java Test Runner
# 15. Language Support for Java(TM) by Red Hat
# 16. LaTeX Workshop
# 17. Markdown PDF/vscode-pdf
# 18. markdownlint
# 19. Maven for Java
# 20. One Monokai Theme
# 21. vscode-icons
# 22. Prettier - Code formatter

# spacemacs
brew tap d12frosted/emacs-plus
brew install emacs-plus
git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d

# standard emacs using brew
brew install emacs --with-cocoa --with-mailutils --with-librsvg --with-imagemagick@6
sudo ln -s $(brew --prefix emacs)/Emacs.app /Applications/
echo "alias emacs=\"\$(brew --prefix emacs)/Emacs.app/Contents/MacOS/Emacs -nw\"" >> ~/.zshrc

# paid software
brew cask install daisydisk \
                  beyond-compare \
                  manuscripts \
                  pdf-expert \
                  tripmode \
                  commander-one \
                  devonthink-pro \
                  dash \
                  moom \
                  contexts \
                  istat-menus \
                  bartender \
                  alfred \
                  vmware-fusion \
                  paragon-ntfs \
                  adobe-creative-cloud \
                  screens \
                  timing \
                  crossover \
                  expressions \
                  imazing \
                  jetbrains-toolbox \
                  disk-drill \
                  hyperdock \
                  synergy

# 1password6
brew cask install caskroom/versions/1password6

# software download directly from the website due to size problem
# 1. paralles
# 2. microsoft-office
# 3. toast titanium
# 4. nutstore
# 5. yu-writer
# 6. mweb

# download from website due to wrong checksum
# 1. coconutbattery
# 2. goodsync

# installation from App Store
# enpass
# The Unarchiver
# Reeder 3
# MindNode 5
# Agenda
# ToothFairy
# Trello
# iA Writer
# Spark
# Easy New File
# Irvue
# Snap
# BlueHarvest
# PopClip
# Slack
# Amphetamine
# TextWrangler
# TickTick

# using npm
npm install -g vtop gtop t-get tldr

# using pip
pip install --user howdoi powerline-status gfwlist2pac ici ydcv cheat
# export PATH
export PATH="$HOME/Library/Python/2.7/bin:$PATH"

# or

# using pip3
pip3 install --user howdoi powerline-status gfwlist2pac ici ydcv cheat
# export PATH
export PATH="$HOME/Library/Python/3.7/bin:$PATH"
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
<!-- 8. Stylish
   1. baidu lite
   2. flat zhihu
   3. weibo v6
   4. YouTube - Nyan Cat progress bar video player theme
9. sVim（启用这个插件后，无法使用左右键控制视频进度） -->
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

```bash
sudo spctl --master-disable
```

## Dictionaries

Copy all files under then old ~/Library/Dictionaries to the new place.

## Snipaste

```bash
git clone https://github.com/Mapleaph/snipaste_config ~/.snipaste
```

## Karabiner Elements

```bash
git clone https://github.com/mapleaph/karabiner ~/.config/karabiner
```

## Development Setup for STM32

```bash
# jlink debugger
brew tap caskroom/drivers
brew cask install segger-jlink

# openocd
brew install openocd

# gcc for arm
brew cask install gcc-arm-embedded
```

Download STM32CubeMX for macOS, then install it:

```bash
sudo xattr -r -d com.apple.quarantine SetupSTM32CubeMX-4.26.0.app
open SetupSTM32CubeMX-4.26.0.app
```

After installing CLion, install plugin called OpenOCD + STM32CubeMX support for ARM embedded development.

## Time machine

uncheck Back Up Automatically to save spaces.

## Dash

Integration, Snippets and Sync file.

## git

```bash
git clone https://github.com/mapleaph/git ~/.gitconfigdir
cd ~
ln -s .gitconfigdir/gitconfig .gitconfig
```

# Mac の移行

※システム環境設定とかは除くインストール系

---

- [Qutebrowser](https://github.com/qutebrowser/qutebrowser)
  - Chrome, Firefox
  - bookmarkのインポート
  - `cd && gcl https://github.com/arsley/dot-qutebrowser .qutebrowser`
- [keypad-layout](https://github.com/janten/keypad-layout)
- homebrew
- [zsh oh-my-zsh](https://sourabhbajaj.com/mac-setup/iTerm/zsh.html)
- [dein](https://github.com/Shougo/dein.vim)
- `cd`
- `gcl https://github.com/arsley/dotfiles.git && cd dotfiles && gco macOS && ./link`
- Edit `.vimrc` `.zshrc` (PATH関係)
- `:call dein#install()`
- `brew install nodebrew rbenv pyenv`
  - with Edit `.vimrc` `.zshrc`
- `nodebrew install VERSION`
  - `mkdir -p $HOME/.nodebrew/src/VERSION` が必要になるかも
  - `nodebrew use VERSION`
- `rbenv install VERSION`
  - `rbenv global VERSION`
- Git
  - `ssh -T git@github.com`
- Atom
  - `apm install sync-settings`
  - `GITHUB_TOKEN=hogehoge GIST_ID=hogehoge atom .`
  - gist : `https://gist.github.com/arsley/f7b5a5e5b9f39a6d6403a8d85cb4dff9`
  - うまくいかなかったら, Settingに追記して `sync-setting:restore`
- [Docker for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
- slack, Line, discord wireshark airmail
- [texlive](https://tug.org/texlive/)
  - ダウンロードリンクは[ココ](https://tug.org/texlive/acquire-netinstall.html)
  - インストールの参考 : https://texwiki.texjp.org/?TeX%20Live
  - mac向けもある : https://texwiki.texjp.org/?TeX%20Live%2FMac
  - [ヒラギノフォントのセットアップ](https://texwiki.texjp.org/?%E3%83%92%E3%83%A9%E3%82%AE%E3%83%8E%E3%83%95%E3%82%A9%E3%83%B3%E3%83%88#macos-hiragino-setup)もある
  - `sudo tlmgr install latexmk`
  - `sudo tlmgr install here float systeme xstring listings xcolor`
- [skim](https://skim-app.sourceforge.io/)
- [dash](https://kapeli.com/dash)
- [notable](https://github.com/notable/notable)
- [trailer](http://ptsochantaris.github.io/trailer/)
- [qlstephen](https://github.com/whomwah/qlstephen)
  - quick look FILEの中身が見られる拡張
- [AppCleaner](https://freemacsoft.net/appcleaner/)
- [hstr](https://github.com/dvorka/hstr)

# Mac の移行

※システム環境設定とかは除くインストール系

---

- [SizeUp](http://www.irradiatedsoftware.com/sizeup/)
- XCode
- run `git` command to install command line tools
- [homebrew](https://brew.sh/index_ja)
- [iterm2](https://www.iterm2.com/)
- [dotfiles](https://github.com/arsley/dotfiles)
- [oh-my-zsh](https://sourabhbajaj.com/mac-setup/iTerm/zsh.html)
- [hstr](https://github.com/dvorka/hstr)
- [dein](https://github.com/Shougo/dein.vim)
- cmd installations

```
brew install asdf vim hub tmux coreutils gpg
bash -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring'
asdf plugin-add yarn
asdf plugin-add ruby
asdf plugin-add nodejs
asdf plugin-add crystal
asdf install
```

- Git
  - [ssh key generation](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
  - `ssh -T git@github.com`
- [Atom](https://atom.io/)
  - `apm install sync-settings`
  - gist : `https://gist.github.com/arsley/f7b5a5e5b9f39a6d6403a8d85cb4dff9`
  - `sync-settings:restore`
- [Docker for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
- slack, discord, spark
- [skim](https://skim-app.sourceforge.io/)
- [trailer](http://ptsochantaris.github.io/trailer/)
- [qlstephen](https://github.com/whomwah/qlstephen)
  - quick look FILEの中身が見られる拡張
- [AppCleaner](https://freemacsoft.net/appcleaner/)
- [tinytex](https://yihui.name/tinytex/)


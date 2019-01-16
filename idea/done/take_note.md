# Note taker

## 要望

- テキストはPCでとりたい
- 図を書きたいこともある
- タイプしながら図を取り込めるソフトウェアはない
  - 作りたい
- GUIアプリケーションを作ってみたかった

## 要件

### 必須

- 文書の打ち込みが可能
- 写真などが「文章中」に添付・挿入可能
- MarkDownのハイライト
- 等幅フォント(Osaka etc.)

### optional

- (個人向けなので)Vimのキーバインドで動かしたい
- iPhoneで写真撮影→AirDropで写真転送→貼り付け
  - このプロセスを簡素にできるよう、iPhoneの方のアプリの開発?
- キーボードから手を動かさないようにしたい

## 環境?

- [electron](https://electronjs.org/)
- [Flammarion](https://github.com/zach-capalbo/flammarion)
  - Rubyによるelectronラッパー

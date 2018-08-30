# Buffer

## Usage

```
"buffername [command]
```

### Numerical buffer

削除したテキストが1~9の順で保持される。

```
# e.g.

"1p # => 直前のyunk
"2P # => その前のyunk
```

### Char buffer

[a-zA-Z]など英字に割り当て可能なクリップボードのようなもの。

```
# e.g.

"ay # => バッファ`a`にyunk
"by # => `b`にyunk
"ap # => ペースト
```

## Ref

- [複数のバッファを使いこなす](http://blog.majide.com/2006/01/vim-how-to-use-buffer/)


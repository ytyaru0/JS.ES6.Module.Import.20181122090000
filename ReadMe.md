# このソフトウェアについて

　JavaScript(ES6)で`import`を使う。[demo](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/)

# 参考

* [export](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/export)
* [import](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/import)

　`import`サポートはChromium61以上 or Firefox60以上。

# 最小コード

* index.html
* style.css
* main.js
* sub.js

## デフォルトexport/import

index.html
```html
<script type="module" src="main.js"></script>
```

　`type="module"`とするのが要点。[前回](https://github.com/ytyaru/JS.ES6.Module.20180809070000)は`type="module"`としていなかったのでインポートに失敗していた。

main.js
```javascript
import Sub from "./Sub.js";
```

　相対パスは必ず先頭に`/`,`./`,`../`を付与せねばならない。

modules/Sub.js
```javascript
export default class Sub {...}
```

* [demo/2](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/2/index.html)
* [demo/5](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/5/index.html)

## 名前付きexport/import

main.js
```javascript
import {Sub1} from "./Sub.js";
import {Sub2} from "./Sub.js";
```

modules/Sub.js
```javascript
export class Sub1 {...}
export class Sub2 {...}
```

* [demo/0](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/2/index.html)

# 遭遇したエラー

## ローカル実行ではインポート不可

```
Access to Script at 'file:///tmp/work/JS.ES6.Module.Import.20181122090000/src/0/main.js' from origin 'null' has been blocked by CORS policy: Invalid response. Origin 'null' is therefore not allowed access.
```

　CORS制約により不可。ローカルサーバを立てる必要がある。

## default exportをインポートできない

```
Uncaught SyntaxError: The requested module './sub.js' does not provide an export named 'Sub'
```

* [demo/1](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/1/index.html)

　`要求されたモジュール './sub.js'は 'Sub'という名前のエクスポートを提供しません`。

　原因不明。未実装と思われる。

## 相対パスの表記ルール

```
Uncaught TypeError: Failed to resolve module specifier "Sub". Relative references must start with either "/", "./", or "../".
```

* [demo/3](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/3/index.html)
* [demo/4](https://ytyaru0.github.io/JS.ES6.Module.Import.20181122090000/src/3/index.html)

　`モジュール指定子 "Sub"の解決に失敗しました。相対参照は "/"、 "./"、または "../"のいずれかで始まらなければなりません。`ということらしい。

# 開発環境

* [Raspberry Pi](https://ja.wikipedia.org/wiki/Raspberry_Pi) 3 Model B+
    * [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) GNU/Linux 9.0 (stretch)
        * Chromium 65.0.3325.181（Official Build）Built on Raspbian , running on Raspbian 9.4 （32 ビット）

# ライセンス

　このソフトウェアはCC0ライセンスである。

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja)

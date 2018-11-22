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
import Sub from "Sub";
```

modules/Sub.js
```javascript
export default class Sub {...}
```

## 名前付きexport/import

main.js
```javascript
import {SubInstance} from "modules/Sub";
```

modules/Sub.js
```javascript
class Sub {...}
export const SubInstance = new Sub();
```

# 開発環境

* [Raspberry Pi](https://ja.wikipedia.org/wiki/Raspberry_Pi) 3 Model B+
    * [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) GNU/Linux 9.0 (stretch)
        * Chromium 65.0.3325.181（Official Build）Built on Raspbian , running on Raspbian 9.4 （32 ビット）

# ライセンス

　このソフトウェアはCC0ライセンスである。

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja)

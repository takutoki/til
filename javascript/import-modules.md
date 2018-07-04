# Import Outer Modules by ES2015

ES2015からは import/export が使えるようになります

外部に公開する関数を定義するには、
関数の宣言functionの前に export を記述します

```export.js
// 外部に公開する関数を定義
export function add (a ,b) {
  retuen a + b
}

export function mul (a, b) {
  return a * b
}
```

```main.js
// 自作の計算モジュールを取り込む
import {add, mul} from './export.js'

console.log(add(2, 3)) // 5
console.log(mul(6, 8)) // 48

```

> import文のバリエーション

import文はさまざまなバリエーションで記述できます
上記の例のように、モジュール内の特定の要素だけを取り込む場合は {} で囲みます

```
import {add, mul} from './export.js'
```

モジュールの全ての要素を取り込む場合、[\*]を使います

```
import * as ex from './export.js'
```

この場合、ex という名前を通して、ex.add() のようにしてモジュール内の関数にアクセスできます

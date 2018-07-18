# Optional Value of nil

オプショナルバリューが`nil`の場合に対応する

> 初期値の設定 ??

```
var count:Int?
var price:Int

price = 250 * (count ?? 5) // countはnilなので、初期値5で計算する
print("\(price)円です")

// 1250円です

count = 3
price = 250 * (count ?? 5) // countがnilでなく3なので、3で計算する
print("\(price)円です")
```

> Opitional Binding

`オプショナルバインディング`は、オプショナルバリューがnilでなければ
値をアンラップして一時変数に代入し、nilの場合はfalseを返す機能です
この機能は`if文`、`while文`、`guard-else文`で利用できます

- if文

```
var str:String?
str = "Swift"

if let msg = str {
    // strがnilでない処理
    print("\(msg)ワールド")
} else {
    // strがnilの時の処理
    print("ハローワールド")
}

```

- for-in文と組み合わせて

```
var sum = 0
let dic:[String:Int?] = ["a":23, "b":nil, "c":10, "d":nil]

for (_, value) in dic { // for-inで辞書型を取り出した場合タプルで取得される　keyは使わないので捨てる
    if let num = value {
        sum += num // dicから取り出したvalueがnilでない時だけ実行される
    }
}
print("数値の合計は\(sum)")
```

- while文

```
var str:String? = "☆★"
var repeatString:String = ""
var i = 0

while let stamp = str { // strがnilでない時、アンラップしてstampに代入します　nilならwhileループを実行しません
  repeatString += stamp
  i += 1
  if (i > 10) {
    break
  }
}
print(repeatString)
```

- guard-else文
guard-else文でオプショナルバインディングを利用することで、オプショナルバリューがnilの場合に処理を中断し、
nilでない場合は値をアンラップして変数/定数に代入しそのまま利用していくことができます
if文と異なるのは、if文ではアンラップした値を代入した変数/定数はif文のブロック内でだけ有効なローカル変数という点です

```
let who = "桜"
var level:Int?

func hello() {
    // levelをtheLevelにオプショナルバインディングする
    guard let theLevel = level else {
        return // theLevelがnilの時は処理を中断する
    }

    if theLevel < 10 {
        print("hello\(who)隊員")
    } else {
        print("hello\(who)上級隊員")
    }
}

// level未設定
hello()  // 処理が中断される
// level設定
level = 9
hello()

// hello桜上級隊員
```

> Optional Chain

`オプショナルチェーン`とは、オブジェクトや配列などの値に`ドットシンタックスでアクセス`する時に
対象に`?`を付けることで、値がnilだった場合に`実行時エラーを回避`する記述方法です

```
// ballsは配列で、タプルの値を持つ
// ballsが空のとき
// 配列操作　[Array.first]　で最初の値にアクセスできる
var balls:[ (size:Int, color:String) ] = []
var ballsize = balls.first?.size  // 値がないのでnilです　ここで処理が中断してballsizeにnilが代入されます
print(ballsize)

// ballsに値があるとき
balls = [ (size:2, color:"red" ), (size:4, color:"green") ]
ballsize = balls.first?.size
print(ballsize)
```

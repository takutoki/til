# Create Server by Node.js

[http.createServer(requestListener)](https://nodejs.org/api/http.html#http_http_createserver_options_requestlistener)を使う
引数である[requestListener](https://www.w3schools.com/nodejs/func_http_requestlistener.asp)はfunction型のコールバック関数
引数は２つ(request, response)とる

```js
// httpモジュールを読み込む
const http = require('http')

// Webサーバー起動
const srv = http.createServer(handler)
// ポート8081で待ち受ける
srv.listen(8081)

// サーバーにアクセスがあった時に実行されるコールバック関数
function handler (req, res) {
  // HTTPヘッダーを出力
  res.writeHead(200, {'Content-Type': 'text.html'})
  // レスポンスの本体を出力
  res.end('<h1>Hello, World</h1>\n')
}
```

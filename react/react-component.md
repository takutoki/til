# Class Component and Stateless Functional Component

`React Component`での基本的なコンポーネントの書き方をまとめます


```js
ReactDOM.render() {
  <Greeting name="Ronaldo" age=33 />,
  document.getElementById('root')
}
```
`ReactDOM.render()`で描画を行う
描画内容である、Greetingコンポーネントに`name`と`age`を`props`として渡します

> Class Component

```js
class Greeting extends React.Component {
  constructor(props) {
    super(props)
  }
  render() {
    return <h1>My name is {this.props.name},{this.props.age} years old.</h1>
  }
}

// > My name is Ronaldo,33 years old.
```

classに`React.Componet`というReactの基本的なコンポーネントを基底クラスとして継承します
`render()`メソッドを定義して、その戻り値でコンポーネントの表示内容を返します
propsをそのまま渡すだけなら、constructorを定義しなくとも問題ない


> Stateless Functional Component

基本的なjsの書き方で実装すると、

```js
function Greeting (props) {
  return <h1>My name is {this.props.name},{this.props.age} years old.</h1>
}

// > My name is Ronaldo,33 years old.
```

ES6のアロー関数を用いると、

```js
const Greeting = (props) => (
  return <h1>My name is {this.props.name},{this.props.age} years old.</h1>
)

// > My name is Ronaldo,33 years old.
```
のように記述できる

> Stateless とは？

処理結果が変わるようなデータを内部に持たない状態を持たないコンポーネントのこと
コードライクでは`this.state.`がない
このようなコンポーネントは上記の２つの書き方の内、`Functional Component`で実装することが推奨されている

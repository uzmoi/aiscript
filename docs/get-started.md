# Getting started
## Introduction
AiScript(あいすくりぷと)は、プログラミング言語です。
このドキュメントでは、既にある程度のプログラミングの知識があることを前提にしています。
したがってAiScriptの構文、仕様などについてだけ書き、プログラミング自体についての説明は省きます。

## Hello, world!
AiScriptでは、次のように書きます:
```
print("Hello, world!")
```

`print( ~ )`は関数呼び出しです。カッコの前に呼び出す関数名を書き、カッコの中に引数を書きます。
引数が複数あるときは`,`で区切って列挙します。
関数についての詳細は後述します。

`"~"`は文字列リテラルです。`"`で囲ったものが文字列になります。

ちなみに、`print( ~ )`には糖衣構文があり、次のようにも書けます:
```
<: "Hello, world!"
```

## コメント
AiScriptのコメントは`//`で始めます。
コメントはプログラムの動作に影響を与えません。

```
// this is a comment
```

## リテラル
<table>
	<tr><th>種類</th><th>型</th><th>例</th></tr>
	<tr><td>文字列</td><td><code>str</code></td><td><code>"kawaii"</code></td></tr>
	<tr><td>数値</td><td><code>num</code></td><td><code>42</code></td></tr>
	<tr><td>真理値</td><td><code>bool</code></td><td><code>yes</code>/<code>no</code></td></tr>
	<tr><td>配列</td><td><code>arr</code></td><td><code>["ai", "chan", "cute"]</code></td></tr>
	<tr><td>オブジェクト</td><td><code>obj</code></td><td><code>{ foo: "bar"; a: 42; }</code></td></tr>
	<tr><td>null</td><td><code>null</code></td><td><code>null</code></td></tr>
	<tr><td>関数</td><td><code>fn</code></td><td><code>@(x) { x }</code></td></tr>
</table>

## 変数
### 宣言
変数宣言は次のように書きます:
```
#message = "Hello"
```

`#`のあとに変数名を書き、`=`の後に値を書きます。

### 参照
変数の値を参照する時は、変数名を書きます。このとき`#`は不要です。
```
print(message)
```

## 演算
演算は、
```
(1 + 1)
```
のように書きます。これは関数呼び出しの糖衣構文で、実際にはこのように解釈されます:
```
add(1, 1)
```

下記で列挙する関数はすべて`(1 + 1)`のような糖衣構文として使えます。
注意点として、`(1 + 1 + 1)`のようには書けず、`(1 + (1 + 1))`のように入れ子にして使います。

### 数の演算
<table>
	<tr><th>関数</th><th>演算子</th><th>意味</th></tr>
	<tr><td><code>add</code></td><td><code>+</code></td><td>加算</td></tr>
	<tr><td><code>sub</code></td><td><code>-</code></td><td>減算</td></tr>
	<tr><td><code>mul</code></td><td><code>*</code></td><td>乗算</td></tr>
	<tr><td><code>div</code></td><td><code>/</code></td><td>除算</td></tr>
	<tr><td><code>mod</code></td><td><code>%</code></td><td>剰余</td></tr>
</table>

### 論理演算
<table>
	<tr><th>関数</th><th>演算子</th><th>意味</th></tr>
	<tr><td><code>eq</code></td><td><code>=</code></td><td>等しい</td></tr>
	<tr><td><code>and</code></td><td><code>&</code></td><td>かつ</td></tr>
	<tr><td><code>or</code></td><td><code>|</code></td><td>または</td></tr>
</table>

## ブロック
ブロックは処理のまとまりで、`{ ~ }`のように書きます。
ブロックの最後に書かれた式が、ブロックの値として返されます。
```
#foo = {
	#a = 1
	#b = 2
	(a + b)
}

<: foo // 3
```

## if

## for

## 関数
### 関数定義
次のように書きます:
```
@fn(x) {
	(x * 2)
}
```

`@`の後に関数名を書き、カッコの中に引数定義を書きます。その後にブロックが関数の処理になります。

### return
関数の最後に書かれた式の値が関数の返り値になりますが、関数の途中で値を返したい時は`<<`を使います。
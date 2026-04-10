## 「描画開幕！Canvasに四角を描く超入門」

## ミッション：Canvasの中に、好きな色の四角を1つ描こう！

この課題では「`canvas` タグで描画エリアを作る」「`getContext('2d')` で描画の道具を取り出す」「`fillRect()` で四角を描く」技術を習得します。

花火シミュレーションに入る前の、いちばん最初の準備運動です。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<p class="hint">Canvasに四角を描いてみよう</p>
<canvas id="stage" width="320" height="240"></canvas>
```

CSSタブに下のコードを貼り付けてください。

```css
body {
  margin: 0;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(180deg, #0f172a, #1e293b);
  font-family: sans-serif;
}

.hint {
  margin-bottom: 16px;
  color: #cbd5e1;
}

#stage {
  background: #0b1220;
  border: 2px solid #334155;
  border-radius: 16px;
}
```

JSタブに下のコードを貼り付けてください。

```js
const canvas = document.querySelector('#stage');
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'gold';
ctx.fillRect(120, 80, 80, 80);
```

Canvasの中に、黄色い四角が1つ表示されることを確認してください。

### コードを読み解こう

#### `<canvas>` ：絵を描くためのキャンバス

```html
<canvas id="stage" width="320" height="240"></canvas>
```

`canvas` は、JavaScriptで絵を描くための特別なタグです。

今回の `width="320"` と `height="240"` は、描画エリアそのものの大きさです。あとで花火を作るときも、このキャンバスの中にロケットや粒を描いていきます。

#### `getContext('2d')` ：2D描画の道具を取り出す

```js
const ctx = canvas.getContext('2d');
```

`canvas` そのものは、まだただの描画エリアです。実際に線や図形を描くには、`getContext('2d')` で描画用の道具を取り出します。

この `ctx` が、これから何度も使う「描画ペン」のようなものです。

#### `fillStyle` ：塗る色を決める

```js
ctx.fillStyle = 'gold';
```

`fillStyle` は、図形を何色で塗るかを決める設定です。

今回は `gold` という黄色系の色を使っています。ここを変えると、四角の色も変わります。

#### `fillRect(x, y, width, height)` ：塗りつぶした四角を描く

```js
ctx.fillRect(120, 80, 80, 80);
```

`fillRect()` は、Canvasの中に塗りつぶしの四角を描く命令です。

| 引数 | 意味 |
|------|------|
| `120` | 左から120pxの位置 |
| `80` | 上から80pxの位置 |
| `80` | 四角の横幅 |
| `80` | 四角の高さ |

Canvasでは、左上が `(0, 0)` です。

- `x` は右に行くほど大きくなる
- `y` は下に行くほど大きくなる

この座標の考え方は、花火のロケットや粒を動かすときにもそのまま使います。

#### Canvasは「描いたものがその場に残る」

HTMLの `<div>` を増やすのとは違って、Canvasは「その場所に絵を描く」仕組みです。

つまり今回は、

1. `canvas` を用意する
2. `ctx` を取り出す
3. `fillStyle` で色を決める
4. `fillRect()` で四角を描く

という順で、画面の中に直接描いています。

### 改造しよう

#### ミッション①：色を変えよう

```js
ctx.fillStyle = 'gold';
```

ここを青や赤に変えると、四角の色が変わります。

#### ミッション②：位置を変えよう

```js
ctx.fillRect(120, 80, 80, 80);
```

最初の2つの数字を変えると、四角が移動します。

#### ミッション③：大きさを変えよう

```js
ctx.fillRect(120, 80, 80, 80);
```

後ろの2つの数字を変えると、横幅と高さが変わります。

#### ミッション④：四角を2つ描こう

`fillStyle` と `fillRect()` をもう1回書くと、別の場所に別の色の四角を描けます。

たとえば、

```js
ctx.fillStyle = 'gold';
ctx.fillRect(120, 80, 80, 80);

ctx.fillStyle = 'skyblue';
ctx.fillRect(40, 40, 60, 120);
```

のようにすると、四角を2つ描けます。


#### チェックしてみよう

✅️ `canvas` タグを使っている
✅️ `getContext('2d')` で描画の道具を取り出している
✅️ `fillStyle` で色を決めている
✅️ `fillRect()` で四角を描いている
✅️ 四角がCanvasの中に表示される


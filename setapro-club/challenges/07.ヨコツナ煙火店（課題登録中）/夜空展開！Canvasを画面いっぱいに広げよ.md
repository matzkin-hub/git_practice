## 「夜空展開！Canvasを画面いっぱいに広げよ」

## ミッション：Canvasを画面いっぱいに広げて、夜空の背景を描こう！

この課題では「Canvasを画面サイズに合わせる」「`fillRect()` で背景を描く」「画面リサイズに対応する」技術を習得します。

花火シミュレーションの土台になる、夜空ステージを作る回です。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<p class="hint">画面いっぱいの夜空を作ろう</p>
<canvas id="canvas"></canvas>
```

CSSタブに下のコードを貼り付けてください。

```css
body {
  margin: 0;
  overflow: hidden;
  background: #000;
  font-family: sans-serif;
}

.hint {
  position: absolute;
  top: 16px;
  left: 16px;
  margin: 0;
  color: white;
  z-index: 1;
}

canvas {
  display: block;
}
```

JSタブに下のコードを貼り付けてください。

```js
const canvas = document.querySelector('#canvas');
const ctx = canvas.getContext('2d');

function drawSky() {
  ctx.fillStyle = '#06142b';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
}

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  drawSky();
}

resizeCanvas();

window.addEventListener('resize', function() {
  resizeCanvas();
});
```

画面いっぱいに暗い夜空が表示されることを確認してください。ブラウザのサイズを変えても、Canvasが追従することも確認してください。

### コードを読み解こう

#### `canvas.width` と `canvas.height` ：描画エリアそのものの大きさ

```js
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

Canvasは、CSSで見た目の大きさを変えるだけでは不十分です。実際に絵を描く面積そのものも、JavaScriptで設定する必要があります。

`window.innerWidth` と `window.innerHeight` は、今のブラウザ画面の幅と高さです。

#### `fillRect(0, 0, canvas.width, canvas.height)` ：画面全体を塗る

```js
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

左上 `(0, 0)` から、Canvasの幅と高さぶんの四角を描くと、背景全体を塗れます。

花火シミュレーションでは、この「画面全体を塗る」処理を何度も使います。

#### `resize` イベント ：画面サイズが変わったときに呼ばれる

```js
window.addEventListener('resize', function() {
  resizeCanvas();
});
```

ブラウザの大きさが変わると、Canvasのサイズも合わせて更新したくなります。そのために `resize` イベントを使っています。

#### `drawSky()` と `resizeCanvas()` を分ける理由

```js
function drawSky() {
  ...
}

function resizeCanvas() {
  ...
  drawSky();
}
```

「サイズを変える処理」と「背景を描く処理」を分けておくと、あとでコードを追加しやすくなります。

### 改造しよう

#### ミッション①：夜空の色を変えよう

```js
ctx.fillStyle = '#06142b';
```

紺色や黒に変えると、夜空の雰囲気が変わります。

#### ミッション②：ヒントの位置を変えよう

```css
.hint {
  top: 16px;
  left: 16px;
}
```

表示位置を変えてみましょう。

#### ミッション③：夜空をもっと明るくしよう

背景色を少し明るくすると、花火の色の見え方も変わります。


#### チェックしてみよう

✅️ `canvas` を画面いっぱいに広げている
✅️ `canvas.width` と `canvas.height` を設定している
✅️ `fillRect()` で夜空を描いている
✅️ 画面サイズを変えてもCanvasが追従する


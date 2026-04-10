## 「ON/OFFスイッチ」

**ミッション：ボタンを押すたびにON/OFFが切り替わり、文字と色が変わる装置をつくろう！**

### コードを写そう

`HTML`タブに下のコードを貼り付けてください。

```html
<button id="btn">スイッチ</button>
<p id="status">OFF</p>
```

`CSS`タブに下のコードを貼り付けてください。

```css
#status {
  font-size: 2rem;
  color: gray;
  transition: color 0.3s;
}

#status.on {
  color: orange;
}
```

`JS`タブに下のコードを貼り付けてください。

```js
const btn = document.querySelector('#btn');
const status = document.querySelector('#status');
let isOn = false;

btn.addEventListener('click', function() {
  if (isOn) {
    status.textContent = 'OFF';
    status.classList.remove('on');
    isOn = false;
  } else {
    status.textContent = 'ON';
    status.classList.add('on');
    isOn = true;
  }
});
```

ボタンを押すたびに「ON（オレンジ）」と「OFF（グレー）」が切り替わることを確認してください。

### コードを読み解こう

#### `classList.toggle` との違い

「色を操る呪文」では `classList.toggle` でクラスを付けたり外したりしていました。今回は `classList.add` と `classList.remove` を `if / else` で明示的に使い分けています。

```js
// toggle を使う書き方（色を操る呪文）
box.classList.toggle('cursed');

// add / remove を使う書き方（今回）
if (isOn) {
  status.classList.remove('on');
} else {
  status.classList.add('on');
}
```

`toggle` は「付いていたら外す、外れていたら付ける」を自動でやってくれます。今回のように「クラスの付け外しと同時に別のこと（テキストの変更）もしたい」場合は、`if / else` で書いた方が処理の流れが見えやすくなります。

#### `#status.on` というCSSセレクタ

```css
#status.on {
  color: orange;
}
```

`#status.on` は「`id="status"` かつ `class="on"` が付いているとき」という意味です。JavaScriptで `.on` クラスを付けたときだけこのスタイルが適用されます。

### 改造しよう

#### ミッション：ON/OFFの文字と色を変えよう

```js
status.textContent = 'OFF';  ← OFFのときの文字
status.textContent = 'ON';   ← ONのときの文字
```

```css
#status.on {
  color: orange;  ← ONのときの色
}
```


### チェックしてみよう

✅️ ボタンを押すと「ON」になりオレンジ色になる
✅️ もう一度押すと「OFF」になりグレーに戻る
✅️ `let isOn` で状態を管理している
✅️ `classList.add` と `classList.remove` を使っている

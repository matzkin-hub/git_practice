## 「軍団召喚！forループ魔法を解放せよ」

## ミッション：ボタンを押すと、絵文字が5個並んで出るようにしよう！

この課題では「`for` ループで同じ処理を指定した回数繰り返す」技術を習得します。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<div class="stage">
  <button id="btn">召喚する</button>
  <div id="field"></div>
</div>
```

CSSタブに下のコードを貼り付けてください。

```css
body {
  margin: 0;
  background: #f5f0ff;
  font-family: sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.stage {
  text-align: center;
}

#btn {
  padding: 12px 32px;
  font-size: 1rem;
  background: #7b5ea7;
  color: white;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  margin-bottom: 24px;
}

#field {
  font-size: 2.5rem;
  min-height: 60px;
}
```

JSタブに下のコードを貼り付けてください。

```js
const btn = document.querySelector('#btn');
const field = document.querySelector('#field');

btn.addEventListener('click', function() {
  field.textContent = '';

  for (let i = 0; i < 5; i++) {
    const item = document.createElement('span');
    item.textContent = '⭐';
    field.appendChild(item);
  }
});
```

「召喚する」ボタンを押すと、星が5個並んで出ることを確認してください。

### コードを読み解こう

#### `for` ループの構造

```js
for (let i = 0; i < 5; i++) {
  // この中が5回実行される
}
```

`for` ループは3つの部分で成り立っています。

| 部分 | 意味 |
|------|------|
| `let i = 0` | カウンター変数 `i` を 0 から始める |
| `i < 5` | `i` が 5 より小さい間は繰り返す |
| `i++` | 1回終わるたびに `i` を1増やす（`i = i + 1` と同じ） |

繰り返しの流れ：

```
i = 0 → 星を1個出す
i = 1 → 星を1個出す
i = 2 → 星を1個出す
i = 3 → 星を1個出す
i = 4 → 星を1個出す
i = 5 → 「i < 5」を満たさないので終了
合計5個の星が出る
```

#### ボタンを押すたびにリセットする

```js
field.textContent = '';
```

`for` ループの前に `field.textContent = ''` を書いておくことで、ボタンを押すたびに中身を空にしてから5個出し直します。これがないと、押すたびに5個ずつ追加され続けます。

#### `i` の値を使うこともできる

今は `i` を使っていませんが、`i` の値（0, 1, 2, 3, 4）をコードの中で使うこともできます。

```js
for (let i = 0; i < 5; i++) {
  const item = document.createElement('span');
  item.textContent = i + 1;  // 1, 2, 3, 4, 5 と表示される
  field.appendChild(item);
}
```

### 改造しよう

#### ミッション①：個数を変えよう

```js
for (let i = 0; i < 5; i++) {
                       ↑ ここを変える
```

`5` を `10` にすると10個、`3` にすると3個になります。

#### ミッション②：絵文字を変えよう

```js
item.textContent = '⭐';  ← 好きな絵文字に変える
```

#### ミッション③（チャレンジ）：押すたびに1個ずつ増やそう

現在は毎回5個固定です。押すたびに1個ずつ増えるようにしてみましょう。

```js
let count = 0;

btn.addEventListener('click', function() {
  count = count + 1;
  field.textContent = '';

  for (let i = 0; i < count; i++) {
    const item = document.createElement('span');
    item.textContent = '⭐';
    field.appendChild(item);
  }
});
```

`count` を `i < count` の条件に使うと、押すたびに個数が増えます。


#### チェックしてみよう

✅️ ボタンを押すと5個の絵文字が出る
✅️ 何度押しても5個（増え続けない）
✅️ `for` ループを使っている


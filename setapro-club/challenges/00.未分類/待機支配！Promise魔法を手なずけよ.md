## 「待機支配！Promise魔法を手なずけよ」

## ミッション：宝箱を開くまで少し待って、成功と失敗を分けて表示しよう！

この課題では「すぐ終わらない処理を `Promise` で表す」「成功時と失敗時で処理を分ける」技術を習得します。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<div class="panel">
  <p class="title">謎の宝箱</p>
  <button id="openBtn">🎁 開ける</button>
  <p id="status">まだ開けていません</p>
</div>
```

CSSタブに下のコードを貼り付けてください。

```css
body {
  margin: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(180deg, #2d1e2f, #4a266a);
  font-family: sans-serif;
}

.panel {
  width: 320px;
  padding: 28px;
  border-radius: 24px;
  background: white;
  text-align: center;
}

.title {
  margin-top: 0;
  color: #223;
  font-size: 1.5rem;
}

#openBtn {
  border: none;
  border-radius: 14px;
  padding: 14px 24px;
  background: #5b7cfa;
  color: white;
  cursor: pointer;
}

#status {
  color: #556;
}
```

JSタブに下のコードを貼り付けてください。

```js
const openBtn = document.querySelector('#openBtn');
const status = document.querySelector('#status');

function openChest() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      const items = ['伝説のつるぎ', '回復の杖', '金貨100枚'];
      const success = Math.random() < 0.7;

      if (success) {
        const item = items[Math.floor(Math.random() * items.length)];
        resolve(item);
      } else {
        reject('ミミックが現れた！');
      }
    }, 1500);
  });
}

openBtn.addEventListener('click', function() {
  status.textContent = '宝箱を開封中...';
  openBtn.disabled = true;

  openChest()
    .then(function(item) {
      status.textContent = '入手：' + item;
      openBtn.disabled = false;
    })
    .catch(function(errorMessage) {
      status.textContent = errorMessage;
      openBtn.disabled = false;
    });
});
```

ボタンを押すと少し待ったあと、成功なら入手アイテム、失敗ならエラーメッセージが表示されることを確認してください。

### コードを読み解こう

#### `Promise` ：未来に終わる処理を表す箱

```js
return new Promise(function(resolve, reject) {
```

`Promise` は「今はまだ終わっていないけれど、あとで結果が出る処理」を表します。

#### `resolve()` と `reject()`

```js
resolve(item);
reject('ミミックが現れた！');
```

- `resolve()` は成功
- `reject()` は失敗

を表します。

今回は宝箱がうまく開いたら `resolve(item)`、失敗したら `reject(...)` に進みます。

#### 受け取る側は `then()` と `catch()` で分ける

```js
openChest()
  .then(function(item) {
    status.textContent = '入手：' + item;
  })
  .catch(function(errorMessage) {
    status.textContent = errorMessage;
  });
```

`then()` は成功時、`catch()` は失敗時です。あとから起こる結果でも、分かりやすく書けます。

#### 待ち時間がある処理と相性がよい

```js
setTimeout(function() {
```

今回のように「1.5秒待ってから結果が出る」処理は、Promiseの練習に向いています。

### 改造しよう

#### ミッション①：成功率を変えよう

```js
const success = Math.random() < 0.7;
```

`0.7` を変えると、成功しやすさが変わります。

#### ミッション②：宝箱の中身を増やそう

```js
const items = ['伝説のつるぎ', '回復の杖', '金貨100枚'];
```

レアアイテムを追加してみましょう。

#### ミッション③：開封中はボタンの文字を変えよう

`開ける` を `開封中...` にすると、待っている感じが伝わります。


#### チェックしてみよう

✅️ `new Promise(...)` を使っている
✅️ `resolve()` と `reject()` を使っている
✅️ `then()` と `catch()` で結果を分けている
✅️ 少し待ってから結果が出る


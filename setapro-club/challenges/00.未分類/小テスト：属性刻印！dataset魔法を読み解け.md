## 「小テスト：属性刻印！dataset魔法を読み解け」

## ミッション：HTMLに書いた情報を `dataset` で読み取れるか確認しよう！

この小テストでは、本編で学んだ `data-*` 属性、`dataset`、`event.currentTarget` を使います。

### 解くときの約束

- 値はHTMLに書いて、JSでは読むだけにしてください
- ボタンごとの処理をコピペしすぎないようにしてください


### 問1：ウォームアップ

次のコードの `TODO` を埋めてください。

```html
<button id="btn" data-name="火">属性を見る</button>
<p id="result">まだ見ていません</p>
```

```js
const btn = document.querySelector('#btn');
const result = document.querySelector('#result');

btn.addEventListener('click', function() {
  // TODO
});
```

#### 条件

- 変更は `1行`
- `火` を `result` に表示する
- `dataset` を使う

#### 確認ポイント

✅️ クリックすると `火` と出る
✅️ HTMLに書いた値をJSで読めている


### 問2：ミニ実装

次のコードに、色も切り替わる機能を追加してください。

```html
<button id="btn" data-name="水" data-color="skyblue">属性を見る</button>
<p id="result">まだ見ていません</p>
```

```js
const btn = document.querySelector('#btn');
const result = document.querySelector('#result');

btn.addEventListener('click', function() {
  result.textContent = btn.dataset.name;
});
```

#### お題

クリックしたら、`result.style.color` も `data-color` の値に変えてください。

#### 条件

- 追加は `1行`
- `btn.dataset.color` を使う

#### 確認ポイント

✅️ 文字が `水` になる
✅️ 文字色も変わる


### 問3：できたら挑戦

次のコードは、ボタンの中の文字を押したときに少し不安があります。

```html
<button class="spellBtn" data-name="雷">
  <span>⚡</span>
  <span>雷</span>
</button>

<p id="result">まだ見ていません</p>
```

```js
const btn = document.querySelector('.spellBtn');
const result = document.querySelector('#result');

btn.addEventListener('click', function(event) {
  result.textContent = event.target.dataset.name;
});
```

#### お題

このコードを直して、どこを押しても `雷` が表示されるようにしてください。

#### ヒント

`event.currentTarget` を使います。

#### 確認ポイント

✅️ 絵文字を押しても動く
✅️ 文字を押しても動く
✅️ ボタンの情報を読めている


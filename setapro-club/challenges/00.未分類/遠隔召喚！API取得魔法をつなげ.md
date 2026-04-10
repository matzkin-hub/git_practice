## 「遠隔召喚！API取得魔法をつなげ」

## ミッション：外部APIから記事データを取得して、画面に表示しよう！

この課題では「`fetch()` で外部データを取りに行く」「`async / await` で非同期処理を書く」技術を習得します。

この課題では、2026年4月時点で公開されている JSONPlaceholder のサンプルAPIを使います。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<div class="panel">
  <p class="title">遠隔記事ビューア</p>
  <button id="loadBtn">記事を取得する</button>
  <p id="status">まだ取得していません</p>
  <h3 id="postTitle">タイトルはここに出ます</h3>
  <p id="postBody">本文はここに出ます</p>
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
  background: linear-gradient(180deg, #102a43, #243b53);
  font-family: sans-serif;
}

.panel {
  width: 420px;
  padding: 28px;
  border-radius: 24px;
  background: white;
}

.title {
  margin-top: 0;
  text-align: center;
  color: #223;
  font-size: 1.5rem;
}

#loadBtn {
  border: none;
  border-radius: 14px;
  padding: 14px 20px;
  background: #5b7cfa;
  color: white;
  cursor: pointer;
}

#status,
#postBody {
  color: #556;
}

#postTitle {
  color: #223;
}
```

JSタブに下のコードを貼り付けてください。

```js
const loadBtn = document.querySelector('#loadBtn');
const status = document.querySelector('#status');
const postTitle = document.querySelector('#postTitle');
const postBody = document.querySelector('#postBody');

async function loadPost() {
  status.textContent = '読み込み中です...';

  const randomId = Math.floor(Math.random() * 100) + 1;
  const response = await fetch('https://jsonplaceholder.typicode.com/posts/' + randomId);
  const post = await response.json();

  postTitle.textContent = post.title;
  postBody.textContent = post.body;
  status.textContent = '記事番号 ' + randomId + ' を取得しました';
}

loadBtn.addEventListener('click', function() {
  loadPost();
});
```

ボタンを押すと、外部APIから記事データを取ってきて表示することを確認してください。

### コードを読み解こう

#### `fetch()` ：URLにデータを取りに行く

```js
const response = await fetch('https://jsonplaceholder.typicode.com/posts/' + randomId);
```

`fetch()` は、指定したURLへアクセスしてデータを取得する命令です。

#### `await` ：終わるまで待つ

```js
const response = await fetch(...);
const post = await response.json();
```

外部通信は一瞬では終わりません。`await` を付けると、その処理が終わるまで待ってから次の行へ進みます。

#### `async` ：`await` を使うための合図

```js
async function loadPost() {
```

`await` は、`async function` の中で使います。セットで覚えると分かりやすいです。

#### `response.json()` ：受け取ったデータをJavaScriptで使える形に変える

```js
const post = await response.json();
```

APIから返ってくるJSON文字列を、オブジェクトに変換しています。

### 改造しよう

#### ミッション①：取得する記事番号を固定しよう

```js
const randomId = Math.floor(Math.random() * 100) + 1;
```

ここを `1` や `10` に変えると、毎回同じ記事を出せます。

#### ミッション②：ボタンを押すたびに別の記事を見よう

今のコードでもランダムですが、前回と同じ記事を避ける工夫もできます。

#### ミッション③：タイトルを大きく目立たせよう

取得したデータをどう見せるかも大事です。CSSを調整して読みやすくしてみましょう。

### 参考にしたドキュメント

- [JSONPlaceholder Guide](https://jsonplaceholder.typicode.com/guide/)


#### チェックしてみよう

✅️ `fetch()` を使っている
✅️ `async / await` を使っている
✅️ `response.json()` でデータを変換している
✅️ APIから取ったタイトルと本文が表示される


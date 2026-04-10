## 「属性刻印！dataset魔法を読み解け」

## ミッション：火・水・雷のボタンを押し分けて、属性名と説明が切り替わるようにしよう！

この課題では「HTMLに情報を持たせる」「`dataset` でその情報をJSから読み取る」技術を習得します。

### コードを写そう

HTMLタブに下のコードを貼り付けてください。

```html
<div class="panel">
  <p class="title">属性を選ぼう</p>

  <div class="spell-list">
    <button
      class="spellBtn"
      data-name="火"
      data-emoji="🔥"
      data-color="#ff6b35"
      data-desc="攻撃力が高い、まっすぐな属性です。"
    >
      <span>🔥</span>
      <span>火</span>
    </button>

    <button
      class="spellBtn"
      data-name="水"
      data-emoji="💧"
      data-color="#3da9fc"
      data-desc="守りが得意で、安定した属性です。"
    >
      <span>💧</span>
      <span>水</span>
    </button>

    <button
      class="spellBtn"
      data-name="雷"
      data-emoji="⚡"
      data-color="#f7c948"
      data-desc="素早さが高く、一撃が重い属性です。"
    >
      <span>⚡</span>
      <span>雷</span>
    </button>
  </div>

  <div id="resultCard" class="result-card">
    <p id="resultName">まだ選ばれていません</p>
    <p id="resultDesc">上のボタンから属性を選んでください</p>
  </div>
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
  background: linear-gradient(180deg, #f6f8ff, #e8eefc);
  font-family: sans-serif;
}

.panel {
  width: 360px;
}

.title {
  text-align: center;
  font-size: 1.4rem;
  font-weight: bold;
  color: #223;
  margin-bottom: 20px;
}

.spell-list {
  display: flex;
  gap: 10px;
}

.spellBtn {
  flex: 1;
  border: none;
  border-radius: 16px;
  padding: 16px 12px;
  background: white;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
  cursor: pointer;
  font-size: 1rem;
  display: flex;
  flex-direction: column;
  gap: 6px;
  align-items: center;
}

.result-card {
  margin-top: 18px;
  padding: 20px;
  border-radius: 20px;
  border: 3px solid #d8deea;
  background: white;
  min-height: 100px;
}

#resultName {
  font-size: 1.2rem;
  font-weight: bold;
  color: #223;
  margin-top: 0;
}

#resultDesc {
  color: #556;
  margin-bottom: 0;
}
```

JSタブに下のコードを貼り付けてください。

```js
const spellButtons = document.querySelectorAll('.spellBtn');
const resultCard = document.querySelector('#resultCard');
const resultName = document.querySelector('#resultName');
const resultDesc = document.querySelector('#resultDesc');

spellButtons.forEach(function(btn) {
  btn.addEventListener('click', function(event) {
    const button = event.currentTarget;
    const name = button.dataset.name;
    const emoji = button.dataset.emoji;
    const color = button.dataset.color;
    const desc = button.dataset.desc;

    resultName.textContent = emoji + ' ' + name + '属性を選択中';
    resultDesc.textContent = desc;
    resultCard.style.borderColor = color;
    resultCard.style.background = color + '12';
  });
});
```

ボタンごとに、表示される属性名と説明が切り替わることを確認してください。

### コードを読み解こう

#### `data-*` 属性：HTMLに自由な情報を持たせる

```html
<button
  class="spellBtn"
  data-name="火"
  data-emoji="🔥"
  data-color="#ff6b35"
  data-desc="攻撃力が高い、まっすぐな属性です。"
>
```

`data-` で始まる属性は、HTMLに自由な情報を持たせるための仕組みです。

今回は1つのボタンに「名前」「絵文字」「色」「説明」を入れています。

#### `dataset` でJavaScriptから読み取る

```js
const name = button.dataset.name;
const emoji = button.dataset.emoji;
const color = button.dataset.color;
const desc = button.dataset.desc;
```

`data-name` は `dataset.name`、`data-color` は `dataset.color` のように読み取れます。

HTMLに書いてある情報を、そのままJavaScriptで使えるのが便利なポイントです。

#### `event.currentTarget` ：イベントを付けたボタン自身

```js
const button = event.currentTarget;
```

今回はボタンの中に `<span>` が入っています。そのため、クリックした場所によっては `event.target` が `<span>` になることがあります。

`event.currentTarget` を使うと、「イベントを付けたボタン自身」を確実に取れます。

#### 1つのコードで3つのボタンに対応できる

```js
spellButtons.forEach(function(btn) {
  btn.addEventListener('click', function(event) {
    // 中身は共通
  });
});
```

ボタンごとの差は、HTMLの `data-*` に入っている情報だけです。JavaScriptの処理は1つで済みます。

### 改造しよう

#### ミッション①：新しい属性を追加しよう

たとえば「風」を追加するなら、HTMLに新しいボタンを1つ足せば動きます。

```html
<button
  class="spellBtn"
  data-name="風"
  data-emoji="🍃"
  data-color="#63d471"
  data-desc="すばやく動ける、軽やかな属性です。"
>
  <span>🍃</span>
  <span>風</span>
</button>
```

#### ミッション②：表示内容を増やそう

`data-power="80"` のような属性を追加して、威力も表示してみましょう。

#### ミッション③：カードの色以外も変えよう

```js
resultCard.style.borderColor = color;
```

文字色や影の色も変えると、属性感がもっと出ます。


#### チェックしてみよう

✅️ 火・水・雷で表示内容が切り替わる
✅️ HTMLに `data-*` 属性を書いている
✅️ JSで `dataset` を使って値を取り出している
✅️ `event.currentTarget` を使ってボタン自身を取っている


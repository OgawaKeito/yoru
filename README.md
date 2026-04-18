# yoru.css

> 夜のための、ひとりぶんの CSS。

ダーク・テック方向に振り切った、**1ファイル完結**の日本製 CSS パッケージ。
LP・コーポレートサイト・ポートフォリオ制作のための、個人用の道具箱です。

```
version : 2.0
size    : 約50KB (gzip後 約10KB)
依存    : なし (Google Fonts は @import で同梱)
対象    : 個人利用
```

---

## もくじ

- [まず、これだけ覚える](#まずこれだけ覚える)
- [インストール](#インストール)
- [最初のページを作る](#最初のページを作る)
- [使い方 ― パーツ別ガイド](#使い方--パーツ別ガイド)
  - 見出しと文章
  - ボタン
  - カード
  - レイアウト（並べる）
  - 余白（すきまをあける）
  - 色を変える・強調する
  - フォーム（入力欄）
  - ナビゲーション（上のメニュー）
  - モーダル（ポップアップ）
  - アコーディオン（FAQ）
  - トースト（右下の通知）
  - ツールチップ（ふきだし）
  - スクロールでふわっと出す
- [色やサイズを全体で変える](#色やサイズを全体で変える)
- [よくあるレシピ](#よくあるレシピ)
- [困ったとき](#困ったとき)
- [含まれているもの一覧](#含まれているもの一覧)
- [v1.0 からの変更点](#v10-からの変更点)

---

## まず、これだけ覚える

yoru.css の使い方は、たった 2 ステップです。

**ステップ 1.** HTML に `yoru.css` を読み込む。
**ステップ 2.** HTML のタグに `class="..."` で名前をつけて飾りつけする。

たとえばこう書けば、

```html
<a href="#" class="btn btn-primary">ボタン</a>
```

きれいなシアンのボタンが出ます。
この「`class` に名前を書くとスタイルが当たる」の繰り返しだけで、サイト全体が組めます。

---

## インストール

`yoru.css` を HTML と同じフォルダに置いて、`<head>` の中にこの 1 行を書くだけです。

```html
<link rel="stylesheet" href="yoru.css">
```

npm も webpack も PostCSS もいりません。テキストエディタとブラウザだけで動きます。

---

## 最初のページを作る

コピペしてブラウザで開いてみてください。これだけで、見栄えのするページになります。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Site</title>
  <link rel="stylesheet" href="yoru.css">
</head>
<body class="has-navbar">

  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <span class="tagline">// hello</span>
        <h1>こんにちは、<span class="text-gradient">夜</span>。</h1>
        <p>ここから始めよう。</p>
        <a href="#" class="btn btn-primary btn-lg">スタート</a>
      </div>
    </div>
  </section>

</body>
</html>
```

### いま何が起きたか

- `<body class="has-navbar">` … 上にメニューバーを置く予定なので、その分の余白を確保しています。メニューがない場合は外して OK です。
- `<section class="hero">` … いちばん上の大きな見せ場のブロック。うしろに薄いグリッド模様とシアンのグロー（光）が自動で入ります。
- `<div class="container">` … 中身を画面の真ん中に寄せて、読みやすい幅に揃えてくれます。**ほぼ全ブロックで使います**。
- `<span class="tagline">` … モノスペースで小さく書かれる、ラベルのような小見出し。
- `<span class="text-gradient">` … 囲んだ文字に、シアンからバイオレットへのグラデーションをかけます。
- `<a class="btn btn-primary btn-lg">` … 大きいシアンのボタン。

**ポイント**：覚えるのは「よく使う道具の名前」だけ。全部覚える必要はありません。下のガイドを、使うときに辞書として開いてください。

---

## 使い方 ― パーツ別ガイド

### 見出しと文章

普通に `<h1>` や `<p>` を書けば、そのままきれいに表示されます。クラスは不要です。

```html
<h1>大きな見出し</h1>
<h2>中くらいの見出し</h2>
<p>これは普通の本文です。</p>
<p class="lead">これは大きめの導入文です。セクションの最初に使います。</p>
<p class="small text-muted">これは小さく薄い注釈です。</p>
```

文字に色をつけたいときは、文字の一部を `<span>` で囲んで色クラスをつけます。

```html
<p>この<span class="text-cyan">単語</span>だけシアンにします。</p>
<p>この<span class="text-violet">単語</span>だけバイオレットにします。</p>
<p>薄く<span class="text-muted">目立たせない</span>こともできます。</p>
```

キラッと光らせたいときは `text-gradient`（グラデーション）や `text-flicker`（ネオンが点滅するエフェクト）を使います。

```html
<h1><span class="text-gradient">未来を作ろう</span></h1>
<p class="text-flicker">SYSTEM ONLINE</p>
```

---

### ボタン

ボタンは全部 `btn` が基本です。そこに「どんなボタンか」を足します。

```html
<a href="#" class="btn btn-primary">メインのボタン（シアン）</a>
<a href="#" class="btn btn-secondary">サブのボタン（枠線のみ）</a>
<a href="#" class="btn btn-violet">バイオレットのボタン</a>
<a href="#" class="btn btn-ghost">控えめ（文字だけ）</a>
<a href="#" class="btn btn-outline-cyan">シアンの枠線だけ</a>
```

**サイズを変えたい**ときは、`btn-sm`（小さい）や `btn-lg`（大きい）を足します。

```html
<a href="#" class="btn btn-primary btn-sm">小さい</a>
<a href="#" class="btn btn-primary">ふつう</a>
<a href="#" class="btn btn-primary btn-lg">大きい</a>
```

**丸いアイコンボタン**にしたいときは `btn-icon` を足します。

```html
<button class="btn btn-icon btn-secondary" aria-label="設定">⚙</button>
```

**「処理中…」の表示**を出したいときは `is-loading` を足すと、ボタンの中にくるくる回るアイコンが出ます。

```html
<button class="btn btn-primary is-loading">送信中</button>
```

覚え方：`btn` + 色の種類 + （オプションでサイズ）。

---

### カード

情報をひとまとまりにして見せたいとき、`card` クラスをつけると、うっすら背景と枠線がついた箱になります。

```html
<div class="card">
  <h4>タイトル</h4>
  <p>中の文章。</p>
</div>
```

**上に色の線を入れたい**ときは `card-accent`（シアン）か `card-accent-violet`（バイオレット）を足します。

```html
<div class="card card-accent">
  <h4>タイトル</h4>
  <p>上がシアンに光ります。</p>
</div>
```

**マウスを乗せると浮かせたい**ときは `card-hover-lift` を足します。

```html
<div class="card card-hover-lift">
  <h4>ホバーで浮きます</h4>
</div>
```

**画像を上に載せたい**ときは `card-image`、**左右に並べたい**ときは `card-horizontal` を使います。

```html
<!-- 画像が上 -->
<div class="card card-image">
  <img src="photo.jpg" class="card-img" alt="">
  <div class="card-body">
    <h4>タイトル</h4>
    <p>説明文。</p>
  </div>
</div>

<!-- 画像が左、文章が右 -->
<div class="card card-horizontal">
  <img src="photo.jpg" class="card-img" alt="">
  <div class="card-body">
    <h4>タイトル</h4>
    <p>説明文。</p>
  </div>
</div>
```

---

### レイアウト（並べる）

中身を画面の真ん中に寄せたいときは `container` で囲みます。ほぼ全部のセクションで使います。

```html
<section>
  <div class="container">
    <!-- ここに中身 -->
  </div>
</section>
```

**横に並べたい**ときは `grid-2`（2列）・`grid-3`（3列）・`grid-4`(4列) を使います。スマホでは自動で縦並びになります。

```html
<div class="grid-3">
  <div class="card">1つめ</div>
  <div class="card">2つめ</div>
  <div class="card">3つめ</div>
</div>
```

**要素数がバラバラで自動調整してほしい**ときは `grid-auto`。横幅に応じて勝手に折り返します。

```html
<div class="grid-auto">
  <div class="card">A</div>
  <div class="card">B</div>
  <div class="card">C</div>
  <div class="card">D</div>
</div>
```

**ちょっとした横並び**には `flex` 系が便利です。

```html
<!-- 中身を中央に寄せる -->
<div class="flex-center gap-md">
  <button class="btn btn-primary">OK</button>
  <button class="btn btn-secondary">キャンセル</button>
</div>

<!-- 両端に寄せる -->
<div class="flex-between">
  <span>タイトル</span>
  <span>2026/04/18</span>
</div>
```

`gap-sm` / `gap-md` / `gap-lg` は、並べた要素どうしの**すきま**を決めます。

---

### 余白（すきまをあける）

ちょっと上下のすきまを足したいときは、`mt-`（上）と `mb-`（下）のクラスを使います。

```html
<h2 class="mb-lg">下に少し余白をあけた見出し</h2>
<p class="mt-md">上に少し余白をあけた段落。</p>
```

サイズは `sm`（小）/ `md`（中）/ `lg`（大）/ `xl`（特大）の 4 段階です。

---

### 色を変える・強調する

**バッジ**（小さいラベル）で強調したいとき：

```html
<span class="badge badge-cyan">NEW</span>
<span class="badge badge-violet">PRO</span>
<span class="badge badge-success badge-dot">公開中</span>
<span class="badge badge-warning badge-dot">保留</span>
<span class="badge badge-danger badge-dot">停止</span>
```

`badge-dot` をつけると、左にぽちっと丸がつきます。ステータス表示に便利です。

**枠のついたメッセージ**を出したいとき（`alert`）：

```html
<div class="alert alert-info">ℹ️ 情報：新しいバージョンがあります。</div>
<div class="alert alert-success">✅ 完了：保存しました。</div>
<div class="alert alert-warning">⚠️ 注意：もうすぐ期限です。</div>
<div class="alert alert-danger">❌ エラー：通信に失敗しました。</div>
```

---

### フォーム（入力欄）

`<input>` や `<textarea>`、`<select>` はクラス不要。置くだけでスタイルが当たります。

```html
<div class="form-group">
  <label>お名前</label>
  <input type="text" placeholder="山田 太郎">
  <span class="form-hint">本名でなくても構いません。</span>
</div>

<div class="form-group">
  <label>メッセージ</label>
  <textarea placeholder="ご自由にどうぞ"></textarea>
</div>

<div class="form-group">
  <label>プラン</label>
  <select>
    <option>Free</option>
    <option>Pro</option>
  </select>
</div>
```

`form-group` で囲むと、ラベル・入力欄・ヒントが自動で縦に並びます。

**ON/OFF スイッチ**がほしいときは `switch` を使います。

```html
<label class="switch-field">
  <span>通知を受け取る</span>
  <span class="switch">
    <input type="checkbox" checked>
    <span class="switch-slider"></span>
  </span>
</label>
```

チェックボックスやラジオボタンもあります：

```html
<label class="checkbox">
  <input type="checkbox" checked>
  <span>利用規約に同意する</span>
</label>

<label class="radio">
  <input type="radio" name="plan" checked>
  <span>Basic</span>
</label>
```

---

### ナビゲーション（上のメニュー）

画面の上に固定されるメニューバーを置くには、`navbar` を使います。`<body>` に `has-navbar` をつけるのを忘れずに（その分の余白を作ってくれます）。

```html
<body class="has-navbar">
  <nav class="navbar">
    <div class="container">
      <a href="#" class="navbar-logo">ロゴ</a>
      <div class="navbar-nav">
        <a href="#about">About</a>
        <a href="#works">Works</a>
        <a href="#contact">Contact</a>
      </div>
      <!-- スマホ用 -->
      <button class="hamburger" id="hamburger" aria-label="メニュー">
        <span></span><span></span><span></span>
      </button>
    </div>
  </nav>

  <!-- スマホで開くメニュー本体 -->
  <div class="nav-drawer" id="navDrawer">
    <nav class="nav-drawer-nav">
      <a href="#about">About</a>
      <a href="#works">Works</a>
      <a href="#contact">Contact</a>
    </nav>
  </div>

  <!-- 以下、本文 -->
</body>
```

ハンバーガー（横線 3 本のボタン）を押すとメニューが開くようにするには、少しだけ JavaScript が必要です。これは `demo.html` の一番下の `<script>` をそのままコピペすれば動きます。

---

### モーダル（ポップアップ）

画面の中央に出るダイアログです。

**1. 開くボタンに `data-modal-open="名前"` を書く**

```html
<button class="btn btn-primary" data-modal-open="myModal">開く</button>
```

**2. モーダル本体を置く**（`id` をさっきの名前と合わせる）

```html
<div class="modal-overlay" id="myModal" data-modal-close>
  <div class="modal" onclick="event.stopPropagation()">
    <div class="modal-header">
      <h3 class="modal-title">タイトル</h3>
      <button class="modal-close" data-modal-close>×</button>
    </div>
    <div class="modal-body">
      <p>中身の文章。</p>
    </div>
    <div class="modal-footer">
      <button class="btn btn-secondary" data-modal-close>キャンセル</button>
      <button class="btn btn-primary" data-modal-close>OK</button>
    </div>
  </div>
</div>
```

**3. `demo.html` のモーダル用 JavaScript をコピペする**。それだけで、背景クリック・Esc キー・× ボタンのどれでも閉じられるようになります。

サイズを変えたいときは `modal-sm` / `modal-lg` / `modal-xl` を `modal` に足します。

---

### アコーディオン（FAQ）

クリックで開閉する部分です。これは **JavaScript なし**で動きます。HTML 標準の `<details>` を使うからです。

```html
<div class="accordion">
  <details class="accordion-item" open>
    <summary>質問1：使い方は難しいですか？</summary>
    <div>簡単です。クラスを書くだけで動きます。</div>
  </details>
  <details class="accordion-item">
    <summary>質問2：ビルドは必要ですか？</summary>
    <div>いりません。</div>
  </details>
  <details class="accordion-item">
    <summary>質問3：カスタマイズできますか？</summary>
    <div>CSS変数で色やサイズを一括で変えられます。</div>
  </details>
</div>
```

最初から開いておきたい項目には `<details>` に `open` をつけます。

---

### トースト（右下の通知）

「保存しました」のような、一時的に出て消えるメッセージです。

**1. 表示先を 1 箇所だけ置いておく**（どこでもいいですが、`</body>` の直前がおすすめ）

```html
<div class="toast-stack" id="toastStack"></div>
```

**2. `demo.html` のトースト用 JavaScript（`yoruToast` 関数）をコピペする**

**3. 出したいタイミングで呼ぶ**

```html
<button class="btn btn-primary"
  onclick="yoruToast({type:'success', title:'保存しました', body:'無事に保存されました'})">
  保存
</button>
```

`type` は `success` / `info` / `warning` / `danger` から選びます。数秒で自動的に消えます。

---

### ツールチップ（ふきだし）

マウスを乗せると小さな説明が出るふきだし。**CSS だけで動きます**。

```html
<button class="btn btn-secondary" data-tip="ここに説明">上に出る</button>
<button class="btn btn-secondary tip-bottom" data-tip="ここに説明">下に出る</button>
<button class="btn btn-secondary tip-left"   data-tip="ここに説明">左に出る</button>
<button class="btn btn-secondary tip-right"  data-tip="ここに説明">右に出る</button>
```

ポイントは `data-tip="説明文"` を書くこと。方向は `tip-top`（既定）/ `tip-bottom` / `tip-left` / `tip-right` で選びます。

---

### スクロールでふわっと出す

スクロールして見えたときに、ふわっと現れる演出です。

**1. 見せたい要素に `reveal` クラスをつける**

```html
<div class="card reveal">
  <h4>下からふわっと</h4>
</div>
<div class="card reveal reveal-left">
  <h4>左からスライド</h4>
</div>
<div class="card reveal reveal-right">
  <h4>右からスライド</h4>
</div>
```

**2. `demo.html` のスクロールリビール用 JavaScript をコピペする**。これで全部の `.reveal` が自動で動きます。

---

## 色やサイズを全体で変える

yoru.css は、**CSS 変数**というしくみで色やサイズを一括管理しています。たとえば「全体のアクセント色をピンクに変えたい」と思ったら、`yoru.css` を直接いじらずに、**自分の CSS ファイル**を 1 つ用意してこう書きます：

```css
/* my-style.css */
:root {
  --cyan:      #ff3d88;
  --cyan-dim:  #d11e68;
  --cyan-glow: rgba(255, 61, 136, 0.15);
}
```

そして HTML で、`yoru.css` の**あとに**読み込みます：

```html
<link rel="stylesheet" href="yoru.css">
<link rel="stylesheet" href="my-style.css">
```

これだけで、ボタン・リンク・フォーカス枠・プログレスバー・タイムライン…など、シアンで作られていた部分がぜんぶピンクに変わります。

### よく使う変数

| 変えたいもの | 変数名 |
|---|---|
| メインのアクセント色 | `--cyan` |
| サブのアクセント色 | `--violet` |
| ページの背景色 | `--bg-1` |
| カードの背景色 | `--bg-2` |
| 本文の文字色 | `--text-1` |
| 見出しの文字色 | `--text-0` |
| 成功の色（緑） | `--success` |
| 警告の色（オレンジ） | `--warning` |
| エラーの色（赤） | `--danger` |

### 少し明るめのダークにしたい

`<body>` に `theme-soft` クラスを足すだけで、全体のトーンが少し明るくなります。

```html
<body class="has-navbar theme-soft">
```

---

## よくあるレシピ

### LP（ランディングページ）の骨組み

```html
<body class="has-navbar">
  <nav class="navbar">...</nav>

  <!-- 1. 大きな見せ場 -->
  <section class="hero">...</section>

  <!-- 2. 特徴を3つ並べる -->
  <section>
    <div class="container">
      <h2 class="mb-lg">特徴</h2>
      <div class="grid-3">
        <div class="card card-accent">...</div>
        <div class="card card-accent">...</div>
        <div class="card card-accent">...</div>
      </div>
    </div>
  </section>

  <!-- 3. 数字で信頼感 -->
  <section class="section-dark">
    <div class="container">
      <div class="grid-4">
        <div class="stat-card">...</div>
        ...
      </div>
    </div>
  </section>

  <!-- 4. FAQ -->
  <section>
    <div class="container container-md">
      <h2 class="mb-lg">よくある質問</h2>
      <div class="accordion">...</div>
    </div>
  </section>

  <!-- 5. 最後の行動喚起 -->
  <section class="section-gradient text-center">
    <div class="container">
      <h2>始めましょう</h2>
      <a href="#" class="btn btn-primary btn-lg">無料で試す</a>
    </div>
  </section>
</body>
```

### ポートフォリオの骨組み

1. ヒーロー（自己紹介）
2. スキル（`skill-item` と `progress-bar`）
3. 作品（`grid-3` で `card-image` を並べる）
4. 経歴（`timeline`）
5. 連絡先（フォーム）

---

## 困ったとき

**Q. `btn-primary` を書いたのにボタンの色が変わらない**
→ `btn` クラスも一緒に書いていますか？ 正しくは `class="btn btn-primary"` のように**2つ並べます**。`btn` が土台、`btn-primary` が色、という役割分担です。

**Q. スマホで確認するとメニューが消えている**
→ これは意図した動作です。スマホでは `hamburger`（三本線ボタン）で `nav-drawer` を開くしくみ。`demo.html` の末尾の `<script>` をコピペしてください。

**Q. モーダルが開かない**
→ 以下をチェック：
- 開くボタンの `data-modal-open="ID"` と、モーダル本体の `id="ID"` が**同じ名前**になっているか
- `demo.html` のモーダル用 JavaScript をコピペしたか

**Q. 背景をもっと暗く / もう少し明るくしたい**
→ 暗くする：セクションに `section-dark` を足す。
→ 明るくする：`<body>` に `theme-soft` を足す。

**Q. 自分で色を細かく変えたい**
→ `:root` 変数を自分の CSS で上書きしてください（「色やサイズを全体で変える」の項を参照）。

**Q. クラスをいっぱい書いたら崩れた**
→ yoru.css は「パーツごとに名前を当てる」考え方です。Tailwind のように `class="mt-5 px-3 bg-blue-500 ..."` のように**小さなクラスを積み上げる使い方はしません**。大きな単位（`card` / `btn` / `form-group` など）から選んで、ちょっとした調整だけ `mt-md` や `text-center` などで足す、が正しい使い方です。

---

## 含まれているもの一覧

### レイアウト
- `.container` / `.container-sm` / `-md` / `-lg`
- `.grid` / `.grid-2` / `-3` / `-4` / `-auto`
- `.flex` / `.flex-center` / `.flex-between` / `.flex-col`
- `.section-dark` / `-grid` / `-gradient` / `-dots` (v2.0)

### ナビゲーション
- `.navbar` / `.navbar-logo` / `.navbar-nav`
- `.hamburger` + `.nav-drawer` (v2.0)

### ボタン
- `.btn` + `-primary` / `-secondary` / `-violet` / `-ghost`
- `.btn-outline-cyan` / `-outline-violet` / `-icon` (v2.0)
- サイズ：`.btn-sm` / `.btn-lg`
- 状態：`.is-loading`（スピナー内蔵・v2.0）

### カード
- `.card` / `.card-accent` / `-accent-violet` / `-glow`
- `.card-hover-lift` / `-image` / `-horizontal` (v2.0)

### フォーム
- `.form-group` / `.form-hint`
- `.checkbox` / `.radio`
- `.switch` / `.switch-slider` / `.switch-field` (v2.0)

### オーバーレイ (v2.0)
- モーダル：`.modal-overlay` / `.modal` / `-sm` / `-lg` / `-xl`
- アコーディオン：`.accordion` + `<details>`（JS 不要）
- ツールチップ：`[data-tip]` + `.tip-top` / `-bottom` / `-left` / `-right`
- トースト：`.toast-stack` / `.toast` + `-success` / `-warning` / `-danger` / `-info`

### ローディング (v2.0)
- `.spinner` / `-sm` / `-lg` / `-cyan` / `-violet`
- `.skeleton` / `-text` / `-title` / `-avatar` / `-card` / `-image`

### その他
- `.badge`（6種）/ `.avatar`（4サイズ）/ `.stat-card`
- `.timeline` / `.progress` / タブ / テーブル / アラート

### アニメーション
- エントリー：`.animate-fadeInUp` / `-fadeIn` / `-pulse` + `.stagger-1`〜`-5`
- スクロール：`.reveal` / `-left` / `-right` / `-up` (v2.0)
- ホバー：`.hover-lift` / `.hover-glow-cyan` / `-violet` (v2.0)
- テキスト：`.text-flicker` / `.text-flicker-violet` (v2.0)

---

## JavaScript について

yoru.css は**可能な限り純 CSS で**動作します。JavaScript が必要なのは以下の 4 つだけで、`demo.html` の末尾にそのまま使える完成版が入っています。コピペするだけで動きます。

| 機能 | 何をしているか |
|---|---|
| ハンバーガーメニュー | ボタンクリックで `.is-open` を ON/OFF する |
| モーダル | `data-modal-open` / `data-modal-close` に反応する |
| トースト | `yoruToast({type, title, body})` を呼ぶと通知を出す |
| スクロールリビール | 見えてきたら `.is-visible` を付けて発火する |

**JS 不要で動くもの**：アコーディオン、ツールチップ、すべてのホバー効果、エントリーアニメーション。

---

## ファイル構成

```
yoru-v2/
├─ yoru.css      # 本体 (v2.0)
├─ demo.html     # 全コンポーネントのライブデモ（JSの完成版つき）
├─ index.html    # ドキュメント兼ランディングページ
└─ README.md     # このファイル
```

3 ファイルを同じフォルダに置いて、`index.html` をブラウザで開けばそのまま動きます。

---

## v1.0 からの変更点

### 🆕 新規追加
- ハンバーガーメニュー＋モバイルドロワー
- モーダル（4サイズ）
- アコーディオン（`<details>`ベース・JS 不要）
- ツールチップ（4方向・CSSのみ）
- スイッチ / トグル
- スピナー（3色×3サイズ）
- スケルトンローダー（shimmer 付き）
- トースト / 通知スタック
- セクション背景 4 種

### 🔧 改善
- カード強化（hover-lift / image / horizontal）
- ボタン強化（outline / icon）
- ボタンのローディング状態にスピナー内蔵
- スクロールリビール（`.reveal`）
- ホバー系ユーティリティ
- ネオンフリッカー（`.text-flicker`）
- z-index レイヤーを変数化
- `.theme-soft` でやや明るめダークに切替可能
- `prefers-reduced-motion` 対応
- `!important` 完全撤廃

### 🔒 後方互換性
v1.0 のクラス名は 1 つも変更していません。v1.0 で作ったサイトは、`yoru.css` を差し替えるだけでそのまま動きます。

---

## ブラウザサポート

モダンブラウザ（Chrome / Edge / Firefox / Safari の直近 2 世代）。
IE は非対応です。

---

*stay dark, stay sharp.*

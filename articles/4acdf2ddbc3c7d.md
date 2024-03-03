---
title: "`:has`を使って「特定の要素が後ろにある場合」にマッチ"
emoji: "👉"
type: "tech"
topics: ['css']
published: true
---

これまでのCSSは、要素の並び順によりスタイルングは「特定の要素に続く要素へのスタイリング」が可能でした。
しかし、最近導入された`:has` セレクタを利用すると、「特定の要素が『後ろ』に続く要素へのスタイリング」できるようになります。

サンプル:
@[jsfiddle](https://jsfiddle.net/8845musign/mzfxhku2/17/embedded/result,css,html/)

四角形の要素は丸の要素があとに続く場合、色が変化しテキストが追加されます。次のコードが該当のセレクタです。

```css
.box:has(+ .circle)
```

`:has` 擬似クラスは、擬似クラスが指定された要素を基準に（参考: [:has() - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/:has)）カッコ内のセレクタを満たす場合にスタイルが有効となります。
このセレクタを文章に置き換えると **`.box`を起点に、`.circle`が隣接している場合の`.box`** です。

別の例で考えてみます。

```css
.box:has(> .circle)
```

これは **`.box` を起点に子要素に`.circle`が存在する場合の `.box`** です。

名前から想像して、`:has` 擬似クラスは子孫要素のみを対象にしたセレクタだと勘違いしていました。

有名な[フクロウセレクタ](https://alistapart.com/article/axiomatic-css-and-lobotomized-owls/)も、:hasを使うと次のように書き換えます。

```css
.item + .item {
  margin-top: 10px;
}

/* :hasを使用 */

.item:has(+ .item) {
  margin-bottom: 10px;
}
```

セレクタはやや複雑ですが、左から右へ読めるため理解はしやすいかもしれません。

このパターンの用途ですが、う〜ん。。。ぱっとは思いつきません。例えばボタンが連続する場合に、前のボタンの角丸やボーダーを消したい場合に使えるでしょうか。覚えておいて損はなさそうです。

この記事を書くきっかけになった[CSS :has() Interactive Guide](https://ishadeed.com/article/css-has-guide/)には`:has`を使った様々なパターンが丁寧なデモつきで紹介されています。是非読んでみてください。

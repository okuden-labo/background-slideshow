# 背景画像のスライダーでよく使う3つのパターン

jQueryプラグインの[jQuery.BgSwitcher](https://rewish.jp/blog/releases/jquery_bg_switcher)を使い、背景画像のスライドショーでよく使われる3つのパターンを作成しました。

1. 全画面表示
2. 画面上部に表示(背景画像の縦横比が同じ)
3. 画面上部に表示(背景画像の高さを固定)


## 1.全画面表示

- 表示領域に対して縦横100％で表示すると、全画面表示になる。
- 画像は横900px縦600pxを利用。

[スライダー1のサンプル](./slide01/index.html?classes=button)

### CSS

```
 html,
  body {
    height: 100%;
    margin: 0 !important;
    padding: 0 !important;
  }

  .box {
    width: 100vw;
    height: 100vh;
    background-position: center center;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .bg-ttl {
    color: #fff;
    line-height: 1.5;
    font-weight: bold;
    text-align: center;
    text-shadow: 1px 1px 1px #000;
  }


```

### HTML

```
<div class="box">
  <h1 class="bg-ttl">背景画像スライダ―1<br>
全画面表示</h1>
</div>

```

### JavaScript

```
jQuery(function($) {
    $('.box').bgSwitcher({
      images: ['01.jpg', '02.jpg', '03.jpg', '04.jpg'], // 切り替える背景画像
      Interval: 5000, //切り替えの間隔 1000=1秒
      start: true, //$.fn.bgswitcher(config)をコールした時に切り替えを開始
      loop: true, //切り替えをループする
      shuffle: false, //背景画像の順番をシャッフルする
      effect: "fade", //エフェクトの種類 (fade / blind / clip / slide / drop / hide)
      duration: 1000, //エフェクトの時間 1000=1秒
      easing: "swing", //エフェクトのイージング 
    });
  });

```

## 2.画面上部に表示(背景画像の縦横比が同じ)

- 表示領域のpadding-topを`表示画像の高さ÷表示画像の幅×100`とすると、背景画像の縦横比を保つことができる。<br>今回の画像は横1500px縦600pxなので、600÷1500×100=40(%)となる。
- 高さが固定ではないので、上下中央に文字を表示させるのが難しく、ここでは固定の位置に文字を表示した。
- 難点として、スマホ表示にすると、縦幅がかなり小さくなる。

[スライダー2のサンプル](./slide01/index.html?classes=button)

### CSS

```
  html,
  body {
    height: 100%;
    margin: 0 !important;
    padding: 0 !important;
  }

  .box {
    width: 100%;
    height: 0;
    padding-top: 40%;　
    background-position: center center; 
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .bg-title {
    position: absolute;
    top:2.5rem;
    right:2.5rem;
    color: #fff;
    line-height: 1.5;
    font-weight: bold;
    text-align: center;
    text-shadow: 1px 1px 1px #000;
  }

```
### HTMLとJavaScript
全画面表示と同じ


## 3.画面上部に表示(背景画像の高さを固定)
- 通常の場合は画像の高さが500pxで固定されているが、スマホ表示(576px以下)は250pxに設定。
- デバイスによって表示される領域が異なる。中心のものは表示されるが、中心から離れると表示されなくなる。
- 2と同じく画像は横1500px縦600pxを利用。
- 画面上部に表示するなら、2より3の方が使い易く、一般的によく使わている。

[スライダー3のサンプル](./slide03/index.html?classes=button)

### CSS
```
html,
  body {
    height: 100%;
    margin: 0 !important;
    padding: 0 !important;
  }
  .box {
　  width: 100%;
　  height: 500px;
    background-position: center center;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  @media screen and (max-width: 576px) {
    .box {
      height: 250px;
    }
  }
  .bg-title {
    color: #fff;
    line-height: 1.5;
    font-weight: bold;
    text-align: center;
    text-shadow: 1px 1px 1px #000;
  }

```

### HTMLとJavaScript
全画面表示と同じ


---

## 最後に

今のところ背景画像のスライドショーならjQuery.BgSwitcherが使いやすいですが、もっといろんな効果を付けたい場合は[Vegas.js](https://vegas.jaysalvat.com/)をおすすめします。

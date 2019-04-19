# coding-tips


## XDなどの「AV」の扱い
「AV」はletter-spacingのことで、「AV」÷1000＝letter-spacing(em)となる。

## レスポンシブコーディング
innerでmax-widthを指定して、Widthの％でいじるとどの画面幅でも表示が崩れない

## ピクセルパーフェクト
・デザイン通り余白を入れても、ずれるのはline-heightを忘れているから

・ピクセルパーフェクトのツール
[ツール](https://haniwaman.com/perfect-pixel/)



## Web制作で自分がよく見落とすところ
・画像のファイルサイズの大きさ（ページ速度）  
・ブラウザ対応  
・レスポンシブ（どの画面幅でも崩さない）  
・横スクロールが発生していないか  
・画像重さ  
・画質  
・フォントファミリー  
**チェック表で必ずチェックするように**  
[チェック表](https://github.com/benzy78/template/blob/master/README.md)

## リキッドデザイン、フルードデザイン、レスポンシブデザインの違い
### 「フルードデザイン」（リキッドデザインもほぼ同じと考えて良いはず）
ボックスサイズを極力固定せず、画面サイズに合わせて伸縮するように作られたデザインのこと。  
ただし、要素やレイアウトによっては幅を固定しないと実現できないものがあるので、そこは臨機応変に対応する。

### 「レスポンシブデザイン」
* メディアクエリを使用し、指定された画面幅に応じてデザインやレイアウトを調整するもの。
* 基本的に相対値で値を指定する。

## ファイル形式の違い
### 「png-8」
* 単色のアイコンなど（色数の少ない画像）
* 容量が小さい
* 256色までしか使えない

### 「png-24」
* 容量が大きい
* 約1670万色のフルカラーが利用できる

### 「png-32」
* 背景透過が必要な画像、もしくはロゴやボタンなどのノイズが入って欲しくないもの。例）ロゴなど
* 容量が大きい
* 約1670万色のフルカラー＋256段階の不透明度（alpha値）が利用できる
* 半透明を使用できる

**＊フォトショップではPNG-24とPNG-32はまとめて「PNG-24」として扱われる。透明部分をチェックするとPNG-32として扱われる。
基本的にはPNG-24として扱い、ファイルサイズ小（8-bit）を使用するとPNG-8として扱われるはず。**

### 「jpg」
* 色数の多い写真など
* 保存を繰り返すと劣化する
* 容量はPNG-24より小さい
* 約1670万色のフルカラーが利用できる
* 画像の劣化とともにファイルサイズを軽くできる

### 「gif」
* 色数の少ないロゴやイラスト
* 透明にできる（半透明は無理）
* アニメーションなど
* 256色までしか使えない

### 「svg」
* 拡大してもボケない
* ロゴやアイコン向き
* サイズは大きめ

## 「nth-of-type」と「nth-child」の違い
* 「nth-of-type (n)」：同じ階層のn番目の要素にスタイルを適応させる。しかし、常に要素ごとの順番が数えられるため、別の要素と同じクラス名を併用した際は、要素ごとの順番でスタイルが適応される。
* 「nth-child(n)」：要素の種類にかかわらず、同じ階層の全ての要素を通して数えられる。

## `display:inline-block`を使い、改行が半角スペースとして扱われるとき、width%の値がずれる際の対処法
* 親要素にfont-sizeを0にすることで解決
* 改行しない
* （タグの中で改行する）＊ダサい
* （改行をコメントアウト）＊これもダサい
* floatを使う
* flexを使う

## footer-list横のボーダーの作り方
**例）item1 | item2**
1. border ＊これは微調整が効かないため、微妙なサイズの場合は使えない
2. 擬似要素

## ルート相対パスと相対パス
* 相対パス：リンク元のファイルを起点として、リンク先のファイルの場所を指定する方法。
* ルート相対パス：そのサイトのルートディレクトリを起点とするパスの指定方法。（大規模サイトなどでよく使われる）
**ルート相対パスだと、作業用パソコンでリンクが繋がらなくなる**

## hover時の下線引くアニメーション
aタグに対して
```
            &::after{
                        margin: 6px auto 0;
                        border-bottom: 1px solid #7c5119;
                        content:'';
                        display: block;
                        transition: width 0.3s ease-in-out;
                        width: 0;
                    }
                    &:hover{
                        &::after{
                            width: 100%;
                        }
                    }
```

## positionを使って中央寄せにしたい時
見出しの「ー」みたいな装飾をposition-absoluteを使って中央寄せするなら、left 50%にして、中央寄せしたい要素の長さの半分のwidthをclac関数を使って引くとどの画面幅でも中央寄せになる。

例）`left: calc(50% - 20px);`

## 縦の中央よせ
1. line-height
2. vertical-align
3. padding
4. align-items


## 三角形の作り方
三角はborderで作れる。仕組みを理解すべし。
[参考になるサイト](https://www.granfairs.com/blog/staff/make-triangle-with-css)

## コーディングの練習
サルワカとかにある、アニメーション豊富のボタンの作り方とかのコーディング勉強するとさらにCSSの理解が深まる
[参考サイト](https://kodocode.net/design-css-radiobutton/)


## labelとinputの紐付け
labelのforとinputを紐付けると見た目も、ユーザービリティも高い
[参考サイト](https://www.subarunari.com/entry/2018/04/15/ラジオボタンをCSSで異なる見た目にしてみたメモ)

## 凹むボタン
```
border-bottom-color: transparent;
transform: translateY(0.1875em);
```

## hover時のアニメーション
hover時のアニメーションなどで、transitionをつけるとサイトの印象が良くなる。必ずtransitionもセットでつけること。
`transition: all 0.3s ease 0s;`
**:hoverの擬似要素ではなく、元の要素につけること**

## アニメーションの注意点
jQueryのアニメーションもユーザーが違和感のないような設計をできるようにならないとダメだな。（でも、自分で考えるより、誰かがすでに考えたやつを真似るほうが効率いい。）
特にアコーディオンをもっと違和感なく作れるようにしよう。

## 「JS勉強のロードマップ」
JSのvueとかやる場合、基本文法、DOM、イベントハンドラー、非同期処理あたりを勉強した後にvueとかreactをやるのがいい。

JQuery＞Node.js＞JavaScript（ES6）＞脱JQuery＞Vue.js/React.js＞Nuxt.js/Next.js

## arrowボタンの作り方
```
@mixin linkArrow {
    position: relative;

    &::after{
        content: "";
        display: block;
        width: 5px;
        height: 5px;
        position: absolute;
        top: 50%;
        right: 10px;
        margin-top: -2.5px;
        border-top: 1px solid #333;
        border-right: 1px solid #333;
        transform: rotate(45deg);
    }
}
```

なお、Selectboxであれば、まずはselectの親をdivでくくり、そのdivに擬似要素でアローボタンを作り、position relativeにしてz-indexを5にする。（z-indexの値はselectboxより小さければどうでもいい）

そして、selectボックスの背景をtransparentにして、position relativeしてz-index10にする。（親のdivよりz-indexの値が高ければなんぼでもいい）

## ラジオボタンのコーディング

* 選択肢のグループにはname属性を指定
* 送信する値はvalue属性で指定
* labelのforの中身を、input[radio]のid属性で指定すると押しやすくなり、ユーザービリティが向上する
* とりあえず困ったら[ハニワマンさんの記事](https://haniwaman.com/form-css/#i-3)で確認しろ

## 下方向にだけbox-shadowをつけたい時

左右の影を消すために、4番目の指定（広がり値）をぼかしの値と同じだけ負の値で指定（縮小）すると消える。

この時、下方向の影の長さを負の値で指定した分だけ足さないと上と同じ影の長さにはならない。
```
.box-shadow {
  box-shadow: 0px 10px 5px -5px rgba(0,0,0,0.2);
}
```
[参考サイト](http://chroma.hatenablog.com/entry/2013/09/25/172809)


## CSSを使った改行
```
.css-br{
  width: 300px;
}

.br{
  content: "\A" ;
  white-space: pre;
}

@media screen and (max-width: 767px){
  /* たまに::before必要になるので注意 */
  .br{
      content: normal;
      white-space: normal;
    }
}
```

## CSSで作るハンバーガーメニュー（サルワカの応用版）
違和感なく右側からスライドしてくるハンバーガーメニュの作り方
参考記事[CSSだけで簡単！ハンバーガーメニューの作り方（スマホ対応）:サルワカ](https://saruwakakun.com/html-css/reference/nav-drawer)

HTML
```
<nav class="header__nav" id="header__nav__drawer">
  <input type="checkbox" id="header__nav__input" class="header__nav__unshow">
  <label for="header__nav__input" id="header__nav__open"><span></span></label>
  <label for="header__nav__input" class="header__nav__unshow" id="header__nav__close"></label>
  <ul class="header__list" id="header__nav__content">
    <li><a href="#news">News</a></li>
    <li><a href="#service">Service</a></li>
    <li><a href="#result">Result</a></li>
    <li><a href="#price">Price</a></li>
    <li><a href="#comments">comments</a></li>
    <li><a href="#qanda">FAQs</a></li>
    <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

CSS
```
@include sp {

	#header__nav__drawer {
        position: absolute;
        top: 0;
        right: 12px;
        padding-top: 18px;

		.header__nav__unshow {
			display: none;
		}

		#header__nav__open {
			display: inline-block;
			width: 30px;
			height: 22px;
			vertical-align: middle;

		}

		#header__nav__open span,
		#header__nav__open span:before,
		#header__nav__open span:after {
			position: absolute;
			height: 4px;
			width: 26px;
			border-radius: 20px;
			background-color: $MainColor;
			display: block;
			content: '';
			cursor: pointer;
		}

		#header__nav__open span {
			&::before {
				bottom: -10px;
			}

			&::after {
				bottom: -20px;
			}
		}

		#header__nav__close {
			display: none;
			position: fixed;
			z-index: 99;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background: $MainColor;
			opacity: 0;
			transition: 0.5s ease-in-out;

			&::before {
				position: absolute;
				content:"";
				top: 40px;
				left: 35px;
                background-color: $SubColor;
                border-radius: 20px;
				display: block;
				width: 30px;
				height: 5px;
				transform: rotate(45deg);
				transition: 0.5s ease-in-out;
			}

			&::after {
				position: absolute;
				content:"";
				top:40px;
				left: 35px;
                background-color: $SubColor;
                border-radius: 20px;
				display: block;
				width: 30px;
				height: 5px;
				transform: rotate(-45deg);
				transition: 0.5s ease-in-out;
			}
		}

		#header__nav__content {
            padding-top: 197px;
			overflow: auto;
			position: fixed;
			top: 0;
			right: 0;
			z-index: 9999;
			width: 80%;
			max-width: 300px;
			height: 100%;
			background: $SubColor;
			transition: 0.3s ease-in-out;
			transform: translateX(150%);

			li {
                margin-right: 0;
                margin-bottom: 20px;
                display: block;
				float: none;

				a {
					position: relative;
                    display: block;
                    text-align: center;
				}
			}
		}

		#header__nav__input:checked~#header__nav__close {
			display: block;
			opacity: 0.7;
		}

		#header__nav__input:checked~#header__nav__content {
			transform: translateX(0%);
			box-shadow: 6px 0 25px rgba(0, 0, 0, 0.15);
		}
	}
}
```

## background-positionの値について
background-position:「横方向の位置」「縦方向の位置」;

## ピラミッドみたいなやつのコーディング方法
　ー  
ー　ー
↑こんな感じのやつ
1. 親要素に`text-align: center;`
2. 「ー」に`display:inline-block`
3. 「ー」に`width: 49%;`

## レスポンシブコーディングのコツ
.innerで
```
.inner{
  margin: 0 auto;
  max-width: 1100px;
  width: 100%;
}
```
の場合、Blockにpaddingを１６〜３２くらい入れとかないと画面縮めた時に余白がなくて変になる。
もしくは、max-widthも相対値でとるか。

## MacでIEのチェック方法
1. グーグルドライブで確認したいファイルを送る。＊なおnodeは重すぎるので入れないように。
2. WindowsのPCでグーグルドライブを開きファイルをダウンロード
3. IEとEdgeで確認する
4. もし変な箇所があれば、Windowsの方でVSCode入れて編集・確認し、そのコードをMacのVSCodeでも書き換える
5. これで万事OK！

## flexのIEでのバグ報告
`flex: 0 0 100px;`
これはバグることがある。
なので、
```
flex: 0 0 auto;
width: 100px;
```
とするとバグらない。
ちなみに、後者では`max-width`とかも使えるよ

## JS/jQuery関係

### JSやjQueryが動かない時に考えるべきこと
検証ツールでコンソールエラーを確認する。

### アコーディオン作り方とマークアップ
html
```
<li class="qanda__content">
  <dl class="qanda__content__in">
    <dt class="qanda__content__question">
      <span class="qanda__content__question__icon">Q</span>
        <span class="qanda__content__question__body">質問</span>
        <span class="qanda__content__question__btn">＋</span>
    </dt>
    <dd class="qanda__content__answer">
      <p class="qanda__content__answer-in">回答</p>
      </dd>
  </dl>
</li>
```

JQuery
```
$('.qanda__content').click(function(){
    var $answer=$(this).find('.qanda__content__answer');
    if($answer.hasClass('open')){
      $answer.removeClass('open');
      $(this).find('.qanda__content__question__btn').text("＋");
      $answer.slideUp();
    }else{
      $answer.addClass('open');
      $(this).find('.qanda__content__question__btn').text("ー");
      $answer.slideDown();
    }
  });
```

### スムーススクロールのコード

```
$(function(){
	$('.header-list a').click(function(){
		var id = $(this).attr('href');
		var position = $(id).offset().top;
		$('html,body').animate({
		  'scrollTop':position
		},'slow');
	  });
});
```

### フローティングアクションボタン

```
jQuery(window).on("scroll", function($) {
	if (jQuery(this).scrollTop() > 100) {
	  jQuery('.btn-floating').show();
	} else {
	  jQuery('.btn-floating').hide();
	}
  });

  jQuery('.btn-floating').click(function () {
	jQuery('body,html').animate({
	  scrollTop: 0
	}, 500);
	return false;
  });
```

### swiperの使い方
まず、function()いらない

```
$(function()){

  }
```
これはHTMLの読み込みが終了してからjQueryの操作を開始するようにするコードね

swiperの使い方は下記の記事が一番わかりやすい

[swiper使い方記事](https://digipress.info/tech/introducing-swiper-js/)


## githubフロー(Github ver)
1. 自分のブランチを作成
2. ファイルの変更
3. `git add .`する
4. `git commit -v`
5. gitプッシュ　`git push origin` 作業用ブランチ (ここまでがローカルの作業ブランチ内での作業。次がGithubでの作業)
6. Githubの＜code＞の画面でbranchを自分の作業用ブランチに切り替える
7. New pull requestを押す
8. メッセージを書く **compareを作業用ブランチになっているか確認**
9. 緑のCreate Pull requestボタンを押す
10. Merge pull request を押す（１０、１１は共同開発なら誰か他の人がやる）
11. Confirm mergeを押す（プルリクが終了）
12. ローカルで自分のブランチをmasterにして、リモートの内容をローカルにpullする。`git pull origin master`
13. ローカルのブランチを作業用ブランチに切り替え、masterの内容を開発ブランチにmergeする。`git merge master`

## githubフロー（Bitbucket ver）
1. 自分のブランチを作成
2. ファイルの変更
3. git addする
4. git commit -v
5. gitプッシュ　git push origin 作業用ブランチ (ここまでがローカルの作業ブランチ内での作業。次がbitbucketでの作業)
6. bitbucketのブランチの画面でプルリクしたいbranchを選択し、プルリクエストの作成を押す（これでプルリクは完成）
7. メッセージを書いて、レビューを待つ。
8. マージを押す(8,9は基本自分ではやらない)
9. 遷移後にさらにマージを押す（プルリクが終了）
10. ローカルで自分のブランチをmasterにして、リモートの内容をローカルにpullする。`git pull origin master`
11. ローカルのブランチを作業用ブランチに切り替え、masterの内容を開発ブランチにmergeする。`git merge master(develop)`


## コーディングの小技

* place-holderの色を変えるには擬似要素を使う。なお、place-holderはIE９以下では非対応。
* headerの右側にナビゲーションを置くには、float:right;
* margin autoはinner以外にもいろんなところに使える（flexとか）
* 文字の両端ゾロえはtext-align:justify;を使う。leftやcenterじゃダメ。
* 大文字で区切るのを「キャメルケース」という
* text indentによる隠しテキストは「不必要なキーワードを検索エンジンのためだけに用意し見えなくする」という場合にペナルティになるが、割と抽象的な見解しかグーグルは出ていないため、基本的にあんまり使わない方がいい。
* セクションタグで見だしタグを使うのは推奨されているだけで必須ではない。デザインで見出しがない場合は見だしタグを作って`displey none`にするというのもありっちゃあり
* 日付とかはspanではなくtimeタグで作るべし
* formとtableはかなり特殊な扱いが必要なので、ハニワマンさんの記事を参考にする
* borderの一部の角だけ丸くするには `border-top-left-radius:;`
* HTML,CSSの各セクションの開始と終わりはコメントで区切ると境目がわかりやすい。
* IEではmainタグはinline要素になるのでmainタグにdisplay:block;をつけることが必要なことに注意が必要。
* コピーライトの©︎はUTF-8であれば問題なく表示できるので、必ずしも特殊文字じゃないとダメではない。けど、特殊文字使う方が無難。
* 一部の例外を除き、フレージングコンテンツ（I  input  label  select  span  button など）にはフレージングコンテンツの要素しか入らない。
* クラス名やディレクトリ名など数字を用いる場合は「01」のように２桁の連番にすると決めると、表記が揺れない。
* 下層ページ多いコーディングの場合はツリー状のサイトマップを作成しながら進める。
* margin３つの場合は、margin: 12px 20px 12px;  「上」、「左右」、「下」のとなる。
* 擬似要素は初期値がdisplay:inline;なので高さや幅をいじりたいならdisplay:block;にしないとダメ
* ボックスやカードの表示領域全体をクリックさせたいなら、paddingとネガティブmarginを使うことで対応。Border-radiusがある場合は、inheritを使って親要素の値を継承させる。なお、hover時にopacity:0.8;に、box-shadow、transition:all 0.3;をかけるとユーザービリティが向上しやすい。
* command + Shift + pでbeautifulを使える(VSCode)
* headerにもclassでheaderと入れないと、詳細度の問題が起こる。だからheaderにheaderクラスを入れる
* 中央寄せには、親要素をtext-align:centerにして、width 50%にして、子要素にwidth 100%すればいい。
* font-famliryを変数にするのはいいかも
* 環境構築でエラーになった時の対処法は再起動するか、sudoつけるかで大体解決する
* ひし形の装飾みたいなやつは擬似要素で四角を作って、transformで回転させて、z-indexをマイナスにする。
* `control + tab`でファイルの移動
* formは基本的にデフォルトの値は全て消さないと各ブラウザで表示がおかしくなる。
* **font-familyの指定には、英語のフォントを先に書くようにする。**
* IEのチェックは実機で確認する
* ハンバーガーメニューのナビゲーションはサルワカで作る。なお書き方は30dayの書き方を参照に。
* 疑似要素は非DOMなので、後からJavaScriptで色を変えたりcontentで設定しているテキストを他のものに書き換えることができない。
* BEMとSassの相性いいな。アンパサンド使うとかなりソースが見やすくなる。
* aタグは生で使わない。必ずpかdivでくくる
* ボタンなどは上下にのみ余白をつけ、横幅はmax-widthで最大幅を指定し、width 100% にしてリキッドデザイン

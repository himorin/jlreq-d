# Requirements for Japanese Digital Text Layout
[日本語の説明](#日本語デジタルテキスト組版の要件)は英文の後にあります。

This is a working document and can change with the progress of the project. The English version of this document is coming soon (how soon?).

## The motivation
Like manuscript and printed text, the printed text and digital text stand on fundamentally different technologies. One fundamental difference is when/where the layout is finalised. With printing, the sender of the text fixes the layout, typically after manual inspections, and the single static image is distributed to the receivers. With the digital text, the layout is not resolved until the last minute, and on the receiver's device many different images are generated automatically depending on the device environment and their preferences. Such differences give digital text unique limitations and possibilities intrinsically different from printed text.

For this reason, we believe there are benefits to producing a document dedicated to the digital text. At the meeting held on Oct. 2021, the JLreq Task Force members agreed to develop such a document as something that succeeds the existing JLreq that describes text layout on print. The tentative name is JLreq-d.

Because the digital text has a shorter history and is evolving, there will be issues that we do not have a definite answer to and ones that are open questions. Still, we believe it is worth collecting practices we have learned and adding our thoughts to them. Because it is evolving, the document would need to be continuously updated, so it does not become obsolete.

(The construction of the English version is in progress)

# 日本語デジタルテキスト組版の要件
これは「生きている文書」であり、内容がプロジェクトの進行につれて変化する可能性があります。

## モティベーション
ちょうど手書きによる書写と印刷のように、印刷とWebに代表されるデジタルテキストでは、技術的な成り立ちが根底から異なっている。一つの根本的な違いは誰が組版を決定するかにある。印刷においては送り手が、しばしばプロによる校正ののち組版を決定し、単一のイメージに固定したものを受け手に配布する。デジタルテキストにおいては組版は送り手の元で完成せず、受け手の元で無数の異なるイメージが生成される。このような違いが印刷と本質的に異なる制約条件と可能性を生み出す[^note]。
[^note]: 詳細は 2019/03/31 Keiko Univ. APL 報告の木田の文章参照（ここにチェックインしておく？）。

このため、印刷のためではない、デジタルネイティブな組版について記述した文書を開発することは有用であると考える。デジタルテキストにフォーカスした要件文章を JLReq の先にあるものとして開発することの合意が JLReq TF で行われた（2021/10）。とりあえずの略称を JLreq-d とする。

デジタルデバイス上の組版は進化しつつある技術なので、単一の答えがなかったり、そもそも答えのない問題もあるだろう。それでも、現在までの経験や考察によりわかっていること、また明らかになった課題などを、一旦ここでまとめておくことに意味があると考える。また、現状に追い越されないように、一旦の完成後も将来のチームによって継続的なアップデートが必要になろう。

このドキュメントは、テキストレイアウトや電子書籍がデジタルネイティブな環境でどのようにあるかを示した、少なくともW3Cの中では、最初のものになると思われる。先例があれば教えてほしい。ゆえ、結果的に、言語共通の考察も多く含まれることとなろう。


新しいドキュメントを作るもう一つのモティベーションは、開発支援である。JLreq を読み下してソフトウェアに落とし込もうとすると、いくつかの障害に突き当たる。
- 多くの部分が技術独立に書かれており、ソフトウェアとの距離がある
- 国内市場で培われてきた技術の記述であり、国際化システムとの距離がある
- ある程度の日本語や日本語組版技術への知識を前提とした記述となっている
- 機能のプライオリティが示されていない

これらのため、ソフトウェアを開発しようとすると、独自の解釈による翻訳、そしてマーケットの知識なしには難しい判断が必要となる。シンプル化、プライオリティ付け、デフォルトの方法の提案などにより規格化コスト・実装コストを下げ、それにより、より早期に、より多くの、またよりベンダ間で統一の取れた実装が得られることを期待する。


デジタルテキストによって可能になることの一つは、より優れたアクセシビリティである。柔軟な表示が可能であることにより、より多くの人に対応することができる。テキストをよりアクセシブルにするために考慮すべき点などを示すことで、より多くの人にとって使いやすい環境が達成されることを期待する。従来の印刷では特殊事例と言えるアクセシビリティを一般的なこととして扱う、これがこの文書の三つ目の柱である。


## 対象読者
- ソフトウェア開発者
- コンテンツ制作者

## 対象とするアプリケーション
- メールやメモなど組版指定のない日常のテキスト
- Web ページ（リフローしスクロールするドキュメント）
- ワードプロセッサー文書（ページがある）
- 電子書籍（書籍としての構成を持つ）
- アクセシビリティの重要なWebページや教科書

#### これらは対象外とする
- 印刷のためのページレイアウトアプリケーション（JLReqが対応）
- グラフィックデザインや広告

## アプローチ
### 書き方の方針
- 考え方を示す：デジタル技術の進化は早く、その上に成り立つデジタルテキストも従来より早い速度で変化してゆくと考えられる。ゆえ、組版の一つの方法をはっきりと示しつつも権威的にならず、同時に他の方法、その機能を考える際に重要なこと、答えのない課題などを提示することによって、判断のベースにし、また将来の進化を促す inspiring な内容にする。
- 基本的機能からより高度な機能へ内容を配列する：入口を低くする

### デジタルにおける新しい要素
- リフローアーキテクチャ。無数の組版が読み手の手元で生成されるアーキテクチャ
- 冊子形態が持つ意味の喪失
- 検索可能性
- ラグ組や空白行で区切られる欧文スタイルのパラグラフ
- ベースラインなど欧文ベースのエンジン上での振る舞い
- プロポーショナルな要素を多く含むテキスト、またプロポーショナルな和文書体の扱い
- リンクによるナビゲーションや注の機能など、デジタルテキストならではの優れた機能の利用
- より良いアクセシビリティの可能性
- 多様なサイズの画面。モバイルデバイスに代表される小さな画面

### 国際化ソフトウェア環境との親和性を高める方法
#### 多言語の中の日本語として記述
- 従来の JLReq は日本語に閉じた環境を扱っている。その意味で JLReq は JIS 文字規格に似ている。JLreq-d では Unicode のように国際化ソフトウェア環境の中の一つの言語としての日本語を扱う。
- その前提で、外国語、数式など日本語組版の中で規定する必要のないものは対象外。界面の振る舞いだけを定義する
#### 技術の扱いの方針
- 現在進行形の技術の中での組版なので、技術の前提なしに議論することは不可能である。同時に、技術の詳細からは中立に記述することによって、寿命の長い記述方法になることを期待する。
- ドキュメントでどの技術を前提としているかを明確化する。確立され、今後も使われると思われる基礎的な技術：Unicode、ウェブ技術、高機能フォント。
- 必要な組版機能に対して規格に不足があれば、その不足を洗い出して指摘する。規格化や実装が前に進んでいない機能を分析する。それらが前に進むことを支援できるように整理を行う。

#### 実装支援
- シンプル化、プライオリティ付け、デフォルトの方法の提案などにより規格化コスト・実装コストを下げる
- 日本語や日本語組版の概念を知らない技術者の理解のため、基本を書く
- 組版指定がなくても自動的に動くべき機能、言い換えるとプレーンテキストでも動くべき機能と、ルビのようにマークアップなどでの指定が必要な機能が見分けられるように書く
- 複数の方法がある場合、それが実装者の選択であるべきか、エンドユーザーの選択であるべきかを見分ける。印刷ではそれらを組版を行うものが決めていた

## 目次案
このレポジトリのGitHub wiki内の[目次案](https://github.com/w3c/jlreq-d/wiki/jlreq-d-ToC-draft)を参照ください。

See [draft Table of Content](https://github.com/w3c/jlreq-d/wiki/jlreq-d-ToC-draft) at GitHub wiki of this repository.

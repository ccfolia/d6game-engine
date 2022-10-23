# はじめに
私はTRPGのようなトークベースで遊べるゲームが好きで、常日頃からもっとたくさん遊びたいと考えていました。そこで、私はちょっとした空き時間で気軽に遊べるような小さなダイスゲーム（六面ダイスを振って、4以上が出たら成功だ！）を作って遊んでみましたが、いまいち面白くありませんでした。それは友人と話しはじめるきっかけとしては十分でしたが、ゲームが面白ければもっと最高です。それから何ヶ月か試行錯誤をして、ポーカーのルールを判定に組み込むことを思いつき試してみると、これが不思議と面白く日常的に楽しめるゲームが作れるようになりました。そういった経緯で、このゲームシステムは以下のことを目指して作られています。
* 同僚や友人と短い時間でも楽しく遊べる
* 最小限の説明でゲームを始められる
* 簡単なルールなのに、奥が深いゲームが作れる
# 概要
d6game engine には、自分だけの小さなTRPGを制作することができるゲームシステムが実装されています。このゲームシステムのドキュメントに書かれていることは、権利表記さえあれば商用・非商用を問わず誰でも無償で自由に利用することができます。また、ルールはゲームの制作者が自由にカスタマイズして構いません。あなたのゲームの世界観に合わせて独自の要素を付け足したり、変更したりすることができます。
#### 権利表記
```
This game is published under ccfolia d6game engine License.
Copyright (c) 2022 ccfolia
```
# 命運（ライフ）
このゲームのあらゆるリソースは、命運と呼ばれるひとつの値に集約されます。命運の値はプレイヤーキャラクターのライフであり、場合によってはマジックパワーであり、資源でもあります。命運が尽きたプレイヤーキャラクターの扱いはゲーム毎に異なりますが、通常はゲームオーバーとなります。命運の値は、例えば戦闘ダメージを受けたり、アクシデントによって減少していきます。逆に、何か重要な手がかりを発見したり、敵を打ち倒したりすると増加することがあります。プレイヤーにとっては、最終ボスとの戦闘やエンディングに向けてなるべく命運の値を高めながらゲームを進めていくことが重要になるでしょう。命運の初期値は、特に指定がなければ 2d6 で決定します。
# 行為判定
このゲームでは、キャラクターの行動が失敗もしくは成功するかどうか、ダイスを使って判定を行うことができます。
1. 六面ダイスを5つ振る
2. ダイスの出目を使って役を作り、得点を確認する
3. 得点が1点以上（ツーペア以上）の場合、判定は成功となる。同時に得点と同じ値の命運を獲得する
4. 役が作れない場合は、ひどい失敗（ファンブル）となり、命運を-5点失う

判定を行う際、キャラクターの所持している技能もしくは能力、設定などを加味してゲームマスターが有利な状況であると判断した場合や難易度が高いと思われる判定では、ツーペア以上ではなくワンペア以上やスリーダイス以上など個別に判定の目標値を設定することもできます。
## 役の種類と得点
### ノーハンド（-5点）
役が作れない（ファンブル）
例 ○○○○○
### ワンペア（0点）
同じ出目が2つある
例 ①①○○○
### ツーペア（1点）
ワンペアが2組ある
例 ①①②②○
### スリーダイス（2点）
同じ出目が3つある
例 ①①①○○
### フルハウス（3点）
ワンペアとスリーダイスがある
例 ①①②②②
### ストレート（4点）
5つ出目が連番になっている
例 ①②③④⑤
### フォーダイス（5点）
同じ出目が4つある（クリティカル）
例 ①①①①○
### ザ・ファイブ（10点）
同じ出目が5つある（スーパークリティカル）
例 ①①①①①
# 戦闘
戦闘を行う場合には、命運の値と判定のルールを使ってゲームマスターやプレイヤー同士が勝負を行います。多くの場合、ゲーム中に手に入れたアイテムや情報を使って最後にゲームマスターの用意した敵役を打ち倒すことがゲームの目標になります。
1. 命運が低い順に手番を得る
2. 手番のプレイヤーは攻撃対象を指定する
3. 手番のプレイヤーは攻撃対象プレイヤーから見えないように判定を行い役を作る
4. 手番のプレイヤーは役を確認し、その攻撃に賭ける命運を1~10点の間で決定する
5. 攻撃対象となったプレイヤーは応戦か回避を選択する
	1. 応戦の場合、攻撃対象となったプレイヤーは判定を行い、役の得点が低い方が賭けられた命運と同じ数だけ命運を失う。得点が同値の場合、命運の減少は行わない
	2. 回避の場合、判定を行わず攻撃対象となったプレイヤーは賭けられた命運の半分（切り捨て）の命運を失う
6. 命運が0以下となった場合、戦闘不能となる。戦闘終了後に味方が生存している場合は、命運が1点の状態で復帰することができる
# キャラクターの創造
名前、年齢などのパーソナルなデータに加えて、命運の値を決定します。また、オプションとしてキャラクターの持つ技能3つと能力値を決定することもできます。
## プロフィール
名前、年齢などのパーソナルなデータを設定します。以下の設定項目は一例であり、ゲームごとに変更して構いません。
* 名前
* 年齢
* 性別
* 職業
* 説明
## 基礎能力（オプション）
能力はそれぞれ 2d6 で決定します。結果が気に入らなければ、何度振り直しても構いません。これらはあくまでキャラクターの設定を数値化するものであり、ゲームマスターが裁定を行う際の参考値として扱います。どのようにこの値を運用しても構いません。
* 力：筋力、力強さ
* 敏捷： 器用さ、速さ
* 健康：頑丈さ、免疫力
* カリスマ：リーダーシップ、交渉
* 知恵：ひらめき、アイデア
* 知識：学問、教養
## 技能（オプション）
技能は以下のうちから三つ選んで記載することができます。技能の種類や内容はゲーム毎に新たに追加したり、拡張して構いません。技能は永久的なものではなく、例えば転職などキャラクターの置かれる状況によって追加・変更されることがあります。これらは基礎能力と同じくゲームマスターが裁定を行う際の参考として利用できます。
* 戦闘（拳銃など、得意分野を併せて自由記述）
* 調査（人探しなど、得意分野を併せて自由記述）
* 芸術・芸能（ダンスなど、得意分野を併せて自由記述）
* 技術・工業（プログラミングなど、得意分野を併せて自由記述）
* 交渉・影響力（話術や経済力など、得意分野を併せて自由記述）
* 知識（生物学や医学など、得意分野を併せて自由記述）
# 新しいゲームの制作
**執筆中**

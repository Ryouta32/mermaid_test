# 課題
Mermaidを触ってみよう

マークダウンファイルを編集して、Mermaidで図を描いてみよう

# 取り組み方
* 本プロジェクトをforkしてください。
* README.mdを編集して、Mermaidを使いこなしてください
* できたらプルリクエストを出します

# 課題項目
## 流れ図
### 条件
- 開始と終了ノードをつける
- 条件分岐を組み込む
- 5ノード以上
- カッコいいほど高得点

## 解答
RPGの戦闘システム
```mermaid
flowchart LR;
  A(("戦闘開始")) --> B{"コマンド入力"}
  B{"コマンド入力"}-->C("こうげき")
  B{"コマンド入力"}-->D("じゅもん")
  B{"コマンド入力"}-->F("どうぐ")
  B{"コマンド入力"}-->G("にげる")
  C("こうげき")-->Q("敵にダメージ")
  D("じゅもん")-->E{"MPが足りる?"}
  E{"MPが足りる?"}-->|MPが足りない|B("コマンド入力")
  E{"MPが足りる?"}-->|MPが足りる|I("敵にダメージor仲間を回復")
  F("どうぐ")-->I("敵にダメージor仲間を回復")
  G("にげる")-->H{"逃走判定"}
  H{"逃走判定"}-->|成功|P(("戦闘終了"))
  H{"逃走判定"}-->|失敗|B("コマンド入力")
  I("敵にダメージor仲間を回復")-->J{"敵のHP判定"}
  J{"敵のHP判定"}-->|HPが0以下|N("勝利")
  J{"敵のHP判定"}-->K("敵のターン")
  K("敵のターン")-->L("プレイヤーに攻撃")
  L("プレイヤーに攻撃")-->M{"プレイヤーのHP判定"}
  M{"プレイヤーのHP判定"}-->|HPが0以下|O("敗北")
  M{"プレイヤーのHP判定"}-->B("コマンド入力")
  N("勝利")-->P(("戦闘終了"))
  O("敗北")-->P(("戦闘終了"))
```

## シーケンス図
### 条件
- 3人以上
- メッセージをやり取りしない人がいないように
- 自己呼び出しを含むこと
- カッコいいほど高得点

## 解答
フリマアプリのやり取り
```mermaid
sequenceDiagram
ユーザー1->>注文システム:アイテムの購入申請
注文システム->>ユーザー2:購入申請の通知
ユーザー2->>注文システム:購入申請の受理
注文システム->>ユーザー1:購入申請の受理の通知
ユーザー1->>注文システム:代金の振り込み

opt 金額が振り込まれたら
注文システム->>ユーザー2:商品の配送申請
end

opt 商品が発送されたら
ユーザー2->>ユーザー1:商品の配送
注文システム->>ユーザー1:発送通知
end

注文システム->>注文システム:取引のやり取りの記録を保存
```

## クラス図

### 条件
- 3つ以上
- 汎化と集約を含むこと
- カッコいいほど高得点

## 解答
RPGのキャラクター
```mermaid
classDiagram
人間<|--戦士
人間<|--魔法使い
人間<|--僧侶
人間<|--勇者
人間:年齢
人間:名前
人間:性別
戦士:+技が使える()
魔法使い:+攻撃魔法が使える()
僧侶:+回復魔法が使える()
勇者:+必殺技が使える()
戦士--oパーティー
魔法使い--oパーティー
僧侶--oパーティー
勇者--oパーティー

# Titanic
URL: https://www.kaggle.com/competitions/titanic

## 課題
乗客データ（名前，年齢，性別など）を使用して，<br>
「どのような人が生き残る可能性が高いのか？」を予測するモデルを構築する．

## データセット
### 概要
- 訓練データセット（train.csv）
- テストデータセット（test.csv）
### 説明変数
|変数名|定義|Key|
|:----|:----|:----|
|survival|生存しているかどうか|0:No, 1:Yes|
|pclass|社会経済的地位| 1:1st, 2:2nd, 3:3rd|
|sex|性別||
|Age|年齢||
|sibsp|タイタニック号に搭乗した兄弟/姉妹/配偶者の数||
|parch|タイタニック号に搭乗した親子の人数||
|ticket|チケット番号||
|fare|旅客運賃||
|cabin|キャビン番号||
|embarked|乗船港|C:Cherbourg, Q:Queenstown, S:Southampton|
### 評価指標
$$Accuracy=\frac{正解数}{回答数}$$
## 提出ログ
|日付|精度|モデル|パラメータ|工夫した点|
|:---|:---|:---|:---|:---|
|2024/06/28|0.77751|ランダムフォレスト|n_estimators=100<br>max_depth=5<br>|なし（ベースライン）|
|2024/06/28|0.76794|LightGBM|objective="binary"<br>learning_rate=0.025<br>num_leaves=20<br>max_depth=5<br>verbosity=-1|モデルの変更|
|2024/07/01|0.77990|LightGBM|objective="binary"<br>learning_rate=0.025<br>num_leaves=20<br>max_depth=5<br>verbosity=-1|欠損のない変数から年齢を予測補完|
|2024/07/01|0.78229|LightGMB|objective="binary"<br>learning_rate=0.025<br>num_leaves=20<br>max_depth=5<br>verbosity=-1|苗字，Ticketから情報抽出|

## アイデア
- 年齢と他の変数の関係を分析して，他の変数から欠損値を推測して補完する
- その他，特徴エンジニアリング！
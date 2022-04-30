# 課題名 証券新入社員一日目教材

## プロダクトの内容
- ローソク足（4本値）を学ぶアプリ
- 4本値をお手本に沿って正しく入力する
  - お手本と入力した値があっていれば正解のメッセージ、不正解なら不正解のメッセージ
  
## 工夫した点・こだわった点
- chart.jsで4本値を描画できたこと
- jsonデータとお手本の回答チェックができたこと
- 検証用の入力ボタンをつけたこと
- ★ここからバージョンアップ部分
  - （勝ち数をつける）
  - 二度入力していた情報を整備
  - （randomで4本値生成）

## 苦戦した点
- randomで4本値を作成するときに高値が安値を下回る時があってrandomで作れなかった。
  - 内容を記入
- レポジトリ作成時にエラー　"The file will have its original line endings in your working directory"
  - 改行コードをCRLFに変換しちゃうよーってやつだったので以下のコマンドでさせないようにした
  - $ git config --global core.autoCRLF false

## 写経チェック
オリジナル課題

## https://sachioka.github.io/202203_localstrage/


## 作成メモ
- お手本のデータを最初は描画する
  - もし入力されたdataがあった時はそっちを描写する
- ans に初期値を入力
  - 回答したdata=candleとして入力されたjsondataと比較して出す

1. 一問目
   1. 一問目を描写する
      1. randomで選ばれた値をlocalStorageに保存（ans）
      2. localStorageから(ans)を持ってくる
      3. (ans)を(candle)に渡して描写する
   2. 回答を入力する
      1. 回答をlocalStorageに保存(ans_)
   3. [チャートを生成する]ボタンを押す
      1. localStorageから回答のデータを持ってくる(ans_)
      2. (ans_)を(candle)に渡して描写する
   4. [答え合わせ]ボタンを押す
      1. 答えがあっているとき　(ans)==(ans_)
         1. 回答記録(ans_array)に1を追加
         2. 記録を保存して合計する　★
            1. (ans_array)をlocalStorageに保存する(ans_array)
            2. (ans_array)を足し算array_reduce
         3. アラートで正解array_reduceを表示
         4. [次へ]ボタンを押す　⇒　2問目へ行く
      2. 答えが間違っているとき　else
         1. 回答記録(ans_array)に0を追加
         2. 記録を保存して合計する　★
            1. (ans_array)をlocalStorageに保存する(ans_array)
            2. (ans_array)を足し算array_reduce
         3. アラートで"不正解＆再度入力してみる"を表示
         4. (q_)を(candle)に渡して再描写する
         5. ⇒1-2. 回答を入力する　or [リトライ]ボタンを押す
            - [リトライ]の時
              - localStorageをリロードする
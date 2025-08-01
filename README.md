# Data-collection


以下のコードは、Pythonの `requests` ライブラリを使って **Web上にあるCSVファイルをダウンロードして保存する** という処理です。

---

## ✅ 全体のコード

```python
import requests

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DS0103EN-SkillsNetwork/labs/Module%202/recipes.csv"
response = requests.get(url)

with open("recipes.csv", "wb") as f:
    f.write(response.content)
```

---

## 🔍 1行ずつ解説

---

### ✅ `import requests`

* `requests` ライブラリを使うことで、**Webからデータをダウンロード**できるようになります。
* Python標準ライブラリには含まれていないので、必要なら `pip install requests` が必要。

---

### ✅ `url = "..."`

* ダウンロードしたいCSVファイルの **URL（アドレス）** を指定しています。
* 今回は IBM のクラウドストレージにある `recipes.csv` です。

---

### ✅ `response = requests.get(url)`

* `requests.get()` は、そのURLに対して「GETリクエスト（＝ください）」を送る命令です。
* その結果が `response` という変数に入ります。

---

### ✅ `with open("recipes.csv", "wb") as f:`

* `open()` はファイルを開く関数です。
* `"recipes.csv"` は保存先のファイル名（好きな名前でOK）。
* `"wb"` は「write binary（バイナリ書き込み）」の意味。

  * CSVはバイナリ形式で扱うこともあるので、ここでは `"wb"` を使っています。
* `with` を使うと、ファイルの開閉（クローズ）を自動でやってくれるので安全です。

---

### ✅ `f.write(response.content)`

* `response.content` は、ダウンロードしたファイルの中身（バイナリ形式）。
* それを `f.write()` でファイルに書き込んでいます。
* この1行で、Web上のCSVファイルがローカルに保存されます。

---

## 💡まとめ表

| 行                      | 役割        | 解説                |
| ---------------------- | --------- | ----------------- |
| `import requests`      | ライブラリ読み込み | Webからデータ取得するための道具 |
| `url = "..."`          | URL指定     | 取りに行く先を指定         |
| `requests.get(url)`    | ダウンロード    | URLの中身を取得         |
| `with open(..., "wb")` | ファイルを開く   | 書き込み用にファイルを開く     |
| `f.write(...)`         | 書き込み      | ダウンロードした中身を保存     |

---

## ✅ よく使う場面

* Web上のCSV・画像・JSONなどをローカルに保存したいとき
* スクレイピングやAPI連携の時など

---

もしこのコードを Jupyter Notebook で使うなら、`requests` ライブラリがインストールされていることが前提です。
不安であれば以下のコードで確認できます：

```python
!pip install requests
```

---
「**後記のコード**（PandasでCSVを読み込んで表示したもの）」は、**今後も何度も使う重要コード**なので、ぜひ覚えておいたほうが良いです！

こちらがそのコードですね：

```python
import pandas as pd

df = pd.read_csv("recipes.csv")
df.head()
```

---

## 🔍 1行ずつ解説

---

### ✅ `import pandas as pd`

これは、「**Pandas**というライブラリ（＝データ分析用ツール）を `pd` という短い名前で使えるようにする」という意味です。

* **Pandas**は、データフレーム（表のようなデータ構造）を扱うために超重要なライブラリ。
* `pd`という略称は慣例なので、ほとんどの資料でもこの書き方です。

---

### ✅ `df = pd.read_csv("recipes.csv")`

* `read_csv()`は「CSVファイルを読み込んで**データフレームに変換**する関数」。
* `recipes.csv` は読み込むファイル名（ローカルに保存されたCSVファイル）。
* `df` という変数にその結果を格納しています。

  * `df` は「dataframe（データフレーム）」の略で、慣例的によく使います。

つまり：

🟡 CSVファイル（表形式データ） → Pandasの表（データフレーム）に変換して使えるようにする

---

### ✅ `df.head()`

* `head()` は、データの**最初の5行**を表示するためのメソッド。
* 中身をパッと確認するのに便利です。

例：大量のデータがあっても、冒頭だけ確認したいときにこう書きます。

---

## 💡 全体をまとめると

| 行                                 | 内容           | よく使う？ | 解説             |
| --------------------------------- | ------------ | ----- | -------------- |
| `import pandas as pd`             | ライブラリの読み込み   | ✅超重要  | pandasを使うには必須  |
| `df = pd.read_csv("recipes.csv")` | CSVファイルを読み込む | ✅超重要  | CSVはデータ分析でよく使う |
| `df.head()`                       | 最初の5行を見る     | ✅超重要  | データ確認に毎回使う     |

---

## ✅ 覚え方のコツ（語呂合わせ風）

* **「インポート パンダス ピーディー」**（pandasライブラリを `pd` にする）
* **「デーエフ イコール ピーディー リード シーエスブイ」**（CSVをdfに入れる）
* **「デーエフ ドット ヘッド！」**（先頭だけ見たいとき）

---

## 💬 おまけ：このコードがよく使われる場面

* データの読み込み
* 表の表示
* 欠損値のチェック（次のステップ）
* グラフ化や集計分析へと進む最初の入口です

---

必要なら「`df.describe()`」「`df.info()`」など、次の便利コマンドもご紹介できますよ！

知識を整理した「Pandas最初の10行」まとめノートが欲しければ、それも作れます✨



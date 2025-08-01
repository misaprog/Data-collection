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

何か書き換えたい場面（例：保存場所を変えたい、ファイル名を日付にしたい）などあれば、そこもカスタマイズできますよ！

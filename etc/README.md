

## Fieldについて

### oTreeでは以下のField形式を扱うことができる．

* BooleanField (for true/false and yes/no values)
  * ブーリアン型，True/FALSEやYES/NOなど．
  * 1/0の値を入力するのにも使える．

* CurrencyField
  * 通貨型
  * 金額を扱う時に使う
  * `settings.py`で`REAL_WORLD_CURRENCY_CODE`や`LANGUAGE_CODE`，`USE_POINTS`の設定に応じて「XXポイント」「XXpoints」「$XX」と言った表記をしてくれる．

* IntegerField
  * 整数型

* FloatField
  * 単精度浮動小数点型？
  * 小数を入れられる

* StringField
  * 文字入力ができる．

* LongStringField
  * （長い）文字入力ができる．





# その他Tips

### 日本語にしよう
* `settings.py`の中で書き換えるといける．

```
# ISO-639 code
# for example: de, fr, ja, ko, zh-hans
LANGUAGE_CODE = 'ja' # 最初はenになっている．

# e.g. EUR, GBP, CNY, JPY
REAL_WORLD_CURRENCY_CODE = 'JPY' # 最初はUSDになっている．
USE_POINTS = True
```
* ちなみに，ここでは「ポイント」を使っているけど，円表記も可能．



### 実際によく使う`if`
  * 例えば，勝った場合と負けた場合の表示を変えたいなど．
  * `if`を使います．

```html
{% if player.is_winner %} あなたの勝ち！ {% endif %}
```

```html
{% if some_number >= 0 %}
    正の数
{% else %}
    負の数
{% endif %}
```


### 動画・画像を入れたい！

* YouTubeを入れてみる．

```html
<img src="https://youtu.be/8AEd1cZoMDw" width="500px" />
```

* 画像を入れてみる．
  * 外部サイトではなく，oTreeのプロジェクトフォルダの中に入れられる．
  * `_static/`の中に保存する．
  * 画像がいっぱいになるとわからないので，実験ごとにフォルダを用意しておくと良い．


```html
<img src="{% static "folder_name/picture.jpg" %}"/>
```


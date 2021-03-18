# 入力形式の変更


## これから作る実験プログラムの概要：

* 先程作ったアンケートの年齢をもとに，様々な入力形式を設定してみよう．
  * 入力方法の変更
    * 数字で入力する方法
    * select形式で入力する方法
    * ラジオボタン（縦長）で入力する方法
    * ラジオボタン（横長）で入力する方法
    * Sliderで入力する方法
    * ボタンで入力する方法



## 数字で入力する方法
```Python
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください．',
                                        min=0,max=125,
                                        initial=None)
```
* 先程は"choices"を設定したが，最小値・最大値を指定するだけであれば，数字で入力が可能である．
    * もちろん，最小値・最大値を指定しないことも可能．


## 選択式で入力する方法

```Python
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください．',
                                        choices=range(0, 125),
                                        initial=None)
```
* `choices`を指定すると，自動的に選択式で入力することができます．


## ラジオボタン（縦長）で入力する方法

```Python
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください．',
                                        choices=range(0, 125),
                                        initial=None,  
                                        widget=widgets.RadioSelect)
```
* `widget=widgets.RadioSelect`を指定することで，ラジオボタン（縦長）で入力できます．


## ラジオボタン（横長）で入力する方法


```Python
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください．',
                                        choices=range(0, 125),
                                        initial=None,  
                                        widget=widgets.RadioSelectHorizontal)
```
* `widgets.RadioSelectHorizontal`を指定することで，ラジオボタン（横長）で入力できます．


## Sliderで入力する方法①

```Python
    q_age = models.IntegerField(verbose_name='あなたの年齢を教えてください．',
                                        choices=range(0, 125),
                                        min = 0,
                                        max = 125,
                                        initial=36,
                                        widget=widgets.SliderInput)
```




## 参考：Sliderで入力する方法②
* これだといくらの値を選択したかわからないため，こういう方法もあるという参考まで．

### Page1.htmlを書き換える
```html
    <input type="range" name="q_age" min="0" max="125" step="1">
```
* もしかしたら使いようがある気もしているが．



## ボタンで入力する方法

### Page1.html

```html
{% formfields player.q_tanmatsu %}
    {% next_button %}
```
* 上記2行を削除する．
  * 入力をボタンで行う＆ボタンを押すと次に進むように設定する．

```html
<p><b>この回答は、どの電子機器で回答していますか？</b></p>
<div>
    <button name="q_tanmatsu" value="パソコン" class="btn btn-primary btn-large">パソコン</button>
    <button name="q_tanmatsu" value="タブレット" class="btn btn-primary btn-large">タブレット</button>
    <button name="q_tanmatsu" value="スマートフォン" class="btn btn-primary btn-large">スマートフォン</button>
    <button name="q_tanmatsu" value="それ以外" class="btn btn-primary btn-large">それ以外</button>
</div>
```

## 演習問題
###  以下の質問項目を追加してみよう．
- [ ] 性別をラジオボタン（縦長）で入力できるようにしてみよう．
  - [ ]  models.pyに追加しましたか？
- [ ] 性別をラジオボタン（横長）で入力できるようにしてみよう．
  - [ ]  models.pyに追加しましたか？
- [ ]  現在，一人暮らしかどうかを尋ねる質問項目の回答をボタンにします．
  - [ ]  template内のhtmlを変更しましたか？
- [ ]  学生であるか否かを2値で尋ねる質問項目の回答をボタンにします．
  - [ ]  template内のhtmlを変更しましたか？





## サーバとして起動
* 自身の端末をサーバとして起動します．
```Python
otree devserver
```
  - これで自身の端末で実験を実施することができます．
  - [http://localhost:8000/](http://localhost:8000/)にアクセスしてみてください．






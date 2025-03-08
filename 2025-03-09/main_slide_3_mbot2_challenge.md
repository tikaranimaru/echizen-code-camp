---
marp: true
theme: gaia
paginate: true

---

<style>
@import 'code-camp.css';
@import url('https://fonts.googleapis.com/css?family=Noto Sans JP&display=swap');
section {
    font-family: 'Noto Sans JP', serif;
    background-image: url("bgimage.png");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}

.compact-text {
    font-size: 32px;
    line-height: 1.3;
    padding: 30px;
}

.compact-text h1 {
    font-size: 48px;
    margin-bottom: 20px;
}

.compact-text h4 {
    font-size: 36px;
    margin-bottom: 15px;
}

.compact-text p {
    margin: 8px 0;
}

.compact-text pre {
    margin: 12px 0;
}

</style>



# Python基礎からmBot2プログラミングへ 【実践編】

---

## 0. 準備：必要なモジュールのインポート

mBot2を制御するために、以下のモジュールを読み込みます。
```python
import cyberpi        # LED、サウンドなどの制御
import mbot2         # mBot2本体の制御
import mbuild         #　センサーなどモジュールの制御
import time          # 時間待機用
```

このプログラムは、以降のすべての例で必要となりますので、
最初に実行しておきましょう。

---

## 1. 「変数」 を使ってLEDを制御しよう

前回学習した**変数**をmBot2のLED制御に活用します。

```python
my_color = "blue"
brightness = 100

# 変数を使ってLEDを制御
cyberpi.led.on(my_color)        # 色を設定
time.sleep(2)                   # 2秒待つ

# 変数の値を変更
my_color = "red"

# 変更した値で再度LEDを制御
cyberpi.led.on(my_color)

# 消す
cyberpi.led.off()
```

---

**👉 ハンズオン: 変数でLED制御**
1. 好きな色の名前を変数に入れてLEDを光らせてみよう
   例: "blue", "green", "yellow", "red"
2. 順番に色を変えてみよう
   例: 青→赤→緑→黄色

---

## 2. 「if文」で距離に応じた動作をさせよう

**if文**を使って、センサーの値に応じた動作を実装します。

```python
# 距離を測る
distance = mbuild.ultrasonic2.get()

if distance < 10:               # (1) 10cmより近い場合
    cyberpi.display.show_label("バックします", 16, 0, 0)
    cyberpi.led.on('red')
    mbot2.backward(50, 1)       # 後退
elif distance < 20:             # (2) やや近い場合
    cyberpi.led.on('yellow')
    cyberpi.display.show_label("停止します", 16, 0, 0)
    mbot2.backward(0, 1)        # 停止
else:                           # (3) 十分な距離がある場合
    cyberpi.led.on('green')
    cyberpi.display.show_label("進みます", 16, 0, 0)
    mbot2.forward(50, 2)        # 前進
```

---

**👉 ハンズオン: if文で条件分岐**
1. 距離センサーの値を使って、異なる動作を設定してみよう
2. LEDの色と動きのパターンを増やしてみよう

---

## 3. 「for文」でパターン動作を作ろう

前回学習した**for文**を使って、繰り返し動作を実装します。

```python
# 色のリストを作成
colors = ["red", "green", "blue", "yellow"]

# リストの色を順番に表示
for color in colors:
    cyberpi.led.on(color)
    time.sleep(1)

# 数値を使った繰り返し
for speed in [30, 50, 70, 90]:
    # 前進して停止を4回繰り返す
    mbot2.forward(speed, 1) # 前進
    time.sleep(0.5)
    mbot2.backward(speed, 1) # 後退
    time.sleep(0.5)
```

---

**👉 ハンズオン: for文で繰り返し**
1. 好きな色のリストを作って、順番に光らせてみよう
  
   hint: 
   ```python
   colors = ["red", "green", "blue", "yellow"]
   ```
2. 四角形を描くように走らせてみよう（4回の直進と回転）
   hint: 
   ```python
    # 50の速さで1秒進む
    mbot2.forward(50, 1)

    # 時計回りに90度曲がる
    mbot2.turn(90, 50)
   ```
---

## 4. 関数で便利な動きをまとめよう

**関数**を使って、よく使う動作をまとめます。

```python
def stop_and_turn_right():
    mbot2.forward(0, 1)
    time.sleep(0.1)
    mbot2.turn_left(50, 1)
    time.sleep(0.1)

def is_require_stop():
    distance = mbuild.ultrasonic2.get()
    if distance < 10:
        return 1
    else:
        return 0
```


---

**👉 ハンズオン: 関数を作って使う**
1. 自分だけの動きパターンを関数にしてみよう
2. 引数を使って、速度や時間を変更できる関数を作ってみよう

---

**👉 チャレンジ課題**


学んだ内容を組み合わせて、以下の課題に挑戦しよう！

1. **ルンバを作ってみよう**
   - 部屋を巡回しながら、障害物を避ける
   - 距離に応じてLEDの色を変える
   - 関数を使って処理をまとめる

2. **ライトショー**
   - 複数の色を順番に表示
   - 明るさを徐々に変化させる
   - for文を使ってパターンを作る

---

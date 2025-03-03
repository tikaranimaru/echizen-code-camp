---
marp: true
theme: gaia
# header: "Code Camp Echizen"
footer: "Code Camp Echizen / コードキャンプ越前"
backgroundColor: "#EEEEEE"
paginate: true
markdownlint:
  MD025: false
  MD033: false

style: |
  :root {
    --fw: 1;
  }
  /* ----- レイアウト ----- */
  .flex{
    display: flex;
    gap: 1em;
  }
  .sa {
    justify-content: space-around;
    /* border: 8px dashed rgb(15, 166, 226);
    background-color: rgb(222, 244, 255); */
  }
  .sb {
    justify-content: space-between;
    /* border: 8px dashed rgb(21, 17, 255);
    background-color: rgb(222, 244, 255); */
  }
  .sa div,.sb div{
    margin: 0.1em;
    /* border: 8px dashed rgb(80, 177, 109);
    background-color: rgb(227, 250, 237); */
  }
  .fw div{
    flex: var(--fw);
    /* background-color: rgb(244, 238, 255);
    border: 8px dashed rgb(93, 0, 255); */
  }/* ---------- */

# 段組の使い方
# https://briboo-pc.hatenablog.jp/entry/2023/11/05/%E3%80%90Marp%E3%80%91%E3%82%B3%E3%83%94%E3%83%9A%E3%81%A7%E7%B0%A1%E5%8D%98%EF%BC%81%E5%A4%9A%E6%AE%B5%E7%B5%84%E3%81%BF%E3%82%B7%E3%83%B3%E3%83%97%E3%83%AB%E3%83%AC%E3%82%A4%E3%82%A2%E3%82%A6


---

# Python基礎からmBot2プログラミングへ 【実践編】

---

## 0. 準備：必要なモジュールのインポート

mBot2を制御するために、以下のモジュールを読み込みます。
```python
import cyberpi        # LED、サウンドなどの制御
import mbuild.mbot2   # mBot2本体の制御
import time          # 時間待機用

# 初期化
mbot = mbuild.mbot2.MBot2()  # mBotを動かすおまじない(準備
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
distance = mbot.ultrasonic.get_distance()

if distance < 10:               # 10cmより近い場合
    cyberpi.led.on('red')
    mbot.move(30, -30)          # 後退
elif distance < 20:             # やや近い場合
    cyberpi.led.on('yellow')
    mbot.move(0, 0)             # 停止
else:                           # 十分な距離がある場合
    cyberpi.led.on('green')
    mbot.move(-30, 30)          # 前進
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
for speed in [100, 200, 300, 400]:
    # 前進して停止を4回繰り返す
    mbot.move(-1 * speed, speed) # 前進
    time.sleep(1)
    mbot.move(speed, -1 * speed) # 後退
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
   # 前進する　場合
   mbot.move(100, 100)

   # 左に90度回転する場合
   mbot.move(0, 100)
   ```
---

## 4. 関数で便利な動きをまとめよう

**関数**を使って、よく使う動作をまとめます。

```python
def stop_and_turn_right():
    mbot.move(0, 0)
    time.sleep(0.1)
    mbot.move(50, 0)
    time.sleep(0.1)

def is_require_stop():
    distance = mbot.ultrasonic.get_distance()
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

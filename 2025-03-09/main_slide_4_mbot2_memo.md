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

---

# Python x mBot2プログラミング 【その他】

---

## 1. ボタンで操作しよう

mBot2のボタンを使って、プログラムを操作することができます。

```python
import cyberpi
import time

# 5秒間、ボタンを監視する
for i in range(5):
    # Aボタンが押されたら
    if cyberpi.controller.is_press("a"):
        cyberpi.led.on("red")
        cyberpi.audio.play("jump")
    
    # Bボタンが押されたら
    if cyberpi.controller.is_press("b"):
        cyberpi.led.on("blue")
        cyberpi.audio.play("wrong")
    
    # 何も押されていなければ消灯
    if not cyberpi.controller.is_press("any_button"):
        cyberpi.led.off()
    
    time.sleep(0.1)  # 少し待つ
```

---

**👉 ハンズオン: ボタン操作**

1. ボタンAを押したら前進、ボタンBを押したら後退するプログラムを作ろう
2. ボタンCを押したら停止するようにしよう

ヒント: `mbot.drive_speed()` を使って動かします

```python
import cyberpi
import mbuild
import mbot2
import time

# 繰り返し確認
for i in range(50):  # 約5秒間
    # ここにプログラムを書こう！
    
    time.sleep(0.1)  # 少し待つ

# 最後に停止
mbot.drive_speed(0, 0)
```

---

## 2. 距離センサーを使おう

mBot2は前方の距離を測ることができます。これを使って、障害物を避けることもできます。

```python
import cyberpi
import mbuild
import mbot2
import time

# 距離を測って表示
distance = mbuild.ultrasonic2.get()
cyberpi.display.show_label(str(distance) + "cm", 16, 0, 0)

# 距離に応じて動作を変える
if distance < 10:  # 10cm未満なら
    cyberpi.led.on("red")  # 赤く光る
    cyberpi.audio.play("warning")  # 警告音
else:  # それ以外なら
    cyberpi.led.on("green")  # 緑に光る
```

---

**👉 ハンズオン: 自動停止車**

1. 前に進むプログラムを書こう
2. 障害物が近づいたら自動的に止まるようにしよう

```python
import cyberpi
import mbuild
import mbot2
import time

# 5秒間繰り返す
for i in range(50):
    # 距離を測る
    distance = mbuild.ultrasonic2.get()
    
    # ここに条件分岐のプログラムを書こう！
    # 距離が10cm未満なら止まる
    # そうでなければ前進する
    
    time.sleep(0.1)  # 少し待つ

# 最後に停止
mbot.drive_speed(0, 0)
```

---

## 3. 明るさセンサーを使おう

mBot2は周りの明るさを測ることができます。これを使って、暗くなったら光るランプを作ることもできます。

```python
import cyberpi
import time

# 明るさを測る
brightness = cyberpi.get_bri()
cyberpi.display.show_label(str(brightness), 16, 0, 0)

# 明るさに応じて動作を変える
if brightness < 30:  # 暗いなら
    cyberpi.led.on("yellow")  # 黄色く光る
else:  # 明るいなら
    cyberpi.led.off()  # 消灯
```

---

**👉 ハンズオン: 自動ライト**

1. 明るさを測るプログラムを書こう
2. 暗くなったらLEDが光り、明るくなったら消えるプログラムを作ろう

```python
import cyberpi
import time

# 10秒間繰り返す
for i in range(100):
    # 明るさを測る
    brightness = cyberpi.get_bri()
    
    # ここに条件分岐のプログラムを書こう！
    # 明るさが30未満なら光らせる
    # そうでなければ消灯する
    
    time.sleep(0.1)  # 少し待つ
```

---

## 7. チャレンジ課題

学んだことを組み合わせて、次のチャレンジに挑戦しよう！

**チャレンジ1: お掃除ロボット**
- mBot2を前に進ませよう
- 障害物を見つけたら、方向を変えて進もう
- 障害物を見つけたら音を鳴らそう

**チャレンジ2: ナイトライダー風ライト**
- LEDを左から右、右から左へと流れるように光らせよう
- ボタンを押すと、流れる速さが変わるようにしよう

**チャレンジ3: リモコンカー**
- ボタンAで前進、ボタンBで後退
- ボタンCで左折、ボタンDで右折
- ボタンを離したら停止

---

## まとめ

今日は以下のことを学びました：

1. ボタンでの操作方法
2. 距離センサーの使い方
3. 明るさセンサーの使い方

---
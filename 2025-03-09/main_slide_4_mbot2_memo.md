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
    margin: 6px 0;
}

.compact-text pre {
    margin: 12px 0;
}

</style>



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

<div class="compact-text">

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

</div>

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
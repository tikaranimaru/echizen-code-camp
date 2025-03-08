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



# Python x mBot2プログラミング 【初級編】

---

## 0. プログラミングってなに？

プログラミングとは、コンピュータやロボットに「やってほしいこと」を「命令」として伝えることです。

mBot2というロボットに、いろいろな「命令」を出して動かしてみましょう！

今日は、「Python（パイソン）」というプログラミング言語を使います。

---

## 1. はじめての命令：画面に表示しよう

まずは、mBot2の画面に文字を表示する命令をやってみましょう。

```python
# mBot2の「脳」を使えるようにする
import cyberpi

# 画面に「こんにちは」と表示する命令
cyberpi.display.show_label("こんにちは", 16, 0, 0)
```

「#」から始まる行は「コメント」といって、ロボットへの説明書きです。
ロボットはコメントを読み飛ばします。

---

**👉 ハンズオン: 自分の名前を表示しよう**

1. 上のプログラムの「こんにちは」の部分を自分の名前に変えてみよう
2. 実行ボタンを押して、画面に表示されるか確認しよう

例:
```python
# 画面に「たろう」と表示する命令
cyberpi.display.show_label("たろう", 16, 0, 0)
```

---

## 2. 光らせてみよう

次は、mBot2の上にあるLEDライトを光らせる命令をやってみましょう。

```python
# mBot2の「脳」を使えるようにする
import cyberpi
# 時間を扱う命令も使えるようにする
import time

# 赤色に光らせる
cyberpi.led.on("red")
# 1秒待つ
time.sleep(1)
# 消す
cyberpi.led.off()
```

---

**👉 ハンズオン: いろんな色で光らせよう**

1. 下のプログラムを実行して、違う色で光らせてみよう
2. 「green」を別の色に変えて試してみよう
   - 「blue」（青色）
   - 「yellow」（黄色）
   - 「purple」（紫色）

---

```python
import cyberpi
import time

# 緑色に光らせる
cyberpi.led.on("green")
# 1秒待つ
time.sleep(1)
# 消す
cyberpi.led.off()
```

---

## 3. 音を鳴らしてみよう

mBot2は音も出すことができます。「話す」命令と「音を鳴らす」命令を試してみましょう。

<!-- `audio.play_until(music_name)`は 再生が終了するまでスレッドをブロックする-->

```python
import cyberpi
import time

# 「hello」と話す
cyberpi.audio.play("hello")
# 少し待つ
time.sleep(2)
# 「bye」と返す
cyberpi.audio.play("bye")
```

---

**👉 ハンズオン: いろんな声と音**

1. 違う効果音を試してみよう
   - 「yeah」（喜ぶ）
   - 「alert」（警告音）
   - 「jump」（ジャンプ音）
   - 「level-up」（レベルアップ音）

---

```python
import cyberpi
import time

# 好きな効果音を鳴らそう
cyberpi.audio.play("level-up")
# 少し待つ
time.sleep(1)
# 好きな効果音を鳴らそう
cyberpi.audio.play("jump")
```

---

## 4. 光と音を組み合わせよう

命令は組み合わせることができます。光と音を一緒に使ってみましょう。

```python
import cyberpi
import time

# 赤く光らせる
cyberpi.led.on("red")
# 銃がなる
cyberpi.audio.play_until("shot")
# 1秒待つ
time.sleep(1)

# 青く光らせる
cyberpi.led.on("blue")
# 回復する
cyberpi.audio.play_until("magic")
# 1秒待つ
time.sleep(1)

# 消す
cyberpi.led.off()
```

---

**👉 ハンズオン: 自分だけの光と音のショー**

1. ドレミを奏でながら、光らせてみよう

例:
```python
import cyberpi
import time


# 音を鳴らす
cyberpi.audio.play_tone(262, 1)  # ドを1秒鳴らす
cyberpi.led.on("red")            # 赤く光らせる
time.sleep(1)

cyberpi.audio.play_tone(294, 1)  # レ音を1秒鳴らす
cyberpi.led.on("green")          # 緑に光らせる
time.sleep(1)

cyberpi.audio.play_tone(330, 1)  # ミ音を1秒鳴らす
cyberpi.led.on("blue")           # 青く光らせる
time.sleep(1)

# 消す
cyberpi.led.off()
```

---

## 5. 動かしてみよう

mBot2を動かす命令を試してみましょう。タイヤの速さを指定して動かすことができます。

```python
# mBot2の「脳」を使えるようにする
import cyberpi
# mBot2本体を動かす命令も使えるようにする
import mbot2
import time

# 50の速さで前に1秒進む
mbot2.forward(50, 1)

# 50の速さで後ろに1秒進む
mbot2.backward(50, 1)
```

数字は「速さ」です。0は止まる、プラスは前に進む、マイナスは後ろに進むという意味です。

---

**👉 ハンズオン: 簡単な動き**

下のプログラムを実行して、mBot2を動かしてみよう！

<!-- 注意!`mbot2.straight`では速さは正の値のみ -->

```python
import cyberpi
import mbot2
import time

# 10cm前に50の速さで進む
mbot2.straight(10, 50)

# 左に50の速さで1秒曲がる
mbot2.turn_left(50, 1)

# 20cm前に50の速さで進む
mbot2.straight(10, 50)

# 時計回りに90度曲がる
mbot2.turn(90, 50)
```

---

**👉 チャレンジ: 四角形を描こう**

1. 前に進む → 右に曲がる → 前に進む → 右に曲がる → 前に進む → 右に曲がる → 前に進む → 止まる

このプログラムを作ると、mBot2は四角形を描くように動きます！

ヒント:
```python
# 50の速さで前に1秒進む
mbot2.forward(50, 1)

# 右に90度曲がる
mbot2.turn(90, 50)

# ここに続きを書こう...
```

---

## 6. 光と音と動きを組み合わせよう

最後に、光・音・動きを全部組み合わせてみましょう。

```python
import cyberpi
import mbot2
import time

# 赤く光らせる
cyberpi.led.on("red")
# 「ハロー」と言う
cyberpi.audio.play_until("hello")
# 50の速さで前に1秒進む
mbot2.forward(50, 1)
# 2秒間待つ
time.sleep(2)

# 青く光らせる
cyberpi.led.on("blue")
# 「バーイ」と言う
cyberpi.audio.play_until("bye")
```

---

## まとめ

以下のことを学びました：

1. プログラムとは「命令」を書くこと
2. mBot2に文字を表示する方法
3. mBot2のLEDを光らせる方法
4. mBot2に音を出させる方法
5. mBot2を動かす方法
6. いろいろな命令を組み合わせる方法

お疲れさまでした！これで「プログラミング基礎編」は終了です。
「実践編」では、もっと複雑なプログラムに挑戦します！

---
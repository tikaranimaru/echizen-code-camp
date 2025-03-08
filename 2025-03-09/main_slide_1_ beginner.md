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


# プログラミング基本編
pythonでプログラミングをしてみよう

---

#### プログラミングの4つの基本

これさえ覚えておけば、どんなプログラムも作れる!!

1. **変数**：データを入れる"箱"
2. **if文**：条件分岐「もし○○なら△△する」
3. **for文**：繰り返し処理「同じ処理を繰り返す」
4. **関数**：よく使う処理をまとめたもの

---

#### 1. 変数 ・・・代入してみる

- **変数**とはデータ(数値、文字など)を入れておく"箱"のようなもの  
- 好きな名前を付けて使える(例: `x`, `myname` など)  

```python
# 変数の例
x = 10         # <- 数値を入れる
y = 20         # <- 別の数値を入れる
print("xの値は:", x)  # 10
print("yの値は:", y)  # 20
```

---

#### 1. 変数 ・・・計算してみる

```python
# 変数同士を足す
z = x + y      # <- 計算結果を新しい変数に保存
print("x + y =", z)  # 30

# 変数の中身は上書きできる
x = 100        # <- xの中身が10から100に変わる
print("新しいxの値:", x)  # 100
```

[> 図解 変数の動き](https://claude.site/artifacts/6b83a592-ef8e-40fc-af3d-c961e36423a4)

---

#### 1. 変数 ・・・文字を入れてみる  

```python
# 文字を入れてみる
firstname = "大谷"
print("私の名前は", firstname, "です")  # 私の名前は大谷です

# 文字を結合する
lastname = "翔平"
fullname = firstname + lastname
print("私の名前は", fullname, "です")  # 私の名前は大谷翔平です

```

---

**👉 Try it!**
- x の値を変えてみて表示がどう変わるかを試してみよう
- 引き算や掛け算も試してみよう
  - 引き算: `z = x - y`
  - 掛け算: `z = x * y`
- myname という変数を作り、自分の名前を入れて表示させよう

---

#### 2. if文 ・・・ if文ってなんだ？

- **if文**: 「もし○○なら△△する」
- 条件分岐でプログラムの流れを変えられる
- イメージ: 「もし信号が赤なら止まる」

```python
signal = "赤"

if signal == "赤":  # もし信号が赤なら
    print("信号が赤なので止まる")
else:               # それ以外の場合
    print("信号が赤でないので進む")
```

---

#### 2. if文 ・・・ 数値の比較

あなたは赤ちゃん？子供?大人?

```python
myage = 12

if myage < 2:
    print("あなたは赤ちゃんです")
elif myage < 13:  # elif は　else if の略で、または の意味
    print("あなたは子供です")
elif myage == 18:
    print("あなたは成人です")
else:             # それ以外の場合
    print("あなたは立派な大人です")
```

[> 図解 if文の動き](https://claude.site/artifacts/9420efcb-8f40-4370-8a74-597435f5e3e8)

---


**👉 Try it!**
- 自分の年齢を入れて、どのような結果になるか確認してみよう
- 高校生も判定できるようにしてみよう

---

#### 3. for文 ・・・ 繰り返し処理

- **for文**: 「同じ処理を何度も繰り返す」
- イメージ: 「箱の中の玉を1つずつ取り出して、色を表示する」

```python
# リストの要素を1つずつ取り出す
colors = ["赤", "青", "緑"]
for color in colors:  # <- "赤", "青", "緑" と順番に color に代入
    print(color + "色")  # <- この行が3回繰り返される
```

---

#### 3. for文 ・・・数字の繰り返しとif文

お年玉をもらって、お年玉の金額を表示させてみよう

```python
# くれた人   [おじいちゃん, おばあちゃん, おじさん, お父さん, お母さん]
otoshidama_list = [6000, 10000, 5000, 1000, 3000]
for otoshidama in otoshidama_list:
    # 5000円以上なら喜ぶ
    if (otoshidama >= 5000):
        print("5000円以上です。嬉しい")
    else:
        print("5000円未満です。悲しい")
```

[図解 for文について](https://claude.site/artifacts/3c38df0e-bd1c-4981-be31-6dc7d333b5cc)

---

**👉 Try it!**

- お年玉を追加してみよう
- 落とし玉が1000円以下なら、「足りない」と表示させてみよう
- **[時間があれば]** お年玉の金額を合計してみよう
  ```python
  # hitn: 1から10の数字を足す方法
  total = 0
  for i in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    total = total + i
  print("合計は", total, "です")
  ```

---

#### 4. 関数 ・・・関数って？

- **関数**: よく使う処理を1つにまとめたもの
- イメージ: 「消費税を計算する関数」

```python
def shohizei(price):  # 消費税を計算する関数
    tax = price * 0.1  # <- 消費税を計算
    return tax  # <- 計算結果を返す

# 関数を呼び出して、結果を代入
tax_result = calc_tax(1000)  # <- 1000円の消費税を計算
print("1000円の消費税は", tax_result, "円です")  # 100円

tax_result = calc_tax(2000)  # <- 2000円の消費税を計算
print("2000円の消費税は", tax_result, "円です")  # 200円
```

[> 図解 関数の動き](https://claude.site/artifacts/9b2b73af-e5de-4dd8-a702-cb18a1f415c7)

---

#### 4. 関数 ・・・ 応用

```python
# 計算をする関数
def tashizan(a, b):  # <- 引数を2つ受け取る
    result = a + b  # <- 計算
    return result   # <- 結果を返す（呼び出し元に戻す）

def hikizan(a, b):  # <- 引数を2つ受け取る
    result = a - b  # <- 計算
    return result   # <- 結果を返す（呼び出し元に戻す）

print(tashizan(5, 3))  # 8
print(hikizan(5, 3))  # 2
```

---

**👉 Try it!**
- 掛け算, 割り算の関数を作ってみよう
  - 掛け算: `a * b` (アスタリスク)
  - 割り算: `a / b` (スラッシュ)
- **[時間があれば]** 三角形の面積を計算する関数を作ってみよう
- **[時間があれば]** お年玉が多いか少ないかを判定する関数を作ってみよう

---

基本編は終わり。お疲れ様でした。

いよいよロボット(mbot2)を動かしてみましょう。

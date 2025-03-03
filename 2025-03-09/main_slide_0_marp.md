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

# Echizen Code Camp

---

## 今日の内容

1. 講師の自己紹介
2. ちょっお勉強
   - プログラミングって？？
   - プログラミングで何ができるの？？
3. プログラミングの超基本
4. 実践
   - mbot2のプログラミング

---

## 1.講師の自己紹介

---

<div class="flex sa">
<div style="--fw: 3;">

##### 山口力丸
- コードキャンプ越前の講師
- 得意分野：XXX

##### 松橋樹
- コードキャンプ越前の講師
- 子どもたちにプログラミングを教えるのが楽しみです
</div>
<div style="--fw: 3;">

##### 寺坂大地
- コードキャンプ越前の講師 
- ロボットプログラミングが好きです

##### 高松 両隊
- コードキャンプ越前の講師
- 子どもたちにプログラミングを教えるのが楽しみです

</div>
</div>

---

## 2.ちょっと勉強

---

# 1. ～プログラミングで何ができる？～ 

---

- **プログラミングとは？**  
  - コンピュータ（ロボット,PC）に「何をどうするか」を指示する
  - 日常生活では?
    - 自動ドア
    - 信号機
    - 家電製品
    - ゲーム, アプリ ...

---

#### **プログラミングでできること**  
  - ゲームを作る
  - ロボットを動かす
  - データ分析

---

- **今日のゴール**  
  1. Pythonの基本(if文, for文, 変数, 関数)を使って、実際にコードを書いてみる  
  2. mBot2を動かしてプログラムが"現実世界"に与える影響を体験する

---

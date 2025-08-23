---
marp: true
theme: default
paginate: true
backgroundColor: #f8f9fa
color: #333
style: |
  section {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 22px;
  }
  h1 {
    color: #2c3e50;
    border-bottom: 3px solid #3498db;
    padding-bottom: 10px;
  }
  h2 {
    color: #34495e;
    margin-top: 30px;
  }
  .highlight {
    background-color: #fff3cd;
    padding: 15px;
    border-left: 4px solid #ffc107;
    margin: 20px 0;
  }
  .code-block {
    background-color: #f8f9fa;
    border: 1px solid #dee2e6;
    border-radius: 5px;
    padding: 15px;
    font-family: 'Courier New', monospace;
  }
  .math {
    font-size: 24px;
    text-align: center;
    margin: 20px 0;
  }
---

# 高校数学とJulia言語 Day 1

**Google Colabの紹介とJulia言語で計算してみよう！**

城北中学校・高等学校　中学3年・高校1年
夏期講習会III 2025/8/24~2025/8/28
担当：清水団

---

## 📅 5日間の学習予定

- **Day 1**：Google Colabの紹介・基本計算 ← 今日はここ！
- **Day 2**：関数のグラフの描画
- **Day 3**：最適化（最大・最小）
- **Day 4**：データの分析
- **Day 5**：確率・シミュレーション

<div class="highlight">
今日のゴール：Juliaで計算できるようになろう！
</div>

---

## 🚀 Julia言語とは

**統計処理や科学技術計算、機械学習に強いプログラミング言語**

### Julia言語の特徴
- **数学的記法が使える**：`2x` のように数学と同じ書き方ができる
- **高速計算**：複雑な計算も瞬時に実行
- **豊富な数学関数**：平方根、三角関数、対数など標準装備
- **美しいグラフ**：関数のグラフを簡単に描画可能

公式サイト：https://julialang.org/

---

## 💻 Google Colabでの設定

**2025年3月6日にGoogle Colab上でJulia言語が使えるようになりました！**

### 📌 設定方法
1. Google Colabを開く
2. **メニュー → ランタイム → ランタイムのタイプを変更**
3. **Julia を選択**
4. 保存をクリック

<div class="highlight">
設定が完了したら、実際にJuliaコードを実行してみましょう！
</div>

---

## 📝 Google Colab の基本的な使い方

### セルの種類

| セルの種類 | 用途 | 入力内容 |
|-----------|------|----------|
| **コードセル** | プログラムを書く | Julia, Python などのコード |
| **テキストセル** | 解説や見出しを書く | Markdown 記法を使った文章や数式 |

### 便利なショートカット
- **セルを実行**：`Shift + Enter` または ▶️ ボタン
- **新しいセルを追加**：上部の `+ コード` または `+ テキスト`

---

## 🧮 基本的な四則演算

まずは電卓として使ってみましょう！

<div class="code-block">

```julia
15 + 7    # 足し算 → 22
15 - 7    # 引き算 → 8
15 * 7    # 掛け算 → 105
15 / 7    # 割り算 → 2.142857...
15 // 7   # 割り算（有理数）→ 15//7
15 % 7    # 割り算の余り → 1
15 ÷ 7    # 割り算の商 → 2
```

</div>

**実際にGoogle Colabで試してみましょう！**

---

## 📐 数学でよく使う定数と関数

### 数学定数
<div class="code-block">

```julia
π         # 円周率パイ
ℯ         # 自然対数の底（ネイピア数）
sqrt(2)   # 平方根（ルート2）
√2        # 平方根（記号で書ける！）
```

</div>

### 基本的な数学関数
<div class="code-block">

```julia
abs(-5)      # 絶対値 → 5
sin(π/6)     # 三角関数 → 0.5  
cos(π/4)     # 三角関数 → √2/2
exp(2)       # 指数関数 → e²
log(2,8)     # 対数 log₂(8) → 3
```

</div>

---

## ✨ Juliaの数学的記法

**数学と同じように書ける！**

<div class="code-block">

```julia
2π           # 2×π と同じ意味
2sqrt(3)     # 2×√3 と同じ意味
3x + 2y      # 変数xとyを使った式（xとyに値を代入済みの場合）
```

</div>

<div class="math">

**数学**: $2\pi$, $2\sqrt{3}$, $3x + 2y$
**Julia**: `2π`, `2sqrt(3)`, `3x + 2y`

</div>

<div class="highlight">
ほとんど数学の記法と同じです！
</div>

---

## 🔢 変数を使った計算

数学と同じように、文字に数値を代入して計算できます。

<div class="code-block">

```julia
# 変数に値を代入
x = 7
y = 10

# 数学的な式で計算
4x - 3y        # 4×7 - 3×10 = -2
(x^2 + y^2)/(x*y)   # (49 + 100)/(70) = 149/70
```

</div>

**実際に試してみましょう！**

---

## 📚 数学の公式を確認してみよう

### 和と積の公式の検証

$x = 2 + \sqrt{3}$, $y = 2 - \sqrt{3}$ のとき

<div class="code-block">

```julia
x, y = 2 + sqrt(3), 2 - sqrt(3)

x + y    # → 4
x * y    # → 1

# 3乗の和の公式
x^3 + y^3                        # 左辺
(x + y) * (x^2 - x*y + y^2)     # 右辺

# 等しいかチェック
x^3 + y^3 ≈ (x + y) * (x^2 - x*y + y^2)  # → true
```

</div>

---

## 🎯 実習：計算チェック

**展開の公式を確認してみましょう**

<div class="math">
$(2\sqrt{3}+5)(\sqrt{3}-1) = 6 - 2\sqrt{3} + 5\sqrt{3} - 5 = 1 + 3\sqrt{3}$
</div>

<div class="code-block">

```julia
# 左辺を計算
left = (2sqrt(3) + 5) * (sqrt(3) - 1)

# 右辺を計算  
right = 1 + 3sqrt(3)

# 両辺が等しいか確認
left ≈ right  # → true
```

</div>

**皆さんも試してみてください！**

---

## 📝 本日の演習問題

### 問題1: 展開と計算
$(2\sqrt{3}+1)(\sqrt{3}-4)$ を計算しよう

1. そのままJuliaで計算
2. 展開してからJuliaで評価
3. 2つの値が等しいかチェック

### 問題2: 変数を使った計算
$x=2+\sqrt{7}$，$y=3-\sqrt{7}$ のとき、$x^3 + xy + y^3$ を求めよう

### 問題3: 三角関数の値
$\sin\frac{\pi}{4} + \cos\frac{\pi}{3}$ の値を求めよう

---

## 🎯 演習問題を解いてみよう！

**Google Colabを開いて、実際にコードを書いてみましょう**

### 取り組み方
1. まずJuliaのコードで計算してみる
2. 次に，自分の手と頭で解く
3. 答えをJuliaでチェックする
4. ノートブックを保存してGoogle Classroomから提出

<div class="highlight">
分からないことがあったら、遠慮なく質問してください！
</div>

---

## 🌟 今日のまとめ

### 学んだこと
- Google Colabの基本的な使い方
- Julia言語の基本的な計算方法
- 数学定数（π、e）の使用
- 数学関数（sqrt、sin、cos、logなど）の活用
- 変数を使った計算
- 手計算とプログラムでの計算結果の比較

### Julia言語のメリット
✅ **直感的な記法**：数学の式をほぼそのまま書ける
✅ **高精度計算**：複雑な計算も正確に実行
✅ **計算の検証**：手計算の結果をすぐに確認できる

---

## 🔮 次回予告：Day 2

**関数のグラフの描画**

- 関数を定義してグラフを描画
- 1次関数、2次関数、三角関数などの美しいグラフを作成
- 関数の性質を視覚的に理解

<div class="highlight">
数学がもっと楽しくなります！お楽しみに！
</div>

### 宿題
今日の演習問題を完成させて、Google Classroomに提出してください。

---

## ❓ 質問タイム

**何か分からないことはありませんか？**

- Google Colabの使い方
- Julia言語の基本操作
- 演習問題について
- その他、何でも！

<div class="highlight">
積極的に質問して、理解を深めましょう！
</div>

**お疲れさまでした！**
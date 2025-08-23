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
    border-bottom: 3px solid #e74c3c;
    padding-bottom: 10px;
  }
  h2 {
    color: #34495e;
    margin-top: 30px;
  }
  .highlight {
    background-color: #e8f5e8;
    padding: 15px;
    border-left: 4px solid #27ae60;
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
  .warning {
    background-color: #fff3cd;
    padding: 15px;
    border-left: 4px solid #ffc107;
    margin: 20px 0;
  }
---

# 高校数学とJulia言語 Day 2

**関数を定義してグラフを描こう！**

城北中学校・高等学校　中学3年・高校1年
夏期講習会III 2025/8/24～2025/8/28
担当：清水団

---

## 📅 5日間の学習予定

- **Day 1**：Google Colabの紹介・基本計算 ✅
- **Day 2**：関数のグラフの描画 ← 今日はここ！
- **Day 3**：最適化（最大・最小）
- **Day 4**：データの分析
- **Day 5**：確率・シミュレーション

<div class="highlight">
今日のゴール：関数を定義してグラフを描けるようになろう！
</div>

---

## 🎯 Julia言語での関数定義

**数学の関数をそのまま書ける！**

### 1. 基本的な関数定義
<div class="code-block">

```julia
function 関数名(引数)
    # 処理
    return 戻り値
end
```

</div>

### 2. 短縮形での関数定義（おすすめ）
<div class="code-block">

```julia
関数名(引数) = 式
```

</div>

<div class="math">
数学: $f(x) = 2x + 1$ → Julia: `f(x) = 2x + 1`
</div>

---

## 🔢 関数を定義してみよう！

### 基本的な関数の例

<div class="code-block">

```julia
# 1次関数
f(x) = 2x + 1

# 2次関数
g(x) = x^2 - 3x + 2

# 三角関数
h(x) = sin(x) + cos(x)
```

</div>

### 関数の値を計算
<div class="code-block">

```julia
f(3)    # → 7
g(1)    # → 0
h(π/4)  # → √2
```

</div>

---

## 📊 グラフを描く準備

**Plots.jlパッケージを使います**

<div class="code-block">

```julia
# パッケージの読み込み
using Plots

# フォント設定（日本語ラベルのため）
gr(fontfamily="ipam")
```

</div>

<div class="warning">
初回だけ時間がかかることがありますが、待ちましょう！
</div>

---

## 🎨 最初のグラフを描こう！

### 基本的なグラフの描き方

<div class="code-block">

```julia
# シンプルなグラフ
plot(f)

# 範囲を指定してグラフを描く
plot(f, xlim=(-10,10))

# ラベルやタイトルを追加
plot(f, label="f(x) = 2x + 1", title="1次関数のグラフ", linewidth=2)
```

</div>

**実際にGoogle Colabで試してみましょう！**

---

## 📈 様々な関数のグラフ

### 1次関数のファミリー

<div class="code-block">

```julia
f1(x) = x
f2(x) = 2x
f3(x) = -x + 3

plot(f1, label="y = x", linewidth=2)
plot!(f2, label="y = 2x", linewidth=2)
plot!(f3, label="y = -x + 3", linewidth=2)
```

</div>

<div class="highlight">
plot!() で既存のグラフに追加できます！
</div>

---

## 📉 2次関数のグラフ

### 放物線のファミリー

<div class="code-block">

```julia
p1(x) = x^2
p2(x) = 2x^2
p3(x) = -x^2
p4(x) = x^2 + 2x + 1

plot(p1, label="y = x²", linewidth=2)
plot!(p2, label="y = 2x²", linewidth=2)
plot!(p3, label="y = -x²", linewidth=2)
plot!(p4, label="y = x² + 2x + 1", linewidth=2)
```

</div>

**グラフの形の変化を観察してみましょう！**

---

## 🌊 三角関数のグラフ

### 波の美しさを見てみよう

<div class="code-block">

```julia
# 基本の三角関数
plot(sin, xlim=(-2π,2π), label="y = sin(x)", linewidth=2)
plot!(cos, xlim=(-2π,2π), label="y = cos(x)", linewidth=2)
```

</div>

### 三角関数の変形
<div class="code-block">

```julia
s1(x) = sin(x)
s2(x) = 2sin(x)        # 振幅2倍
s3(x) = sin(2x)        # 周期1/2倍
s4(x) = sin(x + π/4)   # 位相をπ/4ずらす
```

</div>

---

## 📊 指数関数・対数関数

### 急激に変化する関数たち

<div class="code-block">

```julia
# 指数関数
e1(x) = 2^x
e2(x) = exp(x)    # e^x

# 対数関数
l1(x) = log(2, x) # log₂(x)
l2(x) = log(x)    # 自然対数 ln(x)

plot(e1, xlim=(-3,3), label="y = 2ˣ", linewidth=2)
plot!(l1, xlim=(0.1,8), label="y = log₂(x)", linewidth=2)
```

</div>

**互いに逆関数の関係にあります！**

---

## 🎭 複雑な関数のグラフ

### 関数を組み合わせてみよう

<div class="code-block">

```julia
# 3次関数
complex1(x) = x^3 - 3x^2 + 2x + 1

# 減衰振動
complex2(x) = sin(x) * exp(-x/5)

# 絶対値を含む関数
complex3(x) = abs(x) * sin(x)
```

</div>

<div class="highlight">
複数の関数を掛け合わせたり、足し合わせたりして面白い形を作れます！
</div>

---

## 🎨 グラフの見た目をカスタマイズ

### 線の太さや色を変更

<div class="code-block">

```julia
plot(sin, 
     xlim=(-2π,2π), 
     label="y = sin(x)", 
     linewidth=3,           # 線の太さ
     color=:red,            # 線の色
     title="カスタマイズされたグラフ",
     xlabel="x",            # x軸のラベル
     ylabel="y")            # y軸のラベル
```

</div>

### 利用可能な色
`:red`, `:blue`, `:green`, `:orange`, `:purple`, `:pink`, `:yellow`

---

## 📝 実習：グラフを描いてみよう

**実際にGoogle Colabで以下を試してみましょう**

1. **自分の好きな1次関数を定義してグラフを描く**
2. **2次関数の頂点を視覚的に確認する**
3. **三角関数の周期を観察する**
4. **複数のグラフを重ねて比較する**

<div class="highlight">
分からないことがあったら、遠慮なく質問してください！
</div>

---

## 📚 本日の演習問題

### 問題1: 2次関数の分析
$f(x) = x^2 - 4x + 3$ について：
1. グラフを描く（$-1 ≤ x ≤ 5$）
2. 頂点の座標を求める
3. x切片（根）を求める

### 問題2: 三角関数の合成  
$g(x) = \sin(x) + \cos(x)$ について：
1. グラフを描く（$-2π ≤ x ≤ 2π$）
2. 最大値と最小値を予想
3. 周期を調べる

### 問題3: 自由課題
自分で面白い関数を作ってグラフを描いてみる

---

## 🔍 グラフから読み取れること

### 関数の性質を視覚的に理解

<div class="highlight">

**グラフを見ることで分かること：**
- 📈 **増減の様子**：どこで増加・減少するか
- 🎯 **最大値・最小値**：極値の位置
- 🔄 **周期性**：繰り返しパターン
- ⚖️ **対称性**：対称軸や中心

</div>

**数式だけでは見えない性質が一目で分かります！**

---

## 🎨 演習問題を解いてみよう！

**Google Colabを開いて、実際にコードを書いてみましょう**

### 取り組み方
1. 関数を定義する
2. グラフを描く
3. 特徴を観察する
4. 予想と結果を比較する
5. ノートブックを保存してGoogle Classroomから提出

<div class="warning">
エラーが出ても慌てずに！コードを見直して再実行してみましょう
</div>

---

## 🌟 今日のまとめ

### 学んだこと
- Julia言語での関数の定義方法
- Plots.jlを使ったグラフの描画
- 1次関数、2次関数、三角関数、指数関数のグラフ
- 複数のグラフを重ねて描く方法
- グラフの見た目のカスタマイズ

### 関数とグラフの価値
✅ **直感的理解**：数式を視覚化して理解を深める
✅ **性質の発見**：グラフから新しい性質を発見
✅ **比較分析**：複数の関数を簡単に比較

---

## 🔮 次回予告：Day 3

**最適化（最大・最小）**

- 関数の最大値・最小値を求める方法
- 微分を使った解析的手法
- Juliaを使った数値的手法
- 実際の問題への応用

<div class="highlight">
今日描いたグラフを使って、最適化問題に挑戦します！
</div>

### 宿題
今日の演習問題を完成させて、Google Classroomに提出してください。

---

## 💡 発展的な内容（時間がある人へ）

### より高度なグラフ表現

<div class="code-block">

```julia
# パラメトリック関数（媒介変数表示）
t = 0:0.1:2π
x = cos.(t)
y = sin.(t)
plot(x, y, label="円", aspect_ratio=:equal)

# 極座標グラフ
r(θ) = 1 + cos(θ)
θ = 0:0.1:2π
plot(θ, r.(θ), proj=:polar, label="カージオイド")
```

</div>

**美しい曲線を描けます！**

---

## ❓ 質問タイム

**何か分からないことはありませんか？**

- 関数の定義方法
- グラフの描き方
- エラーの解決方法
- 演習問題について
- その他、何でも！

<div class="highlight">
積極的に質問して、理解を深めましょう！
</div>

**お疲れさまでした！**
---
comments: true
---
# Introduction

生成問題是：給定一個資料集 $\mathcal{D}$ 如何透過學習使得模型的分布 $p_{\theta}$ 近似於資料集的分布 $p_{\mathrm{data}}$？可以以最佳化問題來描述如下：

$$
\min_{\theta} d(p_{\mathrm{data}}, p_{\theta})
$$

其中 $d$ 為測量機率分布的距離函數。但這問題難在 $p_{\mathrm{data}}$ 的組合太多。如果目標是生成 $224 \times 224$ 的 RGB 圖片，每個 channel 像素值落在 $0$&#x2013;$255$，則每張圖片的可能性有 $256^{224 \times 224 \times 3}$。

## Inference

生成模型的推理任務 (inference) 是學習整個資料集的聯合分布 (joint distribution)。其中有三個基礎問題：

1. *Density estimation*: 給定一個資料點 $\mathbf{x}$，它被模型生成的機率 $p_{\theta}(\mathbf{x})$ 是多少？
2. *Sampling*: 我們如何從模型生成新的資料點 $\mathbf{x}_{\mathrm{new}} \sim p_{\theta}(\mathbf{x})$？
3. *Unsupervised representation learning*: 我們如何從資料點 $\mathbf{x}$ 學習出有意義的特徵？

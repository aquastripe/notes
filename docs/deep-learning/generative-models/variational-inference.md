# Variational Inference

## Representation

一個有向的隱變數模型，其機率圖可以如下描述：

``` mermaid
flowchart TD
    1((z)) --> 2((x))
```

其中 $\mathbf{z}$ 為隱變數 (latent variable)，$\mathbf{x}$ 為觀察變數 (observed variable)。它們的聯合分布可以如下表示：

$$
p_\theta(\mathbf{x}, \mathbf{z})=p(\mathbf{x} \mid \mathbf{z}) p(\mathbf{z}).
$$

這個模型使用以下兩個過程來生成 $\mathbf{x}$：

$$
\begin{aligned}
& \mathbf{z} \sim p(\mathbf{z}) \\
& \mathbf{x} \sim p(\mathbf{x} \mid \mathbf{z})
\end{aligned}
$$

這可以理解為，模型首先生成一個高階特徵 $\mathbf{z}$ 再根據這個特徵生成對應的 $\mathbf{x}$。於是我們可以進一步推廣成一種階層式的生成模型 $p\left(\mathbf{x}, \mathbf{z}_1, \ldots, \mathbf{z}_m\right)=p\left(\mathbf{x} \mid \mathbf{z}_1\right) \prod_i p\left(\mathbf{z}_i \mid \mathbf{z}_{i+1}\right)$，對於 $\mathbf{x}$ 的資訊是階層式的生成，或像是 Hidden Markov Model 那種時序模型，根據相關聯的時序資訊來生成 $\mathbf{x}$。

## Learning Directed Latent Variable Models

我們可以透過 KL divergence 來測量兩個機率分布的距離，並且利用最小化 KL divergence 來學習生成模型，如下：

$$
\min _{p \in \mathcal{P}_{\mathbf{x}, \mathbf{z}}} D_{\mathrm{KL}}\left(p_{\text {data }}(\mathbf{x}) \| p(\mathbf{x})\right)
$$

其中邊際分布 $p(\mathbf{x}) = \int p(\mathbf{x}, \mathbf{z}) d\mathbf{z}$。最小化 KL divergence 等價於最大化 marginal log-likelihood $\log p(\mathbf{x})$：

$$
\max _{p \in \mathcal{P}_{\mathbf{x}, \mathbf{z}}} \sum_{\mathbf{x} \in \mathcal{D}} \log p(\mathbf{x})=\sum_{\mathbf{x} \in \mathcal{D}} \log \int p(\mathbf{x}, \mathbf{z}) \mathrm{d} \mathbf{z}
$$

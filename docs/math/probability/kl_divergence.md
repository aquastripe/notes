---
comments: true
---
# KL Divergence

KL divergence (又稱為 relative entropy，相對熵) 是一種統計距離，可以用來測量兩個機率分布的距離。機率分布 $P$ 與 $Q$ 的 KL divergence 以 $D_{\mathrm{KL}}(P \| Q)$ 來表示，讀作 KL divergence of P from Q。

## 定義

對於離散機率分布 $P$ 和 $Q$ 在相同的機率空間 $\mathcal{X}$，其 KL divergence 定義為

$$
D_{\mathrm{KL}}(P \| Q)=\sum_{x \in \mathcal{X}} P(x) \log \left(\frac{P(x)}{Q(x)}\right)
$$

也等價於

$$
D_{\mathrm{KL}}(P \| Q)=-\sum_{x \in \mathcal{X}} P(x) \log \left(\frac{Q(x)}{P(x)}\right)
$$

這可以看作是機率分布 $P$ 與 $Q$ 的對數差的期望值，其中期望值以 $P$ 的機率分布求得。

若 $P$ 和 $Q$ 是連續機率分布，則 KL divergence 為

$$
D_{\mathrm{KL}}(P \| Q)=\int_{-\infty}^{\infty} p(x) \log \left(\frac{p(x)}{q(x)}\right) d x
$$

其中 $p$ 和 $q$ 為 $P$ 和 $Q$ 的 PDF。

## Reference

- [Kullback–Leibler divergence. (2022, October 30). In Wikipedia.](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)

# GitHub Markdown 完全兼容版（GFM MathJax 无渲染故障）
## 适配说明
1. GitHub 不支持 `\boldsymbol{}`、`\tag{}`，全部移除，分项改用文字标注；
2. 统一 `aligned` 对齐语法，续行统一 `\quad` 缩进，不会公式截断溢出；
3. 删除冗余 `\cdot`、多余空格、无效宏包命令；
4. 分式使用 `\frac`，兼容 GitHub 内置轻量 MathJax；
5. 重点物理量使用 Markdown 正文粗体，不依赖公式内加粗。

---

# 严格对照PDF原文107页，完整无省略全推导（含全部中间项，无简写、无截断）
## 一、原文给定两路光电场（完全复刻）
$$
\begin{cases}
E_1(t) = E_0 \cos\big[\omega t + \beta(t)\big] \\
E_2(t) = E_0 \cos\big[\omega(t+s) + \beta(t+s)\big] = E_0 \cos\big[\omega t + \omega s + \beta(t+s)\big]
\end{cases}
$$
$s$：两束光传播时间差；$\beta(t)$：原子自发辐射带来的**随机时变相位**；总电场满足叠加原理：
$$E(t) = E_1(t) + E_2(t)$$
光学瞬时强度定义为电场平方 $I(t)=E(t)^2$（教材约定省略常数 $\varepsilon_0 c$）。

## 二、第一步：完全平方展开（无任何合并、无省略）
$$
\begin{aligned}
I(t) &= \big[E_1(t)+E_2(t)\big]^2 \\
&= E_1^2(t) + E_2^2(t) + 2E_1(t)E_2(t) \\
&= \Big\{E_0 \cos\big[\omega t+\beta(t)\big]\Big\}^2 + \Big\{E_0 \cos\big[\omega t+\omega s+\beta(t+s)\big]\Big\}^2 \\
&\quad + 2E_0 \cos\big[\omega t+\beta(t)\big] E_0 \cos\big[\omega t+\omega s+\beta(t+s)\big] \\
&= E_0^2 \cos^2\big[\omega t+\beta(t)\big] + E_0^2 \cos^2\big[\omega t+\omega s+\beta(t+s)\big] \\
&\quad + 2E_0^2 \cos\big[\omega t+\beta(t)\big]\cos\big[\omega t+\omega s+\beta(t+s)\big]
\end{aligned}
$$
这是平方展开的原始三项式，和PDF原文完全一致。

## 三、第二步：交叉项积化和差完整拆解（补齐全部两项，无丢失）
三角恒等式：$2\cos A \cos B = \cos(A+B) + \cos(A-B)$

令
$$A=\omega t+\beta(t),\quad B=\omega t+\omega s+\beta(t+s)$$

分别计算和、差相位：
$$
\begin{aligned}
A+B &= \omega t+\beta(t)+\omega t+\omega s+\beta(t+s) = 2\omega t + \omega s + \beta(t)+\beta(t+s) \\
A-B &= \omega t+\beta(t)-\big[\omega t+\omega s+\beta(t+s)\big] = -\omega s + \beta(t)-\beta(t+s)
\end{aligned}
$$

由余弦偶函数 $\cos(-x)=\cos x$：
$$\cos(A-B) = \cos\Big[\omega s + \beta(t+s)-\beta(t)\Big]$$

代入交叉项：
$$
\begin{aligned}
2E_0^2\cos A\cos B &= E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big] \\
&\quad + E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]
\end{aligned}
$$

## 四、第三步：完整瞬时光强全式（PDF原文完整四项，无任何省略）
把交叉项代回平方展开式，合并后得到完整 $I(t)$：
$$
\begin{aligned}
I(t) &= E_0^2 \cos^2\big[\omega t+\beta(t)\big] \\
&+ E_0^2 \cos^2\big[\omega t+\omega s+\beta(t+s)\big] \\
&+ E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big] \\
&+ E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]
\end{aligned}
$$

分项说明：
1. 第一项：余弦平方项，仅单束光自身振荡；
2. 第二项：余弦平方项，仅单束光自身振荡；
3. 第三项：含 $2\omega$ 二倍光频，超高频快速振荡；
4. 第四项：不含 $t$ 线性振荡，仅携带两路光相位差 $\Delta\beta(t)=\beta(t+s)-\beta(t)$，唯一和相干性相关，仅此项受 $\beta(t)$ 影响。

## 五、第四步：完整时间平均推导（带全部积分过程，不跳步）
探测器测量长时间平均强度：
$$\overline{I} = \frac{1}{T}\int_{0}^{T} I(t) dt$$
$T$：探测器响应时间（$T\gg 10^{-14}\ \text{s}$ 光波周期），四项分别积分：

### 1. 第一项平均
利用 $\cos^2x=\frac{1+\cos2x}{2}$，高频振荡长时间积分抵消为0：
$$
\overline{E_0^2\cos^2\big[\omega t+\beta(t)\big]}
= E_0^2 \cdot \frac{1}{T}\int_0^T \frac{1+\cos\big[2\omega t+2\beta(t)\big]}{2}dt
= \frac{E_0^2}{2}
$$

### 2. 第二项平均
完全同理，与 $\beta(t)$ 无关：
$$
\overline{E_0^2\cos^2\big[\omega t+\omega s+\beta(t+s)\big]} = \frac{E_0^2}{2}
$$

### 3. 第三项平均
含 $2\omega$ 超高频振荡，正负振荡完全抵消：
$$
\overline{E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big]}
= 0
$$

### 4. 第四项平均（唯一受 $\beta(t)$ 调制的积分）
$$
\overline{E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]}
= E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s + \beta(t+s)-\beta(t)\Big] dt
$$

## 六、合并得到教材最终平均光强（完整推导结果）
$$
\begin{aligned}
\overline{I}
&= \frac{E_0^2}{2} + \frac{E_0^2}{2} + 0 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big] dt \\
&= E_0^2 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big] dt
\end{aligned}
$$

## 七、$\beta(t)$ 的完整影响总结
1. **短光程差 $s\ll \tau_c$（延迟小于相干时间）**
   同一波包分裂，相位无随机跳变：$\beta(t+s)\approx\beta(t)$，积分内余弦为常数 $\cos(\omega s)$，干涉项保留，条纹清晰。
2. **长光程差 $s\gg \tau_c$（延迟大于相干时间）**
   两路光来自完全独立波包，$\Delta\beta(t)=\beta(t+s)-\beta(t)$ 在 $[0,2\pi]$ 均匀随机分布，积分结果为0，干涉项消失，视野均匀无条纹。
3. 前三项时间平均**完全不受 $\beta(t)$ 影响**，只有第四项积分由随机相位差 $\beta(t+s)-\beta(t)$ 决定，这是引入 $\beta(t)$ 前后公式最核心的变化。

---

## GitHub 渲染避坑关键点
1. 禁止使用 `\boldsymbol{}`、`\mathbf{希腊字母}`、`\tag{}`；
2. 多行公式统一 `&=` 对齐，续行开头加 `\quad`；
3. 不要大量连续空白换行，会导致公式折叠/截断；
4. 复杂长公式不要单行挤压，合理分行；
5. 分式统一用 `\frac`，`\dfrac` 在 GitHub 部分页面会缩小排版。
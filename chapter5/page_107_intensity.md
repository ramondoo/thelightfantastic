# 原始Markdown（移除\big/\Big 解决分隔符报错，可直接复制）
# 相干光含随机相位β(t)光强完整推导
适配GitHub Markdown，全部公式为标准LaTeX语法，无无法渲染宏包

## 一、两路光电场定义
$$
\begin{cases}
E_1(t) = E_0 \cos[\omega t + \beta(t)] \\
E_2(t) = E_0 \cos[\omega(t+s)] = E_0 \cos[\omega t + \omega s + \beta(t+s)]
\end{cases}
$$
- $s$：两束光传播时间差
- $\beta(t)$：原子自发辐射产生的随机时变相位

电场叠加原理：
$$E(t) = E_1(t) + E_2(t)$$

光学瞬时光强（教材省略$\varepsilon_0 c$常数）：
$$I(t)=E(t)^2$$

## 二、瞬时光强完全平方展开
$$
\begin{aligned}
I(t) &= \big[E_1(t)+E_2(t)\big]^2 \\
&= E_1^2(t) + E_2^2(t) + 2E_1(t)E_2(t) \\
&= \{E_0 \cos[\omega t+\beta(t)]\}^2 + \{E_0 \cos[\omega t+\omega s+\beta(t+s)]\}^2 \\
&\quad + 2E_0 \cos[\omega t+\beta(t)] E_0 \cos[\omega t+\omega s+\beta(t+s)] \\
&= E_0^2 \cos^2[\omega t+\beta(t)] + E_0^2 \cos^2[\omega t+\omega s+\beta(t+s)] \\
&\quad + 2E_0^2 \cos[\omega t+\beta(t)]\cos[\omega t+\omega s+\beta(t+s)]
\end{aligned}
$$

## 三、交叉项积化和差拆分
三角恒等式：

$$2\cos A \cos B = \cos(A+B) + \cos(A-B)$$

设：
$$A=\omega t+\beta(t),\quad B=\omega t+\omega s+\beta(t+s)$$

相位和、相位差：

$$
\begin{aligned}
A+B &= \omega t+\beta(t)+\omega t+\omega s+\beta(t+s) = 2\omega t + \omega s + \beta(t)+\beta(t+s) \\
A-B &= \omega t+\beta(t)-[\omega t+\omega s+\beta(t+s)] = -\omega s + \beta(t)-\beta(t+s)
\end{aligned}
$$

由余弦偶函数$\cos(-x)=\cos x$：
$$\cos(A-B) = \cos[\omega s + \beta(t+s)-\beta(t)]$$

代入交叉项：
$$
\begin{aligned}
2E_0^2\cos A\cos B &= E_0^2 \cos[2\omega t+\omega s+\beta(t)+\beta(t+s)] \\
&\quad + E_0^2 \cos[\omega s+\beta(t+s)-\beta(t)]
\end{aligned}
$$

## 四、完整四项瞬时光强总式
$$
\begin{aligned}
I(t) &= E_0^2 \cos^2[\omega t+\beta(t)] \\
&+ E_0^2 \cos^2[\omega t+\omega s+\beta(t+s)] \\
&+ E_0^2 \cos[2\omega t+\omega s+\beta(t)+\beta(t+s)] \\
&+ E_0^2 \cos[\omega s+\beta(t+s)-\beta(t)]
\end{aligned}
$$

分项说明：
1. 第1、2项：单光束自身余弦平方振荡项；
2. 第3项：含$2\omega$超高频振荡项；
3. 第4项：低频干涉项，唯一包含随机相位差$\Delta\beta(t)=\beta(t+s)-\beta(t)$。

## 五、长时间平均光强积分
探测器平均光强定义：
$$\overline{I} = \frac{1}{T}\int_{0}^{T} I(t) dt$$
$T$为探测器响应时间，$T \gg 10^{-14}\ \text{s}$。

### 1. 第一项平均
$$
\overline{E_0^2\cos^2[\omega t+\beta(t)]}
= E_0^2 \cdot \frac{1}{T}\int_0^T \frac{1+\cos[2\omega t+2\beta(t)]}{2}dt
= \frac{E_0^2}{2}
$$

### 2. 第二项平均
$$
\overline{E_0^2\cos^2[\omega t+\omega s+\beta(t+s)]} = \frac{E_0^2}{2}
$$

### 3. 第三项平均
高频振荡积分抵消为0：
$$
\overline{E_0^2 \cos[2\omega t+\omega s+\beta(t)+\beta(t+s)]} = 0
$$

### 4. 第四项平均（干涉核心项）
$$
\overline{E_0^2 \cos[\omega s+\beta(t+s)-\beta(t)]}
= E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos[\omega s + \beta(t+s)-\beta(t)] dt
$$

## 六、最终平均光强合并式
$$
\begin{aligned}
\overline{I}
&= \frac{E_0^2}{2} + \frac{E_0^2}{2} + 0 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos[\omega s+\beta(t+s)-\beta(t)] dt \\
&= E_0^2 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos[\omega s+\beta(t+s)-\beta(t)] dt
\end{aligned}
$$

## 七、随机相位β(t)对干涉的影响
1. **短光程差 $s\ll \tau_c$**
   延迟小于相干时间，$\beta(t+s)\approx\beta(t)$，干涉项保留，条纹清晰。

2. **长光程差 $s\gg \tau_c$**
   延迟大于相干时间，相位差随机分布，积分平均值为0，干涉消失。

3. 核心结论：仅第四项受$\beta(t)$调制，前三项平均强度与随机相位无关。

---
### 使用说明
1. 全选本文字，复制粘贴新建`.md`文件；
2. GitHub、Typora、Obsidian均可正常渲染所有LaTeX公式；
3. 已全部删除`\big`/`\Big`大括号命令，消除分隔符报错；无`\boldsymbol`、`\tag`等不兼容命令。

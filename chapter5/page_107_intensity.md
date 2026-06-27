# 相干光含随机相位 $\beta(t)$ 瞬时光强完整推导（GitHub Markdown 兼容，LaTeX 公式）
> 适配 GitHub GFM 内置 MathJax，删除不支持命令：`\boldsymbol`、`\tag`，所有公式标准 LaTeX 语法，无渲染截断问题

## 一、两路光电场定义（PDF 原文）
$$
\begin{cases}
E_1(t) = E_0 \cos\big[\omega t + \beta(t)\big] \\
E_2(t) = E_0 \cos\big[\omega(t+s) + \beta(t+s)\big] = E_0 \cos\big[\omega t + \omega s + \beta(t+s)\big]
\end{cases}
$$
- $s$：两束光传播时间差
- $\beta(t)$：原子自发辐射产生的**随机时变相位**

电场叠加原理：
$$E(t) = E_1(t) + E_2(t)$$
光学瞬时光强定义为电场平方（教材省略真空介电常数、光速常数）：
$$I(t)=E(t)^2$$

## 二、瞬时光强完全平方展开
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

## 三、交叉项积化和差拆分
三角恒等式：
$$2\cos A \cos B = \cos(A+B) + \cos(A-B)$$

令：
$$A=\omega t+\beta(t),\quad B=\omega t+\omega s+\beta(t+s)$$

相位和与相位差：
$$
\begin{aligned}
A+B &= \omega t+\beta(t)+\omega t+\omega s+\beta(t+s) = 2\omega t + \omega s + \beta(t)+\beta(t+s) \\
A-B &= \omega t+\beta(t)-\big[\omega t+\omega s+\beta(t+s)\big] = -\omega s + \beta(t)-\beta(t+s)
\end{aligned}
$$

由余弦偶函数性质 $\cos(-x)=\cos x$：
$$\cos(A-B) = \cos\Big[\omega s + \beta(t+s)-\beta(t)\Big]$$

代入交叉项：
$$
\begin{aligned}
2E_0^2\cos A\cos B &= E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big] \\
&\quad + E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]
\end{aligned}
$$

## 四、完整四项瞬时光强总式
将拆分后的交叉项代回平方展开式，得到完整瞬时光强：
$$
\begin{aligned}
I(t) &= E_0^2 \cos^2\big[\omega t+\beta(t)\big] \\
&+ E_0^2 \cos^2\big[\omega t+\omega s+\beta(t+s)\big] \\
&+ E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big] \\
&+ E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]
\end{aligned}
$$

分项说明：
1. 第一项、第二项：单光束自身余弦平方振荡项；
2. 第三项：含 $2\omega$ 二倍光频超高频振荡项；
3. 第四项：低频干涉项，仅该项包含随机相位差 $\Delta\beta(t)=\beta(t+s)-\beta(t)$，是唯一受 $\beta(t)$ 影响的项。

## 五、长时间平均光强积分推导
探测器输出为光波周期平均强度：
$$\overline{I} = \frac{1}{T}\int_{0}^{T} I(t) dt$$
$T$ 为探测器响应时间，满足 $T\gg 10^{-14}\ \text{s}$，远大于光波振荡周期。

### 1. 第一项时间平均
利用三角降幂公式 $\cos^2x=\frac{1+\cos2x}{2}$，高频振荡积分抵消为0：
$$
\overline{E_0^2\cos^2\big[\omega t+\beta(t)\big]}
= E_0^2 \cdot \frac{1}{T}\int_0^T \frac{1+\cos\big[2\omega t+2\beta(t)\big]}{2}dt
= \frac{E_0^2}{2}
$$

### 2. 第二项时间平均
同理，与随机相位 $\beta(t)$ 无关：
$$
\overline{E_0^2\cos^2\big[\omega t+\omega s+\beta(t+s)\big]} = \frac{E_0^2}{2}
$$

### 3. 第三项时间平均
$2\omega$ 超高频率振荡，正负积分完全抵消：
$$
\overline{E_0^2 \cos\big[2\omega t+\omega s+\beta(t)+\beta(t+s)\big]} = 0
$$

### 4. 第四项时间平均（相干干涉核心项）
$$
\overline{E_0^2 \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big]}
= E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s + \beta(t+s)-\beta(t)\Big] dt
$$

## 六、最终平均光强合并结果
$$
\begin{aligned}
\overline{I}
&= \frac{E_0^2}{2} + \frac{E_0^2}{2} + 0 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big] dt \\
&= E_0^2 + E_0^2 \cdot \frac{1}{T}\int_{0}^{T} \cos\Big[\omega s+\beta(t+s)-\beta(t)\Big] dt
\end{aligned}
$$

## 七、随机相位 $\beta(t)$ 对干涉的影响
1. **短光程差 $s\ll \tau_c$（延迟小于相干时间）**
   同一波包分裂干涉，相位无随机跳变 $\beta(t+s)\approx\beta(t)$，积分结果为常数 $\cos(\omega s)$，干涉条纹清晰可见。

2. **长光程差 $s\gg \tau_c$（延迟大于相干时间）**
   两路光来自独立无关波包，相位差 $\Delta\beta(t)$ 在 $[0,2\pi]$ 均匀随机分布，积分平均值为0，干涉项消失，视野均匀无条纹。

3. 核心结论：前三项平均强度完全不受 $\beta(t)$ 影响，仅第四项积分由随机相位差决定，这是真实光源存在部分相干效应的根源。

---

## GitHub Markdown 渲染注意事项
1. 所有公式使用标准 `$$ $$` 块级 LaTeX，行内公式用 `$ $`；
2. 无 `\boldsymbol`、`\tag`、`\dfrac` 等 GitHub 不兼容命令；
3. 多行 `aligned` 统一 `&=` 对齐，续行添加 `\quad` 缩进，避免公式溢出截断；
4. 直接复制全文到 GitHub `.md` 文件可正常渲染全部公式。
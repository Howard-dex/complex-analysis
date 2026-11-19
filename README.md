# 《复分析》（Ahlfors 原书第 3 版）学习笔记与定理证明

本仓库整理自 **Lars V. Ahlfors** 经典教材 *Complex Analysis (Third Edition)*（中文译本：华章数学译丛《复分析》原书第 3 版）。

## 目录导航

| 章节 | 重点总结 | 形式化定理证明 |
| :--- | :--- | :--- |
| 第 1 章：复数 | 本文档（下方） | [查看全部 19 条定理形式化证明](./chapter1_formal_proofs.md) |

---

## 第 1 章：复数——重点内容与定理证明总结

第 1 章从**代数结构**与**几何表示**两个维度奠定了复分析的基础。Ahlfors 在本章不仅系统推导了复数的运算、不等式、方程求解与黎曼球面模型，更强调了现代分析学的严密性原则：**所有分析结论都必须基于实数性质严格推导，几何仅用于直观描述与启发，而不能替代逻辑证明。**

---

### 1.1 复数代数

#### 1.1.1 算术运算与除法封闭性

- **基本定义**：复数形如 $\alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ），其中 $i^2 = -1$ 。 $\alpha$ 为实部， $\beta$ 为虚部；若 $\alpha = 0$ 则称为纯虚数，若 $\beta = 0$ 则为实数。两个复数相等当且仅当实部和虚部分别相等； $0$ 是唯一既是实数又是纯虚数的数。
- **加法运算**（对任意 $\alpha, \beta, \gamma, \delta \in \mathbb{R}$ ）： $(\alpha + i\beta) + (\gamma + i\delta) = (\alpha + \gamma) + i(\beta + \delta)$ 。
- **乘法运算**（对任意 $\alpha, \beta, \gamma, \delta \in \mathbb{R}$ ）： $(\alpha + i\beta)(\gamma + i\delta) = (\alpha\gamma - \beta\delta) + i(\alpha\delta + \beta\gamma)$ 。
- **虚数单位的幂**：对任意整数 $n \in \mathbb{Z}$ ， $i^n$ 按 $n$ 除以 $4$ 的非负余数 $0, 1, 2, 3$ 周期性取值 $1, i, -1, -i$ 。

**命题 1（除法的存在性与唯一性）**：对任意 $\alpha, \beta, \gamma, \delta \in \mathbb{R}$ 且 $\gamma + i\delta \neq 0$ ，商 $\frac{\alpha + i\beta}{\gamma + i\delta}$ 存在且唯一：

$$
\frac{\alpha + i\beta}{\gamma + i\delta} = \frac{\alpha\gamma + \beta\delta}{\gamma^2 + \delta^2} + i\frac{\beta\gamma - \alpha\delta}{\gamma^2 + \delta^2}
$$

特别地，任意非零复数 $\alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ）的倒数为 $\frac{1}{\alpha + i\beta} = \frac{\alpha - i\beta}{\alpha^2 + \beta^2}$ 。

**证明思路**：设商为 $x + iy$ （ $x, y \in \mathbb{R}$ ），由 $(\gamma + i\delta)(x + iy) = \alpha + i\beta$ 比较实部与虚部，得到关于实数 $x, y$ 的线性方程组：

$$
\begin{cases}
\gamma x - \delta y = \alpha \cr
\delta x + \gamma y = \beta
\end{cases}
$$

因为 $\gamma + i\delta \neq 0$ 且 $\gamma, \delta \in \mathbb{R}$ ，系数行列式 $\gamma^2 + \delta^2 \neq 0$ ，故方程组有唯一解。证明存在性后，实际计算只需将分子分母同乘共轭 $\gamma - i\delta$ 即可。

---

#### 1.1.2 平方根

**命题 2（复数平方根的存在性与显式公式）**：任意复数 $\alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ）均存在平方根，且有两个互为相反数的值（两值相等当且仅当 $\alpha + i\beta = 0$ ）。具体为：

- 当 $\beta = 0$ 且 $\alpha \ge 0$ 时，平方根为 $\pm \sqrt{\alpha}$ ；
- 当 $\beta = 0$ 且 $\alpha \lt 0$ 时，平方根为 $\pm i\sqrt{-\alpha}$ ；
- 当 $\beta \neq 0$ 时（所有根号均取非负算术平方根）：

$$
\sqrt{\alpha + i\beta} = \pm \left[ \sqrt{\frac{\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} + i\frac{\beta}{|\beta|}\sqrt{\frac{-\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} \right]
$$

**证明步骤**：

1. 设 $(x + iy)^2 = \alpha + i\beta$ （ $x, y \in \mathbb{R}$ ），等价于实方程组 $x^2 - y^2 = \alpha$ 且 $2xy = \beta$ 。
2. 若 $\beta = 0$ ，则 $x = 0$ 或 $y = 0$ ，结合 $x^2 - y^2 = \alpha$ 直接分 $\alpha \ge 0$ 与 $\alpha \lt 0$ 两种情形解得上述结果。
3. 若 $\beta \neq 0$ ，利用恒等式 $(x^2 + y^2)^2 = (x^2 - y^2)^2 + 4x^2y^2 = \alpha^2 + \beta^2$ ，因 $x^2 + y^2 \ge 0$ ，开方得 $x^2 + y^2 = \sqrt{\alpha^2 + \beta^2}$ ；与 $x^2 - y^2 = \alpha$ 联立解得 $x^2 = \frac{1}{2}\left(\alpha + \sqrt{\alpha^2 + \beta^2}\right) \gt 0$ 与 $y^2 = \frac{1}{2}\left(-\alpha + \sqrt{\alpha^2 + \beta^2}\right) \gt 0$ 。
4. 由于 $2xy = \beta$ 并非上述方程的推论，必须选取 $x, y$ 的符号使其乘积与 $\beta$ 同号，即引入符号因子 $\frac{\beta}{|\beta|}$ 。

**重点提示**：除 $0$ 外，只有正实数有实平方根，只有负实数有纯虚数平方根。一般复数的两个平方根无法像实数那样自然区分“正负”，**必须以对称的方式处理两个平方根**，避免人为指定主值符号。

---

#### 1.1.3 复数域的合理性（存在性与唯一性）

为了使 $x^2 + 1 = 0$ 的解在逻辑上严密，Ahlfors 从实数系 $\mathbb{R}$ 的公理特征出发构造了复数域 $\mathbb{C}$ ：

1. **域（Field）**：对加、乘法满足结合律、交换律、分配律，存在中性元 $0, 1$ （ $1 \neq 0$ ）及减法、非零除法逆元（从而每个域都是整环）。
2. **有序性（Order）**：通过正实数集 $\mathbb{R}^+$ 定义 $\alpha \lt \beta \iff \beta - \alpha \in \mathbb{R}^+$ 。由此推出对一切 $\alpha \in \mathbb{R}$ 有 $\alpha^2 \ge 0$ ，故 $x^2 + 1 = 0$ 在 $\mathbb{R}$ 中无解。
3. **完备性（Completeness）**：每个单调递增且有上界的实数序列必有极限。

**定理（复数域的唯一性与存在性）**：

- **同构意义下的唯一性**：设 $F$ 是包含 $\mathbb{R}$ 且含有 $x^2 + 1 = 0$ 的根 $i$ 的域。因 $x^2 + 1 = (x+i)(x-i)$ ，方程在 $F$ 中只有两根 $\pm i$ 。令 $C = \lbrace \alpha + i\beta \mid \alpha, \beta \in \mathbb{R} \rbrace$ ：
  - 表示唯一性：若 $\alpha + i\beta = \alpha' + i\beta'$ ，则 $\alpha - \alpha' = -i(\beta - \beta')$ ，两边平方得 $(\alpha - \alpha')^2 = -(\beta - \beta')^2$ ，在 $\mathbb{R}$ 中只能推出 $\alpha = \alpha'$ 且 $\beta = \beta'$ 。
  - 同构无关性： $C$ 是 $F$ 的子域；若另一扩域 $F'$ 含根 $i'$ 并构成子域 $C'$ ，则映射 $\alpha + i\beta \mapsto \alpha + i'\beta$ 是固定 $\mathbb{R}$ 的域同构，说明 $\mathbb{C}$ 的结构不依赖于 $F$ 的选取。
- **存在性构造**：考虑所有形式表达式 $\alpha + i\beta$ （此处 $+$ 和 $i$ 仅为形式符号），按 1.1.1 节的公式定义加法与乘法构成域 $F$ 。子集 $\lbrace \alpha + i0 \mid \alpha \in \mathbb{R} \rbrace$ 同构于 $\mathbb{R}$ ，且 $(0 + i1)^2 = -(1 + i0)$ ，从而证明了 $\mathbb{C}$ 的存在性。

**延伸模型（课后习题重点）**： $\mathbb{C}$ 也同构于商域 $\mathbb{R}[x]/(x^2 + 1)$ ，以及如下实矩阵集合：

$$
\left\lbrace \begin{pmatrix} \alpha & \beta \cr -\beta & \alpha \end{pmatrix} \quad\middle\vert\quad \alpha, \beta \in \mathbb{R} \right\rbrace
$$

---

#### 1.1.4 共轭与绝对值（模）

**复共轭（Complex Conjugation）**：对 $a = \alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ），定义 $\bar{a} = \alpha - i\beta$ 。因为 $-i$ 与 $i$ 满足相同的代数关系 $(-i)^2 = -1$ ，共轭是一个**对合自同构**： $\overline{\bar{a}} = a$ ，且对任意仅由变元与实常数经有限次四则运算构成的有理运算 $R$ （分母非零），满足：

$$
\overline{R(a, b, c, \dots)} = R(\bar{a}, \bar{b}, \bar{c}, \dots)
$$

实部与虚部的共轭表示：

$$
\mathop{\mathrm{Re}} a = \frac{a + \bar{a}}{2}, \qquad \mathop{\mathrm{Im}} a = \frac{a - \bar{a}}{2i}
$$

**推论（实系数方程共轭根定理）**：若 $z_0$ 是方程 $c_0 z^n + c_1 z^{n-1} + \dots + c_n = 0$ 的根，两边取共轭得 $\overline{c_0} (\overline{z_0})^n + \overline{c_1} (\overline{z_0})^{n-1} + \dots + \overline{c_n} = 0$ ，故 $\overline{z_0}$ 是共轭系数方程 $\overline{c_0} z^n + \overline{c_1} z^{n-1} + \dots + \overline{c_n} = 0$ 的根。特别地，若系数全为实数，则非实根必成对共轭出现。

**绝对值 / 模（Modulus）**：对 $a = \alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ），定义为 $|a| = \sqrt{a\bar{a}} = \sqrt{\alpha^2 + \beta^2} \ge 0$ ，即 $a\bar{a} = |a|^2$ ，且 $|\bar{a}| = |a|$ 。

- **乘积与商的模**：由 $|ab|^2 = (ab)\overline{(ab)} = (a\bar{a})(b\bar{b}) = |a|^2|b|^2$ 取非负平方根得 $|ab| = |a|\cdot|b|$ 。同理可推至有限项乘积及商 $\left\lvert \frac{a}{b} \right\rvert = \frac{|a|}{|b|}$ （ $b \neq 0$ ）。
- **和与差的模展开式**：

$$
|a + b|^2 = |a|^2 + |b|^2 + 2\mathop{\mathrm{Re}}(a\bar{b}), \qquad |a - b|^2 = |a|^2 + |b|^2 - 2\mathop{\mathrm{Re}}(a\bar{b})
$$

- **平行四边形恒等式**：将上述两式相加得：

$$
|a + b|^2 + |a - b|^2 = 2\left(|a|^2 + |b|^2\right)
$$

---

#### 1.1.5 重要不等式

> **注意**：复数域 $\mathbb{C}$ 上不存在次序关系，所有不等式均是实数（实部、虚部、模）之间的关系；后文简写 $c \ge 0$ 或 $c \gt 0$ 均约定表示“ $c$ 是非负实数或正实数”。

**1. 基本模估计**

$$
-|a| \le \mathop{\mathrm{Re}} a \le |a|, \qquad -|a| \le \mathop{\mathrm{Im}} a \le |a|
$$

其中 $\mathop{\mathrm{Re}} a = |a|$ 当且仅当 $a \in \mathbb{R}$ 且 $a \ge 0$ 。

**2. 三角形不等式（Triangle Inequality）**

$$
|a + b| \le |a| + |b|, \qquad \left\lvert \sum _ {k=1}^n a_k \right\rvert \le \sum _ {k=1}^n |a_k|
$$

**证明**：由 $\mathop{\mathrm{Re}}(a\bar{b}) \le |a\bar{b}| = |a||b|$ ，代入 $|a+b|^2$ 展开式得 $|a+b|^2 \le (|a|+|b|)^2$ ，开方即得。多项情形由数学归纳法得证。

**等号成立的充要条件**：多项三角形不等式取等号，当且仅当**任意两个非零项之比为正实数**。

- 两项情形：取等号当且仅当 $\mathop{\mathrm{Re}}(a\bar{b}) = |a\bar{b}|$ ，即 $a\bar{b}$ 为非负实数；当 $b \neq 0$ 时等价于 $|b|^2(a/b) \ge 0$ ，即 $a/b$ 为非负实数。
- 多项必要性：对 $n = 1$ 条件自然成立；对 $n \ge 2$ （当 $n = 2$ 时后段求和为空和 $0$ ），利用夹逼不等式

$$
\sum _ {k=1}^n |a_k| = |(a_1 + a_2) + a_3 + \dots + a_n| \le |a_1 + a_2| + \sum _ {k=3}^n |a_k| \le \sum _ {k=1}^n |a_k|
$$

推出 $|a_1 + a_2| = |a_1| + |a_2|$ ，由编号任意性知任意两非零项之比为正实数。

- 多项充分性：若各项全为零则显然成立；否则不妨设 $a_1 \neq 0$ ，提出 $|a_1|$ ，利用各项比值 $\frac{a_k}{a_1}$ 为非负实数直接化简即得等号。

**常用推论**：

- 逆向三角形不等式： $|a - b| \ge \bigl\lvert \lvert a \rvert - \lvert b \rvert \bigr\rvert$ 。
- 分量估计： $|\alpha + i\beta| \le |\alpha| + |\beta|$ （ $\alpha, \beta \in \mathbb{R}$ ）。

**3. 柯西不等式（Cauchy's Inequality）**

$$
\left\lvert \sum _ {k=1}^n a_k b_k \right\rvert^2 \le \left(\sum _ {k=1}^n |a_k|^2\right)\left(\sum _ {k=1}^n |b_k|^2\right)
$$

**证明（Ahlfors 极值构造法）**：若 $\sum _ {k=1}^n |b_k|^2 = 0$ ，结论显然成立。设分母非零，对任意 $\lambda \in \mathbb{C}$ 展开非负实数表达式：

$$
0 \le \sum _ {k=1}^n |a_k - \lambda \overline{b_k}|^2 = \sum _ {k=1}^n |a_k|^2 + |\lambda|^2 \sum _ {k=1}^n |b_k|^2 - 2\mathop{\mathrm{Re}}\left(\bar{\lambda}\sum _ {k=1}^n a_k b_k\right)
$$

选取

$$
\lambda = \frac{\sum _ {k=1}^n a_k b_k}{\sum _ {k=1}^n |b_k|^2}
$$

代入化简，得：

$$
\sum _ {k=1}^n |a_k|^2 - \frac{\left\lvert \sum _ {k=1}^n a_k b_k \right\rvert^2}{\sum _ {k=1}^n |b_k|^2} \ge 0
$$

整理即得柯西不等式。

**等号成立条件**：当且仅当**序列 $\lbrace a_k \rbrace$ 与 $\lbrace \overline{b_k} \rbrace$ 成比例**（严格来说即在 $\mathbb{C}^n$ 中线性相关：存在不全为零的复数 $\mu, \nu$ 使对所有 $k$ 有 $\mu a_k + \nu \overline{b_k} = 0$ ）。

**另证（拉格朗日恒等式，1.1.4 节练习 5；当 $n = 1$ 时空和约定为 $0$ ）**：

$$
\left\lvert \sum _ {k=1}^n a_k b_k \right\rvert^2 = \sum _ {k=1}^n |a_k|^2 \sum _ {k=1}^n |b_k|^2 - \sum _ {1 \le j \lt k \le n} |a_j \overline{b_k} - a_k \overline{b_j}|^2
$$

---

### 1.2 复数的几何表示

在复平面（实轴 $x$ 、虚轴 $y$ ）中，复数 $a = \alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ）既对应点 $(\alpha, \beta)$ ，也对应从原点指向该点的向量。

#### 1.2.1 几何加法与几何乘法

- **加法与减法**：遵循向量的平行四边形法则； $a+b$ 与 $a-b$ 为两对角线， $|a-b|$ 为两点间距离。 $a, \bar{a}, -a, -\bar{a}$ 构成以两坐标轴为对称轴的矩形顶点。
- **极坐标（三角形式）与幅角**：对任意非零复数 $a$ ，可表示为

$$
a = r(\cos\varphi + i\sin\varphi), \qquad r = |a| \gt 0, \qquad \varphi = \arg a
$$

$0$ 的模为 $0$ 且幅角无定义；非零复数的幅角在相差 $2\pi$ （ $360^\circ$ ）整数倍的意义下唯一确定。

- **乘法与除法的幅角法则**：设非零复数 $a_1 = r_1(\cos\varphi_1 + i\sin\varphi_1)$ 与 $a_2 = r_2(\cos\varphi_2 + i\sin\varphi_2)$ （ $r_1, r_2 \gt 0$ ），利用三角函数和角公式直接推出：

$$
a_1 a_2 = r_1 r_2 \left[\cos(\varphi_1 + \varphi_2) + i\sin(\varphi_1 + \varphi_2)\right]
$$

$$
\arg(a_1 a_2) \equiv \arg a_1 + \arg a_2 \pmod{2\pi}, \qquad \arg\frac{a_2}{a_1} \equiv \arg a_2 - \arg a_1 \pmod{2\pi}
$$

- **几何作图**：当 $a_1 \notin \mathbb{R}$ 且 $a_2 \neq 0$ 时，以 $0, 1, a_1$ 为顶点的三角形与以 $0, a_2, a_1 a_2$ 为顶点的三角形同向相似（ $a_1 \in \mathbb{R}$ 时退化为共线比例缩放）。
- **Ahlfors 严密性注记**：上述幅角法则暂时借助了初等三角学，严格的纯解析定义（通过复幂级数定义指数函数、三角函数与对数函数）在第 2.3 节完成。

---

#### 1.2.2 二项方程与单位根

- **整数次幂与棣莫弗公式（De Moivre's Formula）**：对任意非零复数 $a = r(\cos\varphi + i\sin\varphi)$ （ $r \gt 0$ ）与任意整数 $n \in \mathbb{Z}$ （含 $n \le 0$ ），有 $a^n = r^n(\cos n\varphi + i\sin n\varphi)$ 。取 $r = 1$ 得：

$$
(\cos\varphi + i\sin\varphi)^n = \cos n\varphi + i\sin n\varphi
$$

- **定理（二项方程 $z^n = a$ 的完全解）**：设 $a = r(\cos\varphi + i\sin\varphi) \neq 0$ （ $r \gt 0$ ）， $n \in \mathbb{Z}^+$ ，则 $z^n = a$ 恰有 $n$ 个互不相同的根：

$$
z_k = \sqrt[n]{r}\left[\cos\left(\frac{\varphi + 2k\pi}{n}\right) + i\sin\left(\frac{\varphi + 2k\pi}{n}\right)\right], \qquad k = 0, 1, \dots, n-1
$$

- **几何意义**：这 $n$ 个根的模相同、幅角等间隔分布，位于以原点为中心、半径为 $\sqrt[n]{r}$ 的圆周上（ $n = 1$ 为单点， $n = 2$ 为关于原点对称的两点， $n \ge 3$ 时构成**正 $n$ 边形的顶点**）。
- **单位根（ $1$ 的 $n$ 次根）**：令 $\omega = \cos\frac{2\pi}{n} + i\sin\frac{2\pi}{n}$ ，则 $z^n = 1$ 的根为 $1, \omega, \omega^2, \dots, \omega^{n-1}$ 。若 $\sqrt[n]{a}$ 为 $a$ 的任一特定 $n$ 次根，则全部根可统一写为 $\omega^k \sqrt[n]{a}$ （ $k = 0, \dots, n-1$ ）。

---

#### 1.2.3 复数形式的解析几何

一个复方程本质等价于两个实方程；若某复方程在复共轭变换下保持不变，则它代表单一的实轨迹方程。

| 几何对象 | 复数方程 / 判别条件 | 关键说明 |
| :--- | :--- | :--- |
| **圆周与圆盘** | $\lvert z - a \rvert = r \iff (z-a)(\bar{z}-\bar{a}) = r^2$ （ $a \in \mathbb{C}, r \gt 0$ ） | 内部为 $\lvert z - a \rvert \lt r$ |
| **有向直线** | 参数方程： $z = a + bt$ （ $b \neq 0, t \in \mathbb{R}$ ） | 方向由 $\arg b$ 确定；与 $z = a' + b't$ （ $b' \neq 0$ ）表示同一直线，当且仅当 $a' - a$ 为 $b$ 的实倍数且 $b'$ 为 $b$ 的非零实倍数 |
| **两直线关系** | 由 $z = a + bt$ 到 $z = a' + b't$ 的有向夹角为 $\arg(b'/b)$ （模 $2\pi$ ） | 平行当且仅当 $b'/b \in \mathbb{R}$ ；同向当且仅当 $b'/b \gt 0$ ；正交当且仅当 $b'/b$ 为非零纯虚数 |
| **左/右半平面** | 左半平面： $\mathop{\mathrm{Im}}\frac{z-a}{b} \gt 0$ ；右半平面： $\mathop{\mathrm{Im}}\frac{z-a}{b} \lt 0$ | 相对于有向直线 $z = a + bt$ 的定向而言，且不依赖于同向参数表示的选取 |

---

#### 1.2.4 球面表示（黎曼球面与球极平面投影）

**1. 扩充复平面（Extended Complex Plane）**

引入理想点 $\infty$ 构成 $\widehat{\mathbb{C}} = \mathbb{C} \cup \lbrace \infty \rbrace$ 。

- **运算约定**： $a + \infty = \infty + a = \infty$ （ $a \in \mathbb{C}$ ）； $b \cdot \infty = \infty \cdot b = \infty$ （ $b \neq 0$ ，含 $b = \infty$ ）； $a/0 = \infty$ （ $a \neq 0$ ）； $b/\infty = 0$ （ $b \in \mathbb{C}$ ，即 $b \neq \infty$ ）。
- **无意义运算**： $\infty + \infty$ 与 $0 \cdot \infty$ 无定义（同理 $\infty - \infty$ 、 $0/0$ 、 $\infty/\infty$ 亦无定义）。
- **几何约定**：每条直线都通过 $\infty$ ，而任何半平面均不包含 $\infty$ 。

**2. 黎曼球面与球极平面投影（Stereographic Projection）**

考虑 $\mathbb{R}^3$ 中的单位球面 $S: x_1^2 + x_2^2 + x_3^2 = 1$ （即**黎曼球面**），令复平面为 $(x_1, x_2)$ 平面（ $x_3 = 0$ ），北极 $N = (0, 0, 1)$ 对应 $\infty$ 。

正映射（ $x_3 \neq 1$ ）：

$$
z = \frac{x_1 + ix_2}{1 - x_3}
$$

逆映射（由 $|z|^2 = \frac{1 + x_3}{1 - x_3}$ 反解得，证明映射为双射）：

$$
x_1 = \frac{z + \bar{z}}{1 + |z|^2}, \qquad x_2 = \frac{z - \bar{z}}{i(1 + |z|^2)}, \qquad x_3 = \frac{|z|^2 - 1}{|z|^2 + 1}
$$

- **中心投影的几何特征**：记 $z = x + iy$ （ $x, y \in \mathbb{R}$ ），有 $(x_1, x_2, x_3 - 1) = (1 - x_3)(x, y, -1)$ （即比例关系 $x : y : (-1) = x_1 : x_2 : (x_3 - 1)$ ），说明三点 $(x, y, 0)$ 、 $(x_1, x_2, x_3)$ 与北极 $(0, 0, 1)$ 共线。
- **区域对应**：南半球（ $x_3 \lt 0$ ） $\leftrightarrow$ 单位圆盘 $|z| \lt 1$ ；赤道（ $x_3 = 0$ ） $\leftrightarrow$ 单位圆周 $|z| = 1$ ；北半球（ $x_3 \gt 0$ ） $\leftrightarrow$ 外部 $|z| \gt 1$ （含 $\infty$ ）。

**3. 定理：球面上的圆与复平面上的圆或扩充直线一一对应**

设球面 $S$ 上任一圆由平面 $\alpha_1 x_1 + \alpha_2 x_2 + \alpha_3 x_3 = \alpha_0$ （ $\alpha_1^2 + \alpha_2^2 + \alpha_3^2 = 1$ 且 $0 \le \alpha_0 \lt 1$ ）截得，代入逆映射坐标整理为：

$$
(\alpha_0 - \alpha_3)(x^2 + y^2) - 2\alpha_1 x - 2\alpha_2 y + (\alpha_0 + \alpha_3) = 0
$$

- 当 $\alpha_0 \neq \alpha_3$ （平面不过北极 $N$ ）时，方程表示复平面上的一个**圆**；
- 当 $\alpha_0 = \alpha_3$ （平面经过北极 $N$ ）时，方程表示复平面上的一条**直线**（连同 $\infty$ ）；
- 反之，任意圆或扩充直线方程均可规范化为上述形式（当 $\alpha_0 = 0$ 时法向量相差一个正负号，但对应同一球面大圆），故球面圆与扩充复平面上的广义圆存在一一对应。

**4. 球面距离（弦距 / Chordal Distance）**

定义两点 $z, z' \in \widehat{\mathbb{C}}$ 的距离 $d(z, z')$ 为其黎曼球面像之间的三维欧氏距离：

$$
d(z, z') = \frac{2|z - z'|}{\sqrt{(1 + |z|^2)(1 + |z'|^2)}}, \qquad d(z, \infty) = \frac{2}{\sqrt{1 + |z|^2}}
$$

- **延伸结论（课后习题重点）**： $z$ 与 $z'$ 对应黎曼球面上一条直径的两个端点（对径点），当且仅当 $z\overline{z'} = -1$ （并约定 $0$ 与 $\infty$ 互为对径点）。

---

### 本章核心知识脉络

- **代数基础**：域扩张 $\mathbb{R} \hookrightarrow \mathbb{C}$ $\longrightarrow$ 共轭自同构与模 $\longrightarrow$ 三角形不等式（含取等条件）与柯西不等式（极值法 / 拉格朗日恒等式）。
- **几何直观**：复平面向量与极坐标 $\longrightarrow$ 棣莫弗公式与单位根正多边形 $\longrightarrow$ 复方程解析几何。
- **拓扑完备化**：扩充复平面 $\widehat{\mathbb{C}}$ $\longrightarrow$ 黎曼球面与球极平面投影 $\longrightarrow$ 广义圆（圆与直线统一）与球面度量 $d(z, z')$ 。
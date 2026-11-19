# 《复分析》（Ahlfors 第 3 版）第 1 章：全部定理与命题的形式化证明

> [返回主页 README](./README.md)

本文档将《复分析》第 1 章中所有定理、命题与推论整理为严格的**公理—定义—定理—证明**体系，补全原书中“显然”“易证”等省略步骤，确保每一步推导仅依赖于前文已确立的公理、定义或定理。

---

## 1.1 复数代数

### 预备公理：实数系 $\mathbb{R}$ 的基本公理

假设实数系 $(\mathbb{R}, +, \cdot, \mathbb{R}^+)$ 满足以下三组公理：

1. **域公理**： $(\mathbb{R}, +, \cdot)$ 满足加法与乘法的封闭性、结合律、交换律、乘法对加法的分配律；存在加法中性元 $0$ 与乘法中性元 $1$ （ $1 \neq 0$ ）；对任意 $\alpha, \beta \in \mathbb{R}$ ，方程 $\beta + x = \alpha$ 有解，且当 $\beta \neq 0$ 时方程 $\beta x = \alpha$ 有解。
2. **有序公理**：存在子集 $\mathbb{R}^+ \subset \mathbb{R}$ 满足：（i） $0 \notin \mathbb{R}^+$ ；（ii）对任意 $\alpha \in \mathbb{R} \setminus \lbrace 0 \rbrace$ ， $\alpha \in \mathbb{R}^+$ 与 $-\alpha \in \mathbb{R}^+$ 恰有一者成立；（iii）若 $\alpha, \beta \in \mathbb{R}^+$ ，则 $\alpha + \beta \in \mathbb{R}^+$ 且 $\alpha \beta \in \mathbb{R}^+$ 。定义 $\alpha \lt \beta \iff \beta - \alpha \in \mathbb{R}^+$ ， $\beta \gt \alpha \iff \alpha \lt \beta$ ， $\alpha \le \beta \iff (\alpha \lt \beta \lor \alpha = \beta)$ ， $\beta \ge \alpha \iff \alpha \le \beta$ 。
3. **完备性公理**：任意单调递增且有上界的实数序列必收敛于某一实数极限（由此可推出任意非负实数存在唯一非负算术平方根及 $n$ 次算术根）。

---

### 命题 1.1（域与有序域的基本性质）

设 $F$ 为任意域，则：

1. 加法中性元 $0$ 、乘法中性元 $1$ 、减法与非零除法方程的解（特别地，任意元素的加法逆元与非零元素的乘法逆元）均唯一；
2. $F$ 为整环，即 $\forall \alpha, \beta \in F$ ， $\alpha\beta = 0 \iff (\alpha = 0 \lor \beta = 0)$ ；
3. 在有序域 $\mathbb{R}$ 中， $\forall \alpha \in \mathbb{R}$ ， $\alpha^2 \ge 0$ ，且等号成立当且仅当 $\alpha = 0$ ；特别地， $1 = 1^2 \gt 0$ ，方程 $x^2 + 1 = 0$ 在 $\mathbb{R}$ 中无解。

**证明**：

**(1) 唯一性**

- 若 $0, 0' \in F$ 均为加法中性元，则由中性元定义与加法交换律得 $0 = 0 + 0' = 0' + 0 = 0'$ 。乘法中性元同理： $1 = 1 \cdot 1' = 1' \cdot 1 = 1'$ 。
- 对任意 $\alpha, \beta \in F$ ，若 $x_1, x_2 \in F$ 满足 $\beta + x_1 = \alpha$ 且 $\beta + x_2 = \alpha$ ，由域公理知方程 $\beta + y = 0$ 有解，记其一解为 $-\beta$ （由加法交换律有 $(-\beta) + \beta = \beta + (-\beta) = 0$ ），两侧左加 $-\beta$ 并用结合律得：

$$
x_1 = 0 + x_1 = ((-\beta) + \beta) + x_1 = (-\beta) + (\beta + x_1) = (-\beta) + (\beta + x_2) = ((-\beta) + \beta) + x_2 = 0 + x_2 = x_2
$$

- 若 $\beta \neq 0$ 且 $\beta x_1 = \alpha, \beta x_2 = \alpha$ ，由域公理知方程 $\beta y = 1$ 有解，记其一解为 $\beta^{-1}$ （由乘法交换律有 $\beta^{-1}\beta = \beta\beta^{-1} = 1$ ），两侧左乘 $\beta^{-1}$ 并用结合律得：

$$
x_1 = 1 \cdot x_1 = (\beta^{-1}\beta)x_1 = \beta^{-1}(\beta x_1) = \beta^{-1}(\beta x_2) = (\beta^{-1}\beta)x_2 = 1 \cdot x_2 = x_2
$$

- 特别地，取 $\alpha = 0$ 与 $\alpha = 1$ 即得加法逆元 $-\beta$ 与非零元素乘法逆元 $\beta^{-1}$ 的唯一性。

**(2) 整环性质**

- 先证 $\forall \alpha \in F, \alpha \cdot 0 = 0 \cdot \alpha = 0$ ：由分配律 $\alpha \cdot 0 = \alpha \cdot (0 + 0) = \alpha \cdot 0 + \alpha \cdot 0$ ，两侧加 $-(\alpha \cdot 0)$ 即得 $0 = \alpha \cdot 0$ ，再由交换律得 $0 \cdot \alpha = 0$ 。故 $(\alpha = 0 \lor \beta = 0) \implies \alpha\beta = 0$ 。
- 反之，设 $\alpha\beta = 0$ 。若 $\alpha = 0$ ，结论成立；若 $\alpha \neq 0$ ，则存在 $\alpha^{-1} \in F$ ，于是 $\beta = 1 \cdot \beta = (\alpha^{-1}\alpha)\beta = \alpha^{-1}(\alpha\beta) = \alpha^{-1}\cdot 0 = 0$ 。

**(3) 有序域平方非负性**

- 若 $\alpha = 0$ ，则 $\alpha^2 = 0$ 。
- 若 $\alpha \neq 0$ ，由有序公理（ii），必有 $\alpha \in \mathbb{R}^+$ 或 $-\alpha \in \mathbb{R}^+$ 。若 $\alpha \in \mathbb{R}^+$ ，由（iii）得 $\alpha^2 = \alpha \cdot \alpha \in \mathbb{R}^+$ ；若 $-\alpha \in \mathbb{R}^+$ ，由分配律与交换律得 $(-\alpha)\alpha + \alpha^2 = (-\alpha + \alpha)\alpha = 0$ 且 $(-\alpha)\alpha + (-\alpha)(-\alpha) = (-\alpha)(\alpha + (-\alpha)) = (-\alpha)\cdot 0 = 0$ ，由（1）中加法逆元的唯一性即得 $(-\alpha)(-\alpha) = \alpha^2$ ，再由（iii）仍有 $\alpha^2 \in \mathbb{R}^+$ 。
- 故对一切 $\alpha \in \mathbb{R}$ 有 $\alpha^2 \ge 0$ ，且等号成立当且仅当 $\alpha = 0$ 。因 $1 \neq 0$ ，得 $1 = 1^2 \in \mathbb{R}^+$ 。
- 对任意 $x \in \mathbb{R}$ ：若 $x = 0$ ，则 $x^2 + 1 = 1 \in \mathbb{R}^+$ ；若 $x \neq 0$ ，则 $x^2 \in \mathbb{R}^+$ 且 $1 \in \mathbb{R}^+$ ，由公理（iii）得 $x^2 + 1 \in \mathbb{R}^+$ 。因 $0 \notin \mathbb{R}^+$ ，故恒有 $x^2 + 1 \neq 0$ 。 $\blacksquare$

---

### 定理 1.2（复数域的存在性构造）

存在一个域 $\mathbb{C}$ ，它包含一个与 $\mathbb{R}$ 同构的子域 $\mathbb{R} _ 0$ ，且方程 $x^2 + 1 = 0$ 在 $\mathbb{C}$ 中有解。

**证明**：

令集合 $\mathbb{C} = \mathbb{R} \times \mathbb{R} = \lbrace (\alpha, \beta) \mid \alpha, \beta \in \mathbb{R} \rbrace$ 。在 $\mathbb{C}$ 上定义二元运算“ $+$ ”与“ $\cdot$ ”如下：对任意 $(\alpha, \beta), (\gamma, \delta) \in \mathbb{C}$ ，

$$
(\alpha, \beta) + (\gamma, \delta) := (\alpha + \gamma, \beta + \delta)
$$

$$
(\alpha, \beta) \cdot (\gamma, \delta) := (\alpha\gamma - \beta\delta, \alpha\delta + \beta\gamma)
$$

**第一步：验证 $(\mathbb{C}, +, \cdot)$ 满足全部域公理**。设 $u = (\alpha, \beta), v = (\gamma, \delta), w = (\xi, \eta) \in \mathbb{C}$ 。

- **封闭性**：因 $\mathbb{R}$ 对加减乘封闭，运算结果均属于 $\mathbb{C}$ 。
- **加法交换律与结合律**：直接由 $\mathbb{R}$ 的加法交换律与结合律逐分量验证成立。
- **加法中性元与逆元**：令 $0 _ {\mathbb{C}} := (0, 0)$ ，则 $(\alpha, \beta) + (0, 0) = (\alpha, \beta)$ 。对任意 $u = (\alpha, \beta)$ ，令 $-u := (-\alpha, -\beta)$ ，则 $u + (-u) = (0, 0)$ ，故方程 $v + x = u$ 有解 $x = u + (-v)$ 。
- **乘法交换律**：

$$
u \cdot v = (\alpha\gamma - \beta\delta, \alpha\delta + \beta\gamma) = (\gamma\alpha - \delta\beta, \gamma\beta + \delta\alpha) = v \cdot u
$$

- **乘法结合律**：

$$
\begin{aligned}
(u \cdot v) \cdot w &= (\alpha\gamma - \beta\delta, \alpha\delta + \beta\gamma) \cdot (\xi, \eta) \cr
&= ((\alpha\gamma - \beta\delta)\xi - (\alpha\delta + \beta\gamma)\eta, \quad (\alpha\gamma - \beta\delta)\eta + (\alpha\delta + \beta\gamma)\xi) \cr
&= (\alpha\gamma\xi - \beta\delta\xi - \alpha\delta\eta - \beta\gamma\eta, \quad \alpha\gamma\eta - \beta\delta\eta + \alpha\delta\xi + \beta\gamma\xi) \cr
&= (\alpha(\gamma\xi - \delta\eta) - \beta(\gamma\eta + \delta\xi), \quad \alpha(\gamma\eta + \delta\xi) + \beta(\gamma\xi - \delta\eta)) \cr
&= (\alpha, \beta) \cdot (\gamma\xi - \delta\eta, \gamma\eta + \delta\xi) = u \cdot (v \cdot w)
\end{aligned}
$$

- **分配律**：

$$
\begin{aligned}
u \cdot (v + w) &= (\alpha, \beta) \cdot (\gamma + \xi, \delta + \eta) \cr
&= (\alpha(\gamma + \xi) - \beta(\delta + \eta), \quad \alpha(\delta + \eta) + \beta(\gamma + \xi)) \cr
&= (\alpha\gamma - \beta\delta, \alpha\delta + \beta\gamma) + (\alpha\xi - \beta\eta, \alpha\eta + \beta\xi) = u \cdot v + u \cdot w
\end{aligned}
$$

- **乘法中性元**：令 $1 _ {\mathbb{C}} := (1, 0) \neq (0, 0)$ （因 $\mathbb{R}$ 中 $1 \neq 0$ ），则 $(\alpha, \beta) \cdot (1, 0) = (\alpha \cdot 1 - \beta \cdot 0, \alpha \cdot 0 + \beta \cdot 1) = (\alpha, \beta)$ 。
- **非零元素的乘法逆元**：设 $v = (\gamma, \delta) \neq (0, 0)$ ，即 $\gamma \neq 0$ 或 $\delta \neq 0$ 。由命题 1.1(3) 知 $\gamma^2 \ge 0, \delta^2 \ge 0$ 且至少有一项严格大于 $0$ ，故 $\gamma^2 + \delta^2 \gt 0$ ，从而 $\gamma^2 + \delta^2 \neq 0$ 。令

$$
v^{-1} := \left(\frac{\gamma}{\gamma^2 + \delta^2}, \frac{-\delta}{\gamma^2 + \delta^2}\right) \in \mathbb{C}
$$

直接计算得：

$$
v \cdot v^{-1} = \left(\frac{\gamma^2 + \delta^2}{\gamma^2 + \delta^2}, \frac{-\gamma\delta + \delta\gamma}{\gamma^2 + \delta^2}\right) = (1, 0) = 1 _ {\mathbb{C}}
$$

从而对任意 $u \in \mathbb{C}$ ，方程 $v \cdot x = u$ 有解 $x = u \cdot v^{-1}$ 。

**第二步：验证嵌入同构与虚数单位的存在**。

定义映射 $\iota: \mathbb{R} \to \mathbb{C}$ 为 $\iota(\alpha) = (\alpha, 0)$ ，记其像为 $\mathbb{R} _ 0 = \lbrace (\alpha, 0) \mid \alpha \in \mathbb{R} \rbrace$ 。

- 单射性： $\iota(\alpha) = \iota(\beta) \implies (\alpha, 0) = (\beta, 0) \implies \alpha = \beta$ 。
- 保运算与子域封闭性： $\iota(0) = 0 _ {\mathbb{C}}$ ， $\iota(1) = 1 _ {\mathbb{C}}$ ， $\iota(\alpha + \beta) = (\alpha + \beta, 0) = \iota(\alpha) + \iota(\beta)$ ， $\iota(\alpha\beta) = (\alpha\beta, 0) = (\alpha, 0)\cdot(\beta, 0) = \iota(\alpha)\cdot\iota(\beta)$ ， $-\iota(\alpha) = \iota(-\alpha) \in \mathbb{R} _ 0$ ，且对非零 $\alpha \in \mathbb{R}$ 有 $\iota(\alpha)^{-1} = \iota(\alpha^{-1}) \in \mathbb{R} _ 0$ 。

故 $\mathbb{R} _ 0$ 是 $\mathbb{C}$ 的子域且 $\mathbb{R} \cong \mathbb{R} _ 0$ 。令 $i := (0, 1) \in \mathbb{C}$ ，计算得：

$$
i^2 + 1 _ {\mathbb{C}} = (0, 1)\cdot(0, 1) + (1, 0) = (-1, 0) + (1, 0) = (0, 0) = 0 _ {\mathbb{C}}
$$

且任意元素 $(\alpha, \beta) = (\alpha, 0) + (\beta, 0)(0, 1) = \iota(\alpha) + \iota(\beta)i$ 。在将 $\iota(\alpha)$ 与 $\alpha$ 认同后，记为 $\alpha + i\beta$ 。 $\blacksquare$

---

### 定理 1.3（复数域在同构意义下的唯一性）

设 $F$ 是包含 $\mathbb{R}$ 为子域且存在 $i \in F$ 满足 $i^2 + 1 = 0$ 的任意域，定义子集 $C := \lbrace \alpha + i\beta \mid \alpha, \beta \in \mathbb{R} \rbrace \subset F$ 。则：

1. 方程 $x^2 + 1 = 0$ 在 $F$ 中恰有两个解 $i$ 与 $-i$ ；
2. $C$ 中每个元素的 $\alpha + i\beta$ 表示唯一；
3. $C$ 是 $F$ 的子域；
4. 若 $F'$ 为另一包含 $\mathbb{R}$ 且含 $x^2 + 1 = 0$ 的根 $i'$ 的域，相应子集 $C' := \lbrace \alpha + i'\beta \mid \alpha, \beta \in \mathbb{R} \rbrace$ ，则 $C \cong C'$ （固定 $\mathbb{R}$ 的域同构）。

**证明**：

**(1)** 在 $F$ 中对任意 $x \in F$ ，因 $i^2 = -1$ ，由分配律与交换律得：

$$
x^2 + 1 = x^2 - i^2 = (x + i)(x - i)
$$

由命题 1.1(2) 知 $F$ 为整环，故 $x^2 + 1 = 0 \iff x + i = 0 \lor x - i = 0 \iff x = -i \lor x = i$ 。又若 $i = -i$ ，则 $2i = 0$ ，因 $2 = 1 + 1 \in \mathbb{R}^+$ 故 $2 \neq 0$ ，从而 $i = 0$ ，与 $0^2 + 1 = 1 \neq 0$ 矛盾，因此 $i \neq -i$ 。

**(2)** 设 $\alpha, \beta, \alpha', \beta' \in \mathbb{R}$ 满足 $\alpha + i\beta = \alpha' + i\beta'$ ，则 $\alpha - \alpha' = -i(\beta - \beta')$ 。两边平方并使用 $(-i)^2 = i^2 = -1$ 得：

$$
(\alpha - \alpha')^2 = (-i)^2(\beta - \beta')^2 = -(\beta - \beta')^2 \implies (\alpha - \alpha')^2 + (\beta - \beta')^2 = 0
$$

因 $\alpha - \alpha', \beta - \beta' \in \mathbb{R}$ ，由命题 1.1(3) 知两平方项均非负，故必同时为零，即 $\alpha = \alpha'$ 且 $\beta = \beta'$ 。

**(3)** $C$ 继承 $F$ 的结合律、交换律、分配律，且 $0 = 0 + i0 \in C$ ， $1 = 1 + i0 \in C$ 。由定义直接验证对加、减、乘封闭： $(\alpha + i\beta) \pm (\gamma + i\delta) = (\alpha \pm \gamma) + i(\beta \pm \delta) \in C$ ， $(\alpha + i\beta)(\gamma + i\delta) = (\alpha\gamma - \beta\delta) + i(\alpha\delta + \beta\gamma) \in C$ 。对非零元 $\gamma + i\delta \in C$ ，由（2）知 $\gamma, \delta$ 不全为零，故 $\gamma^2 + \delta^2 \gt 0$ ，直接乘积验证知 $\frac{\gamma}{\gamma^2+\delta^2} + i\frac{-\delta}{\gamma^2+\delta^2} \in C$ 为其乘法逆元。故 $C$ 为 $F$ 的子域。

**(4)** 定义映射 $\varphi: C \to C'$ 为 $\varphi(\alpha + i\beta) := \alpha + i'\beta$ 。由（2）的表示唯一性知 $\varphi$ 良定义且为单射；显然满射，且对一切 $\alpha \in \mathbb{R}$ 有 $\varphi(\alpha) = \alpha$ 。进一步，对任意 $z_1 = \alpha + i\beta, z_2 = \gamma + i\delta \in C$ ：

$$
\varphi(z_1 + z_2) = (\alpha + \gamma) + i'(\beta + \delta) = \varphi(z_1) + \varphi(z_2)
$$

$$
\varphi(z_1 z_2) = (\alpha\gamma - \beta\delta) + i'(\alpha\delta + \beta\gamma) = (\alpha + i'\beta)(\gamma + i'\delta) = \varphi(z_1)\varphi(z_2)
$$

故 $\varphi$ 是固定 $\mathbb{R}$ 的域同构， $C \cong C'$ 。 $\blacksquare$

---

### 定理 1.4（复数除法的存在唯一性与显式公式）

对任意 $\alpha, \beta, \gamma, \delta \in \mathbb{R}$ ，若 $\gamma + i\delta \neq 0$ ，则存在唯一的复数 $x + iy$ （ $x, y \in \mathbb{R}$ ）满足 $(\gamma + i\delta)(x + iy) = \alpha + i\beta$ ，且：

$$
\frac{\alpha + i\beta}{\gamma + i\delta} = \frac{\alpha\gamma + \beta\delta}{\gamma^2 + \delta^2} + i\frac{\beta\gamma - \alpha\delta}{\gamma^2 + \delta^2}
$$

**证明**：

由复数乘法定义与表示唯一性（定理 1.3(2)），复方程 $(\gamma + i\delta)(x + iy) = \alpha + i\beta$ 等价于实数二元一次线性方程组：

$$
\begin{cases}
\gamma x - \delta y = \alpha & (1) \cr
\delta x + \gamma y = \beta & (2)
\end{cases}
$$

因 $\gamma + i\delta \neq 0$ ，故 $\gamma, \delta$ 不全为零，从而由命题 1.1(3) 得 $\gamma^2 + \delta^2 \gt 0$ 。

- **必要性（唯一性）**：将 $(1) \times \gamma + (2) \times \delta$ 得 $(\gamma^2 + \delta^2)x = \alpha\gamma + \beta\delta$ ；将 $(2) \times \gamma - (1) \times \delta$ 得 $(\gamma^2 + \delta^2)y = \beta\gamma - \alpha\delta$ 。除以非零数 $\gamma^2 + \delta^2$ ，得唯一候选解：

$$
x = \frac{\alpha\gamma + \beta\delta}{\gamma^2 + \delta^2}, \qquad y = \frac{\beta\gamma - \alpha\delta}{\gamma^2 + \delta^2}
$$

- **充分性（存在性）**：直接将上述 $x, y$ 代入 $(1), (2)$ 左端验证：

$$
\gamma x - \delta y = \frac{\alpha\gamma^2 + \beta\gamma\delta - \beta\gamma\delta + \alpha\delta^2}{\gamma^2 + \delta^2} = \alpha, \qquad \delta x + \gamma y = \frac{\alpha\gamma\delta + \beta\delta^2 + \beta\gamma^2 - \alpha\gamma\delta}{\gamma^2 + \delta^2} = \beta
$$

故该解满足原方程。 $\blacksquare$

---

### 定理 1.5（复数平方根的存在性与显式公式）

对任意复数 $c = \alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ），方程 $z^2 = c$ 在 $\mathbb{C}$ 中必有解，且：

1. 若 $c = 0$ ，方程有唯一解 $z = 0$ ；
2. 若 $c \neq 0$ ，方程恰有两个互为相反数的解 $z_1, z_2$ （ $z_2 = -z_1 \neq z_1$ ）：
   - 当 $\beta = 0, \alpha \gt 0$ 时， $z = \pm \sqrt{\alpha}$ ；
   - 当 $\beta = 0, \alpha \lt 0$ 时， $z = \pm i\sqrt{-\alpha}$ ；
   - 当 $\beta \neq 0$ 时，解由下式给出（其中所有根号均指非负实数的非负算术平方根）：

$$
z = \pm \left[ \sqrt{\frac{\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} + i\frac{\beta}{|\beta|}\sqrt{\frac{-\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} \right]
$$

**证明**：

设 $z = x + iy$ （ $x, y \in \mathbb{R}$ ）。方程 $z^2 = \alpha + i\beta$ 等价于：

$$
\begin{cases}
x^2 - y^2 = \alpha & (1) \cr
2xy = \beta & (2)
\end{cases}
$$

**情形 1**： $c = 0$ （即 $\alpha = \beta = 0$ ）。由 $\mathbb{C}$ 为整环（命题 1.1(2)）， $z^2 = 0 \iff z = 0$ ，唯一解。

**情形 2**： $c \neq 0$ 。若 $z_0$ 为一解，则方程等价于 $z^2 - z_0^2 = (z - z_0)(z + z_0) = 0$ ，由整环性质知全部解必为 $\pm z_0$ ；且因 $z_0^2 = c \neq 0$ 知 $z_0 \neq 0$ ，从而 $2z_0 \neq 0$ ，故 $z_0 \neq -z_0$ 。现求具体解：

**子情形 2a（ $\beta = 0$ ）**：由 $(2)$ 得 $x = 0$ 或 $y = 0$ 。

- 若 $\alpha \gt 0$ ，则由 $(1)$ ， $x = 0$ 导致 $-y^2 = \alpha \gt 0$ 矛盾，故 $y = 0$ 且 $x^2 = \alpha$ ，解为 $z = \pm \sqrt{\alpha}$ 。
- 若 $\alpha \lt 0$ ，则由 $(1)$ ， $y = 0$ 导致 $x^2 = \alpha \lt 0$ 矛盾，故 $x = 0$ 且 $y^2 = -\alpha$ ，解为 $z = \pm i\sqrt{-\alpha}$ 。

**子情形 2b（ $\beta \neq 0$ ）**：

- **必要性**：由 $(1)$ 与 $(2)$ 得：

$$
(x^2 + y^2)^2 = (x^2 - y^2)^2 + 4x^2y^2 = \alpha^2 + \beta^2
$$

因 $x^2 + y^2 \ge 0$ ，开非负平方根得 $x^2 + y^2 = \sqrt{\alpha^2 + \beta^2}$ 。与 $(1)$ 相加减得：

$$
x^2 = \frac{\alpha + \sqrt{\alpha^2 + \beta^2}}{2}, \qquad y^2 = \frac{-\alpha + \sqrt{\alpha^2 + \beta^2}}{2}
$$

因 $\beta \neq 0$ ，有 $\sqrt{\alpha^2 + \beta^2} \gt |\alpha|$ ，从而 $\alpha + \sqrt{\alpha^2 + \beta^2} \gt 0$ 且 $-\alpha + \sqrt{\alpha^2 + \beta^2} \gt 0$ 。记正实数 $u := \sqrt{\frac{\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} \gt 0$ ， $v := \sqrt{\frac{-\alpha + \sqrt{\alpha^2 + \beta^2}}{2}} \gt 0$ ，则 $x = \varepsilon_1 u, y = \varepsilon_2 v$ （ $\varepsilon_1, \varepsilon_2 \in \lbrace 1, -1 \rbrace$ ）。再由 $(2)$ ， $2\varepsilon_1 \varepsilon_2 uv = \beta$ ，因 $2uv \gt 0$ ，必有 $\varepsilon_1 \varepsilon_2 = \frac{\beta}{|\beta|}$ ，即 $\varepsilon_2 = \varepsilon_1 \frac{\beta}{|\beta|}$ ，故 $z = \varepsilon_1\left(u + i\frac{\beta}{|\beta|}v\right)$ 。

- **充分性**：对任意 $\varepsilon \in \lbrace 1, -1 \rbrace$ ，取 $z = \varepsilon\left(u + i\frac{\beta}{|\beta|}v\right)$ ，因 $\varepsilon^2 = 1$ 且 $\left(\frac{\beta}{|\beta|}\right)^2 = 1$ ，直接验证：

$$
(\varepsilon u)^2 - \left(\varepsilon\frac{\beta}{|\beta|}v\right)^2 = u^2 - v^2 = \frac{\alpha + \sqrt{\alpha^2 + \beta^2}}{2} - \frac{-\alpha + \sqrt{\alpha^2 + \beta^2}}{2} = \alpha
$$

$$
2(\varepsilon u)\left(\varepsilon \frac{\beta}{|\beta|}v\right) = 2\frac{\beta}{|\beta|}\sqrt{\frac{(\alpha^2 + \beta^2) - \alpha^2}{4}} = \frac{\beta}{|\beta|}|\beta| = \beta
$$

故满足 $(1)$ 和 $(2)$ ，确为方程的解；又因 $u \gt 0$ ， $\varepsilon = 1$ 与 $\varepsilon = -1$ 给出两个互为相反数的不同解。 $\blacksquare$

---

### 定理 1.6（复共轭的自同构性质与实系数方程共轭根定理）

对 $a = \alpha + i\beta \in \mathbb{C}$ （ $\alpha, \beta \in \mathbb{R}$ ），定义共轭 $\bar{a} := \alpha - i\beta$ 。则对任意 $a, b \in \mathbb{C}$ ：

1. $\overline{\bar{a}} = a$ （对合性）；
2. $a \in \mathbb{R} \iff \bar{a} = a$ ，且 $\mathop{\mathrm{Re}} a = \frac{a + \bar{a}}{2}$ ， $\mathop{\mathrm{Im}} a = \frac{a - \bar{a}}{2i}$ ；
3. $\overline{a + b} = \bar{a} + \bar{b}$ ， $\overline{ab} = \bar{a}\bar{b}$ ；若 $a \neq 0$ ，则 $\overline{(b/a)} = \bar{b}/\bar{a}$ ；
4. 对任意仅由变元 $a_1, \dots, a_m$ 及实常数经有限次加、减、乘、除构成的有理运算表达式 $R(a_1, \dots, a_m)$ （分母非零），有 $\overline{R(a_1, \dots, a_m)} = R(\overline{a_1}, \dots, \overline{a_m})$ ；
5. **推论（共轭根定理）**：若 $z_0$ 是方程 $\sum _ {k=0}^n c_k z^{n-k} = 0$ 的根，则 $\overline{z_0}$ 是方程 $\sum _ {k=0}^n \overline{c_k} z^{n-k} = 0$ 的根。特别地，若 $\forall k, c_k \in \mathbb{R}$ ，则非实根成对共轭出现。

**证明**：

设 $a = \alpha + i\beta, b = \gamma + i\delta$ （ $\alpha, \beta, \gamma, \delta \in \mathbb{R}$ ）。

**(1)** $\overline{\bar{a}} = \overline{\alpha - i\beta} = \alpha - i(-\beta) = \alpha + i\beta = a$ 。

**(2)** $\bar{a} = a \iff \alpha - i\beta = \alpha + i\beta \iff -\beta = \beta \iff \beta = 0 \iff a \in \mathbb{R}$ 。又 $a + \bar{a} = 2\alpha$ ， $a - \bar{a} = 2i\beta$ ，两侧分别除以 $2$ 与 $2i$ 即得实部、虚部公式。

**(3)** 直接验证：

$$
\overline{a + b} = \overline{(\alpha + \gamma) + i(\beta + \delta)} = (\alpha + \gamma) - i(\beta + \delta) = (\alpha - i\beta) + (\gamma - i\delta) = \bar{a} + \bar{b}
$$

$$
\overline{ab} = \overline{(\alpha\gamma - \beta\delta) + i(\alpha\delta + \beta\gamma)} = (\alpha\gamma - \beta\delta) - i(\alpha\delta + \beta\gamma) = (\alpha - i\beta)(\gamma - i\delta) = \bar{a}\bar{b}
$$

对减法：因 $\overline{-b} = \overline{(-1)b} = \overline{-1}\cdot\bar{b} = (-1)\bar{b} = -\bar{b}$ ，故 $\overline{a - b} = \bar{a} - \bar{b}$ 。
对除法：设 $a \neq 0$ 且 $x = b/a$ ，即 $ax = b$ 。两边取共轭得 $\bar{a}\bar{x} = \bar{b}$ 。若 $\bar{a} = 0$ 则 $a = \overline{\bar{a}} = 0$ 矛盾，故 $\bar{a} \neq 0$ ，于是 $\bar{x} = \bar{b}/\bar{a}$ 。

**(4)** 任一此类有理运算 $R(a_1, \dots, a_m)$ 由变元及实常数经有限次加、减、乘、除（步数记为 $N$ ）构造而成。对步数 $N$ 施数学归纳法： $N = 0$ 时表达式为某个 $a_j$ 或实常数 $r \in \mathbb{R}$ （由（2）知 $\bar{r} = r$ ），结论成立；设步数小于 $N$ 时成立，若第 $N$ 步为四则运算之一，则由（3）立即推出第 $N$ 步成立。

**(5)** 将 $\sum _ {k=0}^n c_k z_0^{n-k}$ 视为关于 $n + 2$ 个变元 $(c_0, \dots, c_n, z_0)$ 的有理运算，对等式 $\sum _ {k=0}^n c_k z_0^{n-k} = 0$ 两边取共轭，由（4）及 $\bar{0} = 0$ 得 $\sum _ {k=0}^n \overline{c_k} (\overline{z_0})^{n-k} = 0$ 。当 $c_k \in \mathbb{R}$ 时由（2）有 $\overline{c_k} = c_k$ ，故 $\overline{z_0}$ 亦为原方程的根；若 $z_0 \notin \mathbb{R}$ ，由（2）知 $\overline{z_0} \neq z_0$ ，成对出现。 $\blacksquare$

---

### 定理 1.7（绝对值/模的基本性质与平行四边形恒等式）

对任意 $a = \alpha + i\beta \in \mathbb{C}$ （ $\alpha, \beta \in \mathbb{R}$ ），因 $a\bar{a} = \alpha^2 + \beta^2 \ge 0$ ，定义绝对值（模） $|a| := \sqrt{a\bar{a}} = \sqrt{\alpha^2 + \beta^2} \ge 0$ 。则对任意 $a, b, a_1, \dots, a_n \in \mathbb{C}$ ：

1. $|a| = 0 \iff a = 0$ ，且 $|\bar{a}| = |a|$ ；
2. $|ab| = |a| \cdot |b|$ ，且 $\left\lvert \prod _ {k=1}^n a_k \right\rvert = \prod _ {k=1}^n |a_k|$ ；
3. 若 $b \neq 0$ ，则 $\left\lvert \frac{a}{b} \right\rvert = \frac{|a|}{|b|}$ ；
4. $|a + b|^2 = |a|^2 + |b|^2 + 2\mathop{\mathrm{Re}}(a\bar{b})$ ， $|a - b|^2 = |a|^2 + |b|^2 - 2\mathop{\mathrm{Re}}(a\bar{b})$ ；
5. **平行四边形恒等式**： $|a + b|^2 + |a - b|^2 = 2(|a|^2 + |b|^2)$ 。

**证明**：

**(1)** $|a| = 0 \iff \alpha^2 + \beta^2 = 0 \iff \alpha = \beta = 0 \iff a = 0$ 。又 $|\bar{a}| = \sqrt{\bar{a}\overline{\bar{a}}} = \sqrt{\bar{a}a} = |a|$ 。

**(2)** 利用定理 1.6(3)：

$$
|ab|^2 = (ab)\overline{(ab)} = (ab)(\bar{a}\bar{b}) = (a\bar{a})(b\bar{b}) = |a|^2 |b|^2 = (|a|\cdot|b|)^2
$$

因 $|ab| \ge 0$ 且 $|a|\cdot|b| \ge 0$ ，开非负平方根得 $|ab| = |a|\cdot|b|$ 。一般有限项情形对 $n$ 施数学归纳法： $n = 1$ 平凡；若对 $n - 1$ 成立，则 $|a_1 \cdots a_n| = |(a_1 \cdots a _ {n-1}) a_n| = |a_1 \cdots a _ {n-1}| \cdot |a_n| = \prod _ {k=1}^n |a_k|$ 。

**(3)** 若 $b \neq 0$ ，则 $b \cdot (a/b) = a$ ，由（2）得 $|b| \cdot |a/b| = |a|$ 。因 $|b| \gt 0$ ，两侧除以 $|b|$ 即得。

**(4)** 利用定理 1.6(2)(3) 与 $\overline{a\bar{b}} = \bar{a}b = b\bar{a}$ ：

$$
|a + b|^2 = (a + b)\overline{(a + b)} = (a + b)(\bar{a} + \bar{b}) = a\bar{a} + (a\bar{b} + \overline{a\bar{b}}) + b\bar{b} = |a|^2 + |b|^2 + 2\mathop{\mathrm{Re}}(a\bar{b})
$$

以 $-b$ 代替 $b$ 并注意到 $|-b| = |-1|\cdot|b| = |b|$ 及 $\mathop{\mathrm{Re}}(a\overline{(-b)}) = \mathop{\mathrm{Re}}(-a\bar{b}) = -\mathop{\mathrm{Re}}(a\bar{b})$ ，即得差式。

**(5)** 将（4）中的两式左右分别相加， $2\mathop{\mathrm{Re}}(a\bar{b})$ 项抵消，立得 $|a + b|^2 + |a - b|^2 = 2(|a|^2 + |b|^2)$ 。 $\blacksquare$

---

### 引理 1.8（实部与虚部的模界估计）

对任意 $a \in \mathbb{C}$ ，有：

$$
-|a| \le \mathop{\mathrm{Re}} a \le |a|, \qquad -|a| \le \mathop{\mathrm{Im}} a \le |a|
$$

且 $\mathop{\mathrm{Re}} a = |a| \iff (a \in \mathbb{R} \land a \ge 0)$ 。

**证明**：

设 $a = \alpha + i\beta$ （ $\alpha, \beta \in \mathbb{R}$ ）。由命题 1.1(3) 知 $\beta^2 \ge 0$ ，故 $\alpha^2 \le \alpha^2 + \beta^2 = |a|^2$ ，开方得 $|\alpha| \le |a|$ ，即 $-|a| \le \mathop{\mathrm{Re}} a \le |a|$ 。同理 $\beta^2 \le |a|^2$ 得 $-|a| \le \mathop{\mathrm{Im}} a \le |a|$ 。

现证取等条件：

- **充分性（ $\Leftarrow$ ）**：若 $a \in \mathbb{R}$ 且 $a \ge 0$ ，则 $\beta = 0, \alpha \ge 0$ ，故 $|a| = \sqrt{\alpha^2} = \alpha = \mathop{\mathrm{Re}} a$ 。
- **必要性（ $\Rightarrow$ ）**：若 $\mathop{\mathrm{Re}} a = |a|$ ，则 $\alpha = |a| \ge 0$ ，且两边平方得 $\alpha^2 = \alpha^2 + \beta^2 \implies \beta^2 = 0 \implies \beta = 0$ ，故 $a = \alpha \in \mathbb{R}$ 且 $a \ge 0$ 。 $\blacksquare$

---

### 定理 1.9（三角形不等式及其取等充要条件）

对任意 $n \in \mathbb{Z}^+$ 及 $a_1, a_2, \dots, a_n \in \mathbb{C}$ ，有：

$$
\left\lvert \sum _ {k=1}^n a_k \right\rvert \le \sum _ {k=1}^n |a_k|
$$

等号成立当且仅当：对任意满足 $a_j \neq 0$ 且 $a_k \neq 0$ 的下标 $j, k \in \lbrace 1, \dots, n \rbrace$ ，比值 $\frac{a_j}{a_k}$ 均为正实数（即 $\frac{a_j}{a_k} \in \mathbb{R}^+$ ）。

**证明**：

**第一步：证明 $n = 2$ 的不等式与取等条件**。

对任意 $a, b \in \mathbb{C}$ ，由定理 1.7(4)、引理 1.8 及定理 1.7(1)(2) 得：

$$
|a + b|^2 = |a|^2 + |b|^2 + 2\mathop{\mathrm{Re}}(a\bar{b}) \le |a|^2 + |b|^2 + 2|a\bar{b}| = |a|^2 + |b|^2 + 2|a||b| = (|a| + |b|)^2
$$

因两边均非负，开方得 $|a + b| \le |a| + |b|$ 。上述推导中唯一不等号取等 $\iff \mathop{\mathrm{Re}}(a\bar{b}) = |a\bar{b}|$ 。由引理 1.8，这等价于 $a\bar{b} \in \mathbb{R}$ 且 $a\bar{b} \ge 0$ 。

- 若 $a = 0$ 或 $b = 0$ ，等号显然成立，且非零项至多一项（自身之比为 $1 \in \mathbb{R}^+$ ，全为零时条件空真），故比值条件成立；
- 若 $a \neq 0$ 且 $b \neq 0$ ，则 $\bar{b} \neq 0$ ，由整环性质知 $a\bar{b} \neq 0$ ，故 $a\bar{b} \ge 0 \iff a\bar{b} \in \mathbb{R}^+$ 。又 $a\bar{b} = \frac{a}{b}(b\bar{b}) = |b|^2 \frac{a}{b}$ 且 $|b|^2 \gt 0$ ，故 $a\bar{b} \in \mathbb{R}^+ \iff \frac{a}{b} \in \mathbb{R}^+$ 。

**第二步：用归纳法证明一般 $n \ge 1$ 的不等式**。

$n = 1$ 时为等式 $|a_1| = |a_1|$ 。设对 $n - 1$ 成立，则由 $n = 2$ 与归纳假设：

$$
\left\lvert \sum _ {k=1}^n a_k \right\rvert = \left\lvert \left(\sum _ {k=1}^{n-1} a_k\right) + a_n \right\rvert \le \left\lvert \sum _ {k=1}^{n-1} a_k \right\rvert + |a_n| \le \sum _ {k=1}^n |a_k|
$$

**第三步：证明一般 $n$ 的取等充要条件**。

- **必要性（ $\Rightarrow$ ）**：设 $\left\lvert \sum _ {k=1}^n a_k \right\rvert = \sum _ {k=1}^n |a_k|$ 。任取两个下标 $j, k$ 满足 $a_j \neq 0, a_k \neq 0$ 。若 $j = k$ ，则 $a_j/a_k = 1 \in \mathbb{R}^+$ 。若 $j \neq k$ ，由加法交换律可将 $a_j, a_k$ 置于前两位，记其余项之和为 $S$ （若 $n = 2$ 则 $S = 0$ 且下式中不含 $j, k$ 的求和为空和 $0$ ），利用三角不等式得：

$$
\sum _ {m=1}^n |a_m| = |(a_j + a_k) + S| \le |a_j + a_k| + |S| \le |a_j + a_k| + \sum _ {m \neq j, k} |a_m| \le |a_j| + |a_k| + \sum _ {m \neq j, k} |a_m| = \sum _ {m=1}^n |a_m|
$$

两端相等迫使所有不等号均为等号，特别有 $|a_j + a_k| = |a_j| + |a_k|$ 。由第一步知 $\frac{a_j}{a_k} \in \mathbb{R}^+$ 。

- **充分性（ $\Leftarrow$ ）**：若所有 $a_k = 0$ ，等号显然成立。否则至少有一非零项，由加法交换律不妨设 $a_1 \neq 0$ 。对每个 $k \in \lbrace 1, \dots, n \rbrace$ ，若 $a_k = 0$ 则 $\frac{a_k}{a_1} = 0 = \frac{|a_k|}{|a_1|}$ ；若 $a_k \neq 0$ ，由条件知 $\frac{a_k}{a_1} \in \mathbb{R}^+$ ，故 $\frac{a_k}{a_1} = \left\lvert \frac{a_k}{a_1} \right\rvert = \frac{|a_k|}{|a_1|} \ge 0$ 。因此 $\sum _ {k=1}^n \frac{a_k}{a_1} = \sum _ {k=1}^n \frac{|a_k|}{|a_1|} \ge 0$ ，从而：

$$
\left\lvert \sum _ {k=1}^n a_k \right\rvert = \left\lvert a_1 \sum _ {k=1}^n \frac{a_k}{a_1} \right\rvert = |a_1| \left\lvert \sum _ {k=1}^n \frac{|a_k|}{|a_1|} \right\rvert = |a_1| \sum _ {k=1}^n \frac{|a_k|}{|a_1|} = \sum _ {k=1}^n |a_k|
$$

证毕。 $\blacksquare$

---

### 推论 1.10（逆向三角形不等式与分量模估计）

对任意 $a, b \in \mathbb{C}$ 及 $\alpha, \beta \in \mathbb{R}$ ：

1. $|a - b| \ge \bigl\lvert \lvert a \rvert - \lvert b \rvert \bigr\rvert$ ，且 $|a + b| \ge \bigl\lvert \lvert a \rvert - \lvert b \rvert \bigr\rvert$ ；
2. $|\alpha + i\beta| \le |\alpha| + |\beta|$ 。

**证明**：

1. 由定理 1.9 得 $|a| = |(a - b) + b| \le |a - b| + |b|$ ，移项得 $|a| - |b| \le |a - b|$ 。交换 $a, b$ 并利用 $|b - a| = |-(a - b)| = |a - b|$ ，得 $|b| - |a| \le |a - b|$ 。两式合并即得 $\bigl\lvert \lvert a \rvert - \lvert b \rvert \bigr\rvert \le |a - b|$ 。以 $-b$ 代替 $b$ 即得 $|a + b| \ge \bigl\lvert \lvert a \rvert - \lvert b \rvert \bigr\rvert$ 。
2. 由定理 1.9 与 $|i| = 1$ ，得 $|\alpha + i\beta| \le |\alpha| + |i\beta| = |\alpha| + |i|\cdot|\beta| = |\alpha| + |\beta|$ 。 $\blacksquare$

---

### 定理 1.11（柯西不等式 / Cauchy-Schwarz 不等式及其取等条件）

对任意 $n \in \mathbb{Z}^+$ 及 $a_1, \dots, a_n, b_1, \dots, b_n \in \mathbb{C}$ ，有：

$$
\left\lvert \sum _ {k=1}^n a_k b_k \right\rvert^2 \le \left(\sum _ {k=1}^n |a_k|^2\right)\left(\sum _ {k=1}^n |b_k|^2\right)
$$

等号成立当且仅当向量 $(a_1, \dots, a_n)$ 与 $(\overline{b_1}, \dots, \overline{b_n})$ 在 $\mathbb{C}^n$ 上线性相关（即存在不全为零的复数 $\mu, \nu$ 使 $\forall k, \mu a_k + \nu \overline{b_k} = 0$ ，亦即 $\lbrace a_k \rbrace$ 与 $\lbrace \overline{b_k} \rbrace$ 成比例）。

**证明（法一：Ahlfors 极值构造法）**：

记 $A := \sum _ {k=1}^n |a_k|^2 \ge 0$ ， $B := \sum _ {k=1}^n |b_k|^2 \ge 0$ ， $S := \sum _ {k=1}^n a_k b_k \in \mathbb{C}$ 。

**情形 1（ $B = 0$ ）**：由非负实数和为零推得 $\forall k, |b_k|^2 = 0 \implies b_k = 0$ ，故 $S = 0$ ，不等式化为 $0 \le 0$ ，恒取等号；此时取 $\mu = 0, \nu = 1$ 有 $\mu a_k + \nu \overline{b_k} = 0$ ，两向量线性相关。

**情形 2（ $B \gt 0$ ）**：对任意 $\lambda \in \mathbb{C}$ ，由定理 1.7(4)、 $\overline{\lambda \overline{b_k}} = \bar{\lambda} b_k$ 以及实部运算 $\mathop{\mathrm{Re}}$ 的可加性，展开得：

$$
0 \le \sum _ {k=1}^n |a_k - \lambda \overline{b_k}|^2 = \sum _ {k=1}^n \left(|a_k|^2 + |\lambda|^2 |\overline{b_k}|^2 - 2\mathop{\mathrm{Re}}(\bar{\lambda} a_k b_k)\right) = A + |\lambda|^2 B - 2\mathop{\mathrm{Re}}(\bar{\lambda} S)
$$

选取特定值 $\lambda_0 := \frac{S}{B} \in \mathbb{C}$ 。此时 $|\lambda_0|^2 B = \frac{|S|^2}{B}$ ，且 $\overline{\lambda_0} S = \frac{\bar{S}S}{B} = \frac{|S|^2}{B} \in \mathbb{R}$ ，故 $\mathop{\mathrm{Re}}(\overline{\lambda_0} S) = \frac{|S|^2}{B}$ 。代入上式得：

$$
0 \le \sum _ {k=1}^n |a_k - \lambda_0 \overline{b_k}|^2 = A + \frac{|S|^2}{B} - \frac{2|S|^2}{B} = A - \frac{|S|^2}{B}
$$

两边同乘 $B \gt 0$ 并移项即得 $|S|^2 \le AB$ 。

**情形 2 的取等条件**： $|S|^2 = AB \iff A - \frac{|S|^2}{B} = 0 \iff \sum _ {k=1}^n |a_k - \lambda_0 \overline{b_k}|^2 = 0 \iff \forall k, a_k = \lambda_0 \overline{b_k}$ 。

- **必要性（ $\Rightarrow$ ）**：若取等，取 $\mu = 1, \nu = -\lambda_0$ 即证线性相关。
- **充分性（ $\Leftarrow$ ）**：若存在 $(\mu, \nu) \neq (0, 0)$ 使 $\forall k, \mu a_k + \nu \overline{b_k} = 0$ ，因 $B \gt 0$ 知存在 $k_0$ 使 $\overline{b _ {k_0}} \neq 0$ ，故必有 $\mu \neq 0$ （否则 $\nu\overline{b _ {k_0}} = 0 \implies \nu = 0$ 矛盾），从而 $\forall k, a_k = (-\nu/\mu)\overline{b_k}$ 。直接代入得 $S = (-\nu/\mu) B$ ， $A = |\nu/\mu|^2 B$ ，故 $|S|^2 = |\nu/\mu|^2 B^2 = AB$ ，等号成立。

**附证（法二：拉格朗日恒等式法）**：

注意到 $j = k$ 时各项为零且 $(j, k)$ 与 $(k, j)$ 项相等（当 $n = 1$ 时空和约定为 $0$ ），直接展开验证恒等式：

$$
\begin{aligned}
\sum _ {1 \le j \lt k \le n} |a_j \overline{b_k} - a_k \overline{b_j}|^2 &= \frac{1}{2} \sum _ {j=1}^n \sum _ {k=1}^n (a_j \overline{b_k} - a_k \overline{b_j})(\overline{a_j} b_k - \overline{a_k} b_j) \cr
&= \frac{1}{2} \sum _ {j=1}^n \sum _ {k=1}^n \left(|a_j|^2|b_k|^2 + |a_k|^2|b_j|^2 - a_j b_j \overline{a_k} \overline{b_k} - \overline{a_j} \overline{b_j} a_k b_k\right) \cr
&= \left(\sum _ {j=1}^n |a_j|^2\right)\left(\sum _ {k=1}^n |b_k|^2\right) - \left(\sum _ {j=1}^n a_j b_j\right)\left(\sum _ {k=1}^n \overline{a_k} \overline{b_k}\right) = AB - |S|^2
\end{aligned}
$$

因左端非负，立得 $|S|^2 \le AB$ ；且取等当且仅当 $\forall j \lt k, a_j \overline{b_k} = a_k \overline{b_j}$ ，这在代数上等价于下面 $2 \times n$ 矩阵的秩 $\le 1$ ，即两行线性相关：

$$
\begin{pmatrix}
a_1 & \cdots & a_n \cr
\overline{b_1} & \cdots & \overline{b_n}
\end{pmatrix}
$$

证毕。 $\blacksquare$

---

## 1.2 复数的几何表示

> **严密性说明**：按照 Ahlfors 的处理，本节在 1.2.1 与 1.2.2 节中暂时引用实变三角函数 $\cos\varphi, \sin\varphi$ 的标准性质（满足 $\cos^2\varphi + \sin^2\varphi = 1$ 、和角公式、周期性 $2\pi$ ，以及对任意满足 $u^2 + v^2 = 1$ 的实数对 $(u, v)$ 存在唯一 $\varphi \in [0, 2\pi)$ 使 $\cos\varphi = u, \sin\varphi = v$ ）；这些性质的纯解析证明在第 2.3 节借助复幂级数独立给出。

---

### 定理 1.12（复数的极坐标表示与乘除法幅角法则）

1. 对任意非零复数 $a \in \mathbb{C} \setminus \lbrace 0 \rbrace$ ，存在唯一的 $r = |a| \gt 0$ 与在模 $2\pi$ 意义下唯一的 $\varphi \in \mathbb{R}$ （记其等价类或值集合为 $\arg a$ ），使得 $a = r(\cos\varphi + i\sin\varphi)$ 。
2. 若 $a_k = r_k(\cos\varphi_k + i\sin\varphi_k)$ （ $r_k \gt 0, k = 1, 2$ ），则：

$$
a_1 a_2 = r_1 r_2 \left[\cos(\varphi_1 + \varphi_2) + i\sin(\varphi_1 + \varphi_2)\right]
$$

$$
\frac{a_2}{a_1} = \frac{r_2}{r_1}\left[\cos(\varphi_2 - \varphi_1) + i\sin(\varphi_2 - \varphi_1)\right]
$$

从而在模 $2\pi$ 意义下， $\arg(a_1 a_2) \equiv \arg a_1 + \arg a_2 \pmod{2\pi}$ ， $\arg(a_2 / a_1) \equiv \arg a_2 - \arg a_1 \pmod{2\pi}$ 。

**证明**：

**(1)** 设 $a = \alpha + i\beta \neq 0$ （ $\alpha, \beta \in \mathbb{R}$ ），令 $r = |a| = \sqrt{\alpha^2 + \beta^2} \gt 0$ 。则 $\left(\frac{\alpha}{r}\right)^2 + \left(\frac{\beta}{r}\right)^2 = 1$ ，故存在 $\varphi \in \mathbb{R}$ 使 $\cos\varphi = \frac{\alpha}{r}, \sin\varphi = \frac{\beta}{r}$ ，于是 $a = r(\cos\varphi + i\sin\varphi)$ 。若另有 $r' \gt 0, \varphi' \in \mathbb{R}$ 满足同一等式，取模得 $r' = r'\sqrt{\cos^2\varphi' + \sin^2\varphi'} = |a| = r$ ，进而 $\cos\varphi' = \cos\varphi$ 且 $\sin\varphi' = \sin\varphi$ 。由 $2\pi$ 周期性与 $[0, 2\pi)$ 上的唯一性可知 $\varphi' - \varphi = 2k\pi$ （ $k \in \mathbb{Z}$ ）。

**(2)** 由复数乘法及三角和角公式：

$$
\begin{aligned}
a_1 a_2 &= r_1 r_2 \left[(\cos\varphi_1\cos\varphi_2 - \sin\varphi_1\sin\varphi_2) + i(\sin\varphi_1\cos\varphi_2 + \cos\varphi_1\sin\varphi_2)\right] \cr
&= r_1 r_2 \left[\cos(\varphi_1 + \varphi_2) + i\sin(\varphi_1 + \varphi_2)\right]
\end{aligned}
$$

特别地，对 $a_1^{-1}$ ，由刚证的乘法公式知 $r_1^{-1}(\cos(-\varphi_1) + i\sin(-\varphi_1)) \cdot a_1 = 1\cdot(\cos 0 + i\sin 0) = 1$ ，故 $a_1^{-1} = r_1^{-1}(\cos(-\varphi_1) + i\sin(-\varphi_1))$ 。将 $a_2$ 与 $a_1^{-1}$ 相乘即得商的公式。再由（1）中模与幅角的唯一性即得幅角同余式。 $\blacksquare$

---

### 定理 1.13（棣莫弗公式 / De Moivre's Formula）

对任意 $a = r(\cos\varphi + i\sin\varphi) \neq 0$ （ $r \gt 0$ ）及任意整数 $n \in \mathbb{Z}$ ，有：

$$
a^n = r^n(\cos n\varphi + i\sin n\varphi)
$$

特别地，取 $r = 1$ ，对任意 $\varphi \in \mathbb{R}, n \in \mathbb{Z}$ ，有：

$$
(\cos\varphi + i\sin\varphi)^n = \cos(n\varphi) + i\sin(n\varphi)
$$

**证明**：

- **情形 1（ $n = 0$ ）**：左端 $a^0 = 1$ ；右端 $r^0(\cos 0 + i\sin 0) = 1 \cdot (1 + 0) = 1$ ，成立。
- **情形 2（ $n \gt 0$ ，对 $n$ 施数学归纳法）**： $n = 1$ 时显然成立。设对 $n = m \ge 1$ 成立，则对 $n = m + 1$ ，由定理 1.12(2)：

$$
a^{m+1} = a^m \cdot a = \left[r^m(\cos m\varphi + i\sin m\varphi)\right]\left[r(\cos\varphi + i\sin\varphi)\right] = r^{m+1}\left[\cos((m+1)\varphi) + i\sin((m+1)\varphi)\right]
$$

故对一切 $n \in \mathbb{Z}^+$ 成立。

- **情形 3（ $n \lt 0$ ）**：令 $m = -n \in \mathbb{Z}^+$ 。由定理 1.12(2) 的倒数公式及正整数情形：

$$
a^n = (a^{-1})^m = \left[r^{-1}(\cos(-\varphi) + i\sin(-\varphi))\right]^m = r^{-m}(\cos(-m\varphi) + i\sin(-m\varphi)) = r^n(\cos n\varphi + i\sin n\varphi)
$$

证毕。 $\blacksquare$

---

### 定理 1.14（二项方程 $z^n = a$ 的解集结构与单位根表示）

设 $a = r(\cos\varphi + i\sin\varphi) \neq 0$ （ $r \gt 0$ ）， $n \in \mathbb{Z}^+$ 。则方程 $z^n = a$ 在 $\mathbb{C}$ 中恰有 $n$ 个互不相同的解，解集为：

$$
S = \left\lbrace z_k := \sqrt[n]{r}\left[\cos\left(\frac{\varphi + 2k\pi}{n}\right) + i\sin\left(\frac{\varphi + 2k\pi}{n}\right)\right] \quad\middle\vert\quad k = 0, 1, \dots, n-1 \right\rbrace
$$

此外，记 $\omega := \cos\frac{2\pi}{n} + i\sin\frac{2\pi}{n}$ ，若 $z^{\ast}$ 为 $z^n = a$ 的任一特解，则 $S = \lbrace \omega^k z^{\ast} \mid k = 0, 1, \dots, n-1 \rbrace$ 。

**证明**：

**(1) 每个 $z_k$ 均为解**：由定理 1.13，对任意 $k \in \lbrace 0, \dots, n-1 \rbrace$ ：

$$
z_k^n = (\sqrt[n]{r})^n \left[\cos(\varphi + 2k\pi) + i\sin(\varphi + 2k\pi)\right] = r(\cos\varphi + i\sin\varphi) = a
$$

**(2) 全部 $n$ 个解两两互异**：设 $0 \le k_1 \le k_2 \le n - 1$ 且 $z _ {k_1} = z _ {k_2}$ 。由定理 1.12(1) 的幅角唯一性，必存在 $m \in \mathbb{Z}$ 使

$$
\frac{\varphi + 2k_2\pi}{n} - \frac{\varphi + 2k_1\pi}{n} = 2m\pi \implies k_2 - k_1 = mn
$$

因 $0 \le k_2 - k_1 \le n - 1 \lt n$ ，故只能有 $m = 0$ ，即 $k_1 = k_2$ 。

**(3) 无其他解**：设 $z \in \mathbb{C}$ 满足 $z^n = a$ 。因 $a \neq 0$ ，必有 $z \neq 0$ ，故可写 $z = \rho(\cos\theta + i\sin\theta)$ （ $\rho \gt 0$ ）。由定理 1.13 得 $\rho^n(\cos n\theta + i\sin n\theta) = r(\cos\varphi + i\sin\varphi)$ 。由定理 1.12(1)：

$$
\rho^n = r, \qquad \exists q \in \mathbb{Z} \quad \text{使得} \quad n\theta = \varphi + 2q\pi
$$

由正实数 $n$ 次算术根的唯一性得 $\rho = \sqrt[n]{r}$ 。对整数 $q$ 关于 $n$ 作带余除法： $q = pn + k$ ，其中 $p \in \mathbb{Z}, k \in \lbrace 0, 1, \dots, n-1 \rbrace$ 。于是：

$$
\theta = \frac{\varphi + 2k\pi}{n} + 2p\pi \implies \cos\theta + i\sin\theta = \cos\left(\frac{\varphi + 2k\pi}{n}\right) + i\sin\left(\frac{\varphi + 2k\pi}{n}\right)
$$

故 $z = z_k \in S$ 。

**(4) 单位根表示**：若 $z^{\ast} \in S$ ，因 $a \neq 0$ 故 $z^{\ast} \neq 0$ ，对任意 $z \in \mathbb{C}$ ， $z^n = a = (z^{\ast})^n \iff (z/z^{\ast})^n = 1$ 。将上述结论应用于 $a = 1$ （ $r = 1, \varphi = 0$ ），得 $z/z^{\ast} \in \lbrace \omega^k \mid k = 0, \dots, n-1 \rbrace$ （由定理 1.13 知 $\omega^k = \cos\frac{2k\pi}{n} + i\sin\frac{2k\pi}{n}$ ），故 $S = \lbrace \omega^k z^{\ast} \mid k = 0, \dots, n-1 \rbrace$ 。 $\blacksquare$

---

### 命题 1.15（复形式解析几何：直线等价性、正交性与半平面良定义性）

设 $a, a', b, b' \in \mathbb{C}$ 且 $b \neq 0, b' \neq 0$ ，记直线 $L := \lbrace a + bt \mid t \in \mathbb{R} \rbrace$ ， $L' := \lbrace a' + b's \mid s \in \mathbb{R} \rbrace$ 。则：

1. $L = L' \iff \exists \lambda \in \mathbb{R}, \exists \mu \in \mathbb{R} \setminus \lbrace 0 \rbrace$ ，使得 $a' - a = \lambda b$ 且 $b' = \mu b$ ；
2. 直线 $L$ 与 $L'$ 正交 $\iff \frac{b'}{b}$ 为非零纯虚数（即 $\mathop{\mathrm{Re}}(b'/b) = 0$ ）；
3. 设 $L = L'$ 且同向（即 $\mu = b'/b \gt 0$ ），则对任意 $z \in \mathbb{C}$ ， $\mathop{\mathrm{Im}}\frac{z - a}{b}$ 与 $\mathop{\mathrm{Im}}\frac{z - a'}{b'}$ 同号；从而有向直线的左半平面 $\lbrace z \in \mathbb{C} \mid \mathop{\mathrm{Im}}\frac{z-a}{b} \gt 0 \rbrace$ 与右半平面 $\lbrace z \in \mathbb{C} \mid \mathop{\mathrm{Im}}\frac{z-a}{b} \lt 0 \rbrace$ 不依赖于同向参数表示的选取。

**证明**：

**(1) 直线重合条件**

- **充分性（ $\Leftarrow$ ）**：若 $a' - a = \lambda b, b' = \mu b$ （ $\lambda \in \mathbb{R}, \mu \in \mathbb{R} \setminus \lbrace 0 \rbrace$ ），则对任意 $s \in \mathbb{R}$ ， $a' + b's = a + (\lambda + \mu s)b \in L$ ；反之对任意 $t \in \mathbb{R}$ ，取 $s = (t - \lambda)/\mu \in \mathbb{R}$ 有 $a + bt = a' + b's \in L'$ ，故 $L = L'$ 。
- **必要性（ $\Rightarrow$ ）**：若 $L = L'$ ，取 $s = 0$ 得 $a' \in L$ ，故存在 $\lambda \in \mathbb{R}$ 使 $a' = a + \lambda b$ ，即 $a' - a = \lambda b$ 。取 $s = 1$ 得 $a' + b' \in L$ ，故存在 $t_1 \in \mathbb{R}$ 使 $a' + b' = a + t_1 b$ ，两式相减得 $b' = (t_1 - \lambda)b$ 。因 $b' \neq 0$ ，故 $\mu := t_1 - \lambda \in \mathbb{R} \setminus \lbrace 0 \rbrace$ 。

**(2) 正交条件**

设 $b = b_1 + ib_2, b' = b_1' + ib_2'$ （实虚部为方向向量 $(b_1, b_2), (b_1', b_2') \in \mathbb{R}^2 \setminus \lbrace (0,0) \rbrace$ ）。两直线正交等价于方向向量欧氏内积为零： $b_1 b_1' + b_2 b_2' = 0$ 。而由定理 1.4：

$$
\mathop{\mathrm{Re}}\left(\frac{b'}{b}\right) = \frac{b_1' b_1 + b_2' b_2}{b_1^2 + b_2^2}
$$

因 $b_1^2 + b_2^2 \gt 0$ ，故 $b_1 b_1' + b_2 b_2' = 0 \iff \mathop{\mathrm{Re}}(b'/b) = 0$ 。又 $b' \neq 0$ ，故 $b'/b \neq 0$ ，即 $b'/b$ 为非零纯虚数。

**(3) 半平面良定义性**

设 $a' - a = \lambda b$ （ $\lambda \in \mathbb{R}$ ）且 $b' = \mu b$ （ $\mu \gt 0$ ）。对任意 $z \in \mathbb{C}$ ：

$$
\frac{z - a'}{b'} = \frac{(z - a) - \lambda b}{\mu b} = \frac{1}{\mu}\frac{z - a}{b} - \frac{\lambda}{\mu}
$$

因 $\frac{\lambda}{\mu} \in \mathbb{R}$ 且 $\frac{1}{\mu} \gt 0$ ，取虚部得：

$$
\mathop{\mathrm{Im}}\left(\frac{z - a'}{b'}\right) = \frac{1}{\mu}\mathop{\mathrm{Im}}\left(\frac{z - a}{b}\right)
$$

两者严格同号（同时为正、同时为负或同时为零），故左右半平面良定义。 $\blacksquare$

---

### 定理 1.16（球极平面投影的双射性与中心投影几何特征）

设黎曼球面 $S := \lbrace (x_1, x_2, x_3) \in \mathbb{R}^3 \mid x_1^2 + x_2^2 + x_3^2 = 1 \rbrace$ ，北极 $N := (0, 0, 1) \in S$ ，扩充复平面 $\widehat{\mathbb{C}} := \mathbb{C} \cup \lbrace \infty \rbrace$ 。定义映射 $\Phi: S \to \widehat{\mathbb{C}}$ 为：

$$
\Phi(x_1, x_2, x_3) := \begin{cases}
\dfrac{x_1 + ix_2}{1 - x_3}, & (x_1, x_2, x_3) \in S \setminus \lbrace N \rbrace \cr
\infty, & (x_1, x_2, x_3) = N
\end{cases}
$$

则：

1. $\Phi$ 是双射，其逆映射 $\Psi = \Phi^{-1}: \widehat{\mathbb{C}} \to S$ 为 $\Psi(\infty) = N$ ，以及对 $z \in \mathbb{C}$ ：

$$
\Psi(z) = \left(\frac{z + \bar{z}}{1 + |z|^2}, \quad \frac{z - \bar{z}}{i(1 + |z|^2)}, \quad \frac{|z|^2 - 1}{|z|^2 + 1}\right)
$$

2. 对任意 $P = (x_1, x_2, x_3) \in S \setminus \lbrace N \rbrace$ ，记 $z = \Phi(P) = x + iy$ （ $x, y \in \mathbb{R}$ ）及平面点 $Q = (x, y, 0) \in \mathbb{R}^3$ ，则三点 $N, P, Q$ 在 $\mathbb{R}^3$ 中共线。

**证明**：

**(1) 验证双射性与逆映射**

- **良定义性**：若 $(x_1, x_2, x_3) \in S$ 且 $x_3 = 1$ ，则 $x_1^2 + x_2^2 = 1 - x_3^2 = 0 \implies x_1 = x_2 = 0$ ，即该点必为 $N$ 。故对 $S \setminus \lbrace N \rbrace$ 中任一点有 $1 - x_3 \neq 0$ ， $\Phi$ 良定义。对任意 $z = x + iy \in \mathbb{C}$ ， $\Psi(z) = \left(\frac{2x}{1 + |z|^2}, \frac{2y}{1 + |z|^2}, \frac{|z|^2 - 1}{|z|^2 + 1}\right) \in \mathbb{R}^3$ ，且：

$$
x_1^2 + x_2^2 + x_3^2 = \frac{4x^2 + 4y^2 + (|z|^2 - 1)^2}{(1 + |z|^2)^2} = \frac{4|z|^2 + |z|^4 - 2|z|^2 + 1}{(1 + |z|^2)^2} = \frac{(|z|^2 + 1)^2}{(1 + |z|^2)^2} = 1
$$

又 $x_3 = \frac{|z|^2 - 1}{|z|^2 + 1} = 1 - \frac{2}{|z|^2 + 1} \lt 1$ ，故 $\Psi(z) \in S \setminus \lbrace N \rbrace$ 。

- **验证右逆关系**：要证 $\Phi \circ \Psi = \mathrm{id} _ {\widehat{\mathbb{C}}}$ 。首先 $\Phi(\Psi(\infty)) = \Phi(N) = \infty$ ；对 $z \in \mathbb{C}$ ，注意到 $1 - x_3 = \frac{2}{1 + |z|^2}$ 且 $x_1 + ix_2 = \frac{(z+\bar{z}) + (z-\bar{z})}{1 + |z|^2} = \frac{2z}{1 + |z|^2}$ ，故：

$$
\Phi(\Psi(z)) = \frac{2z/(1+|z|^2)}{2/(1+|z|^2)} = z
$$

- **验证左逆关系**：要证 $\Psi \circ \Phi = \mathrm{id} _ S$ 。首先 $\Psi(\Phi(N)) = \Psi(\infty) = N$ ；对 $P = (x_1, x_2, x_3) \in S \setminus \lbrace N \rbrace$ ，令 $z = \Phi(P) = \frac{x_1 + ix_2}{1 - x_3}$ 。由 $x_1^2 + x_2^2 = 1 - x_3^2 = (1 - x_3)(1 + x_3)$ 得：

$$
|z|^2 = \frac{x_1^2 + x_2^2}{(1 - x_3)^2} = \frac{1 + x_3}{1 - x_3} \implies 1 + |z|^2 = \frac{2}{1 - x_3}, \quad |z|^2 - 1 = \frac{2x_3}{1 - x_3}
$$

因此：

$$
\frac{|z|^2 - 1}{|z|^2 + 1} = x_3, \quad \frac{z + \bar{z}}{1 + |z|^2} = \frac{2x_1/(1-x_3)}{2/(1-x_3)} = x_1, \quad \frac{z - \bar{z}}{i(1 + |z|^2)} = \frac{2ix_2/(1-x_3)}{2i/(1-x_3)} = x_2
$$

即 $\Psi(\Phi(P)) = P$ 。从而 $\Phi$ 为双射且 $\Phi^{-1} = \Psi$ 。

**(2) 验证三点共线**

计算 $\mathbb{R}^3$ 中向量 $\overrightarrow{NP} = (x_1, x_2, x_3 - 1)$ 与 $\overrightarrow{NQ} = (x, y, -1)$ 。由 $x = \frac{x_1}{1 - x_3}, y = \frac{x_2}{1 - x_3}$ ，立即得：

$$
\overrightarrow{NP} = (1 - x_3)\left(\frac{x_1}{1 - x_3}, \quad \frac{x_2}{1 - x_3}, \quad -1\right) = (1 - x_3)\overrightarrow{NQ}
$$

因 $1 - x_3 \gt 0$ ，两向量共线，故 $N, P, Q$ 三点共线。 $\blacksquare$

---

### 定理 1.17（球面圆与扩充复平面广义圆的一一对应）

称 $\Gamma \subset S$ 为黎曼球面上的一个**圆**，若存在 $\alpha_0, \alpha_1, \alpha_2, \alpha_3 \in \mathbb{R}$ 满足 $\alpha_1^2 + \alpha_2^2 + \alpha_3^2 = 1$ 且 $0 \le \alpha_0 \lt 1$ ，使得 $\Gamma = \lbrace (x_1, x_2, x_3) \in S \mid \alpha_1 x_1 + \alpha_2 x_2 + \alpha_3 x_3 = \alpha_0 \rbrace$ 。

则球极平面投影 $\Phi$ 建立如下一一对应：

1. $S$ 上不经过北极 $N$ 的圆 $\longleftrightarrow$ $\mathbb{C}$ 中的圆；
2. $S$ 上经过北极 $N$ 的圆 $\longleftrightarrow$ $\widehat{\mathbb{C}}$ 中的扩充直线 $L \cup \lbrace \infty \rbrace$ （ $L$ 为 $\mathbb{C}$ 中直线）。

**证明**：

**第一步（ $\Rightarrow$ ：球面圆的像必为圆或扩充直线）**。

设 $\Gamma$ 由平面方程 $\alpha_1 x_1 + \alpha_2 x_2 + \alpha_3 x_3 = \alpha_0$ 与 $S$ 相交给出，其中 $\alpha_1^2 + \alpha_2^2 + \alpha_3^2 = 1$ 且 $0 \le \alpha_0 \lt 1$ 。对任意 $z = x + iy \in \mathbb{C}$ ，由定理 1.16(1)， $z \in \Phi(\Gamma) \iff \Psi(z) \in \Gamma$ ，代入 $\Psi(z)$ 坐标并两边同乘 $1 + |z|^2 \gt 0$ ，得等价方程：

$$
2\alpha_1 x + 2\alpha_2 y + \alpha_3(x^2 + y^2 - 1) = \alpha_0(x^2 + y^2 + 1)
$$

整理为方程 $(\dagger)$ ：

$$
(\alpha_0 - \alpha_3)(x^2 + y^2) - 2\alpha_1 x - 2\alpha_2 y + (\alpha_0 + \alpha_3) = 0 \qquad (\dagger)
$$

注意到 $N = (0, 0, 1) \in \Gamma \iff \alpha_3 = \alpha_0$ 。分两种情形：

- **情形 1（ $N \notin \Gamma$ ，即 $\alpha_0 \neq \alpha_3$ ）**：此时 $\infty \notin \Phi(\Gamma)$ 。将 $(\dagger)$ 两边除以 $\alpha_0 - \alpha_3$ 并配方：

$$
\left(x - \frac{\alpha_1}{\alpha_0 - \alpha_3}\right)^2 + \left(y - \frac{\alpha_2}{\alpha_0 - \alpha_3}\right)^2 = \frac{\alpha_1^2 + \alpha_2^2 - (\alpha_0^2 - \alpha_3^2)}{(\alpha_0 - \alpha_3)^2} = \frac{1 - \alpha_0^2}{(\alpha_0 - \alpha_3)^2}
$$

因 $0 \le \alpha_0 \lt 1$ ，右端严格大于 $0$ 。故 $\Phi(\Gamma)$ 是 $\mathbb{C}$ 中以 $\frac{\alpha_1 + i\alpha_2}{\alpha_0 - \alpha_3}$ 为圆心、半径 $r = \frac{\sqrt{1 - \alpha_0^2}}{|\alpha_0 - \alpha_3|} \gt 0$ 的圆。

- **情形 2（ $N \in \Gamma$ ，即 $\alpha_0 = \alpha_3$ ）**：此时 $\infty \in \Phi(\Gamma)$ ，且 $(\dagger)$ 化为：

$$
-\alpha_1 x - \alpha_2 y + \alpha_0 = 0
$$

因 $\alpha_1^2 + \alpha_2^2 = 1 - \alpha_3^2 = 1 - \alpha_0^2 \gt 0$ ，故 $\alpha_1, \alpha_2$ 不全为零，该方程表示 $\mathbb{C}$ 中的一条直线 $L$ ，从而 $\Phi(\Gamma) = L \cup \lbrace \infty \rbrace$ 。

**第二步（ $\Leftarrow$ ：圆或扩充直线的原像必为球面圆）**。

- **给定 $\mathbb{C}$ 中任意圆（ $|z - z_0| = r$ ，其中 $z_0 = x_0 + iy_0, r \gt 0$ ）**：展开得 $x^2 + y^2 - 2x_0 x - 2y_0 y + (|z_0|^2 - r^2) = 0$ 。令：

$$
c_1 := x_0, \quad c_2 := y_0, \quad c_0 := \frac{|z_0|^2 - r^2 + 1}{2}, \quad c_3 := \frac{|z_0|^2 - r^2 - 1}{2}
$$

则 $c_0 - c_3 = 1$ ， $c_0 + c_3 = |z_0|^2 - r^2$ ，且计算得：

$$
c_1^2 + c_2^2 + c_3^2 - c_0^2 = |z_0|^2 + (c_3 - c_0)(c_3 + c_0) = |z_0|^2 - (|z_0|^2 - r^2) = r^2 \gt 0
$$

因此 $K := \sqrt{c_1^2 + c_2^2 + c_3^2} \gt |c_0| \ge 0$ 。选取符号 $\sigma \in \lbrace 1, -1 \rbrace$ 使 $\sigma c_0 \ge 0$ ，并定义 $\alpha_j := \sigma c_j / K$ （ $j = 0, 1, 2, 3$ ）。则 $\alpha_1^2 + \alpha_2^2 + \alpha_3^2 = 1$ ， $0 \le \alpha_0 = |c_0|/K \lt 1$ ，且 $\alpha_0 - \alpha_3 = \sigma/K \neq 0$ 。将该组 $\alpha_j$ 代入 $(\dagger)$ 并同乘 $K/\sigma$ 恰好还原给定圆的方程，故其原像 $\Psi(\lbrace |z-z_0|=r \rbrace)$ 为不经过 $N$ 的球面圆。

- **给定 $\widehat{\mathbb{C}}$ 中任意扩充直线（ $L \cup \lbrace \infty \rbrace$ ）**：设 $L$ 的实方程为 $Ax + By + C = 0$ （ $A, B, C \in \mathbb{R}, A^2 + B^2 \gt 0$ ）。令：

$$
c_1 := -\frac{A}{2}, \quad c_2 := -\frac{B}{2}, \quad c_0 := \frac{C}{2}, \quad c_3 := \frac{C}{2}
$$

则 $c_1^2 + c_2^2 + c_3^2 - c_0^2 = \frac{A^2 + B^2}{4} \gt 0$ ，故 $K := \sqrt{c_1^2 + c_2^2 + c_3^2} \gt |c_0| \ge 0$ 。同上选 $\sigma \in \lbrace 1, -1 \rbrace$ 使 $\sigma c_0 \ge 0$ 并令 $\alpha_j := \sigma c_j / K$ ，则 $\alpha_1^2 + \alpha_2^2 + \alpha_3^2 = 1$ ， $0 \le \alpha_0 \lt 1$ 且 $\alpha_0 = \alpha_3$ （故 $N$ 在对应球面圆上）。代入 $(\dagger)$ 并同乘 $K/\sigma$ 还原直线 $L$ 的方程，故 $\Psi(L \cup \lbrace \infty \rbrace)$ 为经过 $N$ 的球面圆。

因 $\Phi$ 是点集双射，其诱导的子集映射 $\Gamma \mapsto \Phi(\Gamma)$ 自动为单射；第二步说明它满射到全体广义圆，故为一一对应。 $\blacksquare$

---

### 定理 1.18（球面弦距公式及其度量性）

对任意 $z, z' \in \widehat{\mathbb{C}}$ ，定义其球面距离 $d(z, z') := \lVert \Psi(z) - \Psi(z') \rVert _ {\mathbb{R}^3}$ （即球极投影逆像在 $\mathbb{R}^3$ 中的欧氏距离）。则：

1. 对任意 $z, z' \in \mathbb{C}$ ，

$$
d(z, z') = \frac{2|z - z'|}{\sqrt{(1 + |z|^2)(1 + |z'|^2)}}
$$

2. 对任意 $z \in \mathbb{C}$ ，

$$
d(z, \infty) = d(\infty, z) = \frac{2}{\sqrt{1 + |z|^2}}, \qquad d(\infty, \infty) = 0
$$

3. $(\widehat{\mathbb{C}}, d)$ 构成一个度量空间。

**证明**：

**(1)** 设 $\Psi(z) = (x_1, x_2, x_3) \in S$ ， $\Psi(z') = (x_1', x_2', x_3') \in S$ 。由 $x_1^2 + x_2^2 + x_3^2 = 1$ 及 $(x_1')^2 + (x_2')^2 + (x_3')^2 = 1$ ，展开平方距离：

$$
d(z, z')^2 = (x_1 - x_1')^2 + (x_2 - x_2')^2 + (x_3 - x_3')^2 = 2 - 2(x_1 x_1' + x_2 x_2' + x_3 x_3')
$$

将定理 1.16(1) 中的逆映射坐标代入内积 $x_1 x_1' + x_2 x_2' + x_3 x_3'$ （注意 $1/i^2 = -1$ ）：

$$
x_1 x_1' + x_2 x_2' + x_3 x_3' = \frac{(z + \bar{z})(z' + \overline{z'}) - (z - \bar{z})(z' - \overline{z'}) + (|z|^2 - 1)(|z'|^2 - 1)}{(1 + |z|^2)(1 + |z'|^2)}
$$

展开并化简上述右端分子，得：

$$
\begin{aligned}
&(zz' + z\overline{z'} + \bar{z}z' + \bar{z}\overline{z'}) - (zz' - z\overline{z'} - \bar{z}z' + \bar{z}\overline{z'}) + |z|^2|z'|^2 - |z|^2 - |z'|^2 + 1 \cr
&\quad = 2(z\overline{z'} + \bar{z}z') + |z|^2|z'|^2 - |z|^2 - |z'|^2 + 1 \cr
&\quad = \left(1 + |z|^2 + |z'|^2 + |z|^2|z'|^2\right) - 2\left(|z|^2 + |z'|^2 - z\overline{z'} - \bar{z}z'\right) \cr
&\quad = (1 + |z|^2)(1 + |z'|^2) - 2|z - z'|^2
\end{aligned}
$$

因此：

$$
x_1 x_1' + x_2 x_2' + x_3 x_3' = 1 - \frac{2|z - z'|^2}{(1 + |z|^2)(1 + |z'|^2)}
$$

代回 $d(z, z')^2 = 2 - 2(x_1 x_1' + x_2 x_2' + x_3 x_3')$ 得：

$$
d(z, z')^2 = \frac{4|z - z'|^2}{(1 + |z|^2)(1 + |z'|^2)}
$$

两边取非负平方根即得公式。

**(2)** 对 $z \in \mathbb{C}$ 与 $\infty$ （对应 $N = (0, 0, 1)$ ）：

$$
d(z, \infty)^2 = x_1^2 + x_2^2 + (x_3 - 1)^2 = (x_1^2 + x_2^2 + x_3^2) - 2x_3 + 1 = 2(1 - x_3) = 2\left(1 - \frac{|z|^2 - 1}{|z|^2 + 1}\right) = \frac{4}{1 + |z|^2}
$$

开非负平方根得 $d(z, \infty) = \frac{2}{\sqrt{1 + |z|^2}}$ 。显然 $d(\infty, \infty) = \lVert N - N \rVert _ {\mathbb{R}^3} = 0$ 。

**(3)** 因 $\Psi: \widehat{\mathbb{C}} \to S \subset \mathbb{R}^3$ 是双射（定理 1.16），而 $\mathbb{R}^3$ 上的欧氏距离 $\lVert \cdot \rVert _ {\mathbb{R}^3}$ 满足非负正定性、对称性与三角形不等式，故对任意 $z_1, z_2, z_3 \in \widehat{\mathbb{C}}$ ：

- 非负性与正定性： $d(z_1, z_2) \ge 0$ ，且 $d(z_1, z_2) = 0 \iff \Psi(z_1) = \Psi(z_2) \iff z_1 = z_2$ ；
- 对称性： $d(z_1, z_2) = d(z_2, z_1)$ ；
- 三角形不等式：

$$
d(z_1, z_3) = \lVert \Psi(z_1) - \Psi(z_3) \rVert _ {\mathbb{R}^3} \le \lVert \Psi(z_1) - \Psi(z_2) \rVert _ {\mathbb{R}^3} + \lVert \Psi(z_2) - \Psi(z_3) \rVert _ {\mathbb{R}^3} = d(z_1, z_2) + d(z_2, z_3)
$$

故 $(\widehat{\mathbb{C}}, d)$ 为度量空间。 $\blacksquare$

---

### 补充命题 1.19（黎曼球面上的对径点刻画，1.2.4 节习题 1）

两点 $z, z' \in \widehat{\mathbb{C}}$ 在黎曼球面 $S$ 上互为对径点（即 $\Psi(z') = -\Psi(z)$ ，等价于 $d(z, z') = 2$ ），当且仅当满足 $z\overline{z'} = -1$ （并约定 $0$ 与 $\infty$ 互为对径点）。

**证明**：

先验证 $\Psi(z') = -\Psi(z) \iff d(z, z') = 2$ ：对任意单位球面上的点 $P, P' \in S$ ，由平行四边形恒等式得 $\lVert P - P' \rVert _ {\mathbb{R}^3}^2 + \lVert P + P' \rVert _ {\mathbb{R}^3}^2 = 2(\lVert P \rVert _ {\mathbb{R}^3}^2 + \lVert P' \rVert _ {\mathbb{R}^3}^2) = 4$ ，故 $\lVert P - P' \rVert _ {\mathbb{R}^3} = 2 \iff \lVert P + P' \rVert _ {\mathbb{R}^3} = 0 \iff P' = -P$ 。

**情形 1（ $z \in \lbrace 0, \infty \rbrace$ 或 $z' \in \lbrace 0, \infty \rbrace$ ）**：因为 $\Psi(0) = (0, 0, -1) = -N = -\Psi(\infty)$ 且 $\Psi$ 为双射，所以 $0$ 的唯一对径点是 $\infty$ ， $\infty$ 的唯一对径点是 $0$ ，与约定一致。

**情形 2（ $z, z' \in \mathbb{C} \setminus \lbrace 0 \rbrace$ ）**：

- **必要性（ $\Rightarrow$ ）**：若 $\Psi(z') = -\Psi(z)$ ，由第三分量 $\frac{|z'|^2 - 1}{|z'|^2 + 1} = -\frac{|z|^2 - 1}{|z|^2 + 1}$ 交叉相乘得 $(|z'|^2 - 1)(|z|^2 + 1) = (1 - |z|^2)(|z'|^2 + 1)$ ，化简得 $2|z|^2|z'|^2 = 2 \implies |z'|^2 = \frac{1}{|z|^2}$ ，进而 $1 + |z'|^2 = \frac{1 + |z|^2}{|z|^2}$ 。再由前两分量 $x_1' = -x_1, x_2' = -x_2$ 合并为 $x_1' + ix_2' = -(x_1 + ix_2)$ ，即：

$$
\frac{2z'}{1 + |z'|^2} = -\frac{2z}{1 + |z|^2} \implies z' = -\frac{z}{|z|^2} = -\frac{1}{\bar{z}} \implies \bar{z}z' = -1
$$

两边取共轭即得 $z\overline{z'} = -1$ 。

- **充分性（ $\Leftarrow$ ）**：若 $z\overline{z'} = -1$ ，则 $z' = -\frac{1}{\bar{z}}$ ， $|z'|^2 = \frac{1}{|z|^2}$ 。直接代入 $\Psi(z')$ ：

$$
x_3' = \frac{|z|^{-2} - 1}{|z|^{-2} + 1} = \frac{1 - |z|^2}{1 + |z|^2} = -x_3
$$

$$
x_1' + ix_2' = \frac{2z'}{1 + |z'|^2} = \frac{-2/\bar{z}}{1 + |z|^{-2}} = \frac{-2|z|^2/\bar{z}}{|z|^2 + 1} = -\frac{2z}{1 + |z|^2} = -(x_1 + ix_2)
$$

比较实虚部得 $x_1' = -x_1, x_2' = -x_2, x_3' = -x_3$ ，即 $\Psi(z') = -\Psi(z)$ 。 $\blacksquare$
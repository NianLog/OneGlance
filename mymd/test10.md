# 微积分复习手册

## 目录

1. [极限与连续](#极限与连续)
2. [导数与微分](#导数与微分)
3. [微分中值定理](#微分中值定理)
4. [不定积分](#不定积分)
5. [定积分](#定积分)
6. [多元函数微积分](#多元函数微积分)

## 极限与连续

### 数列的极限

若当 $n$ 趋向无穷大时，$a_n$ 无限接近常数 $A$，则称数列 ${a_n}$ 收敛于 $A$。

$$\lim_{n \to \infty} a_n = A$$

**常用极限公式：**

$$\lim_{n \to \infty} \frac{1}{n} = 0$$
$$\lim_{n \to \infty} q^n = 0 \quad (|q| < 1)$$
$$\lim_{n \to \infty} (1 + \frac{1}{n})^n = e$$

### 函数的极限

$$\lim_{x \to x_0} f(x) = A$$

**极限存在的充要条件：**

$$\lim_{x \to x_0^+} f(x) = \lim_{x \to x_0^-} f(x) = A$$

### 无穷小与无穷大

| 类型 | 定义 | 关系 |
|------|------|------|
| 无穷小 | $\lim \alpha(x) = 0$ | $\alpha \cdot \beta$ 仍为无穷小 |
| 无穷大 | $\lim \beta(x) = \infty$ | $0 \cdot \infty$ 不确定 |

### 连续与间断

**连续定义：**
$$\lim_{x \to x_0} f(x) = f(x_0)$$

**间断点类型：**

| 类型 | 条件 |
|------|------|
| 第一类 | 左、右极限都存在 |
| 第二类 | 至少有一个极限不存在 |

## 导数与微分

### 导数定义

$$f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}$$

### 求导法则

| 法则 | 公式 |
|------|------|
| 和差 | $(u \pm v)' = u' \pm v'$ |
| 积 | $(uv)' = u'v + uv'$ |
| 商 | $(\frac{u}{v})' = \frac{u'v - uv'}{v^2}$ |
| 链式 | $[f(g(x))]' = f'(g(x)) \cdot g'(x)$ |

### 基本导数公式

```
(d/dx) C = 0
(d/dx) x^n = nx^(n-1)
(d/dx) sin x = cos x
(d/dx) cos x = -sin x
(d/dx) e^x = e^x
(d/dx) ln x = 1/x
(d/dx) a^x = a^x ln a
```

### 微分

$$dy = f'(x)dx$$

**微分近似公式：**
$$f(x_0 + \Delta x) \approx f(x_0) + f'(x_0)\Delta x$$

## 微分中值定理

### 罗尔定理

若 $f(x)$ 满足：
1. 在 $[a,b]$ 上连续
2. 在 $(a,b)$ 内可导
3. $f(a) = f(b)$

则存在 $\xi \in (a,b)$，使 $f'(\xi) = 0$

### 拉格朗日中值定理

若 $f(x)$ 满足：
1. 在 $[a,b]$ 上连续
2. 在 $(a,b)$ 内可导

则存在 $\xi \in (a,b)$，使
$$f(b) - f(a) = f'(\xi)(b - a)$$

### 泰勒公式

$$f(x) = f(x_0) + f'(x_0)(x-x_0) + \frac{f''(x_0)}{2!}(x-x_0)^2 + \cdots + \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n + R_n$$

**麦克劳林展开：**

$$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots$$
$$\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots$$
$$\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots$$
$$\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots$$

## 不定积分

### 不定积分定义

$$\int f(x)dx = F(x) + C$$
其中 $F'(x) = f(x)$

### 基本积分公式

```
∫ 0 dx = C
∫ x^n dx = x^(n+1)/(n+1) + C
∫ 1/x dx = ln|x| + C
∫ e^x dx = e^x + C
∫ cos x dx = sin x + C
∫ sin x dx = -cos x + C
```

### 换元积分法

**第一类换元：**
$$\int f(\varphi(x))\varphi'(x)dx = \int f(u)du$$

**第二类换元：**
$$\int f(x)dx = \int f(\varphi(t))\varphi'(t)dt$$

### 分部积分法

$$\int u\,dv = uv - \int v\,du$$

**适用场景：**
- $\int x^n e^x dx$ → $u = x^n$
- $\int x^n \ln x dx$ → $u = \ln x$
- $\int e^x \sin x dx$ → $u = e^x$

## 定积分

### 定积分定义

$$\int_a^b f(x)dx = \lim_{\lambda \to 0} \sum_{i=1}^{n} f(\xi_i)\Delta x_i$$

### 牛顿-莱布尼茨公式

$$\int_a^b f(x)dx = F(b) - F(a)$$
其中 $F'(x) = f(x)$

### 定积分计算

**换元法：**
$$\int_a^b f(x)dx = \int_{\alpha}^{\beta} f(\varphi(t))\varphi'(t)dt$$

**分部积分：**
$$\int_a^b u\,dv = [uv]_a^b - \int_a^b v\,du$$

### 定积分应用

**平面图形面积：**
$$S = \int_a^b |f(x) - g(x)|dx$$

**旋转体体积：**
$$V = \pi \int_a^b f^2(x)dx$$

**曲线弧长：**
$$s = \int_a^b \sqrt{1 + [f'(x)]^2}dx$$

## 多元函数微积分

### 二元函数极限

$$\lim_{(x,y) \to (x_0,y_0)} f(x,y) = A$$

### 偏导数

$$f_x(x,y) = \frac{\partial f}{\partial x} = \lim_{\Delta x \to 0} \frac{f(x+\Delta x, y) - f(x,y)}{\Delta x}$$

### 全微分

$$dz = \frac{\partial z}{\partial x}dx + \frac{\partial z}{\partial y}dy$$

### 极值问题

**必要条件：** $\frac{\partial f}{\partial x} = 0, \frac{\partial f}{\partial y} = 0$

**充分条件：**
$$AC - B^2 \begin{cases} > 0 & \text{有极值} \\ < 0 & \text{无极值} \\ = 0 & \text{需进一步判断} \end{cases}$$

其中 $A = f_{xx}, B = f_{xy}, C = f_{yy}$

### 二重积分

$$\iint_D f(x,y)d\sigma$$

**直角坐标系：**
$$\iint_D f(x,y)d\sigma = \int_a^b dx \int_{\varphi_1(x)}^{\varphi_2(x)} f(x,y)dy$$

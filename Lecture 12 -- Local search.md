# Lecture 12 -- Local search

## local search （局部搜索）

### 基本思想

- 实际上是近似算法的一大门类
- 大致思路为：通过局部最优解获得全局近似解（可以不是最优，作为近似算法的一种）

（贪心：通过局部最优解获得全局最优解？）

### 局部范围考虑

- 设计时需要考虑好“局部”的范围

![image-20241221213146429](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221213146429.png)

### 邻居关系

即为 neighbor relation

![image-20241221213437673](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221213437673.png)

### 框架结构

![image-20241221213637323](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221213637323.png)

### 伪代码实现

![image-20241221214423567](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221214423567.png)

- 称为梯度下降法，即gradient descent,沿着梯度下降的方向不断进行局部的搜索
- ![image-20241221214728942](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221214728942.png)

### 和贪心的区别

![image-20241221213958897](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221213958897.png)

局部搜索时如果无法很好的把握局部的范围大小，则很容易跳过最优解，甚至进入死循环

## Vertex cover problem

### 问题描述

![image-20241221214155606](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221214155606.png)

### 基本量

![image-20241221214912810](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221214912810.png)

### 搜索步骤

![image-20241221215000919](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215000919.png)

### 典型案例（使用梯度下降法）

![image-20241221215058170](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215058170.png)

![image-20241221215113965](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215113965.png)

![image-20241221215152870](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215152870.png)

## Metropolis 算法

![image-20241221215625889](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215625889.png)

![image-20241221215909566](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215909566.png)

### 模拟退火算法

即simulated annealing

![image-20241221215957768](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221215957768.png)

- 赋予搜索过程一种时变（T不是固定的，会慢慢下降）且最终趋于零的概率突跳性，从而避免陷入局部极小，使得算法最终趋于全局最优的优化算法

## Hopfield Neural networks

### 问题描述

![image-20241221220317434](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221220317434.png)

![image-20241221220449279](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221220449279.png)

- 输入的graph有整数权重（可正可负）
- 这里的状态都是一种理想，希望，或者说需求，可能不成立
- 某条边权重为正，希望两端点状态不同
- 某条边权重为负，希望两端点状态相同
- 最后输出所有点的状态集合{1，-1}

### sufficiently good

如果出现无法满足顶点全部需求的情况怎么办？

![image-20241221221429040](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221221429040.png)

- 始终无法满足三个顶点两两之间异号的需求
- 需要找到一种不是最好，而是足够好，相对好的布局

### stable

![image-20241221221726403](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221221726403.png)

#### 好边和坏边

![image-20241221222038998](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221222038998.png)

#### 满意点

![image-20241221222152400](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221222152400.png)

### example

![image-20241221223714997](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221223714997.png)

![image-20241221223748939](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221223748939.png)

- 检验布局是否稳定，即判定是否所有点都是满意点

### 状态翻转（state-flipping)算法

![image-20241221224247436](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221224247436.png)

- 只要布局不稳定时，该算法就能找到其中的不满意点，并翻转它的状态，这样就能使其变成满意点，直到所有的点都变为满意点
- ![image-20241221230708457](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221230708457.png)

![image-20241221230748725](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221230748725.png)

![image-20241221230932936](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221230932936.png)

![image-20241221231114647](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231114647.png)

## Maximum cut problem

### 问题描述

![image-20241221231146926](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231146926.png)

![image-20241221231320289](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231320289.png)

**补充结论：最大割的权重和至少是所有边的权重和的一半**

### 局部搜索

![image-20241221231446299](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231446299.png)

### Hopfield 特例

![image-20241221231829546](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231829546.png)

**是伪多项式时间复杂度**

![image-20241221231952331](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221231952331.png)

### 局部最优解有多好？

![image-20241221232349544](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221232349544.png)

![image-20241221232400828](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221232400828.png)

- **maximum cut 这种近似比为2（或更低）**
- 状态翻转算法在本题是一种2-近似算法

![image-20241221232600892](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221232600892.png)

### 大提升局部（big-improvement-flip)

- 去加速max-cut
- ![image-20241221232900116](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221232900116.png)
- 思考能否在多项式时间内得到结果？

![image-20241221233016509](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221233016509.png)

### 更好的局部？

![image-20241221233129471](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221233129471.png)

![image-20241221233310820](C:\Users\97133\AppData\Roaming\Typora\typora-user-images\image-20241221233310820.png)
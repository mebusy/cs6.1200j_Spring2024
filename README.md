# cs6.1200j_Spring2024 Notes

## propositions and predicates

### Implication P ⇒ Q

in programming language: `~P || Q`


`P ⇒ Q` 的 逆否命题是 `~Q ⇒ ~P`，它们是逻辑等价的。


### Modus ponens ((P ⇒ Q) and P ) ⇒ Q

这是离散数学里一个非常核心的逻辑恒真式(有多种写法, 不管P,Q 怎么取值，式子结果永远为真)，

叫做 肯定前件（Modus Ponens.

它的意思是： 如果 “P 推出 Q” 为真，并且 P 为真，那么 Q 一定为真。 直观的理解的，就是逻辑上的“说到做到”。

很多自动定理证明器、SAT 推理系统、甚至你在写约束求解器时的规则传播，本质上都在不断使用：

```bash
如果规则成立 + 前提满足 → 结论成立 因此整个公式恒为真。
```


<details>
<summary>
 真值表证明...
</summary>

P | Q | P ⇒ Q | (P ⇒ Q) ∧ P | 整个式子
---|---|---|---|---
T | T | T | T | T
T | F | F | F | T
F | T | T | F | T
F | F | T | F | T

关键观察：

- 只有第一行 (P ⇒ Q) ^ P 为真, 
    - 在那一行 Q 也为真
- 所以不存在“前面为真而 Q 为假”的情况

整个公式恒为真。

</details>

### Modus tollens: ((P ⇒ Q) and not Q) ⇒ not P

否定后件（Modus Tollens）是另一个逻辑恒真式：

它的意思是： 如果 “P 推出 Q” 为真， 但 Q 实际上是假的，那么 P 一定是假的。


<details>
<summary>
 真值表证明...
</summary>

P | Q | P ⇒ Q | ¬Q | (P ⇒ Q) ∧ ¬Q | ¬P | 整体
---|---|---|---|---|---|---
T | T | T | F | F | F | T
T | F | F | T | F | F | T
F | T | T | F | F | T | T
F | F | T | T | T | T | T


- 只有最后一行前件为真：
    - P: False
    - Q: False

</details>


从逻辑结构上理解, Modus Ponens 和 Modus Tollens 是对偶结构, 也是 逆否命题的关系。

一个是:

```bash
肯定前件 → 肯定后件
```

一个是:

```bash
否定后件 → 否定前件
```



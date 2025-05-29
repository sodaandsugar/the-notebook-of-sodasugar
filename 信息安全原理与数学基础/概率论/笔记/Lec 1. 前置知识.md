# Lec 1. 前置知识
## 1 基本概念
* 数学定义
  * 互斥：$A_i \cap A_j = \empty \quad i \neq j $
  * 穷尽：$A_1 \cup A_2 \cup \cdots \cup A_n = S$
  * 独立：$P(AB)=P(A) \cdot P(B)$
* 中英文对照表
  <div style="text-align:center;">

| English               | 中文         | 
|-----------------------|--------------|
| set                   | 集合         |
| element               | 元素         |
| union                 | 并集         |
| intersection          | 交集         |
| complement            | 补集         |
| mutually exclusive    | 互斥         |
| disjoint              | 不相交       |
| collectively exhaustive | 穷尽       |
| partition             | 分割         |
| random experiment     | 随机试验     |
| sample space          | 样本空间     |
| event                 | 事件         |
| even                  | 偶数         |
| odd                   | 奇数         |
| independent           | 独立         |

</div>

## 2 重要公式
* 容斥原理
  * $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
  * $P\left( \bigcup\limits_{j=1}^{n} A_j \right) = \sum\limits_{j=1}^{n} P(A_j) - \sum\limits_{i<j} P(A_i \cap A_j) + \sum\limits_{i<j<k} P(A_i \cap A_j \cap A_k) - \cdots + (-1)^{n-1} P\left( A_1 \cap A_2 \cap \dots \cap A_n \right)$
* 条件概率
  * $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$
* 乘法公式
  * $P(AB) = P(A) \cdot P(B \mid A) = P(B) \cdot P(A \mid B)$
  * $P(A_1A_2 \dots A_n) = P(A_1) \cdot P(A_2 \mid A_1) \cdot P(A_3 \mid A_1 A_2)  \dots  P(A_n \mid A_1 A_2 \dots  A_{n-1})$
  * $P(A B C) = P(A \mid C) \cdot P(B \mid A C)$
* 全概率公式
  * $P(A) = \sum\limits_{j=1}^{n} P(B_j) \cdot P(A \mid B_j)$
* 贝叶斯公式
  * $P(B_k \mid A) = \frac{P(B_k) \cdot P(A \mid B_k)}{\sum\limits_{j=1}^{n} P(B_j) \cdot P(A \mid B_j)}$ 

## 3 书写规范
* 用大写字母表示随机变量，如 $X$
* 用 $S$ 表示随机变量的取值范围，如 $S_X$
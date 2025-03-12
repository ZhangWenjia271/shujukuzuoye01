# shujukuzuoye01
这是 `张闻珈` 数据库原理与应用课程第一次作业。
## 题目一

### 1. 找到位于成都市的支行的名字

使用关系代数查询位于成都市的支行名字：
Π<sub>branch_name</sub> (σ<sub>branch_city</sub> = "成都" (branch))  

**解释**：
- σ<sub>branch_city</sub> = "成都" (branch)：选择所有 `branch_city` 为 "成都" 的支行。
- Π<sub>branch_name</sub>：投影出 `branch_name` 属性。

---

### 2. 找到在杨柳支行有贷款（loan）的借款人（borrower）的ID

使用关系代数查询在 "杨柳支行" 有贷款的借款人的 ID：
Π<sub>ID</sub> (σ<sub>branch_name</sub> = "杨柳" (loan ⋈ borrower))  或  Π<sub>ID</sub> (σ<sub>branch_name</sub> = "杨柳" (loan) ⋈ borrower)

**解释**：
- σ<sub>branch_name</sub> = "杨柳" (loan)：选择 `branch_name` 为 "杨柳（支行）" 的贷款记录。
- loan ⋈ borrower：将 `loan` 表和 `borrower` 表通过 `loan_number` 进行自然连接。
- Π<sub>ID</sub>：投影出 `ID` 属性。

---

## 题目二

### 结合关系代数简述实现用户登录逻辑的思路

假设用户输入的用户名和密码分别是input_name和input_pswd，同时假设数据库中存储用户名和密码的关系模式是 `users(name, pswd, gender)`，用户登录逻辑可以通过以下关系代数实现：


σ<sub>name=input_name∧pswd=input_pswd</sub> (users)

**解释**：
- σ：选择操作，筛选满足条件的元组。
- name=input_name：筛选 `name` 字段与输入的用户名匹配的记录。
- pswd=input_pswd：筛选 `pswd` 字段与输入的密码匹配的记录。
- ∧：逻辑与操作，表示同时满足两个条件。

**验证结果**：
- 如果结果非空（即存在满足条件的元组），则登录成功。
- 如果结果为空，则登录失败（用户名或密码错误）。

**扩展**：如果需要返回用户的性别信息，可以使用投影操作：

Π<sub>gender</sub> (σ<sub>name=input_name∧pswd=input_pswd</sub> (users))

**解释**：
- Π<sub>gender</sub>：投影出 `gender` 字段。


---

# shujukuzuoye01
这是笨人数据库原理与应用课程第一次作业。
## 题目一

### 1. 找到位于成都市的支行的名字

使用关系代数查询位于成都市的支行名字：

\[
\Pi_{\text{branch\_name}} \left( \sigma_{\text{branch\_city} = "成都"} (\text{branch}) \right)
\]

**解释**：
- \(\sigma_{\text{branch\_city} = "成都"}\)：选择所有 `branch_city` 为 "成都" 的支行。
- \(\Pi_{\text{branch\_name}}\)：投影出 `branch_name` 属性。

---

### 2. 找到在杨柳支行有贷款（loan）的借款人（borrower）的ID

使用关系代数查询在 "杨柳支行" 有贷款的借款人的 ID：

\[
\Pi_{\text{ID}} \left( \sigma_{\text{branch\_name} = "杨柳"} (\text{loan}) \bowtie \text{borrower} \right)
\]

**解释**：
- \(\sigma_{\text{branch\_name} = "杨柳"}\)：选择 `branch_name` 为 "杨柳（支行）" 的贷款记录。
- \(\bowtie\)：将 `loan` 表和 `borrower` 表通过 `loan_number` 进行自然连接。
- \(\Pi_{\text{ID}}\)：投影出 `ID` 属性。

---

## 题目二

### 结合关系代数简述实现用户登录逻辑的思路

假设数据库中存储用户名和密码的关系模式是 `users(name, pswd, gender)`，用户登录逻辑可以通过以下关系代数实现：

\[
\sigma_{\text{name} = \text{input\_name} \land \text{pswd} = \text{input\_pswd}} (\text{users})
\]

**解释**：
- \(\sigma\)：选择操作，筛选满足条件的元组。
- \(\text{name} = \text{input\_name}\)：筛选 `name` 字段与输入的用户名匹配的记录。
- \(\text{pswd} = \text{input\_pswd}\)：筛选 `pswd` 字段与输入的密码匹配的记录。
- \(\land\)：逻辑与操作，表示同时满足两个条件。

**验证结果**：
- 如果结果非空，则登录成功。
- 如果结果为空，则登录失败（用户名或密码错误）。

**扩展**：如果需要返回用户的性别信息，可以使用投影操作：

\[
\Pi_{\text{gender}} \left( \sigma_{\text{name} = \text{input\_name} \land \text{pswd} = \text{input\_pswd}} (\text{users}) \right)
\]


### 账户管理 LWC 说明文档

#### 关联文件
lwc:accountList
apex:AccountController

**概述**：此组件集提供了使用 Apex 和 Lightning Web Components (LWC) 从 Salesforce 获取并显示账户列表的功能。（两个功能）

#### Apex 控制器：`AccountController`
- **目的**：提供一个方法从 Salesforce 检索账户记录。
- **方法**：`getNone()`
  - **描述**：此静态方法查询并返回账户记录，具体包括账户的名称、年收入和行业字段。它使用 `WITH SECURITY_ENFORCED` 确保执行了字段级安全性，且按账户名称对结果进行排序。
  - **访问**：通过 `@AuraEnabled(cacheable=true)` 对 Lightning Web Components 开放，允许客户端缓存数据，通过减少服务器往返次数来提高性能。

#### JavaScript 控制器：`AccountList`
- **目的**：在 LWC 中以表格形式显示 Apex 控制器检索的账户数据。
- **组件**：
  - **字段**：使用 Salesforce 架构中的特定字段（`Account.Name`、`Account.AnnualRevenue` 和 `Account.Industry`）定义要显示的列。
  - **列配置**：定义数据表的列，包
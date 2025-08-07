# Bytebase 数据库变更流程图文教程

*面向初学者的 5 分钟上手手册*

> **背景**  
> 本文是我在练习“中文产品手册撰写”时，以 Bytebase 官方在线 Demo 环境为对象整理的实操案例。  
> **目标**  
> 跟着本文操作，你将能在 Bytebase 中独立完成一次「创建数据库 → 审核 → 发布」的完整变更流程。  
> **前置条件**
> 
> - 电脑浏览器 + 网络
> - 访问 [Bytebase Demo 站点](https://demo.bytebase.com)（官方在线环境，免安装）
> - 截图工具（推荐 Snipaste 或 macOS 的 Shift+⌘+4）
> - Markdown 编辑器（推荐 Typora）

---

## 1. 前置准备

|工具 / 权限|说明|
|---|---|
|登录账号|使用 Bytebase 提供的 GitHub OAuth 一键登录（账号：[demo@example.com](mailto:demo@example.com)，密码：1024）|
|项目选择|选择 **HR Project**（勿选 **bytebase** 元数据库，该数据库受系统保护，不可更改）|

---

## 2. 创建数据库

### 2.1 入口

在左侧菜单栏依次点击 **Instances → Prod Sample Instance → 右上角「Create Database」** 按钮。

### 2.2 填写参数

|字段|示例值|备注|
|---|---|---|
|Project|HR Project|从下拉菜单中选择|
|Database Name|hello_world|自定义名称，确保唯一性|
|Owner|bbsample|保持默认值|

点击 **Create** 按钮后，系统将自动生成一条变更工单（Issue）。

---

## 3. 变更工单三阶段

### 3.1 等待审核（Pending Review）

- **状态标签**：待审核
- **操作人**：Project Owner 或 DBA
- **界面示意**：![审核](https://github.com/lilith887/my-notes/blob/main/docs/images/%E5%8F%91%E5%B8%83.png?raw=true) ![审核1](https://github.com/lilith887/my-notes/blob/main/docs/images/%E5%8F%91%E5%B8%831.png?raw=true)

### 3.2 批准执行（Approve & Rollout）

- 审核通过后，点击 **Approve** 按钮。
- 再点击 **Rollout** 按钮开始执行 SQL。
![批准](https://github.com/lilith887/my-notes/blob/main/docs/images/%E5%BE%85%E5%AE%A1%E6%A0%B8.png?raw=true) ![批准1](https://github.com/lilith887/my-notes/blob/main/docs/images/%E5%BE%85%E5%AE%A1%E6%A0%B81.png?raw=true)
### 3.3 执行完成（Done）

- 状态变为 **Done** 即变更成功。
- 可在 **Databases** 列表中确认 `hello_world` 数据库已成功创建。
![完成](https://github.com/lilith887/my-notes/blob/main/docs/images/%E5%AE%8C%E6%88%90.png?raw=true)
---

## 4. 常见问题 FAQ

|问题|原因 & 解决|
|---|---|
|找不到「Create Database」按钮|确认已进入 **Prod Sample Instance**，而不是 **bytebase** 元数据库|
|审核人迟迟未通过|在 Demo 环境中，当前登录用户即为 Owner，可自行点击 **Approve**|
|执行后数据库仍不存在|刷新 **Databases** 列表或查看 Issue 详情日志|

---

## 5. 小结

至此，你已完整跑通 Bytebase 的数据库变更流程：**创建 → 审核 → 发布**。  
后续可将此流程套用到自建实例或 CI/CD 流水线中。

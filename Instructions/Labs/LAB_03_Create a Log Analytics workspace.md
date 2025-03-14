---
lab:
  title: 练习 03 - 创建 Log Analytics 工作区
  module: Module 04 - Create a Log Analytics workspace
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


收集日志和数据时，信息将存储在工作区中。 工作区具有唯一的工作区 ID 和资源 ID。 给定资源组的工作区名称必须唯一。 创建工作区后，请配置数据源和解决方案以在其中存储数据。 

---

## 技能任务

- 创建 Log Analytics 工作区。
- 将工作区与现有资源组关联。
- 指定部署工作区的特定区域。

## 练习说明 

### 使用Log Analytics 工作区菜单创建工作区。

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 在门户顶部的搜索框中，键入“Log Analytics 工作区”****。 在搜索结果中选择“Log Analytics 工作区”****。

3. 在“**Log Analytics 工作区**”页上，选择 **+ 创建。**

4. 在“**创建 Log Analytics 工作区**”的“**基本信息**”页上，输入或选择以下信息：
   
   |设置|值|
   |---|---|
   |**项目详细信息**|
   |订阅|选择订阅。|
   |资源组|输入 **azure-rg-1**。|
   |**实例详细信息**|
   |名称|输入 **azwrkspc1a。**|
   |区域|选择“美国东部”。|

5. 选择页面底部的“**查看 + 创建**”选项卡。
  
6. 选择**创建**。

> **结果：** 已创建 Log Analytics 工作区，用于从 Azure 资源收集数据，以及从 Azure 存储收集诊断或日志数据。

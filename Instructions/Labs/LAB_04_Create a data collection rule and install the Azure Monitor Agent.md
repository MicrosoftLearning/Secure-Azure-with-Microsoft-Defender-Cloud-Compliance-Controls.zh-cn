---
lab:
  title: 练习 04 - 创建数据收集规则并安装 Azure Monitor 代理
  module: Module 05 - Create a data collection rule and install the Azure Monitor Agent
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


数据收集规则 (DCR) 指定要收集的数据，而 Azure Monitor 代理则应用这些规则从 Azure、其他云或本地的虚拟机收集日志和指标。 它们共同实现了跨不同环境的一致且集中的监视。

---

## 技能任务

- 创建和定义数据收集规则。

- 为数据收集选择目标资源。
  
- 配置数据源和目标。

- 选择数据源类型和要收集的数据。

- 选择数据传送目标。

## 练习说明 

### 创建和定义数据收集规则。

>**备注**：在目标 Log Analytics 工作区或 Azure Monitor 工作区所在的同一区域中创建数据收集规则。 可以将数据收集规则关联到租户中任何订阅或资源组中的计算机或容器。 
   
1. 在门户顶部的搜索框中，输入数据收集规则。 在搜索结果中选择数据收集规则。

2. 选择“+ 新建”。

![image](https://github.com/user-attachments/assets/e428c441-9d8d-4460-acd9-a97e2aa2b5af)

3. 在“**创建数据收集规则**”边栏选项卡的“**基本信息**”选项卡上，指定以下设置（将其他设置保留为默认值）：

    |设置|“值”|
    |---|---|
    |**规则详细信息**|
    |规则名称|**dcr-1**|
    |订阅|此实验室中使用的 Iginte 订阅的名称|
    |资源组|**az-rg-1**|
    |区域|**美国东部**|
    |平台类型|**Windows**|
    |数据收集终结点|*保留默认值“无”*|

![image](https://github.com/user-attachments/assets/eee884f6-b20f-4d51-9310-6e755746ed9a)   

4. 单击标签为“下一步: 资源 >”的按钮以继续操作。

5. 在“资源”选项卡上，选择 **+ 添加资源**。
  
>**备注**：Azure Monitor 代理将自动安装到所选的虚拟机（资源）上以便收集数据。
   
![image](https://github.com/user-attachments/assets/619106b4-7f5e-44dd-98c7-129689ab89c0)

6. 在“选择范围模板”中，选中“范围”选择中的 **Ignite-subscription** 框，然后单击**应用。**

![image](https://github.com/user-attachments/assets/c95b76cd-1515-47a5-b07b-02dcb28c0bf3)


8. 选择“查看 + 创建”。








> **结果**：您已创建数据收集规则并安装 Azure Monitor 代理。

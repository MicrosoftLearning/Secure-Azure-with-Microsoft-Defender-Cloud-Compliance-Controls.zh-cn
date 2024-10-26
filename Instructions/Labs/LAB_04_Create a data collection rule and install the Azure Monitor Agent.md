---
lab:
  title: 练习 04 - 创建数据收集规则并安装 Azure Monitor 代理
  module: Module 05 - Collect guest operating system monitoring data from Azure and hybrid virtual machines using Azure Monitor Agent
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


数据收集规则 (DCR) 指定要收集的数据，而 Azure Monitor 代理则应用这些规则从 Azure、其他云或本地的虚拟机收集日志和指标。 它们共同实现了跨不同环境的一致且集中的监视。

---

## 技能任务

- 创建和定义数据收集规则。

- 为数据收集选择目标资源。

- 安装 Azure Monitor 代理。
  
- 配置数据源和目标。

- 选择数据源类型和要收集的数据。

- 选择数据传送目标。

## 练习说明 

### 创建和定义数据收集规则，并安装 Azure Monitor 代理。

>**备注**：在 Log Analytics 或 Azure Monitor 工作区所在的同一区域中创建数据收集规则。 可以将其关联到租户中任何订阅或资源组中的计算机或容器。 Azure Monitor 代理将自动安装在 Azure 虚拟资源上。

1. 在门户顶部的搜索框中，输入**数据收集规则**。 在搜索结果中选择“**数据收集规则**”。
  
2. 在“**数据收集规则**”页上，选择“**+ 创建**”。
  
   ![image](https://github.com/user-attachments/assets/99b9ac51-f2f4-466f-80bb-79d74874b573)

3. 在**创建数据收集规则边栏选项卡**的“**基本信息**”页上，指定以下设置（将其他设置保留为默认值）：

    |设置|“值”|
    |---|---|
    |**规则详细信息**|
    |规则名称|**dcr-1**|
    |订阅|选择订阅。|
    |资源组|**az-rg-1**|
    |区域|**美国东部**|
    |平台类型|**Windows**|
    |数据收集终结点|将默认设置保留为“无”。|

    ![image](https://github.com/user-attachments/assets/35c527cf-499d-44b9-966f-0114b8643ef2)

4. 单击“**基本信息**”页底部标记为“**下一步: 资源 > 继续**”的按钮。
   
5. 在“**资源**”页上，选择“**+ 添加资源**”。

    ![image](https://github.com/user-attachments/assets/6aabf2c9-bea2-47c1-9b0b-bf131cdec4e3)

6. 在“**选择范围**”模板中，选中“**范围**”中的“**订阅**”框。

    ![image](https://github.com/user-attachments/assets/2215e8cd-5047-4fc6-91ba-b2c645571bbd)

7. 在“**选择范围**”模板底部，单击“**应用**”。
  
8. 在“**资源**”页底部，选择“**下一步：收集和传递 >**”。

    ![image](https://github.com/user-attachments/assets/717226c3-5ce0-454f-93a4-11b0e67d5a23)

9. 在**收集和传递页**上，单击“**+ 添加数据源**”。

    ![image](https://github.com/user-attachments/assets/0809cf5b-a460-40d1-8508-e42ba7ce78c1)

10. 在“**添加数据源**”模板的“**数据源类型**”下，选择以下设置。
    
    |设置|“值”|
    |---|---|
    |**添加数据源**|
    |选择要为资源收集的数据源类型和数据。|
    |数据源类型*|**Windows 事件日志**|
    |选择“基本”以启用事件日志收集。|
    |配置要收集的事件日志和级别：|
    |应用程序|**严重**、**错误**、**警告**|
    |安全性|**审核成功**、**审核失败**|
    |系统|**严重**、**错误**、**警告**|

    ![image](https://github.com/user-attachments/assets/5bc891ea-8cef-4baa-95c4-a432364179b1)

12. 在“**添加数据源**”模板底部，选择“**下一步：目标 >**”。
   
13. 在“**添加数据源**”模板的“**目标**”选项卡下，选择以下设置。
    
    |设置|“值”|
    |---|---|
    |**添加数据源**|
    |目标|**+ 添加目标**|
    |目标类型|**Azure Monitor 日志**|
    |订阅|选择订阅。|
    |目标详细信息|**azwrkspc1a (az-rg-1**)|

    ![image](https://github.com/user-attachments/assets/e00c17c8-5a70-4caa-8504-92f482cc5e57)

14. 在“**添加数据源**”模板底部，选择“**添加数据源**”。

    ![image](https://github.com/user-attachments/assets/4277089c-971c-4334-a49d-6ac6bfe93ff4)

15. 在“**收集和传递**”页面底部，选择“**查看 + 创建**”。

    ![image](https://github.com/user-attachments/assets/0235fed9-6309-444c-9269-b9dbd1118b63)

16. 在“**查看 + 创建**”页面底部，选择“**创建**”。

> **结果**：已创建数据收集规则并安装 Azure Monitor 代理。

---
lab:
  title: 练习 01 - 在 Azure 订阅上启用 Defender for Cloud
  module: Module 02 - Enable Defender for Cloud on your Azure subscription
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


本练习的主要目的是提供在 Azure 订阅中配置和启用 Microsoft Defender for Cloud 的实践经验。 这将使您能够监控和保护云资源免受安全威胁。 

---

## 技能任务

- 升级 Microsoft Defender for Cloud 订阅。
  
- 将 Microsoft Monitoring Agent 部署到必要的机器上，以实现全面覆盖。

## 练习说明

### 升级 Microsoft Defender for Cloud

1. 登录 [Azure 门户菜单。](https://portal.azure.com/)

2. 在 Azure 门户中，在 Azure 门户页面顶部的搜索资源、服务和文档文本框中，键入Microsoft Defender for Cloud，然后按 Enter 键  。

3. 在 **Microsoft Defender for Cloud** 的 **入门边栏选项卡中**，转到 **升级选项卡**。向下滚动，直到 **选择订阅和工作区以增强的安全功能** 部分可见。

4. 选择您的**订阅**和在模块 02 中创建的 **Log Analytics 工作区**，打开 Microsoft Defender 计划。

5. 单击页面底部的蓝色大**升级**按钮。
   
    ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/256bd584-b04f-4d5b-81a7-c83dd1af3b4f)
   
6. 在**Microsoft Defender for Cloud****入门边栏选项卡**上，转到**安装代理**选项卡并向下滚动。

    ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/8120ec8f-23dc-4636-bc45-b415c7894b8c)

7. 选中与要安装代理的订阅相关联的复选框，然后单击**安装代理**。

### 升级 Microsoft Defender for Cloud 订阅的替代操作。

1. 导航到**Microsoft Defender for Cloud**，然后在左侧导航面板中的管理部分下，单击**环境设置**。
   
2. 在**Microsoft Defender for Cloud **环境设置边栏选项卡上，单击**全部展开**，向下滚动直到出现您的订购，然后单击相关订购。

3. 在**设置、卫士计划**边栏选项卡上，选择**启用所有计划**，然后单击**保存**。

   ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Defender-for-Cloud-regulatory-compliance-controls/assets/91347931/4b684851-98ae-4720-a3e3-afa99aab8c43)




   

   
> **结果**：您已在 Azure 订阅上升级并启用了 Defender for Cloud。

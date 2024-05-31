---
lab:
  title: 练习 4 - 在 Defender for Cloud 中配置 Log Analytics 代理和工作区并进行集成
  module: Module 05 - Configure and integrate a Log Analytics agent and workspace in Defender for Cloud
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


Defender for Cloud 从 Azure 虚拟机 (VM)、虚拟机规模集、IaaS 容器和非 Azure 计算机（包括本地计算机）收集数据，以监视安全漏洞和威胁。 一些 Defender 计划要求监视组件从工作负载收集数据。 当 Log Analytics 代理启用时，Defender for Cloud 可在所有受支持的 Azure VM 以及创建的所有新 Azure VM 上部署代理。 

---

## 技能任务

- 使用代理类型的 Log Analytics 代理默认值。

- 选择工作区。
  
- 定义在工作区级别存储安全事件数据的级别。

## 练习说明 

### 配置与 Log Analytics 代理的集成。

>**注意**：当 Log Analytics 代理启用时，Defender for Cloud 可在所有受支持的 Azure VM 以及创建的所有新 Azure VM 上部署代理。 

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 在 Defender for Cloud 的菜单中，打开**环境设置**。

4. 选择你的订阅。

5. 在 Defender 计划的设置和监控覆盖范围列中，选择**设置和监控**。

7. 在 Log Analytics 行的配置列中，单击**编辑配置**。

8. 在自动配置配置模板中完成以下操作：

   - 在工作区选择下，单击**自定义工作区**。

   - 单击**下拉菜单**并**选择**之前创建的工作区。

   - 在**安全事件存储**下，单击**下拉菜单**并选择**所有事件**。

   - 在自动配置模板的底部，单击**应用**。
   
![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/c1c812e7-b5ca-4caa-b8e6-34a6e4b325fd)




> **结果**：您已在 Microsoft Defender for Cloud 中配置了 Log Analytics 代理和工作区。

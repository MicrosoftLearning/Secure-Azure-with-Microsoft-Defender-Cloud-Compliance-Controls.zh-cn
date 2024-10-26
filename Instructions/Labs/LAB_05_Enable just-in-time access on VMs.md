---
lab:
  title: 练习 05 - 在 VM 上启用实时访问
  module: Module 06 - Explore just-in-time VM access
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


可以使用 Microsoft Defender for Cloud 的实时 (JIT) 访问保护 Azure 虚拟机 (VM) 免遭未经授权的网络访问。 很多时候，防火墙包含使 VM 容易受到攻击的允许规则。 JIT 使你能够仅在需要访问时、在所需端口上以及在所需的时间段内允许访问 VM。 

---

## 技能任务

- 从 Azure 门户在虚拟机上启用 JIT。

- 从 Azure 门户请求访问已启用 JIT 的虚拟机。

## 练习说明 

### 从 Azure 虚拟机对 VM 启用 JIT

>**注意**：可以从 Azure 门户的 Azure 虚拟机页面对 VM 启用 JIT。

1. 在门户顶部的搜索框中，输入“虚拟机”。 在搜索结果中，选择“虚拟机”。

2. 选择 **vm-1**。
 
3. 从 vm-1 的“**设置**”部分中选择“**配置**”。
   
4. 在“**实时 VM 访问**”下，选择**启用实时。**

5. 在**即时虚拟机**访问下，单击 **Open Microsoft Defender for Cloud** 链接。

6. 默认情况下，VM 的实时访问使用以下设置：

   - Windows 计算机
   
     - RDP 端口：3389
     - 允许的最长访问时间：三小时
     - 允许的源 IP 地址：任意

   - Linux 计算机
     - SSH 端口：22
     - 允许的最长访问时间：三小时
     - 允许的源 IP 地址：任意
   
7. 默认情况下，VM 的实时访问使用以下设置：

   - 在**已配置**选项卡上，右键单击要向其添加端口的 VM，然后选择编辑。
  
 ![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Defender-for-Cloud-regulatory-compliance-controls/assets/91347931/66cf98b6-2ce0-43c7-a7be-b5d69bcfac1d)

   - 在**JIT VM 访问配置**下，可以编辑已保护的端口的现有设置，也可以添加新的自定义端口。
   - 编辑完端口后，选择**保存**。   

### 从 Azure 虚拟机的连接页请求访问启用了 JIT 的 VM。

>**注意**：如果 VM 启用了 JIT，则必须请求连接到它所需的访问权限。 不管你启用 JIT 的方式如何，你都可以通过任何受支持的方式请求访问权限。
   
1. 在 Azure 门户中，打开虚拟机页面。

2. 选择要连接到的 VM，然后打开**连接**页。

   - Azure 会查看是否已在该 VM 上启用了 JIT。

        - 如果没有为该 VM 启用 JIT，系统会提示你启用它。
    
        - 如果启用了 JIT，则选择**请求访问**，以便传递访问请求，其中包含已为该 VM 配置的请求 IP、时间范围和端口。

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Defender-for-Cloud-regulatory-compliance-controls/assets/91347931/7e454150-bc04-47bc-afa1-e0a1e8af17f9)






> **结果**：你已探索了有关如何在 VM 上启用 JIT 的各种方法，以及如何请求访问在 Microsoft Defender for Cloud 中启用了 JIT 的 VM。

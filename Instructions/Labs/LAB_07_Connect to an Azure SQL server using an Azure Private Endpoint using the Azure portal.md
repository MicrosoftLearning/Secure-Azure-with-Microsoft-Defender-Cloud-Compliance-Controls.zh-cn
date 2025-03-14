---
lab:
  title: 练习 07 - 通过 Azure 门户使用 Azure 专用终结点连接到 Azure SQL 服务器
  module: Module 08 - Connect to an Azure SQL server using an Azure Private Endpoint using the Azure portal
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


Azure 专用终结点是 Azure 中专用链接的构建基块。 它使 Azure 资源（例如虚拟机 (VM)）能够以私密且安全的方式来与 Azure SQL 服务器等专用链接资源通信。

---

## 技能任务

- 创建虚拟网络和堡垒主机。
  
- 创建虚拟机。
  
- 创建 Azure SQL 服务器和专用终结点。
  
- 测试到 SQL 服务器专用终结点的连接。

## 练习说明 

### 创建资源组和虚拟网络。

>**注意**：堡垒主机将用于安全地连接到虚拟机，以测试专用终结点。 

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 在门户顶部的搜索框中，键入“虚拟网络”****。 在搜索结果中，选择**虚拟网络**。

3. 在“**虚拟网络**”页面上，选择“**+ 创建**”。

4. 在**创建虚拟网络**的**基本信息**选项卡中，输入或选择以下信息：
   
   |设置|值|
   |---|---|
   |订阅|选择订阅。|
   |资源组|选择 **az-rg-1。**|
   |**实例详细信息**|
   |虚拟网络名称|输入 **vnet-2。**|
   |区域|选择 **(US)美国东部**。|  
    
5. 选择**下一步**，转到**安全性**选项卡。
  
6. 在“安全性”选项卡的 Azure Bastion 部分中选择“**启用 Azure Bastion**”。

>**备注**：Azure Bastion 是一项付费服务，可通过 TLS 为虚拟机提供安全的 RDP/SSH 连接。 在你通过 Azure Bastion 连接时，你的虚拟机无需公共 IP 地址。 

7. 在 **Azure Bastion** 字段中输入或选择以下信息：

   |设置|“值”|
   |---|---|
   |Azure Bastion 主机 |输入 **az-bastionhost-1a。**|
   |Azure Bastion 公共 IP 地址名称|选择“**创建公共 IP 地址**”|
   |添加公共 IP 地址|选择**确定**|

8. 选择“下一步”，转到“IP 地址”选项卡。

9. 在**子网**列下现有配置的“**IPv4 地址空间**”框中，单击**默认**条目。

10. 在“**编辑子网**”模板中，输入或选择以下信息：

    |设置|“值”|
    |---|---|
    |子网用途|将默认设置保留为“默认”。|
    |名称|**subnet-2**|
    |包括 IPv4 地址空间|将默认设置保留为复选标记。|
    |IPv4 地址范围|将默认设置保留为 10.0.0.0/16。|
    |开始地址|10.0.0.0.|
    |大小|将默认设置保留为 /24（256 个地址）。|
    |子网地址范围|10.0.0.0-10.0.0.255。|

11. 在“**编辑子网**”页底部，选择“**保存**”。

12. 在“**IP 地址**”页底部，选择“**查看 + 创建**”。

13. 在“**查看 + 创建**”页底部，选择**创建。**

>**注意**：Bastion 部署需要最多 15 分钟来完成实例化。
 
### 创建虚拟机。

>**注意：** 在此任务中，您将创建一个用于测试专用终结点的虚拟机。

1. 在门户中，搜索并选择“虚拟机”****。

2. 在**虚拟机**中，依次选择+ **创建**、**Azure 虚拟机**。

3. 在“创建虚拟机”的“**基本信息**”页中，输入或选择以下信息：

   |设置|“值”|
   |---|---|
   |Susbcription|选择订阅。|
   |资源组|选择 **az-rg-1。**|
   |**实例详细信息**|
   |虚拟机名称|输入**vm-3。**|
   |区域|选择 **(US)美国东部**。|
   |可用性选项|从“可用性区域”下拉菜单中，选择“**不需要基础结构冗余**”。|
   |安全类型|在“安全类型”下拉菜单中，选择“**标准**”。|
   |映像|选择**Windows Server 2022 Datacenter - x64 Gen2**。|
   |VM 架构|选择**x64**。|
   |使用 Azure Spot 折扣运行|将默认设置保留为“未选中”。|
   |大小|将默认设置保留为 Standard_D2s_v3-2 vcpus、8 GiB 内存。|
   |**管理员帐户**|
   |用户名|输入 **Tenantadmin2。**|
   |密码|输入 **Superuser#170。**|
   |确认密码|重新输入 **Superuser#170。**|
   |**入站端口规则**|
   |公共入站端口|选择**无**。|
   |选择入站端口|默认设置灰显。|

4. 选择“下一步: 磁盘”，然后选择“下一步: 网络”。
  
5. 在“**网络**”页中，输入或选择以下信息：

   |设置|值|
   |---|---|
   |**网络接口**|
   |虚拟网络|选择“**vnet-2**”。|
   |子网|将默认设置保留为 subnet-2 (10.0.0.0/24)。|
   |公共 IP|将默认设置保留为（新建）vm-3-ip。|
   |NIC 网络安全组|将默认设置保留为“无”。|
   |删除 VM 时删除 NIC|将默认设置保留为“选中启用加速网络”。|
   |负载均衡|将默认设置保留为“无”。|
  
6. 选择“查看 + 创建”。

7. 检查设置，然后选择**创建**。

### 创建 Azure SQL 服务器和专用终结点

>**注意：** 在此任务中，您将在 Azure 中创建一个 SQL 服务器。

1. 在门户顶部的搜索框中，输入 **SQL 数据库。** 在搜索结果中选择“SQL 数据库”。

2. 在“**SQL 数据库**”页上，选择“**+ 创建**”。
   
3. 在**创建 SQL 数据库**的**基本信息**选项卡中，输入或选择以下信息：

   |设置|值|
   |---|---|
   |订阅|选择订阅。|
   |资源组|选择 **az-rg-1。**|
   |**数据库详细信息**|
   |数据库名称|输入 **az-sql-db1a。**|
   |服务器|选择**新建**。|
   |**服务器详细信息**|
   |服务器名称|输入 **az-sql-srv1a。**|
   |位置|将默认设置保留为（美国）美国东部|
   |**身份验证**|
   |身份验证方法|选择**使用 SQL 身份验证**。|  
   |服务器管理员登录名|输入 **Tenantadmin2。**|
   |密码|输入**Superuser#170.**|
   |确认密码|输入**Superuser#170.**|

4. 选择确定****。
    
   |设置|值|
   |---|---|
   |**数据库详细信息**|
   |想要使用 SQL 弹性池|将默认设置保留为“否”。|
   |工作负载环境|将默认设置保留为“开发”。|
   |计算 + 存储|将默认设置保留为“常规用途 - 无服务器”。|
   |**备份存储冗余**|
   |备份存储冗余|选择**本地冗余备份存储**。|
   
5. 选择**网络**选项卡，或选择**下一步：网络**按钮。

6. 在**网络**选项卡中，输入或选择以下信息：

   |设置|值|
   |---|---|
   |**网络连接**|
   |连接方法|选择**专用终结点**。|
   |连接策略|将默认设置保留为“默认” - 对源自 Azure 内部的所有客户端连接使用“重定向策略”（专用终结点除外），并对源自 Azure 外部的所有客户端连接使用“代理”|
   |加密连接|将默认设置保留为“TLS.12”|

7. 在“**专用终结点**”部分，选择“**+ 添加专用终结点**”。

8. 选择“查看 + 创建”。

9. 选择“创建”。

10. 在**创建专用终结点**中，输入或选择以下信息：

       |设置|值|
       |---|---|
       |订阅|选择订阅。|
       |资源组|选择 **az-rg-1。**|
       |位置|选择**美国东部**。|
       |名称|输入 **az-pe1a。**|
       |目标子资源|将默认设置保留为 SqlServer。|
       |**联网**|
       |虚拟网络|选择“**vnet-2**”。|
       |子网|选择 **subnet-2。**|
       |**专用 DNS 集成**|
       |与私有 DNS 区域集成|将默认设置保留为“是”。|
       |专用 DNS 区域|将默认设置保留为（新建）privatelink.database.windows.net。|

12. 选择“确定”。

13. 选择**查看 + 创建**。

14. 选择“创建”。

>**备注**：Azure SQL Server 和专用终结点部署可能需要长达 10 分钟才能完成实例化。

### 允许某些公共 Internet IP 地址访问逻辑服务器。

>**备注**：在此任务中，假设要启用对 Azure SQL 服务器的所有公共访问，只允许从虚拟网络进行连接。 公共访问设置可能默认为**禁用。**

1. 在 Azure 门户搜索框中，输入 **az-sql-srv1a** 或前面步骤中输入的服务器名称。
   
2. 从 **az-sql-svr1a** 的“**安全**”部分中选择“**网络**”。
  
3. 在“**网络**”页上，转到“**公共访问**”选项卡。
  
4. 检查**公共网络访问**是否已禁用。 如果已禁用，选择“**选定网络**”进行公共网络访问。

>**备注**：来自以下“防火墙规则”部分中配置的 IP 地址的连接将有权访问此数据库。 默认情况下，不允许使用公共 IP 地址。

5. 如果需要，请转到“**网络**”页上的“**防火墙规则**”部分，然后选择“**+添加客户端 IPv4 地址**”（如果尚未在“**规则名称**”、“**起始 IPv4 地址**”和“**结束 IPv4 地址**”字段中填充客户端 IP 地址）。

   ![image](https://github.com/user-attachments/assets/fff5bfb1-53fd-40ea-9a31-5a095e7f3dbc) 

7. 选择**保存**。

### 测试到专用终结点的连接

>**注意**：在此任务中，您将使用在前面步骤中创建的虚拟机通过专用终结点连接到 SQL 服务器。

1. 在Azure 门户搜索框中，键入 **vm-3，** 然后从“资源”下拉列表中选择它。

2. 在 vm-3 的“**概述**”页上，选择“**连接**”，然后选择 **Bastion。**

3. 输入创建虚拟机时输入的用户名 **Tenantadmin2** 和密码 **Superuser#170**。

   **重要说明：** 重要说明：转到 Edge 设置并导航到“弹出窗口和重定向”****。 选择标记为“始终允许来自 https://portal.azure.com 的弹出窗口和重定向”**** 的径向选项，然后单击“完成”****。

4. 选择**连接**按钮。
  
5. 连接后，在服务器上打开 Windows PowerShell。

6. 若要验证专用终结点的名称解析，请在终端窗口中输入以下命令：

   ```bash
   nslookup server-name.database.windows.net

>**Note**: Replace **sqlserver-name** with the name of the SQL server you created in the previous steps. For example, enter **nslookup az-sql-srv1a.database.windows.net** You’ll receive a message similar to the one shown below:

   ````
   
   服务器：未知地址：168.63.129.16
   
   非权威答案：姓名：az-sql-srv1a.privatelink.database.windows.net 地址：10.1.0.5 别名：az-sql-srv1a.database.windows.net
   ````
   
>**Note**: A  private IP address of 10.1.0.5 is returned for the SQL server name. This address is in **az-sql-srv1a** subnet of **vnet-2** virtual network you created previously.

7. Install [SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?preserve-view=true&amp;view=sql-server-2017) on **vm-3.**
 
8. Open **SQL Server Management Studio.**

9. In **Connect to server,** enter or select this information:

    |Setting|Value|
    |---|---|
    |Server type|Leave the default setting as Database Engine.|
    |Server name|Enter **az-sql-srv1a.database.windows.net.**|
    |Authentication|Select **SQL Server Authentication.**|
    |User name|Enter **Tenantadmin2**.|
    |Password|Enter **Superuser#170**.|
    |Remember password|Select **Yes.**|
    |Connectivity Security|
    |Encryption|Leave the default setting as Mandatory.|
   
10. Select **Connect.**

11. Browse databases from left menu.

12. Close the remote desktop connection to vm-3.
  
> **Results**: You have connected to an Azure SQL server using an Azure Private Endpoint using the Azure portal.

---
lab:
  title: 练习 06a - 配置 Azure Key Vault 网络设置
  module: Module 07 - Configure Azure Key Vault networking settings
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


可以通过 Azure 门户将 Azure Key Vault 网络设置配置为与其他应用程序和 Azure 服务配合使用。 

---

## 技能任务

- 使用 Azure 门户创建密钥保管库。

- 将现有虚拟网络添加到防火墙和虚拟网络规则中。

- 配置虚拟网络和子网，允许访问密钥库。

## 练习说明 

### 使用 Azure 门户创建 Azure Key Vault。

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
  
2. 在门户顶部的搜索框中，输入“密钥保管库”****。 在搜索结果中选择“密钥保管库”****。

3. 从结果列表中选择“密钥保管库”****。

4. 在密钥保管库部分，选择创建****。

5. 在创建密钥保管库的基本信息选项卡中，输入或选择以下信息：********
   
   |设置|值|
   |---|---|
   |**项目详细信息**|
   |订阅|选择订阅。|
   |资源组|输入 **azure-rg-1**。|
   |**实例详细信息**|
   |密钥保管库名称|保管库名称必须只包含字母数字字符和虚线，且不能以数字开头。 *示例：az-securevault150*|
   |区域|选择“美国东部”。|
   |定价层|将默认设置保留为“标准”。|
   |保留已删除保管库的天数|将默认设置保留为 90。|

6. 选择**查看 + 创建**选项卡或页面底部的查看 + 创建按钮。
  
7. 选择**创建**。

### 配置密钥库防火墙和虚拟网络设置。

1. 在 Azure 门户搜索框中，输入“密钥保管库”****。

2. 浏览到先前创建的密钥库。

3. 选择“**设置**”，然后选择“**网络**”，再选择“**防火墙和虚拟网络**”选项卡。
   
4. 在允许的访问来源下，选择**允许来自特定虚拟网络和 IP 地址的公共访问**。

5. 在虚拟网络部分，选择 + **添加一个虚拟网络**，然后选择 + **添加现有虚拟网络。**

6. 在“**添加网络**”模板中，从“**虚拟网络**”下拉列表和“**子网**”下拉列表中选择先前创建的虚拟网络。

7. 在“**添加网络**”模板的底部，选择“**启用**”，然后选择“**添加**”。 

8. 在“**防火墙和虚拟网络**”页底部，选择“**应用**”。

  > **结果**：您已在 Azure 门户中创建了密钥库并配置了密钥库防火墙和虚拟网络设置。

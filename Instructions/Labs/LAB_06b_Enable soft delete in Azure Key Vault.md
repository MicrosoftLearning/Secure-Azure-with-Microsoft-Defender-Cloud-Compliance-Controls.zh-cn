---
lab:
  title: 练习 06b - 在 Azure 密钥保管库中启用软删除
  module: Module 07 - Configure Azure Key Vault networking settings
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


在未启用软删除的情况下删除密钥保管库，将永久删除密钥保管库中存储的所有机密、密钥和证书。 意外删除密钥保管库可能会导致永久丢失数据。 软删除允许在可配置的保持期内恢复意外删除的密钥保管库。

---

## 技能任务

- 验证是否对密钥保管库启用了软删除，并在未启用软删除的情况下将其启用。

## 练习说明 

### 验证是否对密钥保管库启用了软删除，并在未启用软删除的情况下将其启用

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 选择密钥保管库。

3. 在“设置”**** 边栏选项卡中，选择“属性”****。

4. 验证软删除旁边的单选按钮是否设置为**启用清除保护（强制删除的保管库和保管库对象的强制保留期）。**

5. 如果未在密钥保管库上启用软删除，请单击“**启用清除保护(对已删除的保管库和保管库对象实施强制保留期)**”单选按钮以启用软删除，然后单击“**保存**”。

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/06131a60-7f00-4764-a424-87ea41a78394)

> **结果**：已成功启用软删除，确保已删除的资源保留 90 天（默认）并可以恢复，从而有效地通过 Azure 门户撤销删除。

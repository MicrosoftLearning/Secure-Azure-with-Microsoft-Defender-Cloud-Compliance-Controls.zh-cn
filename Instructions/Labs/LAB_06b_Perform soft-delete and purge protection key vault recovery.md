---
lab:
  title: 练习 06b - 执行软删除和清除保护 - 密钥保管库恢复
  module: Module 07 - Configure Azure Key Vault networking settings
---


>**注意**：为了完成此实验室，你将需要一个 [Azure 订阅](https://azure.microsoft.com/en-us/free/?azure-portal=true)。 其中您拥有管理权限。 


您可以使用清除保护来防止恶意内部人员删除密钥库、密钥、机密和证书。 可以将此视为一个带有基于时间的锁的回收站。 你可以在可配置的保持期内随时恢复项。 在保持期结束之前，你将无法永久删除或清除密钥保管库。 保持期结束后，系统会自动清除密钥保管库或密钥保管库对象。

---

## 技能任务

- 验证是否对密钥保管库启用了软删除，并在未启用软删除的情况下将其启用。

- 列出、恢复或清除软删除的密钥保管库。

- 列出、恢复或清除已软删除的机密、密钥和证书。

## 练习说明 

### 验证是否对密钥保管库启用了软删除，并在未启用软删除的情况下将其启用

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 选择密钥保管库。

3. 单击**属性**边栏选项卡。

4. 确认软删除旁边的单选按钮是否设置为**启用清除保护**。

5. 如果未对密钥保管库启用软删除，请单击该单选按钮以启用软删除，然后单击**保存**。

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/06131a60-7f00-4764-a424-87ea41a78394)


### 列出、恢复或清除软删除的密钥保管库。

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 单击页面顶部的搜索栏。

3. 搜索**密钥保管库**服务。 不要单击单个密钥保管库。

4. 在屏幕顶部，单击管理已删除的保管库选项

5. 此时会在屏幕右侧打开一个上下文窗格。

6. 选择订阅。

7. 如果你的密钥保管库已被软删除，则它会显示在右侧的上下文窗格中。

8. 如果保管库过多，可以单击上下文窗格底部的加载更多，也可以使用 CLI 或 PowerShell 来获取结果。

9. 找到要**恢复**或清除的**保管库**后，选中其旁边的**复选框**。

10. 如果要恢复密钥保管库，请选择上下文窗格底部的恢复选项。

11. 如果要永久删除密钥保管库，请选择清除选项。

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/f41c0673-3832-4d3f-8b05-48e46e6c2282)


### 列出、恢复或清除已软删除的机密、密钥和证书。

1. 启动浏览器会话并登录到 [Azure 门户](https://portal.azure.com/)。
   
2. 选择密钥保管库。

3. 选择与要管理的机密类型（密钥、机密或证书）对应的边栏选项卡。

4. 在屏幕顶部，单击管理已删除项(密钥、机密或证书)

5. 此时会在屏幕右侧显示一个上下文窗格。

6. 如果机密、密钥或证书未显示在此列表中，则表明它没有处于软删除状态。

7. 选择要管理的机密、密钥或证书。

8. 选择上下文窗格底部用于恢复或清除的选项。

![image](https://github.com/MicrosoftLearning/Secure-Azure-services-and-workloads-with-Microsoft-Cloud-Security-Benchmark/assets/91347931/dab95f78-1642-4883-b56f-70e1e5320d45)


  > **结果**：您已在 Azure 门户中使用软删除和清除保护功能执行了 Azure 密钥库恢复管理。

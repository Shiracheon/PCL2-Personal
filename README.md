# PCL2-Personal

第三方基于 PCL 公开源码独立修改的 Windows 启动器，并非 PCL 官方发行版。原作者为龙腾猫跃，贡献者名单与原许可保留在完整源码及程序关于页中。

本修改版恢复 Minecraft 版本下载和整合包安装，关闭启动器自身更新、官方公告、官方新闻主页及遥测。保留微软正版登录流程、游戏下载、启动和模组管理的公开实现。名称、程序文件名和目录规则暂沿用原源码。

## 源码与构建方式

- [上游 PCL](https://github.com/Meloong-Git/PCL)，固定提交 `6b9a50df911c9d68b69b24c979efba477fb14b67`。
- [MeloongCore](https://github.com/Meloong-Git/MeloongCore)，固定提交 `98157d65c7627721c816c02e8be96ac4fe61d615`。
- `personal-build.patch.gz.b64` 是本仓库的修改补丁：Base64 解码后以 gzip 解压。工作流校验解压补丁的 SHA-256，再以 `git apply -p2` 应用于固定版本源码。
- 完整对应源码随 Windows 构建产物中的 `Personal-Source.zip` 提供，包括原许可、作者署名、修改说明和构建脚本。修改范围与配置细节见其中的 `PERSONAL-README.md`。

打开 [Actions](https://github.com/Shiracheon/PCL2-Personal/actions/workflows/windows-build.yml)，选择 **Run workflow**。默认产生测试包；成功后在该次运行底部的 Artifacts 下载 `PCL2-Personal-Windows`，解压产物和内部的 Windows ZIP 后运行 `Plain Craft Launcher 2.exe`。建议 Windows 10/11 x64 和 .NET Framework 4.8，并在独立空文件夹测试。

## 正版账号与模组服务

每位使用者登录自己的微软账号，无需自行注册开发者应用。维护者需配置自己注册、且已获 Minecraft 服务允许的 Microsoft 公共客户端应用。未配置的测试包不能完成微软正版登录；不能把测试编译成功当作登录验证。

维护者在仓库 Variables 设置 `PERSONAL_MS_CLIENT_ID`，然后选择 `distribution=true` 构建。若需要 CurseForge，另在 Secrets 设置按其条款取得的 `PERSONAL_CURSEFORGE_API_KEY`。不要提交玩家账号、密码、令牌或客户端密钥。CurseForge 尚未配置时不能保证其相关功能；Modrinth 和 Minecraft 使用各自的服务。

## 验证与范围

工作流检查源码与官方服务禁用策略，并在 Windows 编译、打包。实际安装游戏、图形界面、账号登录及多用户使用仍需 Windows 实机验证。下载源的独立网络检查已验证 Mojang 与 BMCLAPI 版本索引、版本元数据和小型依赖文件校验。

公开源码未包含的赞助主题、部分百宝箱内部实现及可直接使用的官方联机配置不在本次实现范围内。关闭自动更新后，协议变化需要维护者手动维护和重新构建。

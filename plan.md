# ShitBotUltra Minecraft 计划

状态：仓库已建立，当前只包含计划、协作入口和许可证，尚未实现插件或 SDK。

## 定位与语言

使用 **Java + Maven 多模块**，根包固定为 `shitbotteam.ultra.minecraft`。共用连接与协议代码归 `.bridge`，公开 API 归 `.api`，平台入口分别放在 `.bukkit`、`.velocity`、`.bungee`、`.nukkit`。

JAR 是游戏侧薄适配器：监听事件并转发给 Core，按请求采集游戏数据，在正确线程应用 Core 的授权结果和执行游戏动作。群命令业务、机器人连接、SQL 存储与图片渲染由 Core 处理。

## 组件范围

| 范围 | 本仓库责任 |
| --- | --- |
| 连接 | 使用 Core 发布的 Bridge 契约，完成身份认证、握手、能力协商与有界重连 |
| 事件与快照 | 采集登录、退出、聊天、状态、背包等平台数据，按协议标记来源与事件标识 |
| 游戏动作 | 按能力和权限限制执行游戏操作，处理超时与结果未知，不盲目重发有副作用的命令 |
| 调度 | 将平台对象访问切回正确线程；Folia 按实体 / 区域调度，不阻塞游戏线程等待网络 |
| 登录与状态缓存 | 应用 Core 决策，保留明确期限的必要状态；断线策略按公共协议实施，不另造白名单数据库 |
| 插件 API | 后续提供异步 Java 桥接 API；明确离线、超时与回调线程语义 |
| bStats | Bukkit、BungeeCord、Velocity 使用各自官方集成与 Ultra 独立 ID；缺少 ID 时不上报 |

所有协议字段、消息顺序、登录策略、代理与后端去重规则统一在 Core 文档维护，本仓库不创建另一份协议。

## 本仓库任务

1. 优先落实 Paper 单服适配，再按计划扩展 Folia、Velocity / BungeeCord 和 Nukkit-MOT；正式首发矩阵由维护者确定。
2. 建立共享 Bridge 与平台模块，固定协议来源版本；各平台独立输出 JAR，明确各自 Java 运行要求。
3. 配合 Core 与 CLI 打通文本互通、账号绑定、登录授权和必要状态采集，后续按普通版迁移表补能力。
4. 维护者提供 bStats 项目 ID 后接入对应平台统计，保留全局与项目关闭方式。Nukkit-MOT 的统计接入方式待确认，不冒用 Bukkit 身份。
5. 随后完善异步插件 API、占位符、代理多服与发行说明；第三方接口和未确定能力继续登记在 Core 公共计划。

Maven 坐标、平台模块目录与产物名称以 Core 的结构文档为准；这里不提前生成工程骨架或承诺兼容结果。普通版作为迁移参考，复用其代码时遵守原许可与版权声明。

## 公共文档引用

- [总体规划](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/plan/01-总体规划.md)：组件边界、语言、进程与阶段。
- [仓库结构与开发规范](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/plan/02-仓库结构与开发规范.md)：Java 包名、Maven 模块、平台依赖与产物。
- [协议配置与迁移](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/plan/03-协议配置与迁移.md)：Bridge、普通版能力迁移、登录、去重和 bStats。
- [思维导图](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/plan/04-思维导图.md)：四组件关系。
- [共享 Agent 规则](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/agent.md)与[贡献指南](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/CONTRIBUTING.md)：工作范围、提交格式、签名与 PR。

公共文档不在本仓库复制。许可证为 [AGPL-3.0-only](LICENSE)，统一说明见 [Core 许可证说明](https://github.com/ShitBot-Team/ShitBotUltra/blob/main/docs/licensing.md)。README 后续再写；后续实现范围由维护者指定，测试由维护者自行安排。

---
name: engineering-topics
description: "工程专题手册：46 篇工程专题加 2 篇速判页，按任务加载，覆盖 API 设计、MySQL 与数据库、领域驱动设计、分布式系统、重构、代码审查、测试生成、根因调试、威胁建模、LLM 应用安全、生产就绪与 SLO、Java/Laravel/CMS 专项、前端设计、架构决策与选型、Spec 驱动开发、任务拆解与项目记忆等。用于需要专业判据而非通用建议的实现、审查、排障与设计工作；支持 @专题标识 直接定位。只问概念时直接回答。"
metadata:
  slug: "engineering-topics"
  displayName: "工程专题手册"
  version: "1.0.0"
  summary: "46 篇上游工程专题加 2 篇速判页，附本地路径与行段查找器"
---

# 工程专题手册

本技能是一部可按任务翻阅的工程专题库，内容派生自 **编程专家 2.0.3**（原作者 智慧&半岛-www.52yuer.cn，原包声明 MIT），保留原作者署名与 MIT 声明。作者与版权边界见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。本名称不表示原作者、腾讯或华为联合发布、认证或背书。

它只提供判据与检查方法，不代替对当前代码库的实际勘察：任何结论仍要落到本次项目的真实文件、真实调用与真实输出上。

## 执行原则与规则优先级

本页是共同执行规则。专题在各自场景补充具体判据；专题里的历史固定模板、轮数、加载预算和环境建议不得扩大用户授权或覆盖以下原则。

1. **先理解现场再动手。** 确认项目约定、真实入口、版本、用户已有改动与验收目标。沿用现有风格和架构；关键假设用文件或小实验核实，不能为局部修复强制换技术栈。
2. **最小完整实现。** 找到生产者、消费者、存量数据和失败分支，改实际接线源码。新增抽象、依赖、兼容层必须解决本次约束；保护用户已有修改，只清理本次变更产生的冗余。
3. **继承既有授权。** “实现”“修好”“审查并修复”包含范围内的可逆本地工作和必要验证；“只看”“先评估”保持只读。目标、业务后果或权限确有缺口时只等待依赖该答案的部分。外部部署、费用、生产数据、公开分享等按具体目标与既有授权执行；需要新授权时准备具体方案再询问，沉默或超时不会产生授权。
4. **验收驱动，结果有据。** Bug 先复现或说明复现缺口；修改后重走真实调用与必要回归。构建、安装、截图、接口成功和实际业务通过分开报告。有效旧证据可复用，代码/环境变化或缺口再补验；不修改验收来掩盖失败。
5. **按需加载，持续推进。** 小改动直接定位、改动和核对，复杂任务按边界安排计划和检查点。只读当前领域及直接依赖的小节，不要求每次通读全部专题、填写全套模板或固定内部思考篇幅。每次重试检验新假设；仍有证据进展就继续，确有外部阻塞时留下可执行交接。
6. **凭据隔离。** 模型只使用凭据文件路径和脱敏状态，秘密由宿主或可信程序在进程内读取。不得要求用户粘贴 Token、持久化到模型记忆、输出认证头/完整环境/含秘密日志或写入包中。普通知识文本和云账单状态不等于后端授权。

前四条参考 Karpathy 相关编码理念，并沿用上游对应专题；本版本的表达调整与冲突修正已注明来源与修改。

## 路由：一个入口，按任务读取

用户开头或独立段落中的 `@<专题标识>` 用于明确选择本包参考，不是另一个必须安装的 Skill。明确意图优先，多领域围绕当前主目标组合，不因显式标签机械停下重复确认。

| 当前目标 | 首选资料 |
| --- | --- |
| 不确定该读哪篇、想先看全部专题 | [工程专题目录](references/expert-topics.md)，全部专题一览 |
| 通用实现、Bug、审查、重构、测试、性能、Spec、选型、文档 | [工程专题目录](references/expert-topics.md)，只打开对应主题 |
| 接口契约、版本兼容、错误码、幂等 | [API 设计](references/api-design.md) |
| 表结构、SQL 安全、索引、慢查询、迁移回滚 | [MySQL 与数据库](references/mysql-database.md) |
| 领域边界、聚合、事务一致性、贫血模型 | [领域驱动设计](references/domain-driven-design.md) |
| 分布式事务、一致性、分片、消息、故障隔离 | [分布式系统](references/distributed-systems.md) |
| 架构取舍、技术选型、演进路线、技术战略 | [架构决策](references/architecture-decision.md)、[技术选型](references/tech-selection.md)、[技术战略](references/technical-strategy.md) |
| 结构性改造、遗留代码、去重复、迁移旧范式 | [重构](references/refactoring.md) |
| 代码审查、改动评估、合并前把关 | [代码审查](references/code-review.md) |
| 补测试、特征测试、覆盖率是否真实 | [测试生成](references/test-generation.md)，速判见 [测试与验证](references/testing.md) |
| 疑难 Bug、反复修不好、需要根因 | [Bug 诊断](references/bug-diagnosis.md)、[根因调试](references/root-cause-debugging.md) |
| 安全设计、权限、注入面、依赖引入前审查 | [威胁建模](references/threat-modeling.md)，速判见 [安全与信任边界](references/security.md) |
| 模型应用、提示注入、工具调用、检索内容可信度 | [LLM 应用安全](references/llm-application-security.md) |
| 上线前检查、SLO、容量、灰度与回滚 | [生产就绪](references/production-readiness.md)、[事故复盘与 SLO](references/incident-review.md) |
| Java / Java 测试 | [Java 专项](references/java-development.md)、[Java 测试](references/java-testing.md) |
| Laravel / CMS 二次开发 | [Laravel 开发](references/laravel-development.md)、[CMS 开发](references/cms-development.md) |
| JavaScript / 前端设计 / 样式对齐 / 设计审计 | [JavaScript](references/javascript-development.md)、[前端设计](references/frontend-design.md)、[样式对齐](references/style-alignment.md)、[设计审计](references/design-audit.md) |
| 接口设计的认知负荷、方案评审 | [设计评审](references/design-critique.md) |
| 需求不清、先写规格再实现 | [Spec 驱动开发](references/spec-driven-development.md) |
| 长任务、子任务拆分、中断继续 | [任务拆解与执行](references/task-decomposition-and-execution.md) |
| 跨会话记忆、项目约定沉淀、交接 | [项目记忆](references/project-memory-management.md)、[阶段导航](references/dev-navigation.md) |
| 记录踩过的坑、判断回溯 | [判断回溯录](references/error-ledger.md) |
| 大仓库依赖与符号图谱 | [项目知识图谱](references/project-knowledge-graph.md) |
| 辅助脚本与 hooks 的已知边界 | [工具边界](references/legacy-tools.md)、[工具清单](references/legacy-tools-index.md) |
| 新建软件项目、网站项目的总控 | [软件项目](references/software-project.md)、[网站项目](references/website-project.md) |

沿用上游六步工作框架：分析 → 方案 → 执行 → 验证 → 交付 → 必要复盘。开始时先读目标代码和调用方；只有与本次目标有关的专题需要读取。概念问答直接解释，环境缺失时完成能独立推进的部分并具体标明待验条件。

## 专题的两种用法

**速判优先。** [测试与验证](references/testing.md) 与 [安全与信任边界](references/security.md) 是本包新增的两篇短页，按「能不能证明」「边界在哪里」组织，用于快速判断；它们各自指向 [测试生成](references/test-generation.md)、[威胁建模](references/threat-modeling.md) 等深度篇，两者冲突时以深度篇为准。

**深度篇按需读。** 46 篇专题沿用上游写法，开头有「输入要求」与必填信息清单。那是为了把模糊需求收敛成可验收判断，不是要求每次填表；信息已在对话中给全时直接跳到判据部分。

## 实际文件查找与调用

下面路径均相对本技能的安装目录，不能假设用户工程里也有同名 `scripts/`。目录移动后，以当前入口位置定位本技能根目录。

Python 可用时，用[本地专题查找器](scripts/skill_lookup.py)取得文件路径、源小节锚点和 `start_line/end_line`；它只读[集成索引](references/integration-map.json)，不联网、不下载、不安装、不调用云或执行其他脚本：

```text
python3 "<本技能目录>/scripts/skill_lookup.py" --list
python3 "<本技能目录>/scripts/skill_lookup.py" @mysql-database
python3 "<本技能目录>/scripts/skill_lookup.py" @threat-modeling
```

读取查找结果指定的行段，按返回路径继续追踪本包链接。没有 Python 时，直接读 [工程专题目录](references/expert-topics.md)，标识即文件名。

本包附带上游的可选辅助源码与 hooks 模板，原样保留。它们的执行、失败提示和写入限制仍有已知缺口，见[工具边界](references/legacy-tools.md)。**只加载本技能不会启用任何 hook**；不要自动运行安装器，也不要把文件存在当作已生效的保护。使用任何会写入工程、备份或配置的脚本前，先核对源码、目标及用户授权，必要时在隔离副本验证。

这是知识与判据包，不包含账号、付费服务、SDK、IDE 或后端权限。无需为了使用本包安装 MCP、注册 hooks、改全局配置或部署云服务；实际需要且有授权时才执行对应接入。

交付先报已完成结果，再给改动位置、当前代码/环境的实际验证和剩余事项。部分完成、mock、仅构建或未连接到真实环境都如实说明；不虚构线上地址、已支付状态或兼容结果。

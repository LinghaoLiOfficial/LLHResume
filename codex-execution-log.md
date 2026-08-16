## 2026-08-16 20:30 +08 - 新增科研项目经历

- Request: 用户要求把核心技术材料文件对应的 `【大数据科研论文AI定位评估机制，2026.05 - 2026.06，中国科学院大学】` 项目写进“项目&研究经验”模块。
- Actions: 修改 `src/views/resume/Resume.vue`，在“项目&研究经验”顶部新增一条 2026.05 - 2026.06 的项目卡片，补充项目标题、机构、方法说明以及时间与位置标签；随后运行构建验证。
- Result: 简历页面已包含该科研项目条目，文案聚焦论文摘要中的 AI 使用环节识别、功能识别、AI 定位与必要性评估四维机制。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 20:38 +08 - 强化科研项目收益表述

- Request: 用户要求在该科研项目描述中补充并批量进行的 LLM 推理提速和 Token 成本下降。
- Actions: 修改 `src/views/resume/Resume.vue` 中项目描述段落，加入“极大加快 LLM 总体推理速度”和“显著降低 Token 成本”的收益表述，并重新构建验证。
- Result: 该项目条目现在同时体现方法框架与实际收益，表达更完整。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:06 +08 - 更新网页标签标题与图标

- Request: 用户要求将网页标签名称更换为 `Linghao Li Resume`，并为网页标签寻找一个炫酷的 icon。
- Actions: 修改 `index.html` 的 `<title>` 与 favicon 引用，新增 `public/favicon.svg` 作为霓虹渐变 `LL` 简历图标，并保留 `public/favicon.ico` 作为兼容回退。
- Result: 浏览器标签标题现在显示为 `Linghao Li Resume`，现代浏览器会优先使用新的 SVG favicon。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:08 +08 - 调整 favicon 为单个居中 L

- Request: 用户要求将 favicon 的两个 `L` 改为一个水平垂直居中的 `L`。
- Actions: 修改 `public/favicon.svg`，将双 `L` 路径替换为单个居中的粗体 `L`，并更新 SVG 描述文本。
- Result: favicon 保留霓虹渐变和发光背景效果，主体标记变为单个居中 `L`。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:09 +08 - 去除 favicon 装饰线

- Request: 用户要求去除 favicon 中的两条线。
- Actions: 修改 `public/favicon.svg`，删除斜向蓝色装饰线和底部粉色装饰线。
- Result: favicon 现在仅保留背景和居中 `L` 主体。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:11 +08 - 删除 ICO favicon

- Request: 用户要求删除 `public/favicon.ico`。
- Actions: 删除 `public/favicon.ico`，并移除 `index.html` 中指向 `/favicon.ico` 的回退引用。
- Result: 项目现在仅使用 `public/favicon.svg` 作为网页标签图标。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:14 +08 - 调整姓名展示

- Request: 用户要求将“李凌浩”和“Linghao Li”改为上下两排，中文在上、英文在下，并将英文改为 `Linghao Li (Lion)`。
- Actions: 修改 `src/views/resume/Resume.vue` 的头部姓名区域，将横向双标题改为居中的垂直排列。
- Result: 简历头部姓名现在上方显示 `李凌浩`，下方显示 `Linghao Li (Lion)`。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:37 +08 - 新增微信与 WhatsApp 联系方式

- Request: 用户要求在邮箱和电话下方增加微信和 WhatsApp，号码与电话一致，并询问如何排版。
- Actions: 修改 `src/views/resume/Resume.vue`，在联系方式列表中按原有图标、标签、号码的纵向排版新增微信和 WhatsApp。
- Result: 左侧联系方式现在依次显示邮箱、电话、微信、WhatsApp，微信和 WhatsApp 使用与电话相同的号码。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:38 +08 - 合并重复联系号码

- Request: 用户采纳对重复电话号码冗余的评估，要求修改联系方式排版。
- Actions: 修改 `src/views/resume/Resume.vue`，将电话、微信、WhatsApp 三个重复号码合并为一个“联系号码”条目，并在下方注明 `Phone · WeChat · WhatsApp`。
- Result: 左侧联系方式现在只显示一次号码，信息更紧凑清晰。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:39 +08 - 中文化联系渠道说明

- Request: 用户要求将联系方式渠道说明中的 `WeChat` 和 `Phone` 改为中文。
- Actions: 修改 `src/views/resume/Resume.vue`，将 `Phone · WeChat · WhatsApp` 改为 `电话 · 微信 · WhatsApp`。
- Result: 联系号码下方的渠道说明现在为中文优先，保留 WhatsApp 品牌名。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:41 +08 - 垂直居中右侧能力简介

- Request: 用户要求将简历头部右侧四段能力简介内容垂直居中。
- Actions: 修改 `src/views/resume/Resume.vue`，将右侧能力简介外层容器改为 `flex h-full flex-col justify-center`。
- Result: 四段能力简介会作为整体在 header 右栏中垂直居中，与左侧头像、姓名和联系方式区域对齐更自然。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 14:46 +08 - 更新 NTU 教育背景中英文信息

- Request: 用户要求将海外教育背景中的南洋理工大学、学位和专业名称补充为中英文展示，并将“硕士”改为“理学硕士”。
- Actions: 修改 `src/views/resume/Resume.vue` 的教育背景首条记录，将学校、学位和专业分别更新为 `南洋理工大学 Nanyang Technological University (NTU)`、`理学硕士 MSc`、`企业人工智能专业 Enterprise Artificial Intelligence`。
- Result: 南洋理工大学教育经历现在以中英文并列方式展示，更准确体现海外院校与学位名称。
- Verification: 已用 `rg` 核对目标文本，并运行 `npm run build`，构建通过。

## 2026-08-16 15:45 +08 - 扩写 AAAI 论文标签

- Request: 用户要求模仿其他论文条目的写法，扩写 `二作，人工智能方向，AAAI 会议，CCF-A` 这一行文本。
- Actions: 修改 `src/views/resume/Resume.vue` 中 MetaphorTree 会议论文的标签行，补充 AAAI 的国际顶级会议、CCF-A、人工智能研究核心阵地和多模态理解与推理方向认可度表述。
- Result: 该论文条目现在与其他科研成果的“作者身份 + 方向 + 平台 + 含金量标签”表达风格保持一致。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 16:02 +08 - 增加教育背景位置标签

- Request: 用户要求为教育背景中的学校增加位置标签，南洋理工大学为新加坡，浙江工业大学为浙江杭州。
- Actions: 修改 `src/views/resume/Resume.vue` 的三条教育经历，将右侧日期区域扩展为位置与时间两枚胶囊标签，并使用 `lucide:map-pin` 图标标识位置。
- Result: 南洋理工大学条目显示 `新加坡`，两条浙江工业大学条目显示 `浙江杭州`，日期信息保持原有展示。
- Verification: 已运行 `npm run build`，构建通过，并用 `rg` 核对三处位置标签。

## 2026-08-16 16:03 +08 - 调整教育背景标签顺序

- Request: 用户要求将教育背景卡片右侧的位置和时间上下互换。
- Actions: 修改 `src/views/resume/Resume.vue`，将三条教育经历右侧胶囊标签调整为时间在上、位置在下。
- Result: 教育背景右侧信息现在先显示时间，再显示带 `lucide:map-pin` 图标的位置。
- Verification: 已运行 `npm run build`，构建通过，并检查教育背景代码片段确认顺序。

## 2026-08-16 16:11 +08 - 项目研究经验倒序排序

- Request: 用户要求“项目&研究经验”按照时间顺序倒着排序。
- Actions: 修改 `src/views/resume/Resume.vue`，将“项目&研究经验”中的 11 张项目卡片按显示起始时间从新到旧重排。
- Result: 项目顺序现在从 `2025.04 - 2025.06` 的物流运输成本优化算法开始，到 `2023.06 - 2024.10` 的科技资源检索引擎后端结束。
- Verification: 已运行 `npm run build`，构建通过，并抽取 section 日期序列确认倒序。

## 2026-08-16 16:18 +08 - 项目经历增加位置胶囊标签

- Request: 用户要求将“项目&研究经验”中各项目的位置改为教育背景中的位置标签样式。
- Actions: 修改 `src/views/resume/Resume.vue`，将项目卡片机构行中的城市拆出，统一放到右侧时间下方的 `lucide:map-pin` 胶囊标签中。
- Result: 11 张项目卡片均采用“时间在上、位置在下”的双胶囊标签布局，机构行只保留机构或团队名称。
- Verification: 已运行 `npm run build`，构建通过，并核对项目 section 中共有 11 个位置标签。

## 2026-08-16 17:20 +08 - 新增出生日期

- Request: 用户询问如何增加出生日期 `2002年11月21日`。
- Actions: 修改 `src/views/resume/Resume.vue` 的头部左侧信息区，在联系方式下方新增出生日期条目，并使用 `lucide:calendar-days` 图标。
- Result: 简历头部左栏现在显示 `出生日期` 和 `2002 年 11 月 21 日`。
- Verification: 已运行 `npm run build`，构建通过，并检查头部信息片段。

## 2026-08-16 17:32 +08 - 工作经历增加位置标签

- Request: 用户要求工作经历也增加位置标签，且两条均为浙江杭州。
- Actions: 修改 `src/views/resume/Resume.vue` 的两条工作经历，将右侧单个时间标签扩展为时间与 `lucide:map-pin` 位置双胶囊标签。
- Result: 浙江火炬生产力促进中心有限公司和杭州国信大数据应用研究院两条工作经历均显示 `浙江杭州` 位置标签。
- Verification: 已运行 `npm run build`，构建通过，并核对工作经历 section 中共有 2 个位置标签。

## 2026-08-16 18:08 +08 - 融合 Vibe Coding 与实验室科研经验

- Request: 用户要求保留头部四条主线不变，并把 `Vibe Coding` 和 `实验室科研经验` 作为子表达塞进去。
- Actions: 修改 `src/views/resume/Resume.vue` 的头部能力简介文案，在 `AI 模型算法工程化落地` 中加入 Vibe Coding 的需求拆解、原型验证与迭代落地表述，在 `跨领域技术结合` 中加入实验室科研经验与文献研读、实验设计、复现验证说明。
- Result: 头部四条主线保持不变，但两个补充能力已自然嵌入现有文案。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 18:22 +08 - 撰写医院病历项目说明

- Request: 用户要求为 `【技术顾问】医院病历文本挖掘和病历质量监控模型` 撰写说明，重点体现 LLM 专家经验、小样本标准库和 CNN 改进。
- Actions: 修改 `src/views/resume/Resume.vue` 中该项目卡片的描述段落，补充基于 LLM 专家经验构建高质量小样本标准库、结合 CNN 改进训练流程和特征表达、提升识别准确率与 F1 的说明。
- Result: 该项目条目现在完整说明了方法链路和效果目标，适合简历展示。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 19:16 +08 - 新增核心演讲经历模块

- Request: 用户要求在“调研&参会经历”开头新增模块，重点突出 POMS 国际学术会议和浙江工业大学 MBA 企业高管课堂两段台上演讲经验。
- Actions: 修改 `src/views/resume/Resume.vue`，新增 `FeaturedSeminarItem` 类型和 `featuredSeminarData` 数据，并在表格前增加两张响应式精选演讲卡片；同步更新项目技术文档。
- Result: “调研&参会经历”现在采用“核心演讲经历卡片 + 完整表格”的结构，强化国际学术会议、高管课堂、台上分享和现场答疑信号，原 `seminarData` 表格记录保持完整。
- Verification: 已运行 `npm run build`，构建通过；已用本地浏览器检查桌面和移动视口，确认精选卡片存在、表格仍保留 POMS 与 MBA 两条记录，移动端卡片未横向溢出。

## 2026-08-16 19:22 +08 - 修复 localhost 8080 Upgrade Required

- Request: 用户反馈访问 `http://localhost:8080/` 时只显示 `Upgrade Required`，没有页面内容。
- Actions: 检查 `8080` 与 `5173` 端口监听状态，停止异常 Vite 进程，修改 `vite.config.ts` 移除硬编码的 `server.hmr.port = 8080`，重新以 `npm run dev` 启动默认 `8080` 服务。
- Result: `http://localhost:8080/` 现在正常返回简历页面 HTML，避免 HMR WebSocket 与页面 HTTP 服务抢占同一端口。
- Verification: 已用 `curl -i http://localhost:8080/` 确认返回 `HTTP/1.1 200 OK` 和 HTML；已运行 `npm run build`，构建通过。

## 2026-08-16 20:17 +08 - 收窄参会经历地点列宽度

- Request: 用户要求缩小“调研&参会经历”模块的“地点/机构”字段宽度。
- Actions: 修改 `src/views/resume/Resume.vue` 中该表格列的 `th`/`td` 样式，给“地点/机构”列设置固定宽度并允许长文本换行。
- Result: 地点/机构列不再被长英文机构名撑宽，表格整体更紧凑。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 21:51 +08 - 新增 AI 暴露度计算项目经历

- Request: 用户要求将核心技术材料对应的 2025.08 - 2026.07 中国科学院大学项目写入“项目&研究经验”，并与已有 LLM 专家定位评估项目区分。
- Actions: 阅读用户提供的 AI 暴露度计算 PDF 与 Markdown 技术材料，修改 `src/views/resume/Resume.vue`，在项目模块新增 `【科研计量实验】AI 暴露度计算与科研方法替代潜力测算程序` 独立条目；同步更新项目技术文档。
- Result: 新条目展示了三阶段 AI 暴露度测算框架、AI 技术库与历史方法库匹配、分块持久化、批量 LLM 推理提速和总体调用成本下降，已有 2026.05 - 2026.06 的 LLM 专家定位评估项目保持独立。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:00 +08 - 优化两个中科院项目描述边界

- Request: 用户要求优化“百万级科研论文 LLM 专家定位评估实验程序”和“百万级 AI 暴露度计算与科研方法替代潜力测算程序”的描述，明确前者关注已使用 AI 论文中的 AI 重要程度，后者关注能源转型与气候变化全量论文使用 AI 进行科研的潜力。
- Actions: 修改 `src/views/resume/Resume.vue` 中两个中国科学院大学项目的描述段落，并更新 `codex-project-tech-doc.md` 中的项目边界说明。
- Result: 两个条目的研究对象和指标含义已分清：前者强调 AI 方法学定位与必要性强度，后者强调全量主题论文科研流程被 AI 原生方法重构或替代的潜力。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:07 +08 - 补充 AI 暴露度项目依赖式三阶段难点

- Request: 用户要求在“百万级 AI 暴露度计算与科研方法替代潜力测算程序”条目中体现三阶段逻辑依赖，不能直接全量批量推理。
- Actions: 修改 `src/views/resume/Resume.vue` 中该项目的描述段落，并同步更新 `codex-project-tech-doc.md` 的项目边界说明。
- Result: 项目描述现在明确了先筛选、再阶段映射、再暴露度计算的依赖式流程，以及无法一步式对全量论文直接批推的技术约束。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:12 +08 - 精简 AI 暴露度项目表述

- Request: 用户要求进一步优化“百万级 AI 暴露度计算与科研方法替代潜力测算程序”条目的文字表述。
- Actions: 精简 `src/views/resume/Resume.vue` 中该项目的描述句式，并同步收紧 `codex-project-tech-doc.md` 的项目边界说明。
- Result: 描述更清楚地突出了“全量相关论文”“三阶段依赖式测算”“无法一步式批推但仍可高效运行”。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:18 +08 - 修正 AI 暴露度句式冲突

- Request: 用户指出“因此无法直接对全量论文一步式批量推理，但仍可支持百万级论文规模的高效运行”表述不够顺。
- Actions: 修改 `src/views/resume/Resume.vue` 中对应句子，将其改写为分阶段串联处理的表达，并同步更新 `codex-project-tech-doc.md`。
- Result: 句子从“否定一步式推理 + 反向补充高效运行”改为“分阶段串联处理 + 支撑百万级高效运行”，语义更顺。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:17 +08 - 新增公共管理学报论文科研成果

- Request: 用户要求将论文《人智协同驱动的复杂网络舆情涌现机制及其生成式治理研究》写入“科研成果”，并标注学生一作、公共管理学报期刊、评审一轮中、2026.04 - 至今。
- Actions: 只读提取用户提供的 DOCX 论文标题与摘要信息，修改 `src/views/resume/Resume.vue`，在“科研成果”顶部新增对应期刊论文卡片；同步更新 `codex-project-tech-doc.md`。
- Result: 简历科研成果已新增该论文，包含评审状态、作者身份、期刊平台、时间与基于摘要概括的研究说明。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 22:20 +08 - 优化公共管理学报论文方向标签

- Request: 用户要求优化科研成果中“复杂治理与数字治理方向高度契合”的表述。
- Actions: 修改 `src/views/resume/Resume.vue` 中该论文绿色标签行，将方向匹配表述改为更具体的“复杂系统治理、数字治理与人智协同前沿议题”。
- Result: 该科研成果条目的期刊与方向标签更贴合论文主题和公共管理表达。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 23:02 +08 - 提炼个人介绍总结

- Request: 用户要求模仿给定格式，总结当前简历人物的背景与核心技能。
- Actions: 只读核对 `src/views/resume/Resume.vue` 中的姓名、教育背景、能力简介、项目研究与演讲经历。
- Result: 提炼出李凌浩以企业人工智能、LLM 科研应用、跨领域算法结合、全栈 Web 开发和项目协作为核心的复合型画像。
- Verification: 已完成简历内容交叉核对，未修改业务代码。

## 2026-08-16 23:15 +08 - 新增新能源汽车舆情评估论文科研成果

- Request: 用户要求将论文《基于大语言模型复合决策网络的新能源汽车负面舆情动态评估框架》写入“科研成果”，并标注一作、撰写中、2026.06 - 至今。
- Actions: 只读参考用户提供的技术框架材料，修改 `src/views/resume/Resume.vue`，在“科研成果”顶部新增对应期刊论文卡片；同步更新 `codex-project-tech-doc.md`。
- Result: 简历科研成果已新增该论文，包含撰写状态、作者身份、时间以及动态指标裂变、RAG、对比思维链、多智能体贝叶斯研判和 LLM-FCE-TOPSIS 策略寻优等研究说明。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-16 23:17 +08 - 英文化新能源汽车舆情评估论文条目

- Request: 用户指出该论文最终以英文呈现，因此论文标题和描述都应改为学术英文。
- Actions: 修改 `src/views/resume/Resume.vue` 中该科研成果的论文标题与描述段落，并同步更新 `codex-project-tech-doc.md`。
- Result: 该论文条目现在使用英文题名 `A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles`，正文描述也改为学术英文。
- Verification: 已运行 `npm run build`，构建通过。

## 2026-08-17 00:41 +08 - 新增 Matrix 数字雨背景

- Request: 用户要求按既定方案实现黑客帝国风格绿色随机数字雨背景动画，并在落下过程中逐渐消失。
- Actions: 修改 `src/views/resume/Resume.vue`，在简历根 section 增加全屏背景 `canvas`，使用 Vue 生命周期管理高清画布、ResizeObserver、`requestAnimationFrame`、随机数字绘制和 `prefers-reduced-motion` 静态降级；同时弱化原绿色光斑以免背景拥挤。
- Result: 简历页新增不阻挡内容的绿色数字雨背景，字符通过半透明深色覆盖逐帧淡出，主体卡片保持前景层级和高可读性。
- Verification: 已运行 `npm run build`，构建通过；已启动 `npm run dev`，因 8080 被占用自动使用 `http://localhost:8081/`；已用应用浏览器确认页面标题、canvas 存在且可见、主体 article 可见，并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-preview.jpg`。

## 2026-08-17 00:52 +08 - 优化 Matrix 数字雨滚动性能

- Request: 用户反馈纵向滚动网页中 Matrix 数字雨背景非常卡顿，要求按固定视口画布方案优化。
- Actions: 修改 `src/views/resume/Resume.vue`，将数字雨 canvas 从整页 `absolute h-full` 改为 `fixed h-screen w-screen`，尺寸来源改为 `window.innerWidth/innerHeight`，移除 `ResizeObserver`，改用 `window.resize` 与 `visualViewport.resize`，并限制 DPR、增大列间距、降低文字阴影开销。
- Result: 数字雨动画现在只重绘当前视口，不再对约一万像素高的整页画布逐帧绘制，滚动时背景保持固定且不阻挡主体内容。
- Verification: 已运行 `npm run build`，构建通过；已用应用浏览器检查 `http://localhost:8080/`，确认页面 `bodyScrollHeight` 约 `10417px` 时 canvas 仍为视口 `1280x720`，滚动至中段后 canvas 仍固定在 `top: 0`，并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-optimized.jpg`。

## 2026-08-17 00:57 +08 - 去除数字雨浅绿色残影

- Request: 用户认为数字雨过后的印记留存时间过长，导致背景变成条纹状，希望直接去除浅绿色印记。
- Actions: 修改 `src/views/resume/Resume.vue`，删除每列头部后方额外绘制的浅绿色拖影字符，关闭文字阴影，并将每帧深色覆盖层透明度从 `0.1` 提高到 `0.28`。
- Result: 数字雨旧字符更快消失，不再通过浅绿色残影形成明显竖向条纹，背景更干净。
- Verification: 已运行 `npm run build`，构建通过；已用应用浏览器检查 `http://localhost:8080/`，确认 canvas 仍为固定视口背景并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-no-trail.jpg`。

## 2026-08-17 01:03 +08 - 恢复光斑与 Resume 背景层

- Request: 用户要求保留原有背景中的绿色光斑和绿色 `Resume` 文字，并将它们放到数字雨后面。
- Actions: 修改 `src/views/resume/Resume.vue`，将数字雨 canvas 提升为 `z-[1]`，原光斑和竖排 `Resume` 背景层保持 `z-0`，并恢复光斑为原先的绿色透明度强度。
- Result: 页面背景层级变为原光斑/`Resume` 在底层、数字雨在中层、简历主体内容在 `z-10` 顶层。
- Verification: 已运行 `npm run build`，构建通过；已用应用浏览器检查 `http://localhost:8080/`，确认背景层 `z-index: 0`、canvas `z-index: 1`、主体内容 `z-index: 10`，并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-layered.jpg`。

## 2026-08-17 01:10 +08 - 让底层光斑和 Resume 透出

- Request: 用户反馈绿色光斑和绿色 `Resume` 文字仍未显示。
- Actions: 修改 `src/views/resume/Resume.vue`，将数字雨 canvas 从深色填充改为透明 `clearRect` 清空，仅绘制当前帧数字；同时将光斑/`Resume` 背景层改为 `fixed inset-0 z-0`，并把 `Resume` 从 `text-[#24c781]/10` 调整为 `/15`。
- Result: 数字雨不再用深色矩形遮挡底层背景，原绿色光斑和竖排 `Resume` 能在数字雨后方显示。
- Verification: 已运行 `npm run build`，构建通过；已用应用浏览器检查 `http://localhost:8080/`，确认背景层为 `fixed z-0`、canvas 为 `fixed z-[1]`，并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-visible-bg.jpg`。

## 2026-08-17 01:14 +08 - 恢复数字雨短串效果

- Request: 用户反馈透明清空 canvas 后数字雨变成只有单个数字坠落。
- Actions: 修改 `src/views/resume/Resume.vue`，为每个 Matrix 列增加 `trailLength` 和字符缓存，每帧透明清空后即时绘制 5-9 个逐渐变淡的数字短串，而不是依赖旧帧残影。
- Result: 数字雨恢复连续短串下落效果，同时不会留下持久浅绿色印记，也不会遮挡底层光斑和 `Resume`。
- Verification: 已运行 `npm run build`，构建通过；已用应用浏览器检查 `http://localhost:8080/`，确认固定透明 canvas、底层装饰和短串数字雨同时存在，并保存预览截图到 `/tmp/codex-resume-matrix-check/resume-matrix-trail-restored.jpg`。

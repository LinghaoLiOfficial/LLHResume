# Project Technical Documentation

## Overview

这是一个基于 Vite、Vue 3 和 TypeScript 的个人简历网页项目。当前网页标签标题为 `Linghao Li Resume`，标签图标使用 `public/favicon.svg` 中的霓虹渐变居中 `L` monogram，无额外装饰线。

## Architecture

- `index.html` 是 Vite HTML 入口，负责声明 favicon、viewport、theme color、页面标题，以及挂载 `src/main.ts`。
- `src/main.ts` 创建并挂载 Vue 应用。
- `src/App.vue` 是应用根组件。
- `src/views/resume/Resume.vue` 承载主要简历页面视图。
- 简历头部姓名区域采用中文名在上、英文名与昵称 `Linghao Li (Lion)` 在下的垂直展示。
- 左侧联系方式采用纵向列表，邮箱独立展示；电话、微信、WhatsApp 合并为一个“联系号码”条目，并用 `电话 · 微信 · WhatsApp` 标明支持渠道。
- 左侧个人信息区在联系方式下方展示出生日期 `2002 年 11 月 21 日`，使用 `lucide:calendar-days` 图标。
- 简历头部右侧四段能力简介使用 `flex h-full flex-col justify-center`，作为整体在 header 右栏中垂直居中。
- 头部能力简介保持四条主线不变，其中 `AI 模型算法工程化落地` 融合了 `Vibe Coding` 的需求拆解、原型验证与迭代落地表达，`跨领域技术结合` 融合了实验室科研经验、文献研读、实验设计与复现验证表达。
- 教育背景中南洋理工大学条目采用中英文并列展示：学校为 `南洋理工大学 Nanyang Technological University (NTU)`，学位为 `理学硕士 MSc`，专业为 `企业人工智能专业 Enterprise Artificial Intelligence`。
- 教育背景卡片右侧使用两枚胶囊标签展示时间与地点；当前顺序为时间在上、地点在下，地点标签带 `lucide:map-pin` 图标，南洋理工大学为 `新加坡`，浙江工业大学为 `浙江杭州`。
- 科研成果条目的绿色标签行采用“作者身份 + 方向 + 平台 + 含金量标签”的扩写风格，例如 AAAI 论文强调人工智能国际顶级会议、CCF-A、核心阵地和多模态理解与推理方向认可度。当前列表顶部包含 `【撰写中】期刊论文《 A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles 》`，标注为一作、人工智能&新能源汽车舆情治理方向、`2026.06 - 至今`，标题与正文描述均采用学术英文，概括其动态指标裂变、RAG与对比思维链虚假舆情剥离、多智能体贝叶斯研判以及 LLM-FCE-TOPSIS 策略寻优框架；其后包含 `【评审一轮中】期刊论文《 人智协同驱动的复杂网络舆情涌现机制及其生成式治理研究 》`，标注为学生一作、公共管理学报期刊、`2026.04 - 至今`，描述概括其复杂适应系统理论、生成式治理框架和全过程能力建设逻辑。
- `【技术顾问】医院病历文本挖掘和病历质量监控模型` 的描述强调了基于 LLM 专家经验构建高质量小样本标准库，并结合 CNN 识别神经网络改进训练数据不足问题，以提升识别准确率和 F1。
- “项目&研究经验”卡片目前为模板内手写条目，按显示起始时间倒序排列，最新项目置顶；右侧采用与教育背景一致的双胶囊标签布局，时间在上、带 `lucide:map-pin` 图标的位置在下，机构行不再混写城市。
- “项目&研究经验”中的两个中国科学院大学项目需要分开展示：`【论文实验】百万级科研论文 LLM 专家定位评估实验程序` 面向已识别为使用 AI 的科研论文，强调 AI 在具体研究中的重要程度、方法学定位和必要性强度；`【科研计量实验】百万级 AI 暴露度计算与科研方法替代潜力测算程序` 面向能源转型与气候变化领域全量相关论文，强调当前研究即使尚未使用 AI，其科研流程被 AI 原生方法重构或替代的潜力。后者的三阶段逻辑彼此依赖，因此采用先综述剔除、再主题筛选、再科研流程阶段映射的分阶段串联处理，以支撑百万级论文规模的高效运行。两条均保留批量 LLM 推理提速与总体调用成本下降的表述。
- “工作经历”卡片右侧同样采用时间在上、位置在下的双胶囊标签布局；当前两条工作经历位置均为 `浙江杭州`。
- “调研&参会经历”标题下方先展示两张“核心演讲经历”精选卡片，当前突出 `2026.07` 西安 POMS 国际学术会议和 `2025.06` 浙江工业大学 MBA 企业高管课堂，强调台上演讲、现场答疑和高价值受众；下方完整表格继续保留全部 `seminarData` 记录，表格的“地点/机构”列固定为较窄宽度并允许长文本换行。
- 当前人物介绍可概括为：李凌浩，南洋理工大学企业人工智能理学硕士在读，拥有浙江工业大学信息管理与信息系统本科及光电信息科学与工程二学位背景，聚焦企业 AI 落地、LLM 科研应用、跨领域算法结合、全栈 Web 开发与项目协作。
- `src/style.css` 提供全局样式。

## Key Files and Directories

- `index.html`: 页面入口、网页标签标题、favicon 引用。
- `public/favicon.svg`: 网页标签图标，当前为单个居中 `L`。
- `public/avatar.jpg`: 简历页面头像资源。
- `vite.config.ts`: Vite 配置。
- `package.json`: 项目脚本与依赖声明。

## Setup and Runbook

- 安装依赖: `npm install`
- 本地开发: `npm run dev`，默认服务地址为 `http://localhost:8080/`
- 生产构建: `npm run build`
- 本地预览构建产物: `npm run preview`

## Testing and Verification

- 当前已验证命令: `npm run build`
- 构建链路包括 `vue-tsc --build` 和 `vite build`。

## Current Decisions and Conventions

- favicon 使用 SVG，以便在高分辨率屏幕上保持清晰。
- 页面标题在 `index.html` 中维护。
- 资源文件放在 `public/`，由 Vite 以根路径方式引用。
- `vite.config.ts` 中只固定 `server.port = 8080`，不再单独指定 `server.hmr.port`，避免 HTTP 页面和 HMR WebSocket 抢占同一端口导致浏览器显示 `Upgrade Required`。

## Known Issues and Follow-ups

- 暂无已知问题。

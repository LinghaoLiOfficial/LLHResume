# Project Technical Documentation

## Overview

这是一个基于 Vite、Vue 3 和 TypeScript 的个人简历网页项目。当前网页标签标题为 `Linghao Li Resume`，标签图标使用 `public/favicon.svg` 中的霓虹渐变居中 `L` monogram，无额外装饰线。站点支持路径级双语分流：`/` 和 `/cn` 保持当前版本，`/en` 显示完整英文版。

## Architecture

- `index.html` 是 Vite HTML 入口，负责声明 favicon、viewport、theme color、页面标题，以及挂载 `src/main.ts`。
- `src/main.ts` 创建并挂载 Vue 应用。
- `src/App.vue` 是应用根组件。
- `src/views/resume/Resume.vue` 承载主要简历页面视图。
- `src/views/resume/Resume.vue` 通过 `window.location.pathname` 识别语言路径；在 `/en` 下会在首轮渲染后遍历文本节点并用英文翻译字典替换页面文案，未引入 Vue Router。
- `vercel.json` 为 Vercel 静态部署配置 SPA fallback，将所有路径 rewrite 到 `/index.html`，避免直接访问 `/cn`、`/en` 时由平台按真实文件查找而返回 `404: NOT_FOUND`。
- `src/views/resume/Resume.vue` 内置 Matrix 风格绿色随机数字雨背景；原绿色光斑和竖排 `Resume` 文字使用 `fixed inset-0 z-0` 底层，桌面 canvas 使用 `fixed inset-0 h-screen w-screen`、`z-[1]` 与 `pointer-events-none`，移动端视频背景同样位于 `z-[1]`，主体内容保持 `relative z-10`。
- 移动端通过 `resume-page`、`resume-bg`、`resume-shell`、`resume-card`、`resume-header`、`resume-profile`、`resume-contact`、`resume-intro` 等类在 `src/style.css` 中集中控制 640px 以下布局；桌面端继续主要依赖 Tailwind 工具类。
- 桌面端数字雨动画使用 `requestAnimationFrame`，canvas 每帧通过 `clearRect` 透明清空后为每列即时绘制 5-9 个逐渐变淡的数字短串，只绘制当前 viewport 尺寸，DPR 上限为 `1.5`，不再依赖旧帧残影、文字阴影或深色覆盖层；通过 `prefers-reduced-motion` 在减少动态效果时切换为淡绿色静态纹理。640px 以下移动端隐藏 canvas，改用 `public/matrix-mobile.mp4` 作为自动播放、循环、静音、`playsinline` 的视频背景；按当前产品决定，移动端视频不额外接入减少动态效果分支。
- 简历头部姓名区域采用中文名在上、英文名与昵称 `Linghao Li (Lion)` 在下的垂直展示。
- 左侧联系方式采用纵向列表，邮箱独立展示；电话、微信、WhatsApp 合并为一个“联系号码”条目，并用 `电话 · 微信 · WhatsApp` 标明支持渠道。
- 左侧个人信息区在联系方式下方展示出生日期 `2002 年 11 月 21 日`，使用 `lucide:calendar-days` 图标。
- 首屏联系方式中的邮箱、电话、日历图标已通过 `@iconify/vue` 的 `addIcon` 注册为本地 `resume:mail`、`resume:phone`、`resume:calendar-days`，避免移动端首屏等待远程图标集加载；三个图标均使用 `stroke="currentColor"`，继承外层主题绿色。
- 简历头部右侧四段能力简介使用 `flex h-full flex-col justify-center`，作为整体在 header 右栏中垂直居中。
- 头部能力简介保持四条主线不变，其中 `AI 模型算法工程化落地` 融合了 `Vibe Coding` 的需求拆解、原型验证与迭代落地表达，`跨领域技术结合` 融合了实验室科研经验、文献研读、实验设计与复现验证表达。
- 教育背景之前新增了“未来发展”模块，使用两张卡片分别表达 `读博？` 与 `创业？` 的规划：读博方向优先考虑新加坡、香港、上海或浙江，创业方向强调依托高校资源和科研成果转化。
- “未来发展”模块的正文说明当前放宽到 `max-w-3xl`，比教育背景和科研成果里常见的 `max-w-2xl` 更宽，便于长路径与机构名在更少换行下展示。
- 教育背景中南洋理工大学条目采用中英文并列展示：学校为 `南洋理工大学 Nanyang Technological University (NTU)`，学位为 `理学硕士 MSc`，专业为 `企业人工智能专业 Enterprise Artificial Intelligence`。
- 教育背景卡片右侧使用两枚胶囊标签展示时间与地点；当前顺序为时间在上、地点在下，地点标签带 `lucide:map-pin` 图标，南洋理工大学为 `新加坡`，浙江工业大学为 `浙江杭州`。
- 科研成果条目的绿色标签行采用“作者身份 + 方向 + 平台 + 含金量标签”的扩写风格，例如 AAAI 论文强调人工智能国际顶级会议、CCF-A、核心阵地和多模态理解与推理方向认可度。当前列表顶部包含 `【撰写中】期刊论文《 A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles 》`，标注为一作、人工智能&新能源汽车舆情治理方向、`2026.06 - 至今`，标题与正文描述均采用学术英文，概括其动态指标裂变、RAG与对比思维链虚假舆情剥离、多智能体贝叶斯研判以及 LLM-FCE-TOPSIS 策略寻优框架；其后包含 `【评审一轮中】期刊论文《 人智协同驱动的复杂网络舆情涌现机制及其生成式治理研究 》`，标注为学生一作、公共管理学报期刊、`2026.04 - 至今`，描述概括其复杂适应系统理论、生成式治理框架和全过程能力建设逻辑。
- `【技术顾问】医院病历文本挖掘和病历质量监控模型` 的描述强调了基于 LLM 专家经验构建高质量小样本标准库，并结合 CNN 识别神经网络改进训练数据不足问题，以提升识别准确率和 F1。
- “项目&研究经验”卡片目前为模板内手写条目，按显示起始时间倒序排列，最新项目置顶；右侧采用与教育背景一致的双胶囊标签布局，时间在上、带 `lucide:map-pin` 图标的位置在下，机构行不再混写城市。当前 `2026.07 - 至今`、`新加坡` 位置包含 `【开发中】【生成式AI风险感知】面向职业社群的动态多风险感知框架`，机构为 `自研`，描述概括领域自适应语义表征、贝叶斯在线变化点语义事件切分、扎根式风险本体开放编码、原子风险事件抽取、多维度置信校准、风险主题动态演化、交叉激发建模、多跨度预测、最快变化检测和人机协同概念漂移闭环。
- “项目&研究经验”中的两个中国科学院大学项目需要分开展示：`【论文实验】百万级科研论文 LLM 专家定位评估实验程序` 面向已识别为使用 AI 的科研论文，强调 AI 在具体研究中的重要程度、方法学定位和必要性强度；`【科研计量实验】百万级 AI 暴露度计算与科研方法替代潜力测算程序` 面向能源转型与气候变化领域全量相关论文，强调当前研究即使尚未使用 AI，其科研流程被 AI 原生方法重构或替代的潜力。后者的三阶段逻辑彼此依赖，因此采用先综述剔除、再主题筛选、再科研流程阶段映射的分阶段串联处理，以支撑百万级论文规模的高效运行。两条均保留批量 LLM 推理提速与总体调用成本下降的表述。
- “工作经历”卡片右侧同样采用时间在上、位置在下的双胶囊标签布局；当前两条工作经历位置均为 `浙江杭州`。
- “调研&参会经历”标题下方先展示两张“核心演讲经历”精选卡片，当前突出 `2026.07` 西安 POMS 国际学术会议和 `2025.06` 浙江工业大学 MBA 企业高管课堂，强调台上演讲、现场答疑和高价值受众；下方完整表格继续保留全部 `seminarData` 记录，表格的“地点/机构”列固定为较窄宽度并允许长文本换行。
- “调研&参会经历”的完整记录在移动端显示为纵向卡片列表，在 `md` 及以上视口保留原表格展示，避免手机端横向滚动表格造成阅读成本。
- 当前人物介绍可概括为：李凌浩，南洋理工大学企业人工智能理学硕士在读，拥有浙江工业大学信息管理与信息系统本科及光电信息科学与工程二学位背景，聚焦企业 AI 落地、LLM 科研应用、跨领域算法结合、全栈 Web 开发与项目协作。
- `src/style.css` 提供全局样式。
- 路由行为约定为：`http://localhost:8080/` 和 `http://localhost:8080/cn` 指向当前版本，`http://localhost:8080/en` 指向英文版本。开发服务器若端口 8080 被占用，会自动切换到其他可用端口。

## Key Files and Directories

- `index.html`: 页面入口、网页标签标题、favicon 引用。
- `public/favicon.svg`: 网页标签图标，当前为单个居中 `L`。
- `public/avatar.jpg`: 简历页面头像资源。
- `public/matrix-mobile.mp4`: 移动端数字雨循环背景视频，约 104KB，字符集为 `0-9` 随机数字，当前版本下落速度较快，在 640px 以下由页面 `<video>` 加载。
- `vite.config.ts`: Vite 配置。
- `vercel.json`: Vercel rewrite 配置，用于支持前端路径直连。
- `package.json`: 项目脚本与依赖声明。

## Setup and Runbook

- 安装依赖: `npm install`
- 本地开发: `npm run dev`，默认服务地址为 `http://localhost:8080/`
- 生产构建: `npm run build`
- 本地预览构建产物: `npm run preview`
- 上线形态: 纯静态站点，部署时发布 `dist/` 目录；当前不需要 Node.js 常驻进程、数据库或后端 API。Vercel 部署需保留项目根目录的 `vercel.json`，让 `/cn`、`/en` 等前端路径回退到 `index.html`。
- 推荐上线顺序: 先使用 Cloudflare Pages、Vercel 或 GitHub Pages 之一绑定自定义域名快速发布；若中国大陆访问是硬性要求，再迁移到中国大陆云厂商的 OSS/COS 静态托管与 CDN，并按服务商要求完成 ICP 备案。

## Testing and Verification

- 当前已验证命令: `npm run build`
- 构建链路包括 `vue-tsc --build` 和 `vite build`。
- Matrix 数字雨背景已通过本地开发服务 `http://localhost:8080/` 做浏览器检查，确认长页面中 canvas 保持视口尺寸 `1280x720` 且滚动后仍固定在 `top: 0`，主体 article 保持可见；当前版本已去除持久浅绿色残影以避免背景形成竖向条纹，并通过每帧重绘短数字串保持雨状连续感，原光斑/`Resume` 背景层可在透明数字雨后方显示。
- 双语路径行为已通过本地浏览器检查：`http://localhost:8080/` 与 `http://localhost:8080/cn` 保持中文当前版，`http://localhost:8080/en` 的正文区域已切换为英文且未检出中文字符残留。

## Current Decisions and Conventions

- favicon 使用 SVG，以便在高分辨率屏幕上保持清晰。
- 页面标题在 `index.html` 中维护。
- 资源文件放在 `public/`，由 Vite 以根路径方式引用。
- 背景氛围效果优先使用固定视口 canvas，不使用大量 DOM 字符节点，也不使用整页 `scrollHeight` 画布；动画应保持在背景层，不能阻挡滚动、点击或主体文字阅读。
- `vite.config.ts` 中只固定 `server.port = 8080`，不再单独指定 `server.hmr.port`，避免 HTTP 页面和 HMR WebSocket 抢占同一端口导致浏览器显示 `Upgrade Required`。
- 双语内容目前采用页面加载后文本节点替换的方式维护英文版，没有引入额外路由库；后续若要扩展更多语言，建议继续沿用当前的路径识别 + 文本映射模式，或再评估是否迁移到真正的路由/本地化方案。

## Known Issues and Follow-ups

- 已完成上线可行性评估：当前构建通过，静态资源体量较小，适合静态托管。
- 中国大陆与全球同时稳定访问尚未实测，最终可达性取决于托管节点、DNS、域名状态和网络环境。
- 若采用中国大陆节点，需预留域名实名认证、ICP备案、公安联网备案等合规流程评估；若仅部署在境外节点，通常可免去大陆服务器备案流程，但不能承诺中国大陆网络环境下始终稳定访问。
- 移动端第一轮布局优化已完成：外层边距、主卡片 padding/圆角/阴影、头像尺寸、姓名字号、头像与姓名间距、个人信息与核心要点间距、联系方式缩进、联系方式图标垂直位置、能力摘要缩进、背景数字雨透明度和竖排 `Resume` 装饰均已针对 640px 以下视口处理。移动端图标尺寸规则当前仅作用于 `article > div.flex > div:first-child`，避免误伤“核心演讲经历”中的文本信息卡片。
- 移动端正文当前采用 CSS 统一控制标题降级、正文行高提升、长文本 `overflow-wrap` 和最多 5 行截断；为避免长页面首轮渲染和滚动卡顿，展开交互不再批量测量所有段落高度，而是在 640px 以下点击条目时按需切换对应 `article.is-expanded`。
- `index.html` viewport 已移除 `maximum-scale=1.0, user-scalable=no`，允许移动端用户缩放页面。

<template>
  <section
    ref="resumeRoot"
    :lang="activeLocale"
    class="resume-page relative min-h-screen overflow-hidden bg-[#121212] px-6 py-12 font-['Inter','Roboto','sans-serif'] text-white md:px-10"
  >
    <canvas
      ref="matrixCanvas"
      aria-hidden="true"
      class="pointer-events-none fixed inset-0 z-[1] h-screen w-screen opacity-90"
    />

    <video
      aria-hidden="true"
      autoplay
      loop
      muted
      playsinline
      preload="auto"
      class="matrix-mobile-video pointer-events-none fixed inset-0 z-[1] h-screen w-screen object-cover"
    >
      <source src="/matrix-mobile.mp4" type="video/mp4">
    </video>

    <div class="resume-bg pointer-events-none fixed inset-0 z-0">
      <div class="absolute left-[12%] top-16 h-72 w-72 rounded-full bg-[#24c781]/25 blur-[120px]" />
      <div class="absolute bottom-20 right-[14%] h-80 w-80 rounded-full bg-[#24c781]/20 blur-[140px]" />
      <p
        class="absolute right-6 top-1/2 -translate-y-1/2 rotate-180 text-[130px] font-bold uppercase leading-none tracking-[0.24em] text-[#24c781]/15 [writing-mode:vertical-rl]"
      >
        Resume
      </p>
    </div>

    <div class="resume-shell relative z-10 mx-auto flex min-h-[80vh] w-full max-w-6xl items-center justify-center">
      <article class="resume-card w-full rounded-3xl border border-[#333333] bg-[#1a1a1a]/95 p-6 shadow-[inset_0_1px_0_rgba(255,255,255,0.03),0_30px_90px_rgba(0,0,0,0.5)] backdrop-blur-sm md:p-10">
        <header class="resume-header grid gap-8 border-b border-[#2b2b2b] pb-10 lg:grid-cols-[320px_1fr]">
          <div class="resume-profile space-y-6 flex flex-col items-center">
            <img
              :src="avatarSrc"
              alt="Lion Lee"
              class="h-36 w-36 rounded-2xl border border-[#3b3b3b] object-cover object-[65%_65%]"
            >

            <div>
              <div class="resume-name flex flex-col items-center space-y-2 pt-8">
                  <h1 class="text-3xl font-semibold text-white">{{ activeLocale === 'en' ? 'Linghao Li (Lion)' : '李凌浩' }}</h1>
                  <h2 v-if="activeLocale !== 'en'" class="text-2xl font-semibold text-[#c8c8c8]">Linghao Li (Lion)</h2>
              </div>

                <div class="resume-contact flex flex-col space-y-4 mt-8 ml-10">
                    <div class="flex flex-row space-x-2 items-center">
                        <div class="inline-flex h-9 w-9 items-center justify-center rounded-full border bg-[#202020] transition border-[#24c781] text-[#24c781]">
                            <Icon icon="resume:mail" class="text-base" />
                        </div>
                        <div class="flex flex-col space-y-1">
                            <span class="text-[#24c781]">邮箱</span>
                            <span class="break-all text-sm">linghao.li.2002@gmail.com</span>
                        </div>
                    </div>
                    <div class="flex flex-row space-x-2 items-center">
                        <div class="inline-flex h-9 w-9 items-center justify-center rounded-full border bg-[#202020] transition border-[#24c781] text-[#24c781]">
                            <Icon icon="resume:phone" class="text-base" />
                        </div>
                        <div class="flex flex-col space-y-1">
                            <span class="text-[#24c781]">联系号码</span>
                            <span class="text-sm">(+86) 13857750421</span>
                            <span class="text-xs text-[#8f8f8f]">电话 · 微信 · WhatsApp</span>
                        </div>
                    </div>
                    <div class="flex flex-row space-x-2 items-center">
                        <div class="inline-flex h-9 w-9 items-center justify-center rounded-full border bg-[#202020] transition border-[#24c781] text-[#24c781]">
                            <Icon icon="resume:calendar-days" class="text-base" />
                        </div>
                        <div class="flex flex-col space-y-1">
                            <span class="text-[#24c781]">出生日期</span>
                            <span class="text-sm">2002年11月21日</span>
                        </div>
                    </div>
                </div>

<!--              <div class="mt-4 flex items-center gap-3 justify-center">-->
<!--                <a-->
<!--                  v-for="social in socialLinks"-->
<!--                  :key="social.name"-->
<!--                  :href="social.link"-->
<!--                  class="inline-flex h-9 w-9 items-center justify-center rounded-full border border-[#333] bg-[#202020] text-[#c8c8c8] transition hover:border-[#24c781] hover:text-[#24c781]"-->
<!--                  target="_blank"-->
<!--                  rel="noreferrer"-->
<!--                >-->
<!--                  <Icon :icon="social.icon" class="text-base" />-->
<!--                </a>-->
<!--              </div>-->
            </div>

<!--            <div class="flex gap-3">-->
<!--              <button class="rounded-full bg-[#24c781] px-5 py-2.5 text-sm font-semibold text-[#0f1a15] transition hover:bg-[#1fb271]">-->
<!--                Download CV-->
<!--              </button>-->
<!--              <button class="rounded-full border border-[#3a3a3a] bg-[#222] px-5 py-2.5 text-sm font-semibold text-white transition hover:border-[#24c781] hover:text-[#24c781]">-->
<!--                Contact-->
<!--              </button>-->
<!--            </div>-->
          </div>

          <div class="resume-intro flex h-full flex-col justify-center space-y-6 pl-12">

            <div>
                <div class="inline-flex items-center gap-2 rounded-full border border-[#2c664a] bg-[#1a2a22] px-3 py-1 text-sm text-[#9ae9c4]">
                    <span class="h-2 w-2 rounded-full bg-[#24c781]" />
                    <div class="tracking-widest">AI 模型算法工程化落地</div>
                </div>
                <p class="text-sm leading-relaxed text-[#8f8f8f] pt-2">
                    专注于创新应用人工智能解决企业实际复杂问题，结合 Vibe Coding 加速需求拆解、原型验证与迭代落地，实现业务流程数字化和 AI 化改造，为企业降本增效
                </p>
            </div>

              <div>
                  <div class="inline-flex items-center gap-2 rounded-full border border-[#2c664a] bg-[#1a2a22] px-3 py-1 text-sm text-[#9ae9c4]">
                      <span class="h-2 w-2 rounded-full bg-[#24c781]" />
                      <div class="tracking-widest">跨领域技术结合</div>
                  </div>
                  <p class="text-sm leading-relaxed text-[#8f8f8f] pt-2">
                      擅长将工业检测、知识管理、供应链管理、金融预测、舆情监测等领域知识，与神经网络模型改进、大语言模型工程应用、深度强化学习算法设计、经典机器学习模型应用等技术跨领域结合，并具备实验室科研经验，覆盖文献研读、框架搭建、实验设计与复现验证
                  </p>
              </div>

              <div>
                  <div class="inline-flex items-center gap-2 rounded-full border border-[#2c664a] bg-[#1a2a22] px-3 py-1 text-sm text-[#9ae9c4]">
                      <span class="h-2 w-2 rounded-full bg-[#24c781]" />
                      <div class="tracking-widest">全栈 Web 程序开发</div>
                  </div>
                  <p class="text-sm leading-relaxed text-[#8f8f8f] pt-2">
                      擅长 FastAPI 和 Flask 后端开发，熟悉 Vue 和 React 前端开发，具备快速搭建、迭代全栈演示产品 MVP 的能力，高效验证业务可行性并为技术团队提供架构方案、为管理团队提供提供技术可行性分析
                  </p>
              </div>

              <div>
                  <div class="inline-flex items-center gap-2 rounded-full border border-[#2c664a] bg-[#1a2a22] px-3 py-1 text-sm text-[#9ae9c4]">
                      <span class="h-2 w-2 rounded-full bg-[#24c781]" />
                      <div class="tracking-widest">项目管理团队协作</div>
                  </div>
                  <p class="text-sm leading-relaxed text-[#8f8f8f] pt-2">
                      拥有 2 年与多个技术团队（产品经理、产品设计、前端、后端、测试、运维）协同经验，具备从架构设计到落地实施的项目主导能力与合作经验，以及代码重构优化经验
                  </p>
              </div>
          </div>
        </header>

<!--        <section class="grid gap-4 border-b border-[#2b2b2b] py-8 sm:grid-cols-2 lg:grid-cols-4">-->
<!--          <div-->
<!--            v-for="item in statsData"-->
<!--            :key="item.label"-->
<!--            class="rounded-2xl border border-[#2f2f2f] bg-[#202020] p-4"-->
<!--          >-->
<!--            <p class="text-3xl font-semibold text-white">{{ item.number }}</p>-->
<!--            <p class="mt-2 text-sm text-[#9a9a9a]">{{ item.label }}</p>-->
<!--          </div>-->
<!--        </section>-->

        <section class="pt-8 border-b border-[#2b2b2b] py-8">
          <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
            <Icon icon="lucide:compass" class="text-[#24c781]" />
            未来发展
          </h3>

          <div class="space-y-4">
            <article
              class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
            >
              <div class="flex gap-4">
                <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                  <Icon icon="lucide:graduation-cap" class="text-xl" />
                </div>
                <div>
                  <p class="text-lg font-semibold text-white">读博 ？</p>
                  <p class="mt-1 max-w-3xl text-sm leading-relaxed text-[#8f8f8f]">
                    上海 (上海交通大学、复旦大学) or 浙江 (浙江大学) or 新加坡 (NTU、NUS) or 香港 (香港大学、香港科技大学)
                  </p>
                </div>
              </div>
            </article>

            <article
              class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
            >
              <div class="flex gap-4">
                <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                  <Icon icon="lucide:rocket" class="text-xl" />
                </div>
                <div>
                  <p class="text-lg font-semibold text-white">创业 ？</p>
                  <p class="mt-1 max-w-3xl text-sm leading-relaxed text-[#8f8f8f]">
                    依托高校资源，重点放到科研成果转化
                  </p>
                </div>
              </div>
            </article>
          </div>
        </section>

        <section class="pt-8 border-b border-[#2b2b2b] py-8">
          <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
            <Icon icon="lucide:graduation-cap" class="text-[#24c781]" />
            教育背景
          </h3>

          <div class="space-y-4">
            <article
              class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
            >
              <div class="flex gap-4">
                <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                  <Icon icon="lucide:book-open-check" class="text-xl" />
                </div>
                <div>
                  <p class="text-lg max-w-2xl font-semibold text-white">【 理学硕士 MSc 】南洋理工大学 Nanyang Technological University ( NTU )</p>
                  <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">QS 全球排名第 12（2026），QS 亚洲排名第 3（2026），亚洲顶尖工科强校</p>
                  <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                    企业人工智能专业 Enterprise Artificial Intelligence
                  </p>
                </div>
              </div>

              <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                  2026.08 - 至今
                </span>
                <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                  <Icon icon="lucide:map-pin" class="text-sm" />
                  新加坡
                </span>
              </div>
            </article>

              <article
                  class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
              >
                  <div class="flex gap-4">
                      <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                          <Icon icon="lucide:book-open-check" class="text-xl" />
                      </div>
                      <div>
                          <p class="text-lg max-w-2xl font-semibold text-white">【 二学位 】浙江工业大学 ( ZJUT )</p>
                          <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">国内省属重点，省部共建重点大学，浙江省工科龙头</p>
                          <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              光电信息科学与工程专业
                          </p>
                      </div>
                  </div>

                  <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                    <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                      2025.09 - 2026.06
                    </span>
                    <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                      <Icon icon="lucide:map-pin" class="text-sm" />
                      浙江杭州
                    </span>
                  </div>
              </article>

              <article
                  class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
              >
                  <div class="flex gap-4">
                      <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                          <Icon icon="lucide:book-open-check" class="text-xl" />
                      </div>
                      <div>
                          <p class="text-lg max-w-2xl font-semibold text-white">【 本科 】浙江工业大学 ( ZJUT )</p>
                          <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">国内省属重点，省部共建重点大学，浙江省工科龙头</p>
                          <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              信息管理与信息系统专业
                          </p>
                      </div>
                  </div>

                  <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                    <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                      2021.09 - 2025.06
                    </span>
                    <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                      <Icon icon="lucide:map-pin" class="text-sm" />
                      浙江杭州
                    </span>
                  </div>
              </article>

          </div>
        </section>

          <section class="pt-8 border-b border-[#2b2b2b] py-8">
              <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
                  <Icon icon="lucide:flask-conical" class="text-[#24c781]" />
                  科研成果
              </h3>

              <div class="space-y-4">
                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">【撰写中】期刊论文《 A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">一作，人工智能&舆情治理方向</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  This study develops a composite LLM-based decision network for dynamically assessing negative public opinion in the new energy vehicle sector, where technical complexity, high-noise social media data, coordinated manipulation, and nonlinear crisis propagation jointly challenge conventional sentiment analysis and static risk evaluation. The proposed framework elevates LLMs from generic text-processing tools to composite decision agents that integrate semantic reasoning, adaptive knowledge updating, and operations-research-based quantitative evaluation. It first constructs an evolving indicator network through multi-source heterogeneous data ingestion and emerging terminology tracking; then combines retrieval-augmented generation with contrastive chain-of-thought reasoning to distinguish authentic engineering feedback from manipulated opinion signals. The framework further instantiates heterogeneous expert agents, including engineering, legal-compliance, and consumer-rights perspectives, and aggregates their probabilistic judgments through Bayesian belief updating. Finally, an LLM-FCE-TOPSIS decision module integrates fuzzy comprehensive evaluation, tree-of-thought strategy generation, and dynamic ideal-solution ranking to support root-cause diagnosis, risk assessment, and intervention strategy optimization for explainable and high-validity public opinion governance in new energy vehicle enterprises.
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2026.06 - 至今
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">【评审一轮中】期刊论文《 人智协同驱动的复杂网络舆情涌现机制及其生成式治理研究 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">学生一作，人工智能&公共管理方向，公共管理学报期刊，公共管理领域重要学术期刊 + CSSCI收录 + 北大核心收录 + 复杂系统治理与数字治理前沿议题</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  平台化传播与生成式智能扩散正在推动网络舆情风险由内容失真问题加速演化为兼具认知操纵、规则反身性、信息级联与风险涌现特征的“能力型风险”，对当前我国乃至全球网络舆情治理产生新一轮挑战。本文在系统梳理AIGC情境下网络舆情风险演化与治理研究的基础上，以复杂适应系统理论为核心理论基础，综合协同治理、全过程治理与生成式治理等理念，构建由“技术—组织—制度”协同生态架构、“数据流—信息流—决策流—工作流”闭环运行机制和“风险特征—治理适配”能力建设逻辑组成的生成式治理框架。研究表明，能力型风险的治理重点已由末端内容处置转向前置识别、生成推演、协同处置与迭代优化相衔接的全过程能力建设，其关键在于通过制度规范、组织协同与技术赋能的持续耦合，实现网络舆情治理从事后控制向持续能力建设转变，并为我国网络舆情风险治理的制度重构与路径优化提供理论参照。
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2026.04 - 至今
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">【评审二轮中】会议论文《 MetaphorTree: Tree-Structured Hypothesis Search for Grounded Multimodal Metaphor Understanding 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">二作，人工智能&多模态方向，AAAI 会议，CCF-A + 人工智能领域国际会议 Top + 国际人工智能研究核心阵地 + 多模态理解与推理方向高度认可</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  Multimodal metaphor understanding requires not only determining whether an image-text pair is figurative, but also grounding the source-target role assignment, identifying the local carrier, and justifying the mapping with local evidence. Current one-shot or single-path inference collapses several locally plausible interpretations into a single answer, which is brittle when different regions or text spans support competing readings. To overcome this limitation, we propose MetaphorTree, a test-time framework that treats inference as search over grounded branch states, each anchored to a specific local image region or text span, source-target assignment, and evidence set. The method combines a task-specific branch representation with a bounded repair-and-prune search policy, allowing candidate interpretations to be verified, revised, and globally compared before commitment. We evaluate on five public benchmarks covering four task families: detection, source-target mapping, weak grounding, and strong grounding. Notably, compared with one-shot direct inference, MetaphorTree improves Mapping JPA by 12.11 points, Weak Grounding Avg. TS-F1 by 8.96 points, and Strong Grounding Box F1 by 9.99 points. Together with ablations and process diagnostics, these results indicate that the benefit comes from grounded hypothesis competition, grounding-before-context, and bounded repair-and-prune search rather than from extra sampling alone.
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2025.12 - 至今
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">【外审三轮中】期刊论文《 网络舆情风险的“生成式模拟干预”治理研究——基于AI智能体赋能视角 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">学生一作，人工智能&管理学方向，管理世界期刊，中国管理类 Premier + 中国国家智库核心阵地 + AMI Top + FMS Top + CSSCI收录 + 北大核心收录</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  智能传播时代，企业网络舆情风险呈现出生成主体多元化、传播结构复杂化与演化路径非线性增强的特征，传统基于事后监测与静态响应的治理模式难以支撑企业在高不确定环境下开展前瞻性研判与策略优化。针对上述问题，本文提出“生成式模拟—干预”（Generative Simulation–Intervention，GSI）治理框架。GSI框架构建了由风险感知、生成式推演与决策干预构成的三层智能体体系，并通过“表征—思考—行动—反馈”（RTAF）闭环机制实现多源舆情数据的结构化表达、微观行为模拟与宏观态势演化。在方法上，框架进一步引入反事实推演机制，在统一初始条件下对多种治理策略进行路径模拟与效果比较，使企业舆情回应从事后评估拓展为事前可计算实验。在此基础上，通过嵌入数据知识底座与人智协同机制，实现舆情风险识别、演化推演与策略优化的统一建模与持续学习。基于新能源汽车企业典型舆情事件的实证检验结果表明，GSI能够有效刻画长时序舆情风险演化过程，并显著区分不同治理策略在信念、立场与情绪结构上的影响差异，同时支持策略在反事实条件下的可比性评估。进一步地，人智协同机制验证了AI在风险识别与策略推演中的辅助作用，以及人类在价值判断与合规决策中的主导地位。本文拓展了生成式人工智能在企业风险治理领域的理论边界，将舆情治理从“静态识别—事后响应”推进至“动态模拟—策略实验”的生成式治理范式，为企业开展舆情压力测试、策略预演与人智协同决策提供了新的分析框架与方法支持。
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2025.08 - 至今
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">【评审二轮中】期刊论文《 Early Fault Detection in Wind Turbines Using an Innovative Contrast-Based Mode 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">一作，人工智能&新能源方向，Wind Energy 期刊，风电细分领域权威 + SCI-E + Mechanical Engineering Q2 + 全球风电行业高度认可 + 理论与工程结合</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  Large-scale wind turbines present significant mechanical complexity and are subject to environmental uncertainties, making traditional physical model-driven fault warning methods inadequate for the operational and maintenance needs of modern wind farms. To address this, we propose an innovative deep learning model, WeibullMirrorTVAE, for early fault detection in wind turbines. The model integrates a Weibull distribution mapping mechanism to transform discrete fault labels into continuous accumulation signals, enhancing temporal dynamics capture. It employs mirror-structured time-series variational autoencoders with attention mechanisms for reconstructing normal and abnormal samples separately, and a mirror adaptive feature threshold setting mechanism for precise anomaly detection. Experiments on the 'CARE to Compare' dataset demonstrate superior performance, achieving a CARE-score of 0.681 and Earliness of 0.407, highlighting model’s ability to balance accurate early detection with fewer false alarm.
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2025.07 - 至今
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:file-text" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg max-w-2xl font-semibold text-white">期刊论文《 基于不平衡正负样本对比自监督学习的风力发电机故障预警模型 》</p>
                              <p class="mt-1 max-w-2xl text-sm font-medium text-[#24c781]">一作，人工智能&新能源方向，计算机集成制造系统 ( CIMS ) 期刊，计算机与智能制造交叉领域 + EI收录 + CSCD收录 + 北大核心收录 + CCF推荐中文高质量</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  为了避免大型风力发电机因异常导致严重经济损失，需要尽早对一些关键故障进行预警。针对现有SCADA系统预警时间不足，以及大量的状态时间序列数据与稀少的故障标签数据之间存在极大不平衡问题，提出了一种基于不平衡正负样本对比自监督学习模型的风力发电机故障预警方法。在引入箱线下采样方法对输入的高频时间序列数据进行合理压缩的基础上，采用核贝叶斯多元自回归模型与注意力变分自编码器模型对正、负样本数据集分别进行非对称重构，结合自适应阈值树分类模型，实现在不平衡数据集上的异常状态监测与预警能力。通过来自实际风场数据的实验，以及与传统机器学习和当前主流深度学习中的监督学习范式进行对比分析，结果显示所提出的对比自监督学习模型在风力发电机故障预警任务的各项评价指标中均表现优越并展示了巨大潜力。
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2024.07 - 2025.09
              </span>
                  </article>

              </div>
          </section>

          <section class="pt-8 border-b border-[#2b2b2b] py-8">
              <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
                  <Icon icon="lucide:award" class="text-[#24c781]" />
                  证书&竞赛荣誉
              </h3>

              <div class="space-y-4">
                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:trophy" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">“运河杯” 课外学术科技作品竞赛</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">二等奖</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">

                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2026.01
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:trophy" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">“挑战杯” 课外学术科技作品竞赛 “人工智能+” 专项赛</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">银奖</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  “数智舆控”——双引擎驱动的涉企舆情⻛险智能预警与协同治理系统
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2025.07
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:trophy" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">CAMCM 认证杯数学建模国际赛</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">Finalist (F奖)，特等奖提名</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  Classification and segmentation of product surface defects based on Lite DS-MobileNet
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2023.12
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:trophy" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">Neo4j 图数据库</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">Certified Professional，认证专家</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">

                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2023.08
              </span>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:trophy" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">电子商务“创新、创意及创业”挑战赛 (三创赛)</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">浙江省银奖</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  基于“机-网-云”的山区农业产销服务平台
                              </p>
                          </div>
                      </div>

                      <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                2023.05
              </span>
                  </article>

              </div>
          </section>

          <section class="pt-8 border-b border-[#2b2b2b] py-8">
              <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
                  <Icon icon="lucide:folder-kanban" class="text-[#24c781]" />
                  项目&研究经验
              </h3>

              <div class="space-y-4">

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【待开始】【Web全栈开发】基于持续学习的科研团队生产力促进 AI 系统</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">待定</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          预计 2026.08 开始
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          新加坡
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【开发中】【论文实验】面向职业社群的动态舆情多风险感知框架</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">浙江大学&阿里巴巴淘宝闪购</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  面向网络职业社群高上下文依赖、风险语义漂移与多类型风险耦合演化问题，设计以生成式 AI 为核心的动态多风险感知框架：通过领域自适应语义表征与贝叶斯在线变化点检测完成聊天流语义事件切分，结合扎根式风险本体开放编码、原子风险事件抽取和多维度置信校准，实现高召回、可审计的风险识别；进一步构建风险主题动态演化、交叉激发建模、多跨度预测与最快变化检测机制，并以人机协同闭环支持概念漂移监测、风险知识版本化迭代和有限审核资源下的预警优先级优化
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.07 - 至今
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【开发中】【Web全栈开发】全栈上下文编排器</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">自研</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.07 - 至今
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          新加坡
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【开发中】【Web全栈开发】小红书 AI 全流程自动化自媒体运营系统</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">待定</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.06 - 至今
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【开发中】【Web全栈开发】AI 金融分析系统</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">自研</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.05 - 至今
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          新加坡
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【论文实验】百万级论文 LLM 专家定位评估实验程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">中国科学院大学</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  面向已识别为使用 AI 的科研论文摘要，构建“研究环节识别、AI 功能识别、方法学定位与必要性强度评分”四维判定框架，用于判断 AI 在具体研究中的重要程度：是常规辅助工具、核心分析方法，还是传统方法难以替代的知识生产机制；设计提示词模板、结构化输出规范与批量后处理机制，支持百万级摘要的定位评估、证据归因和结果统计，显著加快了并批量进行的 LLM 总体推理速度，并显著降低了总体 LLM 调用成本
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.05 - 2026.06
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          北京
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【开发中】【Web全栈开发】国际媒体舆情AI采集分析系统</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">浙江工业大学区域国别研究院</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2026.04 - 至今
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【技术顾问】医院病历文本挖掘和病历质量监控模型</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">浙江省人民医院</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  基于 LLM 专家经验构建高质量小样本标准库，并结合既有 CNN 识别神经网络对训练流程与特征表达进行改进，有效缓解病历标注数据不足带来的模型训练瓶颈，提升了病历文本识别准确率与 F1 表现，支撑病历质量监控与文本挖掘任务落地
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.09 - 2025.10
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【论文实验】百万级论文 AI 暴露度计算与科研方法替代潜力测算程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">中国科学院大学</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  面向能源转型与气候变化领域的全量相关论文，构建“LLM 语义判别 + 向量检索匹配 + 技术成熟度约束加权”的三阶段 AI 暴露度测算框架，用于评估即使当前研究尚未使用 AI，其科研流程在 AI 原生方法、成熟 AI 技术库与历史方法库支持下被重构或替代的潜力；由于三阶段逻辑彼此依赖，采用先综述剔除、再主题筛选、再科研流程阶段映射的分阶段串联处理，并进一步完成 AI 使用度、不可替代性与暴露度计算及分块持久化输出，以支撑百万级论文规模的高效运行，同时显著加快 LLM 总体推理速度并降低调用成本
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.08 - 2026.07
                        </span>
                          <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          北京
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【算法设计】物流运输成本优化算法</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">天能电池集团股份有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  主导设计大规模动态规划时间窗口订单合并算法，结合企业阶梯式业务规则，通过时空合并将30K订单压缩至9K组，降低约5.8%的运输总成本，同时设计了基于甘特图的合并订单可视化方法
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.04 - 2025.06
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【模型设计】虚拟仿真智能采购数据分析教学程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">一鼎堂软件科技有限公司杭州分公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  撰写多种模型机器学习数据分析实验代码，并实现特征过滤法、特征嵌入法、特征包裹法等特征工程和决策树、神经网络模型训练可视化方法
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.03 - 2025.06
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【Web全栈开发】基于 LLM 的自动化论文知识网络构建平台全栈程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">浙江工业大学图书馆</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  应用大语言模型，实现根据多检索词自动化构建论文-主题短语的知识网络并生成多角度文献综述，快速呈现某领域研究现状
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.01 - 2025.05
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【技术顾问】服装设计草图生成 AIGC 程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">南郊韫典服装厂</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  为企业的运动女装服饰设计草图AI生成模型提供技术框架，搭建企业服饰草图数据库，助力提高服装设计师的效率和工厂的数字化转型
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.01 - 2025.02
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江温州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【技术顾问】智能投标文件辅助写作 LLM 程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">温州微极光智能科技有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  设计结合企业多部门资料库的智能投标文件辅助写作LLM程序的技术框架，提高投标文件书写规范
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.01 - 2025.02
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江温州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【Web全栈开发】深度学习模型全流程可研实验平台全栈程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">綦方中教授科研团队</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  设计开发支持模型组件自定义设计的全栈平台，覆盖数据定义、模型定义、模型训练、数据可视化全流程，助力模型结构调优自动化实验研究
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2024.07 - 2024.09
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【Web全栈开发】知识管理互联应用平台全栈程序</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">綦方中教授科研团队</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  设计开发支持 PDF、Markdown 和知识图谱文件互联功能整合的全栈平台，同时开发了支持自由编辑图谱结构的前端组件，实现了团队文件管理、图谱编辑、Markdown 文件编辑、PDF 预览等功能整合
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2024.07 - 2024.09
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【技术文档撰写】LLM 双层嵌套支撑电力物资管理智能化技术研究</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">国家电网浙江省电力有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  为团队项目规划提供核心研究思路：基于大语言模型双层嵌套框架的二次学习方法、电力物料族谱生成方法、需求知识网络生成方法、场景化应用路径生成方法研究等技术方法
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2024.05 - 2024.06
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【模型设计】高光谱油液多元素预测模型</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">联桥网云信息科技有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  为手持检测设备提供核心预测算法，提出基于可学习参数小波变换的 BiScaleWaveNet 双流异构神经网络模型，通过将低频趋势与高频瞬态数据特征解耦，实现风机齿轮箱中油液的高光谱多元素定量预测
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2024.03 - 2025.01
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          湖南长沙
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【Web后端开发】项目计划智能度量后端</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">国家电网浙江省电力有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  主导项目二期重构与开发，个人完成核心模块改进与新需求实现，实现了 Excel 项目估算书智能解析、Word 项目可研文本智能解析、语料库搭建、Excel 因子公式动态公式配置等功能
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2023.07 - 2024.08
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>


                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:code-xml" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">【Web后端开发】科技资源检索引擎后端</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">国家电网浙江省电力有限公司</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">
                                  主导项目全生命周期开发，基于图数据库构建企业级异构知识图谱，实现了关系型和图结构数据双重智能检索、异构图数据重构、关键热词排序、专业词语义总结等功能
                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2023.06 - 2024.10
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

              </div>
          </section>

          <section class="pt-8 border-b border-[#2b2b2b] py-8">
              <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
                  <Icon icon="lucide:building-2" class="text-[#24c781]" />
                  工作经历
              </h3>

              <div class="space-y-4">
                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:briefcase-business" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">浙江火炬生产力促进中心有限公司</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">【实习】数据分析师</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">

                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2025.02 - 2025.05
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

                  <article
                      class="flex flex-col gap-4 rounded-2xl border border-[#2f2f2f] bg-[#202020] p-5 md:flex-row md:items-start md:justify-between"
                  >
                      <div class="flex gap-4">
                          <div class="mt-0.5 inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#325a47] bg-[#193025] text-[#24c781]">
                              <Icon icon="lucide:briefcase-business" class="text-xl" />
                          </div>
                          <div>
                              <p class="text-lg font-semibold text-white">杭州国信大数据应用研究院</p>
                              <p class="mt-1 text-sm font-medium text-[#24c781]">【实习】数据分析师</p>
                              <p class="mt-3 max-w-2xl text-sm leading-relaxed text-[#8f8f8f]">

                              </p>
                          </div>
                      </div>

                      <div class="flex shrink-0 flex-col items-start gap-2 md:items-end">
                        <span class="w-fit rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          2023.06 - 2023.09
                        </span>
                        <span class="inline-flex w-fit items-center gap-1.5 rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                          <Icon icon="lucide:map-pin" class="text-sm" />
                          浙江杭州
                        </span>
                      </div>
                  </article>

              </div>
          </section>

          <section class="pt-8 py-8">
              <h3 class="mb-5 flex items-center gap-2 text-xl font-semibold text-white">
                  <Icon icon="lucide:presentation" class="text-[#24c781]" />
                  调研&参会经历
              </h3>

              <div class="mb-5 grid gap-4 lg:grid-cols-2">
                  <article
                    v-for="item in featuredSeminarData"
                    :key="`${item.time}-${item.title}`"
                    class="flex min-w-0 flex-col gap-4 rounded-2xl border border-[#34674f] bg-[#1b261f] p-5"
                  >
                      <div class="flex min-w-0 items-start gap-4">
                          <div class="inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-[#34674f] bg-[#193025] text-[#24c781]">
                              <Icon :icon="item.icon" class="text-xl" />
                          </div>
                          <div class="min-w-0">
                              <div class="flex flex-wrap items-center gap-2">
                                  <span class="rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                                      {{ item.time }}
                                  </span>
                                  <span class="rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                                      核心演讲经历
                                  </span>
                              </div>
                              <p class="mt-3 break-words text-lg font-semibold leading-snug text-white">{{ item.title }}</p>
                              <p class="mt-2 break-words text-sm font-medium leading-relaxed text-[#24c781]">{{ item.location }}</p>
                          </div>
                      </div>

                      <div class="grid gap-3 text-sm text-[#d4d4d4] sm:grid-cols-2">
                          <div class="flex min-w-0 items-start gap-2 rounded-xl border border-[#2f2f2f] bg-[#202020] p-3">
                              <Icon icon="lucide:users" class="mt-0.5 shrink-0 text-base text-[#24c781]" />
                              <span class="break-words leading-relaxed">{{ item.audience }}</span>
                          </div>
                          <div class="flex min-w-0 items-start gap-2 rounded-xl border border-[#2f2f2f] bg-[#202020] p-3">
                              <Icon icon="lucide:mic-2" class="mt-0.5 shrink-0 text-base text-[#24c781]" />
                              <span class="break-words leading-relaxed">{{ item.role }}</span>
                          </div>
                      </div>

                      <p class="break-words rounded-xl border border-[#2f2f2f] bg-[#202020] p-3 text-sm leading-relaxed text-[#8f8f8f]">
                          {{ item.value }}
                      </p>
                  </article>
              </div>

              <div class="space-y-3 md:hidden">
                  <article
                    v-for="item in seminarData"
                    :key="`mobile-${item.time}-${item.location}-${item.project}`"
                    class="rounded-2xl border border-[#2f2f2f] bg-[#202020] p-4"
                  >
                      <div class="flex flex-wrap gap-2">
                          <span class="rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                              {{ item.time }}
                          </span>
                          <span class="rounded-full border border-[#34674f] bg-[#1c3026] px-3 py-1 text-xs font-medium text-[#9ae9c4]">
                              {{ item.direction }}
                          </span>
                      </div>
                      <p class="mt-3 break-words text-base font-semibold leading-snug text-white">{{ item.project }}</p>
                      <p class="mt-2 break-words text-sm font-medium leading-relaxed text-[#24c781]">{{ item.location }}</p>
                  </article>
              </div>

              <div class="hidden overflow-x-auto rounded-2xl border border-[#2f2f2f] bg-[#202020] md:block">
                  <table class="min-w-full divide-y divide-[#2f2f2f]">
                      <thead class="bg-[#1b1b1b]">
                      <tr>
                          <th class="px-4 py-3 text-left text-xs font-semibold uppercase tracking-wider text-[#9ae9c4]">时间</th>
                          <th class="w-56 px-4 py-3 text-left text-xs font-semibold uppercase tracking-wider text-[#9ae9c4]">地点/机构</th>
                          <th class="px-4 py-3 text-left text-xs font-semibold uppercase tracking-wider text-[#9ae9c4]">项目/活动内容</th>
                          <th class="px-4 py-3 text-left text-xs font-semibold uppercase tracking-wider text-[#9ae9c4]">角色/技术方向</th>
                      </tr>
                      </thead>
                      <tbody class="divide-y divide-[#2f2f2f]">
                      <tr
                        v-for="item in seminarData"
                        :key="`${item.time}-${item.location}-${item.project}`"
                        class="bg-[#202020] even:bg-[#252525]"
                      >
                          <td class="whitespace-nowrap px-4 py-3 text-sm text-[#d4d4d4]">{{ item.time }}</td>
                          <td class="w-56 max-w-56 break-words px-4 py-3 text-sm leading-relaxed text-[#d4d4d4]">{{ item.location }}</td>
                          <td class="px-4 py-3 text-sm text-[#d4d4d4]">{{ item.project }}</td>
                          <td class="px-4 py-3 text-sm text-[#d4d4d4]">{{ item.direction }}</td>
                      </tr>
                      </tbody>
                  </table>
              </div>
          </section>


      </article>
    </div>
  </section>
</template>

<script setup lang="ts">
import { Icon, addIcon } from '@iconify/vue';
import { nextTick, onBeforeUnmount, onMounted, ref } from 'vue';

interface StatItem {
  number: string;
  label: string;
}

interface ExperienceItem {
  icon: string;
  title: string;
  company: string;
  date: string;
  description: string;
}

interface SocialItem {
  name: string;
  icon: string;
  link: string;
}

interface SeminarItem {
  time: string;
  location: string;
  project: string;
  direction: string;
}

interface FeaturedSeminarItem {
  time: string;
  location: string;
  title: string;
  audience: string;
  role: string;
  value: string;
  icon: string;
}

const avatarSrc = ref('/avatar.jpg');
const matrixCanvas = ref<HTMLCanvasElement | null>(null);
const resumeRoot = ref<HTMLElement | null>(null);

const activeLocale = window.location.pathname === '/en' ? 'en' : 'zh-CN';

addIcon('resume:mail', {
  width: 24,
  height: 24,
  body: '<g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></g>',
});

addIcon('resume:phone', {
  width: 24,
  height: 24,
  body: '<path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M22 16.92v3a2 2 0 0 1-2.18 2 19.8 19.8 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6A19.8 19.8 0 0 1 2.12 4.18 2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z"/>',
});

addIcon('resume:calendar-days', {
  width: 24,
  height: 24,
  body: '<g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path d="M8 2v4"/><path d="M16 2v4"/><rect width="18" height="18" x="3" y="4" rx="2"/><path d="M3 10h18"/><path d="M8 14h.01"/><path d="M12 14h.01"/><path d="M16 14h.01"/><path d="M8 18h.01"/><path d="M12 18h.01"/><path d="M16 18h.01"/></g>',
});

type MatrixColumn = {
  y: number;
  speed: number;
  trailLength: number;
  characters: string[];
};

const matrixCharacters = '01010123456789';
const matrixFontSize = 18;
const matrixColumnWidth = 22;
const matrixFrameDelay = 44;

let matrixColumns: MatrixColumn[] = [];
let matrixAnimationFrame = 0;
let lastMatrixFrame = 0;
let reducedMotionQuery: MediaQueryList | null = null;
let logicalCanvasWidth = 0;
let logicalCanvasHeight = 0;

const isMobileViewport = () => window.matchMedia('(max-width: 640px)').matches;

const randomMatrixCharacter = () => matrixCharacters[Math.floor(Math.random() * matrixCharacters.length)];

const createMatrixColumns = () => {
  const columnCount = Math.ceil(logicalCanvasWidth / matrixColumnWidth);

  matrixColumns = Array.from({ length: columnCount }, () => ({
    y: Math.random() * logicalCanvasHeight,
    speed: 0.8 + Math.random() * 1.8,
    trailLength: 5 + Math.floor(Math.random() * 5),
    characters: Array.from({ length: 9 }, randomMatrixCharacter),
  }));
};

const sizeMatrixCanvas = () => {
  const canvas = matrixCanvas.value;
  const context = canvas?.getContext('2d');

  if (!canvas || !context) {
    return;
  }

  const dpr = Math.min(window.devicePixelRatio || 1, 1.5);
  logicalCanvasWidth = Math.ceil(window.innerWidth);
  logicalCanvasHeight = Math.ceil(window.innerHeight);

  canvas.width = Math.floor(logicalCanvasWidth * dpr);
  canvas.height = Math.floor(logicalCanvasHeight * dpr);
  canvas.style.width = `${logicalCanvasWidth}px`;
  canvas.style.height = `${logicalCanvasHeight}px`;
  context.setTransform(dpr, 0, 0, dpr, 0, 0);
  context.clearRect(0, 0, logicalCanvasWidth, logicalCanvasHeight);

  createMatrixColumns();
};

const drawStaticMatrixTexture = () => {
  const canvas = matrixCanvas.value;
  const context = canvas?.getContext('2d');

  if (!canvas || !context) {
    return;
  }

  context.clearRect(0, 0, logicalCanvasWidth, logicalCanvasHeight);
  context.font = `${matrixFontSize}px ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace`;
  context.textAlign = 'center';
  context.textBaseline = 'top';
  context.fillStyle = isMobileViewport() ? 'rgba(36, 199, 129, 0.24)' : 'rgba(36, 199, 129, 0.12)';

  const isMobile = isMobileViewport();
  const rowStep = matrixFontSize * (isMobile ? 3.3 : 6);
  const drawThreshold = isMobile ? 0.46 : 0.62;
  const edgeBandWidth = Math.min(92, logicalCanvasWidth * 0.24);

  matrixColumns.forEach((_, columnIndex) => {
    const x = columnIndex * matrixColumnWidth + matrixColumnWidth / 2;
    const distanceToEdge = Math.min(x, logicalCanvasWidth - x);
    const edgeStrength = isMobile ? Math.max(0, 1 - distanceToEdge / edgeBandWidth) : 0;
    const opacity = isMobile ? 0.2 + edgeStrength * 0.58 : 0.12;
    const threshold = isMobile ? drawThreshold - edgeStrength * 0.22 : drawThreshold;

    context.fillStyle = `rgba(36, 199, 129, ${opacity})`;

    for (let y = 0; y < logicalCanvasHeight; y += rowStep) {
      if (Math.random() > threshold) {
        context.fillText(randomMatrixCharacter(), x, y + Math.random() * matrixFontSize * (isMobile ? 2.2 : 4));
      }
    }
  });
};

const drawMatrixRain = (timestamp: number) => {
  const canvas = matrixCanvas.value;
  const context = canvas?.getContext('2d');

  if (!canvas || !context) {
    return;
  }

  if (timestamp - lastMatrixFrame < matrixFrameDelay) {
    matrixAnimationFrame = window.requestAnimationFrame(drawMatrixRain);
    return;
  }

  lastMatrixFrame = timestamp;
  context.clearRect(0, 0, logicalCanvasWidth, logicalCanvasHeight);
  context.font = `${matrixFontSize}px ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace`;
  context.textAlign = 'center';
  context.textBaseline = 'top';
  context.shadowColor = 'transparent';
  context.shadowBlur = 0;

  matrixColumns.forEach((column, columnIndex) => {
    const x = columnIndex * matrixColumnWidth + matrixColumnWidth / 2;

    for (let trailIndex = 0; trailIndex < column.trailLength; trailIndex += 1) {
      const y = column.y - trailIndex * matrixFontSize;

      if (y < -matrixFontSize || y > logicalCanvasHeight + matrixFontSize) {
        continue;
      }

      const opacity = trailIndex === 0 ? 0.95 : Math.max(0.08, 0.48 - trailIndex * 0.07);
      context.fillStyle = trailIndex === 0
        ? `rgba(154, 233, 196, ${opacity})`
        : `rgba(36, 199, 129, ${opacity})`;
      context.fillText(column.characters[trailIndex] ?? randomMatrixCharacter(), x, y);
    }

    column.y += matrixFontSize * column.speed;
    column.characters.unshift(randomMatrixCharacter());
    column.characters.length = column.trailLength;

    if (column.y > logicalCanvasHeight + Math.random() * 900) {
      column.y = -Math.random() * logicalCanvasHeight * 0.35;
      column.speed = 0.8 + Math.random() * 1.8;
      column.trailLength = 5 + Math.floor(Math.random() * 5);
      column.characters = Array.from({ length: column.trailLength }, randomMatrixCharacter);
    }
  });

  matrixAnimationFrame = window.requestAnimationFrame(drawMatrixRain);
};

const startMatrixRain = () => {
  window.cancelAnimationFrame(matrixAnimationFrame);
  lastMatrixFrame = 0;

  if (isMobileViewport()) {
    return;
  }

  if (reducedMotionQuery?.matches) {
    drawStaticMatrixTexture();
    return;
  }

  matrixAnimationFrame = window.requestAnimationFrame(drawMatrixRain);
};

const handleReducedMotionChange = () => {
  sizeMatrixCanvas();
  startMatrixRain();
};

const handleMatrixResize = () => {
  sizeMatrixCanvas();
  startMatrixRain();
};

const expandableTextSelector = 'section article p[class*="leading-relaxed"]';

const toggleExpandableArticle = (element: HTMLElement) => {
  if (!isMobileViewport()) {
    return;
  }

  element.classList.toggle('is-expanded');
};

const handleExpandableTextClick = (event: MouseEvent) => {
  const target = event.target as Element | null;
  const expandableArticle = target?.closest<HTMLElement>('article');

  if (!expandableArticle || !resumeRoot.value?.contains(expandableArticle) || !expandableArticle.querySelector(expandableTextSelector)) {
    return;
  }

  toggleExpandableArticle(expandableArticle);
};

const handleExpandableTextKeydown = (event: KeyboardEvent) => {
  if (event.key !== 'Enter' && event.key !== ' ') {
    return;
  }

  const target = event.target as HTMLElement | null;
  const expandableArticle = target?.closest<HTMLElement>('article');

  if (!expandableArticle || !resumeRoot.value?.contains(expandableArticle) || !expandableArticle.querySelector(expandableTextSelector)) {
    return;
  }

  event.preventDefault();
  toggleExpandableArticle(expandableArticle);
};

const englishCopy: Record<string, string> = {
  '李凌浩': 'Linghao Li',
  '邮箱': 'Email',
  '联系号码': 'Phone',
  '电话 · 微信 · WhatsApp': 'Phone · WeChat · WhatsApp',
  '出生日期': 'Date of Birth',
  '2002年11月21日': 'November 21, 2002',
  'AI 模型算法工程化落地': 'AI Model and Algorithm Engineering',
  '专注于创新应用人工智能解决企业实际复杂问题，结合 Vibe Coding 加速需求拆解、原型验证与迭代落地，实现业务流程数字化和 AI 化改造，为企业降本增效':
    'Focused on applying AI to solve complex business problems, using Vibe Coding to accelerate requirement decomposition, prototype validation, and iterative delivery. Drives digital and AI-enabled business process transformation to reduce cost and improve efficiency.',
  '跨领域技术结合': 'Cross-Domain Technology Integration',
  '擅长将工业检测、知识管理、供应链管理、金融预测、舆情监测等领域知识，与神经网络模型改进、大语言模型工程应用、深度强化学习算法设计、经典机器学习模型应用等技术跨领域结合，并具备实验室科研经验，覆盖文献研读、框架搭建、实验设计与复现验证':
    'Skilled at combining domain knowledge in industrial inspection, knowledge management, supply chain management, financial forecasting, and public-opinion monitoring with neural network improvement, LLM engineering, deep reinforcement learning algorithm design, and classical machine learning applications. Experienced in lab research covering literature review, framework construction, experimental design, reproduction, and validation.',
  '全栈 Web 程序开发': 'Full-Stack Web Development',
  '擅长 FastAPI 和 Flask 后端开发，熟悉 Vue 和 React 前端开发，具备快速搭建、迭代全栈演示产品 MVP 的能力，高效验证业务可行性并为技术团队提供架构方案、为管理团队提供提供技术可行性分析':
    'Strong in FastAPI and Flask backend development, familiar with Vue and React frontend development, and able to rapidly build and iterate full-stack MVP demos to validate business feasibility, provide architecture options for engineering teams, and deliver technical feasibility analysis for management teams.',
  '项目管理团队协作': 'Project Management and Team Collaboration',
  '拥有 2 年与多个技术团队（产品经理、产品设计、前端、后端、测试、运维）协同经验，具备从架构设计到落地实施的项目主导能力与合作经验，以及代码重构优化经验':
    'Two years of collaboration experience with product managers, product designers, frontend, backend, QA, and operations teams. Capable of leading projects from architecture design to implementation, with practical experience in cooperation, code refactoring, and optimization.',
  '未来发展': 'Future Direction',
  '读博 ？': 'PhD Track?',
  '上海 (上海交通大学、复旦大学) or 浙江 (浙江大学) or 新加坡 (NTU、NUS) or 香港 (香港大学、香港科技大学)':
    'Shanghai (Shanghai Jiao Tong University, Fudan University) or Zhejiang (Zhejiang University) or Singapore (NTU, NUS) or Hong Kong (The University of Hong Kong, HKUST)',
  '创业 ？': 'Startup Track?',
  '依托高校资源，重点放到科研成果转化': 'Leverage university resources, with a focus on research commercialization.',
  '教育背景': 'Education',
  '【 理学硕士 MSc 】南洋理工大学 Nanyang Technological University ( NTU )':
    '[MSc] Nanyang Technological University (NTU)',
  'QS 全球排名第 12（2026），QS 亚洲排名第 3（2026），亚洲顶尖工科强校':
    'QS World University Ranking No. 12 (2026), QS Asia Ranking No. 3 (2026), a leading engineering university in Asia',
  '企业人工智能专业 Enterprise Artificial Intelligence': 'Enterprise Artificial Intelligence',
  '2026.08 - 至今': '2026.08 - Present',
  '2026.06 - 至今': '2026.06 - Present',
  '2026.04 - 至今': '2026.04 - Present',
  '2025.12 - 至今': '2025.12 - Present',
  '2025.08 - 至今': '2025.08 - Present',
  '2025.07 - 至今': '2025.07 - Present',
  '2026.07 - 至今': '2026.07 - Present',
  '2026.05 - 至今': '2026.05 - Present',
  '预计 2026.08 开始': 'Expected to start in 2026.08',
  '新加坡': 'Singapore',
  '浙江杭州': 'Hangzhou, Zhejiang',
  '北京': 'Beijing',
  '浙江温州': 'Wenzhou, Zhejiang',
  '湖南长沙': 'Changsha, Hunan',
  '【 二学位 】浙江工业大学 ( ZJUT )': '[Second Degree] Zhejiang University of Technology (ZJUT)',
  '国内省属重点，省部共建重点大学，浙江省工科龙头':
    'A key provincial university jointly supported by the province and ministry, and a leading engineering university in Zhejiang',
  '光电信息科学与工程专业': 'Optoelectronic Information Science and Engineering',
  '【 本科 】浙江工业大学 ( ZJUT )': '[Bachelor] Zhejiang University of Technology (ZJUT)',
  '信息管理与信息系统专业': 'Information Management and Information Systems',
  '科研成果': 'Research Output',
  '【撰写中】期刊论文《 A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles 》':
    '[In Writing] Journal Paper: A Composite LLM-Based Decision Network for Dynamic Assessment of Negative Public Opinion in New Energy Vehicles',
  '一作，人工智能&舆情治理方向': 'First author, AI and public-opinion governance',
  '【评审一轮中】期刊论文《 人智协同驱动的复杂网络舆情涌现机制及其生成式治理研究 》':
    '[Under First-Round Review] Journal Paper: Human-AI Collaboration Driven Emergence Mechanisms and Generative Governance of Public Opinion in Complex Networks',
  '学生一作，人工智能&公共管理方向，公共管理学报期刊，公共管理领域重要学术期刊 + CSSCI收录 + 北大核心收录 + 复杂系统治理与数字治理前沿议题':
    'Student first author, AI and public administration; Journal of Public Management, an important public administration journal indexed by CSSCI and Peking University Core, focused on frontier topics in complex-system governance and digital governance',
  '平台化传播与生成式智能扩散正在推动网络舆情风险由内容失真问题加速演化为兼具认知操纵、规则反身性、信息级联与风险涌现特征的“能力型风险”，对当前我国乃至全球网络舆情治理产生新一轮挑战。本文在系统梳理AIGC情境下网络舆情风险演化与治理研究的基础上，以复杂适应系统理论为核心理论基础，综合协同治理、全过程治理与生成式治理等理念，构建由“技术—组织—制度”协同生态架构、“数据流—信息流—决策流—工作流”闭环运行机制和“风险特征—治理适配”能力建设逻辑组成的生成式治理框架。研究表明，能力型风险的治理重点已由末端内容处置转向前置识别、生成推演、协同处置与迭代优化相衔接的全过程能力建设，其关键在于通过制度规范、组织协同与技术赋能的持续耦合，实现网络舆情治理从事后控制向持续能力建设转变，并为我国网络舆情风险治理的制度重构与路径优化提供理论参照。':
    'Platform-based communication and the diffusion of generative intelligence are accelerating the evolution of online public-opinion risk from content distortion into a capability-based risk characterized by cognitive manipulation, rule reflexivity, information cascades, and emergent risk. This creates new challenges for public-opinion governance in China and globally. Based on a systematic review of risk evolution and governance under AIGC, the paper uses complex adaptive systems theory as its core foundation and integrates collaborative governance, whole-process governance, and generative governance to build a framework consisting of a technology-organization-institution ecosystem, a closed-loop mechanism across data, information, decision, and workflow, and a capability-building logic linking risk characteristics with governance adaptation. The study argues that governance should move from downstream content disposal to whole-process capability building that connects early identification, generative simulation, collaborative response, and iterative optimization.',
  '【评审二轮中】会议论文《 MetaphorTree: Tree-Structured Hypothesis Search for Grounded Multimodal Metaphor Understanding 》':
    '[Under Second-Round Review] Conference Paper: MetaphorTree: Tree-Structured Hypothesis Search for Grounded Multimodal Metaphor Understanding',
  '二作，人工智能&多模态方向，AAAI 会议，CCF-A + 人工智能领域国际会议 Top + 国际人工智能研究核心阵地 + 多模态理解与推理方向高度认可':
    'Second author, AI and multimodal learning; AAAI conference, CCF-A, top international AI venue, and highly recognized venue for multimodal understanding and reasoning',
  '【外审三轮中】期刊论文《 网络舆情风险的“生成式模拟干预”治理研究——基于AI智能体赋能视角 》':
    '[Under Third-Round External Review] Journal Paper: Generative Simulation-Intervention Governance of Online Public-Opinion Risk from the Perspective of AI Agent Empowerment',
  '学生一作，人工智能&管理学方向，管理世界期刊，中国管理类 Premier + 中国国家智库核心阵地 + AMI Top + FMS Top + CSSCI收录 + 北大核心收录':
    'Student first author, AI and management; Management World, a premier Chinese management journal and national think-tank platform, indexed by AMI Top, FMS Top, CSSCI, and Peking University Core',
  '智能传播时代，企业网络舆情风险呈现出生成主体多元化、传播结构复杂化与演化路径非线性增强的特征，传统基于事后监测与静态响应的治理模式难以支撑企业在高不确定环境下开展前瞻性研判与策略优化。针对上述问题，本文提出“生成式模拟—干预”（Generative Simulation–Intervention，GSI）治理框架。GSI框架构建了由风险感知、生成式推演与决策干预构成的三层智能体体系，并通过“表征—思考—行动—反馈”（RTAF）闭环机制实现多源舆情数据的结构化表达、微观行为模拟与宏观态势演化。在方法上，框架进一步引入反事实推演机制，在统一初始条件下对多种治理策略进行路径模拟与效果比较，使企业舆情回应从事后评估拓展为事前可计算实验。在此基础上，通过嵌入数据知识底座与人智协同机制，实现舆情风险识别、演化推演与策略优化的统一建模与持续学习。基于新能源汽车企业典型舆情事件的实证检验结果表明，GSI能够有效刻画长时序舆情风险演化过程，并显著区分不同治理策略在信念、立场与情绪结构上的影响差异，同时支持策略在反事实条件下的可比性评估。进一步地，人智协同机制验证了AI在风险识别与策略推演中的辅助作用，以及人类在价值判断与合规决策中的主导地位。本文拓展了生成式人工智能在企业风险治理领域的理论边界，将舆情治理从“静态识别—事后响应”推进至“动态模拟—策略实验”的生成式治理范式，为企业开展舆情压力测试、策略预演与人智协同决策提供了新的分析框架与方法支持。':
    'In the era of intelligent communication, corporate online public-opinion risk is marked by diversified generative actors, complex propagation structures, and increasingly nonlinear evolution paths. Traditional governance based on post-event monitoring and static response is insufficient for proactive judgment and strategy optimization under high uncertainty. This paper proposes a Generative Simulation-Intervention (GSI) governance framework with a three-layer agent system for risk perception, generative simulation, and decision intervention. Through a representation-thinking-action-feedback loop, it structures multi-source public-opinion data, simulates micro behaviors, and models macro situation evolution. The framework introduces counterfactual simulation to compare governance strategies under unified initial conditions, turning corporate response from post-event assessment into pre-event computable experimentation. Empirical tests on typical new-energy vehicle public-opinion incidents show that GSI can model long-term risk evolution and distinguish strategy effects on beliefs, positions, and emotion structures.',
  '【评审二轮中】期刊论文《 Early Fault Detection in Wind Turbines Using an Innovative Contrast-Based Mode 》':
    '[Under Second-Round Review] Journal Paper: Early Fault Detection in Wind Turbines Using an Innovative Contrast-Based Mode',
  '一作，人工智能&新能源方向，Wind Energy 期刊，风电细分领域权威 + SCI-E + Mechanical Engineering Q2 + 全球风电行业高度认可 + 理论与工程结合':
    'First author, AI and new energy; Wind Energy journal, an authoritative wind-power venue indexed by SCI-E, Mechanical Engineering Q2, highly recognized by the global wind-power industry and combining theory with engineering',
  '期刊论文《 基于不平衡正负样本对比自监督学习的风力发电机故障预警模型 》':
    'Journal Paper: A Wind Turbine Fault Early-Warning Model Based on Contrastive Self-Supervised Learning with Imbalanced Positive and Negative Samples',
  '一作，人工智能&新能源方向，计算机集成制造系统 ( CIMS ) 期刊，计算机与智能制造交叉领域 + EI收录 + CSCD收录 + 北大核心收录 + CCF推荐中文高质量':
    'First author, AI and new energy; Computer Integrated Manufacturing Systems (CIMS), an interdisciplinary journal in computing and intelligent manufacturing, indexed by EI, CSCD, Peking University Core, and recommended by CCF as a high-quality Chinese journal',
  '为了避免大型风力发电机因异常导致严重经济损失，需要尽早对一些关键故障进行预警。针对现有SCADA系统预警时间不足，以及大量的状态时间序列数据与稀少的故障标签数据之间存在极大不平衡问题，提出了一种基于不平衡正负样本对比自监督学习模型的风力发电机故障预警方法。在引入箱线下采样方法对输入的高频时间序列数据进行合理压缩的基础上，采用核贝叶斯多元自回归模型与注意力变分自编码器模型对正、负样本数据集分别进行非对称重构，结合自适应阈值树分类模型，实现在不平衡数据集上的异常状态监测与预警能力。通过来自实际风场数据的实验，以及与传统机器学习和当前主流深度学习中的监督学习范式进行对比分析，结果显示所提出的对比自监督学习模型在风力发电机故障预警任务的各项评价指标中均表现优越并展示了巨大潜力。':
    'To avoid severe economic losses caused by large wind turbine faults, key failures must be warned as early as possible. Addressing insufficient warning lead time in existing SCADA systems and the severe imbalance between abundant state time-series data and scarce fault labels, this work proposes a wind turbine fault early-warning method based on contrastive self-supervised learning with imbalanced positive and negative samples. After applying boxplot downsampling to compress high-frequency input time series, the method uses a kernel Bayesian multivariate autoregressive model and an attention variational autoencoder to asymmetrically reconstruct positive and negative samples, then combines an adaptive threshold tree classifier for anomaly monitoring and early warning on imbalanced datasets. Experiments on real wind-farm data show strong performance across early-warning metrics.',
  '证书&竞赛荣誉': 'Certificates and Competition Honors',
  '“运河杯” 课外学术科技作品竞赛': 'Canal Cup Extracurricular Academic and Scientific Works Competition',
  '二等奖': 'Second Prize',
  '“挑战杯” 课外学术科技作品竞赛 “人工智能+” 专项赛': 'Challenge Cup Extracurricular Academic and Scientific Works Competition, Artificial Intelligence+ Special Track',
  '银奖': 'Silver Award',
  '“数智舆控”——双引擎驱动的涉企舆情⻛险智能预警与协同治理系统':
    'Digital-Intelligent Public Opinion Control: A Dual-Engine Intelligent Early-Warning and Collaborative Governance System for Corporate Public-Opinion Risk',
  'CAMCM 认证杯数学建模国际赛': 'CAMCM Certification Cup International Mathematical Modeling Competition',
  'CAMCM认证杯数学建模国际赛': 'CAMCM Certification Cup International Mathematical Modeling Competition',
  'Finalist (F奖)，特等奖提名': 'Finalist (F Award), Grand Prize Nominee',
  'Neo4j 图数据库': 'Neo4j Graph Database',
  'Certified Professional，认证专家': 'Certified Professional',
  '电子商务“创新、创意及创业”挑战赛 (三创赛)': 'E-Commerce Innovation, Creativity and Entrepreneurship Challenge',
  '电子商务三创赛': 'E-Commerce Innovation, Creativity and Entrepreneurship Challenge',
  '浙江省银奖': 'Zhejiang Provincial Silver Award',
  '基于“机-网-云”的山区农业产销服务平台': 'A Mountain Agriculture Production and Sales Service Platform Based on Machine-Network-Cloud Integration',
  '项目&研究经验': 'Projects and Research Experience',
  '【待开始】【Web全栈开发】基于持续学习的科研团队生产力促进 AI 系统':
    '[Planned] [Full-Stack Web Development] Continual-Learning-Based AI Productivity System for Research Teams',
  '待定': 'TBD',
  '【开发中】【论文实验】面向职业社群的动态舆情多风险感知框架':
    '[In Development] [Paper Experiment] Dynamic Multi-Risk Public-Opinion Perception Framework for Professional Communities',
  '浙江大学&阿里巴巴淘宝闪购': 'Zhejiang University & Alibaba Taobao Flash Purchase',
  '面向网络职业社群高上下文依赖、风险语义漂移与多类型风险耦合演化问题，设计以生成式 AI 为核心的动态多风险感知框架：通过领域自适应语义表征与贝叶斯在线变化点检测完成聊天流语义事件切分，结合扎根式风险本体开放编码、原子风险事件抽取和多维度置信校准，实现高召回、可审计的风险识别；进一步构建风险主题动态演化、交叉激发建模、多跨度预测与最快变化检测机制，并以人机协同闭环支持概念漂移监测、风险知识版本化迭代和有限审核资源下的预警优先级优化':
    'Designed a generative-AI-centered dynamic multi-risk perception framework for online professional communities with high contextual dependency, drifting risk semantics, and coupled multi-type risk evolution. The framework segments chat-stream semantic events through domain-adaptive representation and Bayesian online change-point detection, combines open coding for grounded risk ontology, atomic risk-event extraction, and multidimensional confidence calibration for high-recall, auditable risk identification, and further supports risk topic evolution, cross-excitation modeling, multi-horizon prediction, fastest change detection, concept-drift monitoring, versioned risk knowledge iteration, and warning-priority optimization under limited review resources.',
  '【开发中】【Web全栈开发】全栈上下文编排器': '[In Development] [Full-Stack Web Development] Full-Stack Context Orchestrator',
  '自研': 'Self-developed',
  '【开发中】【Web全栈开发】小红书 AI 全流程自动化自媒体运营系统':
    '[In Development] [Full-Stack Web Development] Xiaohongshu AI End-to-End Automated Media Operations System',
  '【开发中】【Web全栈开发】AI 金融分析系统': '[In Development] [Full-Stack Web Development] AI Financial Analysis System',
  '【论文实验】百万级论文 LLM 专家定位评估实验程序':
    '[Paper Experiment] Million-Scale Paper LLM Expert Positioning and Evaluation Program',
  '中国科学院大学': 'University of Chinese Academy of Sciences',
  '面向已识别为使用 AI 的科研论文摘要，构建“研究环节识别、AI 功能识别、方法学定位与必要性强度评分”四维判定框架，用于判断 AI 在具体研究中的重要程度：是常规辅助工具、核心分析方法，还是传统方法难以替代的知识生产机制；设计提示词模板、结构化输出规范与批量后处理机制，支持百万级摘要的定位评估、证据归因和结果统计，显著加快了并批量进行的 LLM 总体推理速度，并显著降低了总体 LLM 调用成本':
    'Built a four-dimensional evaluation framework for abstracts of AI-using research papers, covering research-stage identification, AI-function identification, methodological positioning, and necessity-strength scoring to determine whether AI acts as a routine auxiliary tool, a core analytical method, or a knowledge-production mechanism difficult to replace with traditional methods. Designed prompt templates, structured output specifications, and batch post-processing to support million-scale abstract evaluation, evidence attribution, result statistics, faster aggregate LLM inference, and lower overall LLM cost.',
  '【开发中】【Web全栈开发】国际媒体舆情AI采集分析系统':
    '[In Development] [Full-Stack Web Development] International Media Public-Opinion AI Collection and Analysis System',
  '浙江工业大学区域国别研究院': 'Institute of Area Studies, Zhejiang University of Technology',
  '【技术顾问】医院病历文本挖掘和病历质量监控模型':
    '[Technical Consultant] Medical Record Text Mining and Medical Record Quality Monitoring Model',
  '浙江省人民医院': "Zhejiang Provincial People's Hospital",
  '基于 LLM 专家经验构建高质量小样本标准库，并结合既有 CNN 识别神经网络对训练流程与特征表达进行改进，有效缓解病历标注数据不足带来的模型训练瓶颈，提升了病历文本识别准确率与 F1 表现，支撑病历质量监控与文本挖掘任务落地':
    'Built a high-quality small-sample standard library based on LLM expert experience, and improved the training process and feature representation of an existing CNN recognition network. The work alleviated model-training bottlenecks caused by limited labeled medical record data, improved text-recognition accuracy and F1 performance, and supported deployment of medical record quality monitoring and text mining tasks.',
  '【论文实验】百万级论文 AI 暴露度计算与科研方法替代潜力测算程序':
    '[Paper Experiment] Million-Scale Paper AI Exposure and Research-Method Substitution Potential Calculation Program',
  '面向能源转型与气候变化领域的全量相关论文，构建“LLM 语义判别 + 向量检索匹配 + 技术成熟度约束加权”的三阶段 AI 暴露度测算框架，用于评估即使当前研究尚未使用 AI，其科研流程在 AI 原生方法、成熟 AI 技术库与历史方法库支持下被重构或替代的潜力；由于三阶段逻辑彼此依赖，采用先综述剔除、再主题筛选、再科研流程阶段映射的分阶段串联处理，并进一步完成 AI 使用度、不可替代性与暴露度计算及分块持久化输出，以支撑百万级论文规模的高效运行，同时显著加快 LLM 总体推理速度并降低调用成本':
    'For full-scope papers in energy transition and climate change, built a three-stage AI exposure calculation framework combining LLM semantic judgment, vector retrieval matching, and technology-maturity-constrained weighting. The framework evaluates the potential for research workflows to be reconstructed or substituted by AI-native methods, mature AI technology libraries, and historical method libraries even when current studies do not use AI. Because the three stages are interdependent, it uses staged serial processing from review exclusion to topic screening and research-process mapping, then calculates AI usage, non-substitutability, and exposure with chunked persistent output to support efficient million-scale operation, faster aggregate LLM inference, and lower cost.',
  '【算法设计】物流运输成本优化算法': '[Algorithm Design] Logistics Transportation Cost Optimization Algorithm',
  '天能电池集团股份有限公司': 'Tianneng Battery Group Co., Ltd.',
  '主导设计大规模动态规划时间窗口订单合并算法，结合企业阶梯式业务规则，通过时空合并将30K订单压缩至9K组，降低约5.8%的运输总成本，同时设计了基于甘特图的合并订单可视化方法':
    'Led the design of a large-scale dynamic-programming time-window order-merging algorithm. Combined with tiered enterprise business rules, the algorithm compressed 30K orders into 9K groups through spatiotemporal merging, reduced total transportation cost by about 5.8%, and included a Gantt-chart-based merged-order visualization method.',
  '【模型设计】虚拟仿真智能采购数据分析教学程序':
    '[Model Design] Virtual Simulation Intelligent Procurement Data Analysis Teaching Program',
  '一鼎堂软件科技有限公司杭州分公司': 'Hangzhou Branch of Yidingtang Software Technology Co., Ltd.',
  '撰写多种模型机器学习数据分析实验代码，并实现特征过滤法、特征嵌入法、特征包裹法等特征工程和决策树、神经网络模型训练可视化方法':
    'Developed machine learning data-analysis experiment code for multiple models, and implemented feature filtering, feature embedding, wrapper-based feature engineering, and visual training methods for decision trees and neural network models.',
  '【Web全栈开发】基于 LLM 的自动化论文知识网络构建平台全栈程序':
    '[Full-Stack Web Development] LLM-Based Automated Paper Knowledge Network Construction Platform',
  '浙江工业大学图书馆': 'Zhejiang University of Technology Library',
  '应用大语言模型，实现根据多检索词自动化构建论文-主题短语的知识网络并生成多角度文献综述，快速呈现某领域研究现状':
    'Applied large language models to automatically construct paper-topic phrase knowledge networks from multiple search terms and generate multi-perspective literature reviews, enabling rapid presentation of a research field.',
  '【技术顾问】服装设计草图生成 AIGC 程序': '[Technical Consultant] AIGC Fashion Design Sketch Generation Program',
  '南郊韫典服装厂': 'Nanjiao Yundian Garment Factory',
  '为企业的运动女装服饰设计草图AI生成模型提供技术框架，搭建企业服饰草图数据库，助力提高服装设计师的效率和工厂的数字化转型':
    'Provided the technical framework for an AI sketch-generation model for women’s sportswear design, built a corporate fashion sketch database, and helped improve designer efficiency and factory digital transformation.',
  '【技术顾问】智能投标文件辅助写作 LLM 程序': '[Technical Consultant] LLM-Assisted Intelligent Bid Document Writing Program',
  '温州微极光智能科技有限公司': 'Wenzhou Weijiguang Intelligent Technology Co., Ltd.',
  '设计结合企业多部门资料库的智能投标文件辅助写作LLM程序的技术框架，提高投标文件书写规范':
    'Designed the technical framework for an LLM-assisted intelligent bid document writing program integrated with multi-department enterprise knowledge bases, improving bid document writing standards.',
  '【Web全栈开发】深度学习模型全流程可研实验平台全栈程序':
    '[Full-Stack Web Development] End-to-End Deep Learning Model Research Experiment Platform',
  '綦方中教授科研团队': 'Professor Qi Fangzhong Research Team',
  '设计开发支持模型组件自定义设计的全栈平台，覆盖数据定义、模型定义、模型训练、数据可视化全流程，助力模型结构调优自动化实验研究':
    'Designed and developed a full-stack platform supporting custom model component design, covering data definition, model definition, model training, and data visualization to support automated experimental research for model-structure tuning.',
  '【Web全栈开发】知识管理互联应用平台全栈程序':
    '[Full-Stack Web Development] Knowledge Management Interconnection Application Platform',
  '设计开发支持 PDF、Markdown 和知识图谱文件互联功能整合的全栈平台，同时开发了支持自由编辑图谱结构的前端组件，实现了团队文件管理、图谱编辑、Markdown 文件编辑、PDF 预览等功能整合':
    'Designed and developed a full-stack platform integrating PDF, Markdown, and knowledge graph file interconnection. Also developed frontend components for freely editing graph structures, integrating team file management, graph editing, Markdown editing, and PDF preview.',
  '【技术文档撰写】LLM 双层嵌套支撑电力物资管理智能化技术研究':
    '[Technical Documentation] Research on LLM Double-Nested Architecture for Intelligent Power Materials Management',
  '国家电网浙江省电力有限公司': 'State Grid Zhejiang Electric Power Co., Ltd.',
  '为团队项目规划提供核心研究思路：基于大语言模型双层嵌套框架的二次学习方法、电力物料族谱生成方法、需求知识网络生成方法、场景化应用路径生成方法研究等技术方法':
    'Provided core research ideas for team project planning, including secondary learning based on an LLM double-nested framework, power-material lineage generation, demand knowledge network generation, and scenario-based application path generation.',
  '【模型设计】高光谱油液多元素预测模型': '[Model Design] Hyperspectral Oil Multi-Element Prediction Model',
  '联桥网云信息科技有限公司': 'Lianqiao Wangyun Information Technology Co., Ltd.',
  '为手持检测设备提供核心预测算法，提出基于可学习参数小波变换的 BiScaleWaveNet 双流异构神经网络模型，通过将低频趋势与高频瞬态数据特征解耦，实现风机齿轮箱中油液的高光谱多元素定量预测':
    'Provided the core prediction algorithm for handheld detection equipment. Proposed the BiScaleWaveNet dual-stream heterogeneous neural network based on learnable-parameter wavelet transformation, decoupling low-frequency trends from high-frequency transient features to achieve hyperspectral quantitative multi-element prediction for wind turbine gearbox oil.',
  '【Web后端开发】项目计划智能度量后端': '[Backend Web Development] Intelligent Project Planning Measurement Backend',
  '主导项目二期重构与开发，个人完成核心模块改进与新需求实现，实现了 Excel 项目估算书智能解析、Word 项目可研文本智能解析、语料库搭建、Excel 因子公式动态公式配置等功能':
    'Led phase-two refactoring and development. Personally completed core module improvements and new requirements, including intelligent parsing of Excel project estimation sheets, intelligent parsing of Word feasibility study documents, corpus construction, and dynamic configuration of Excel factor formulas.',
  '【Web后端开发】科技资源检索引擎后端': '[Backend Web Development] Science and Technology Resource Search Engine Backend',
  '主导项目全生命周期开发，基于图数据库构建企业级异构知识图谱，实现了关系型和图结构数据双重智能检索、异构图数据重构、关键热词排序、专业词语义总结等功能':
    'Led full-lifecycle development and built an enterprise-grade heterogeneous knowledge graph using graph databases. Implemented intelligent retrieval across relational and graph-structured data, heterogeneous graph data reconstruction, key hot-word ranking, and professional term semantic summarization.',
  '工作经历': 'Work Experience',
  '浙江火炬生产力促进中心有限公司': 'Zhejiang Torch Productivity Promotion Center Co., Ltd.',
  '【实习】数据分析师': '[Internship] Data Analyst',
  '杭州国信大数据应用研究院': 'Hangzhou Guoxin Big Data Application Research Institute',
  '调研&参会经历': 'Research Visits and Conference Experience',
  '核心演讲经历': 'Featured Speaking Experience',
  '时间': 'Time',
  '地点/机构': 'Location / Institution',
  '项目/活动内容': 'Project / Activity',
  '角色/技术方向': 'Role / Technical Focus',
  '西安·Production and Operations Management Society International Conference (POMS) 国际学术会议':
    "Xi'an · Production and Operations Management Society International Conference (POMS)",
  'Artificial Intelligence and Operations Management 分会场': 'Artificial Intelligence and Operations Management Session',
  '面向博士生、高校教师等学术受众': 'Academic audience including PhD students and university faculty',
  '台上学术分享演讲与现场答疑': 'On-stage academic presentation and live Q&A',
  '在国际学术会议场景中完成公开表达，具备 AI 与运营管理交叉研究理解、议题组织能力和问答应对能力':
    'Delivered public speaking in an international academic conference setting, demonstrating understanding of AI and operations management research, topic organization, and Q&A handling.',
  '浙江工业大学管理学院 MBA 企业高管课堂': 'ZJUT School of Management MBA Executive Class',
  '浙江工业大学管理学院MBA企业高管课堂': 'ZJUT School of Management MBA Executive Class',
  'AI技术落地方案': 'AI Technology Implementation Solutions',
  '面向企业高级管理人员': 'Audience of senior enterprise managers',
  '台上技术方案分享与现场答疑': 'On-stage technical solution sharing and live Q&A',
  '将 AI 技术能力转译为企业管理者可理解的落地方案，具备跨技术、业务与管理语境的表达和沟通能力':
    'Translated AI technical capabilities into implementation plans understandable to enterprise managers, showing communication ability across technical, business, and management contexts.',
  '台上学术分享演讲和答疑（博士生和高校教师为主）':
    'On-stage academic presentation and Q&A, mainly for PhD students and university faculty',
  '杭州·浙江省人民医院': "Hangzhou · Zhejiang Provincial People's Hospital",
  '医院病历文本挖掘和病历质量监控技术探讨': 'Discussion on medical record text mining and medical record quality monitoring technology',
  '技术顾问（朱教授、童教授合作）': 'Technical consultant, collaborating with Professor Zhu and Professor Tong',
  '杭州·用友软件公司': 'Hangzhou · Yonyou Software Company',
  '大模型赋能BI商务智能的企业应用前沿技术交流': 'Frontier technical exchange on LLM-enabled enterprise BI applications',
  '技术交流（綦教授带队）': 'Technical exchange, led by Professor Qi',
  '浙江省房地产研究院': 'Zhejiang Real Estate Research Institute',
  'RWA区块链技术在房地产融资中的可行性研究': 'Feasibility study of RWA blockchain technology in real estate financing',
  '应用技术研究讨论（綦教授带队）': 'Applied technology research discussion, led by Professor Qi',
  '台上分享技术方案和答疑（高级管理人员课程）': 'On-stage technical solution sharing and Q&A for an executive management course',
  '浙江工业大学': 'Zhejiang University of Technology',
  '通用大模型与企业战略管理交叉研究高端论坛': 'High-end forum on general-purpose large models and enterprise strategic management',
  '参会学习（贾教授：LLM赋能企业考核与培训）': 'Conference learning, Professor Jia on LLM-enabled enterprise assessment and training',
  '北京·宝健公司': 'Beijing · Baojian Company',
  '健康管理全周期能力调研': 'Full-cycle health management capability research',
  '产业调研': 'Industry research',
  '北京·亦庄生物医药园': 'Beijing · Yizhuang Biopharmaceutical Park',
  '生物医药全链条服务调研': 'Biopharmaceutical full-chain service research',
  '北京·中科电商谷园区': 'Beijing · Zhongke E-Commerce Valley Park',
  '跨境电商与数字贸易创新实地调研': 'Field research on cross-border e-commerce and digital trade innovation',
  '北京·生物医药大健康创新路演会': 'Beijing · Biomedical and Healthcare Innovation Roadshow',
  '外泌体生物技术创新产品研讨 + 生信多模态专家大模型科研应用系统构建方案交流':
    'Discussion on exosome biotechnology innovation products plus exchange on a bioinformatics multimodal expert LLM research application system',
  '技术交流（覃教授、俞院长、王博士合作）':
    'Technical exchange, collaborating with Professor Qin, Dean Yu, and Dr. Wang',
  '杭州·天能集团': 'Hangzhou · Tianneng Group',
  '供应链物流成本优化策略研讨会（降低零担物流率与整车物流率提升措施）':
    'Seminar on supply-chain logistics cost optimization, including reducing LTL rate and improving FTL rate',
  '业务逻辑分析和技术实现（胡教授带队）': 'Business logic analysis and technical implementation, led by Professor Hu',
  '全国人工智能应用创新大赛': 'National Artificial Intelligence Application Innovation Competition',
  'AI智能体赋能涉企舆情治理研究（百度智能云千帆平台）':
    'Research on AI-agent-enabled corporate public-opinion governance using Baidu AI Cloud Qianfan platform',
  '团队技术探讨（AI智能体开发）': 'Team technical discussion on AI agent development',
  '浙江工业大学+红杉资本公司': 'Zhejiang University of Technology + Sequoia Capital',
  '大语言模型在知识管理中的应用进展汇报': 'Progress report on LLM applications in knowledge management',
  '企业技术探讨（綦教授带队）': 'Enterprise technical discussion, led by Professor Qi',
  '杭州·一鼎堂软件公司': 'Hangzhou · Yidingtang Software Company',
  '机器学习数据分析教学任务代码设计开发': 'Code design and development for machine learning data-analysis teaching tasks',
  '开发实施（周教授项目）': 'Development implementation, Professor Zhou project',
  '杭州·火炬中心+技术转移转化中心': 'Hangzhou · Torch Center + Technology Transfer and Commercialization Center',
  '产学研三端匹配大模型与应用研究': 'Research on large models and applications for matching industry, academia, and research',
  '技术调研（綦教授带队）': 'Technical research, led by Professor Qi',
  '文献计量学与LLM在知识管理中的应用': 'Bibliometrics and LLM applications in knowledge management',
  '学术研讨（方教授、綦教授合作）': 'Academic seminar, collaborating with Professor Fang and Professor Qi',
  '温州·微极光智能科技有限公司': 'Wenzhou · Weijiguang Intelligent Technology Co., Ltd.',
  '智能投标文件辅助写作LLM程序技术探讨': 'Technical discussion on an LLM-assisted intelligent bid document writing program',
  '技术方案探讨（自己主导）': 'Technical solution discussion, self-led',
  '温州·南郊韫典服装厂': 'Wenzhou · Nanjiao Yundian Garment Factory',
  '服装设计草图生成AIGC程序技术探讨': 'Technical discussion on an AIGC fashion design sketch generation program',
  '长沙·联桥网云公司': 'Changsha · Lianqiao Wangyun Company',
  '高光谱油液元素检测技术在风机运维中的应用交流':
    'Application exchange on hyperspectral oil element detection technology in wind turbine operations and maintenance',
  '杭州·国网浙江省电力有限公司': 'Hangzhou · State Grid Zhejiang Electric Power Co., Ltd.',
  'LLM双层嵌套支撑电力物资管理智能化技术研究':
    'Research on LLM double-nested architecture for intelligent power materials management',
  '技术方案提供（周教授项目）': 'Technical solution provision, Professor Zhou project',
  '数学建模美赛': 'Mathematical Contest in Modeling',
  '网球比赛预测模型设计': 'Tennis match prediction model design',
  '团队技术负责': 'Team technical lead',
  '基于动态蛇形卷积的MobileNet模型改进（Classification and segmentation of product surface defects based on Lite DS-MobileNet）':
    'MobileNet improvement based on dynamic snake convolution (Classification and segmentation of product surface defects based on Lite DS-MobileNet)',
  '团队技术负责（计算机视觉模型优化）': 'Team technical lead, computer vision model optimization',
  '杭州·云栖人工智能大会': 'Hangzhou · Yunqi AI Conference',
  '大模型技术应用趋势调研': 'Research on application trends of large-model technologies',
  '南京·南瑞集团': 'Nanjing · NARI Group',
  '风机运维技术服务实地调研': 'Field research on wind turbine operations and maintenance technical services',
  '项目计划智能度量系统后端开发': 'Backend development for an intelligent project planning measurement system',
  '后端开发（周教授项目）': 'Backend development, Professor Zhou project',
  '科技资源检索引擎后端开发': 'Backend development for a science and technology resource search engine',
  '队伍二：基于“机-网-云”的山区农业产销服务平台（农业无人机病虫害图像识别监测）':
    'Team 2: Mountain agriculture production and sales service platform based on machine-network-cloud integration, including UAV pest and disease image recognition monitoring',
  '团队技术负责（无人机视觉识别）': 'Team technical lead, UAV visual recognition',
  '队伍一：AI+BI商务智能应用服务开发': 'Team 1: AI + BI business intelligence application service development',
  '杭州·中艺实业公司': 'Hangzhou · Zhongyi Industrial Company',
  '户外家具产品出海电商策略实地调研': 'Field research on overseas e-commerce strategy for outdoor furniture products',
};

const normalizeCopy = (value: string) => value.replace(/\s+/g, ' ').trim();

const translateCopy = (value: string) => englishCopy[normalizeCopy(value)];

const translateTextNodes = (root: HTMLElement) => {
  const walker = document.createTreeWalker(root, NodeFilter.SHOW_TEXT);
  const nodes: Text[] = [];

  while (walker.nextNode()) {
    nodes.push(walker.currentNode as Text);
  }

  nodes.forEach((node) => {
    const original = node.textContent ?? '';
    const translated = translateCopy(original);

    if (!translated) {
      return;
    }

    const leadingWhitespace = original.match(/^\s*/)?.[0] ?? '';
    const trailingWhitespace = original.match(/\s*$/)?.[0] ?? '';
    node.textContent = `${leadingWhitespace}${translated}${trailingWhitespace}`;
  });
};

const translateResumeCopy = async () => {
  if (activeLocale !== 'en') {
    return;
  }

  await nextTick();

  if (resumeRoot.value) {
    translateTextNodes(resumeRoot.value);
  }

  document.documentElement.lang = 'en';
};

onMounted(() => {
  reducedMotionQuery = window.matchMedia('(prefers-reduced-motion: reduce)');
  sizeMatrixCanvas();
  startMatrixRain();
  void translateResumeCopy();

  window.addEventListener('resize', handleMatrixResize);
  window.visualViewport?.addEventListener('resize', handleMatrixResize);
  reducedMotionQuery.addEventListener('change', handleReducedMotionChange);
  resumeRoot.value?.addEventListener('click', handleExpandableTextClick);
  resumeRoot.value?.addEventListener('keydown', handleExpandableTextKeydown);
});

onBeforeUnmount(() => {
  window.cancelAnimationFrame(matrixAnimationFrame);
  window.removeEventListener('resize', handleMatrixResize);
  window.visualViewport?.removeEventListener('resize', handleMatrixResize);
  reducedMotionQuery?.removeEventListener('change', handleReducedMotionChange);
  resumeRoot.value?.removeEventListener('click', handleExpandableTextClick);
  resumeRoot.value?.removeEventListener('keydown', handleExpandableTextKeydown);
});

const socialLinks: SocialItem[] = [
  { name: 'LinkedIn', icon: 'mdi:linkedin', link: '#' },
  { name: 'Reddit', icon: 'mdi:reddit', link: '#' },
  { name: 'X', icon: 'ri:twitter-x-fill', link: '#' },
  { name: 'GitHub', icon: 'mdi:github', link: '#' },
];

const statsData: StatItem[] = [
  { number: '30+', label: 'Completed Projects' },
  { number: '8+', label: 'Years of Experience' },
  { number: '36+', label: 'Happy Clients' },
  { number: '10+', label: 'Awards Received' },
];

const experienceData: ExperienceItem[] = [
  {
    icon: 'lucide:layers',
    title: 'Framer & UI/UX Designer',
    company: 'Circulum Tech',
    date: '2023 - Present',
    description:
      'Designing interactive prototypes with Framer, focusing on seamless user experiences and scalable solutions through user feedback and collaboration.',
  },
  {
    icon: 'lucide:monitor-cog',
    title: 'UI/UX Designer',
    company: 'CoreOS',
    date: '2021 - 2023',
    description:
      'Led end-to-end interface design across web products, from user journey mapping to polished visual systems that improved consistency and usability.',
  },
  {
    icon: 'lucide:pen-tool',
    title: 'Graphics Designer',
    company: 'Pixel Square',
    date: '2020 - 2021',
    description:
      'Created marketing and brand assets with strong visual hierarchy, supporting campaigns through iterative design reviews and data-informed refinements.',
  },
];

const featuredSeminarData: FeaturedSeminarItem[] = [
    {
        time: '2026.07',
        location: '西安·Production and Operations Management Society International Conference (POMS) 国际学术会议',
        title: 'Artificial Intelligence and Operations Management 分会场',
        audience: '面向博士生、高校教师等学术受众',
        role: '台上学术分享演讲与现场答疑',
        value: '在国际学术会议场景中完成公开表达，具备 AI 与运营管理交叉研究理解、议题组织能力和问答应对能力',
        icon: 'lucide:presentation'
    },
    {
        time: '2025.06',
        location: '浙江工业大学管理学院 MBA 企业高管课堂',
        title: 'AI技术落地方案',
        audience: '面向企业高级管理人员',
        role: '台上技术方案分享与现场答疑',
        value: '将 AI 技术能力转译为企业管理者可理解的落地方案，具备跨技术、业务与管理语境的表达和沟通能力',
        icon: 'lucide:graduation-cap'
    },
];

const seminarData: SeminarItem[] = [
    {
        time: '2026.07',
        location: '西安·Production and Operations Management Society International Conference (POMS) 国际学术会议',
        project: 'Artificial Intelligence and Operations Management 分会场',
        direction: '台上学术分享演讲和答疑（博士生和高校教师为主）'
    },
    {
        time: '2025.10',
        location: '杭州·浙江省人民医院',
        project: '医院病历文本挖掘和病历质量监控技术探讨',
        direction: '技术顾问（朱教授、童教授合作）'
    },
    {
        time: '2025.08',
        location: '杭州·用友软件公司',
        project: '大模型赋能BI商务智能的企业应用前沿技术交流',
        direction: '技术交流（綦教授带队）'
    },
    {
        time: '2025.07',
        location: '浙江省房地产研究院',
        project: 'RWA区块链技术在房地产融资中的可行性研究',
        direction: '应用技术研究讨论（綦教授带队）'
    },
    {
        time: '2025.06',
        location: '浙江工业大学管理学院MBA企业高管课堂',
        project: 'AI技术落地方案',
        direction: '台上分享技术方案和答疑（高级管理人员课程）'
    },
    {
        time: '2025.05',
        location: '浙江工业大学',
        project: '通用大模型与企业战略管理交叉研究高端论坛',
        direction: '参会学习（贾教授：LLM赋能企业考核与培训）'
    },
    {
        time: '2025.04',
        location: '北京·宝健公司',
        project: '健康管理全周期能力调研',
        direction: '产业调研'
    },
    {
        time: '2025.04',
        location: '北京·亦庄生物医药园',
        project: '生物医药全链条服务调研',
        direction: '产业调研'
    },
    {
        time: '2025.04',
        location: '北京·中科电商谷园区',
        project: '跨境电商与数字贸易创新实地调研',
        direction: '产业调研'
    },
    {
        time: '2025.04',
        location: '北京·生物医药大健康创新路演会',
        project: '外泌体生物技术创新产品研讨 + 生信多模态专家大模型科研应用系统构建方案交流',
        direction: '技术交流（覃教授、俞院长、王博士合作）'
    },
    {
        time: '2025.04',
        location: '杭州·天能集团',
        project: '供应链物流成本优化策略研讨会（降低零担物流率与整车物流率提升措施）',
        direction: '业务逻辑分析和技术实现（胡教授带队）'
    },
    {
        time: '2025.04',
        location: '全国人工智能应用创新大赛',
        project: 'AI智能体赋能涉企舆情治理研究（百度智能云千帆平台）',
        direction: '团队技术探讨（AI智能体开发）'
    },
    {
        time: '2025.04',
        location: '浙江工业大学+红杉资本公司',
        project: '大语言模型在知识管理中的应用进展汇报',
        direction: '企业技术探讨（綦教授带队）'
    },
    {
        time: '2025.03',
        location: '杭州·一鼎堂软件公司',
        project: '机器学习数据分析教学任务代码设计开发',
        direction: '开发实施（周教授项目）'
    },
    {
        time: '2025.03',
        location: '杭州·火炬中心+技术转移转化中心',
        project: '产学研三端匹配大模型与应用研究',
        direction: '技术调研（綦教授带队）'
    },
    {
        time: '2025.03',
        location: '浙江工业大学图书馆',
        project: '文献计量学与LLM在知识管理中的应用',
        direction: '学术研讨（方教授、綦教授合作）'
    },
    {
        time: '2025.02',
        location: '温州·微极光智能科技有限公司',
        project: '智能投标文件辅助写作LLM程序技术探讨',
        direction: '技术方案探讨（自己主导）'
    },
    {
        time: '2025.02',
        location: '温州·南郊韫典服装厂',
        project: '服装设计草图生成AIGC程序技术探讨',
        direction: '技术方案探讨（自己主导）'
    },
    {
        time: '2024.08',
        location: '长沙·联桥网云公司',
        project: '高光谱油液元素检测技术在风机运维中的应用交流',
        direction: '技术交流（綦教授带队）'
    },
    {
        time: '2024.05',
        location: '杭州·国网浙江省电力有限公司',
        project: 'LLM双层嵌套支撑电力物资管理智能化技术研究',
        direction: '技术方案提供（周教授项目）'
    },
    {
        time: '2024.02',
        location: '数学建模美赛',
        project: '网球比赛预测模型设计',
        direction: '团队技术负责'
    },
    {
        time: '2023.12',
        location: 'CAMCM认证杯数学建模国际赛',
        project: '基于动态蛇形卷积的MobileNet模型改进（Classification and segmentation of product surface defects based on Lite DS-MobileNet）',
        direction: '团队技术负责（计算机视觉模型优化）'
    },
    {
        time: '2023.09',
        location: '杭州·云栖人工智能大会',
        project: '大模型技术应用趋势调研',
        direction: '产业调研'
    },
    {
        time: '2023.08',
        location: '南京·南瑞集团',
        project: '风机运维技术服务实地调研',
        direction: '技术调研（綦教授带队）'
    },
    {
        time: '2023.07',
        location: '杭州·国网浙江省电力有限公司',
        project: '项目计划智能度量系统后端开发',
        direction: '后端开发（周教授项目）'
    },
    {
        time: '2023.06',
        location: '杭州·国网浙江省电力有限公司',
        project: '科技资源检索引擎后端开发',
        direction: '后端开发（周教授项目）'
    },
    {
        time: '2023.05',
        location: '电子商务三创赛',
        project: '队伍二：基于“机-网-云”的山区农业产销服务平台（农业无人机病虫害图像识别监测）',
        direction: '团队技术负责（无人机视觉识别）'
    },
    {
        time: '2023.04',
        location: '电子商务三创赛',
        project: '队伍一：AI+BI商务智能应用服务开发',
        direction: '团队技术负责'
    },
    {
        time: '2022.10',
        location: '杭州·中艺实业公司',
        project: '户外家具产品出海电商策略实地调研',
        direction: '产业调研'
    },
];
</script>

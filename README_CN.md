# csxo 的 GitHub Stars 结构化整理

> 把 [@csxo](https://github.com/csxo) 在 GitHub 上 Star 的 678 个项目，自动归类、按相似项目聚合、按价值评分整理成一份可检索的 Markdown 知识库。

[![Repo](https://img.shields.io/badge/repo-csxo--stars--analysis-blue)]() [![Repos](https://img.shields.io/badge/stars-678-orange)]() [![Categories](https://img.shields.io/badge/categories-26-green)]() [![License](https://img.shields.io/badge/license-MIT-lightgrey)]()

## 📌 链接

- 📊 本仓库（分析结果）：<https://github.com/csxo/csxo-stars-analysis>
- 👤 csxo GitHub 主页：<https://github.com/csxo>
- ⭐ csxo Stars 列表（数据源）：<https://github.com/csxo?tab=stars>
- 🛠 用的分析工具：[`github-stars-analyzer`](https://github.com/csxo/github-stars-analyzer)

## 📊 规模一览

| 指标 | 数值 |
| --- | --- |
| 总 Stars | **678** |
| 分类数 | **26** |
| Markdown 文件 | **705**（1 索引 + 26 分类 + 678 详情） |
| Top 语言 | TypeScript 220 · Python 206 · JavaScript 188 |
| 分析方法 | 元数据启发式（description + topics + language），未读 README |

## 🗂️ 仓库内容

```
csxo-stars-analysis/
├── README.md                          # 你正在读的中文版 README
├── README_EN.md                       # 英文版 README
├── index.md                           # 26 分类总览 + 入口
├── categories/                        # 26 个分类页（中文名）
│   ├── ai-llm.md                      #   76 个 AI / LLM 项目
│   ├── 代理-网络工具.md                #   65 个代理 / 规则工具
│   ├── 媒体-播放器.md                 #   55 个媒体类
│   ├── 桌面工具-windows优化.md        #   36 个桌面工具
│   ├── 浏览器-扩展.md                 #   35 个
│   ├── rss-阅读.md                    #   28 个
│   ├── 输入法-rime.md                 #   12 个
│   └── ... (共 26 个)
└── repos/                             # 678 个 repo 详情页
    └── <owner>-<repo>.md
```

打开 [`index.md`](./index.md) 开始浏览，或直接跳进感兴趣的分类。

## 🎯 csxo 的兴趣画像

基于元数据聚类可以看出，csxo 的兴趣大致如下（**未经 LLM 深读 README，仅由 description / topics 推断**）：

| 主题 | 数量 | 代表项目 |
| --- | --- | --- |
| **AI / Agent / LLM** | 76 | `openai/openai-python` · `deepseek-ai/DeepEP` · 模型 / Agent 框架 / 应用层全覆盖 |
| **代理 / 网络工具** | 65 | Clash / QX / Shadowrocket / Surge / sing-box / rule-set |
| **媒体 / 播放器 / 下载** | 55 | yt-dlp / YouTube / 离线音乐视频工具 |
| **桌面工具 / Windows 优化** | 36 | 各种 Windows 美化 / 性能优化 / 启动器 |
| **浏览器扩展 / 油猴** | 35 | Tampermonkey / 各类效率扩展 |
| **RSS / 阅读 / 稍后读** | 28 | RSSHub / Miniflux / 阅读器 |
| **输入法 / Rime** | 12 | 鼠须管 / 各种 RIME 词库 / 输入方案 |
| **Awesome / 资源清单** | — | 大量 Awesome 系列表收藏 |
| **开发工具 / CLI** | — | ripgrep / fzf / bat / eza / Starship 这一档 |
| **macOS / iOS** | — | 大量苹果生态工具 |

**一句话画像**：
> AI Agent 重度关注者 + 折腾代理规则的硬核玩家 + macOS / iOS 工具极客 + Rime 输入法调教 + 音视频离线下载 + Awesome 列表收藏家。

## 🧠 分析方法（诚实说明）

本仓库目前的内容用**启发式 / 元数据规则**生成，**未调用真实 LLM**：

- `summary` — 直接复用 GitHub 描述
- `features` / `capabilities` — 把描述按逗号 / 分号切片
- `use_cases` — 默认值 `["research", "explore", "evaluate"]`
- `tech_stack` — 仅根据 `language` + `topics` 推断
- `value_score` — `log(stars) + topics_count × 0.3`，分布在 5–9.3
- **同类对比** — 用 tags / topics 的 **Jaccard 相似度**，区分度有限

> 也就是说：**目前的内容适合"盘点"，不适合"决策"。**

## 🚀 升级到真 LLM 分析

如果你想让每条分析更有深度，可在 [`github-stars-analyzer`](https://github.com/csxo/github-stars-analyzer) 上配：

```env
GITHUB_TOKEN=<fine-grained-token-with-public_repo>   # 把 GitHub API 配额提到 5000/h
LLM_API_KEY=<DeepSeek / OpenAI / 任意兼容服务>
```

```bash
gsa sync --user csxo                           # 重新拉 README
gsa analyze --provider openai_compatible \
            --model deepseek-chat              # 跑真 LLM 分析
gsa report                                      # 重新生成 Markdown（覆盖）
```

跑完后：

- `summary` 会变成基于 README 的真正摘要
- `features` / `capabilities` / `use_cases` 是真读出来的
- `value_score` 是真判定的，而非 log(stars)
- 同类对比可升级到嵌入向量，效果更好

## ⚠️ 局限

- 同一份数据**只在仓库本身刷新**时才更新；csxo 实际新增的 star 不会自动进来
- 不读真 README → 总结深度有限（升级路径见上）
- Jaccard 相似度对长尾项目区分度低
- 排序基于 stars 数 + topics 数，不代表真实质量

## 📚 相关项目

- 🛠 [`github-stars-analyzer`](https://github.com/csxo/github-stars-analyzer) — 本次分析所用的工具
- 📘 [`ARCHITECTURE.md`](https://github.com/csxo/github-stars-analyzer/blob/main/ARCHITECTURE.md) — 工具架构说明

## 📄 License

MIT — 数据来自 GitHub 公开 stars；每条详情页均链接至原始仓库；版权归原作者所有。

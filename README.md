# 🧠 LLM Research Wiki

> AI/ML/NLP/CV 科研知识库 - 由 LLM 自动维护

## 🌐 在线访问

**GitHub Pages:** https://yhn-liu.github.io/LLM-Research-Wiki/

## 📊 功能特性

- ✅ 每日自动导入 arXiv 论文
- ✅ 中英双语摘要
- ✅ 论文图片自动提取
- ✅ 自动分类和标签
- ✅ GitHub Pages 自动部署
- ✅ 支持手动导入论文

## 🚀 快速开始

### 自动更新（已配置）

每天丹麦时间 08:00 自动执行：
1. 获取最新 arXiv 论文
2. 生成双语 PDF 报告
3. 导入论文到 Wiki
4. 推送到 GitHub
5. 自动部署到 GitHub Pages

### 手动导入论文

```bash
# 从 URL 导入
python3 ~/.hermes/scripts/import_paper.py https://arxiv.org/abs/2404.07143

# 从 PDF 导入
python3 ~/.hermes/scripts/import_paper.py --pdf /path/to/paper.pdf
```

### 手动同步到 GitHub

```bash
bash ~/.hermes/scripts/sync_wiki.sh
```

## 📁 目录结构

```
LLM-Research-Wiki/
├── index.html              # 首页（GitHub Pages）
├── index.md                # 索引（Obsidian）
├── _config.yml             # Jekyll 配置
├── _layouts/               # 页面模板
├── entities/papers/        # 论文页面
├── concepts/               # 概念页面
├── comparisons/            # 对比分析
├── queries/                # 查询结果
├── raw/                    # 原始资料（不发布）
├── SCHEMA.md               # 知识库规范
└── log.md                  # 操作日志
```

## 🛠️ 配置

### GitHub 认证

详见 [GITHUB_SETUP.md](GITHUB_SETUP.md)

### 定时任务

查看当前定时任务：
```bash
hermes cron list
```

## 📚 使用的工具

- **Hermes Agent** - AI 代理框架
- **arXiv API** - 论文获取
- **Google Translate** - 中英翻译
- **Jekyll** - 静态网站生成
- **GitHub Pages** - 网站托管

## 📝 更新日志

### 2026-05-01
- 🎉 初始化知识库
- 📚 导入 11 篇论文
- 🌐 配置 GitHub Pages
- ⏰ 配置每日自动更新

---

*Powered by Hermes Agent + Karpathy's LLM Wiki Pattern*

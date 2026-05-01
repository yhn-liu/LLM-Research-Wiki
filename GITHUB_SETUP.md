# GitHub 认证配置指南

为了让 Wiki 自动同步到 GitHub，你需要配置认证。以下是几种方法：

## 方法 1：使用 GitHub Personal Access Token（推荐）

### 1. 创建 Personal Access Token
1. 访问 https://github.com/settings/tokens
2. 点击 "Generate new token"
3. 选择 "Fine-grained token"
4. 设置权限：
   - Repository access: 选择 "Only select repositories" → 选择 "LLM-Research-Wiki"
   - Permissions: 选择 "Contents" → "Read and write"
5. 点击 "Generate token"
6. 复制生成的 token

### 2. 配置 Git
```bash
cd /tmp/LLM-Research-Wiki
git remote set-url origin https://<YOUR_TOKEN>@github.com/yhn-liu/LLM-Research-Wiki.git
```

### 3. 测试同步
```bash
bash ~/.hermes/scripts/sync_wiki.sh
```

## 方法 2：使用 SSH 密钥

### 1. 生成 SSH 密钥（如果没有）
```bash
ssh-keygen -t ed25519 -C "hermes-agent@localhost"
```

### 2. 添加到 GitHub
1. 复制公钥内容：`cat ~/.ssh/id_ed25519.pub`
2. 访问 https://github.com/settings/keys
3. 点击 "New SSH key"
4. 粘贴公钥并保存

### 3. 配置 Git
```bash
cd /tmp/LLM-Research-Wiki
git remote set-url origin git@github.com:yhn-liu/LLM-Research-Wiki.git
```

### 4. 测试同步
```bash
bash ~/.hermes/scripts/sync_wiki.sh
```

## 方法 3：使用 GitHub CLI

### 1. 安装 GitHub CLI
```bash
# macOS
brew install gh

# Ubuntu/Debian
sudo apt install gh
```

### 2. 登录
```bash
gh auth login
```

### 3. 配置 Git
```bash
gh auth setup-git
```

### 4. 测试同步
```bash
bash ~/.hermes/scripts/sync_wiki.sh
```

## 验证配置

运行以下命令验证配置是否成功：
```bash
cd /tmp/LLM-Research-Wiki
git push origin main
```

如果推送成功，你会看到：
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
...
To https://github.com/yhn-liu/LLM-Research-Wiki.git
   abc1234..def5678  main -> main
```

## 启用 GitHub Pages

配置认证后，需要启用 GitHub Pages：

1. 访问 https://github.com/yhn-liu/LLM-Research-Wiki/settings/pages
2. 在 "Source" 部分，选择 "GitHub Actions"
3. 保存设置

之后，每次推送到 main 分支，GitHub Actions 会自动构建并部署网站。

## 访问网站

部署完成后，访问：
**https://yhn-liu.github.io/LLM-Research-Wiki/**

## 故障排除

### 推送失败
```
fatal: Could not read from remote repository.
```
- 检查认证配置是否正确
- 确保有推送权限

### 网站未更新
- 检查 GitHub Actions 是否成功运行：https://github.com/yhn-liu/LLM-Research-Wiki/actions
- 确保已启用 GitHub Pages

### Jekyll 构建失败
- 检查 `_config.yml` 配置
- 确保 Markdown 文件格式正确

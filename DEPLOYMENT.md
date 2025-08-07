# 部署指南

## 🚀 GitHub Pages 部署

### 1. 创建 GitHub 仓库

1. 在 GitHub 上创建新仓库，名称建议为 `aalto-survival-guide`
2. 设置仓库为公开 (Public)
3. 不要初始化 README、.gitignore 或 license（因为我们已经有了）

### 2. 推送代码到 GitHub

```bash
# 添加远程仓库（替换为你的用户名）
git remote add origin https://github.com/yourusername/aalto-survival-guide.git

# 推送代码
git branch -M main
git push -u origin main
```

### 3. 启用 GitHub Pages

1. 进入仓库的 **Settings** 选项卡
2. 滚动到 **Pages** 部分
3. 在 **Source** 下选择 **GitHub Actions**
4. 保存设置

### 4. 配置 GitHub Actions

我们已经在 `.github/workflows/deploy.yml` 中配置了自动部署。

每次推送到 `main` 分支时，GitHub Actions 会自动：

1. 安装 Python 和依赖
2. 构建 MkDocs 网站
3. 部署到 GitHub Pages

### 5. 访问网站

部署完成后，你的网站将在以下地址可用：
```
https://yourusername.github.io/aalto-survival-guide/
```

## 🔧 自定义配置

### 更新 mkdocs.yml

在部署前，请更新 `mkdocs.yml` 中的以下信息：

```yaml
site_url: https://yourusername.github.io/aalto-survival-guide/
repo_name: yourusername/aalto-survival-guide
repo_url: https://github.com/yourusername/aalto-survival-guide
```

替换 `yourusername` 为你的 GitHub 用户名。

### 更新 README.md

更新 README.md 中的链接：

```markdown
访问我们的网站：[https://yourusername.github.io/aalto-survival-guide/](https://yourusername.github.io/aalto-survival-guide/)
```

## 🛠 本地开发

### 设置环境

```bash
# 克隆仓库
git clone https://github.com/yourusername/aalto-survival-guide.git
cd aalto-survival-guide

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖
pip install -r requirements.txt
```

### 本地预览

```bash
# 启动开发服务器
mkdocs serve

# 在浏览器中访问
# http://localhost:8000
```

### 构建静态文件

```bash
# 构建网站
mkdocs build

# 构建结果在 site/ 目录中
```

## 📝 添加内容

### 创建新页面

1. 在相应目录下创建 `.md` 文件
2. 更新 `mkdocs.yml` 中的 `nav` 部分
3. 提交并推送更改

### 示例：添加新的生活指南页面

```bash
# 创建新文件
touch docs/living/laundry.md

# 编辑内容
echo "# 洗衣指南" > docs/living/laundry.md
```

然后在 `mkdocs.yml` 中添加：

```yaml
nav:
  # ... 其他内容
  - 生活指南:
    - 住宿: living/housing.md
    - 交通: living/transportation.md
    - 购物: living/shopping.md
    - 饮食: living/food.md
    - 洗衣: living/laundry.md  # 新增
```

## 🔍 故障排除

### 构建失败

1. 检查 `mkdocs.yml` 语法
2. 确保所有在 `nav` 中引用的文件都存在
3. 查看 GitHub Actions 日志

### 链接错误

1. 使用相对路径链接
2. 确保目标文件存在
3. 检查文件名拼写

### 权限问题

确保 GitHub 仓库有正确的 Pages 权限：

1. 进入 **Settings** > **Actions** > **General**
2. 在 **Workflow permissions** 下选择 **Read and write permissions**
3. 保存设置

## 📊 自定义主题

### 更改颜色

在 `mkdocs.yml` 中修改：

```yaml
theme:
  palette:
    - scheme: default
      primary: blue  # 改为你喜欢的颜色
      accent: blue
```

### 添加自定义 CSS

1. 创建 `docs/stylesheets/extra.css`
2. 在 `mkdocs.yml` 中添加：

```yaml
extra_css:
  - stylesheets/extra.css
```

## 🤝 协作开发

### 分支策略

1. 为每个功能创建分支
2. 通过 Pull Request 合并到 main
3. main 分支自动部署

### 代码审查

1. 创建 Pull Request
2. 等待其他贡献者审查
3. 合并后自动部署

---

*Happy coding! 🎉* 
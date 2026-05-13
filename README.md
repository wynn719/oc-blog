# 阿伟的博客

基于 [Hugo](https://gohugo.io/) 和 [Blowfish](https://blowfish.page/) 主题构建的个人博客。

## 依赖

- [Hugo](https://gohugo.io/) >= 0.141.0 (extended version)
- [Blowfish Theme](https://blowfish.page/) >= 2.103.0

## 快速开始

### 1. 克隆项目（包含 submodule）

```bash
# 首次克隆
git clone --recursive https://github.com/wynn719/oc-blog.git

# 或者已克隆后初始化 submodule
git submodule update --init --recursive
```

### 2. 本地开发

```bash
# 启动开发服务器（子路径模式）
hugo server --baseURL http://localhost:1313/blog/

# 或直接启动（根路径）
hugo server
```

访问 http://localhost:1313/blog/ 预览。

### 3. 构建

```bash
# 构建静态文件到 public/
hugo

# 构建并压缩
hugo --minify
```

## 部署

项目使用 GitHub Actions 自动部署到 GitHub Pages。

推送代码到 `master` 分支即可触发自动构建和部署。

## 项目结构

```
.
├── archetypes/          # 内容模板
├── assets/              # 资源文件（CSS、图片等）
│   ├── css/custom.css   # 自定义样式
│   └── img/             # 图片资源
├── config/              # 配置文件
├── content/             # 博客内容
│   ├── posts/           # 文章
│   └── archives/        # 归档文章
├── hugo.toml            # Hugo 主配置
├── public/              # 构建输出（gitignored）
└── themes/blowfish/     # Blowfish 主题（submodule）
```

## 创建新文章

```bash
hugo new posts/my-new-post.md
```

## 许可证

内容版权归作者所有，代码部分遵循 MIT 许可证。

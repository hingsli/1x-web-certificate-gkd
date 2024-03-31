---
layout: post
title: "如何开发和部署此网站"
date: 2024-03-30 17:01:34 -0700
categories: jekyll
---

# **关于Jekyll**

Jekyll 是一个静态网站生成器，可以将你的纯文本转换成美观的静态网站和博客。

它可以用于文档、博客等网站，我用来它作为维护我的开源文档的网站生成器。

在本文中我们会安装并配置 Jekyll，使用 Chirpy 主题。

接着配置网站，用 Markdown 创建一些页面，使用 GitHub Action 自动构建，并且在 GitHub Pages 上托管。

# **安装依赖**

## **在 Mac 上安装**

### 安装 Homebrew

首先，如果你没有安装 Homebrew（Mac 的包管理器），打开终端（Terminal）并运行以下命令：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### 安装 Ruby

通过 Homebrew 安装最新版的 Ruby：

```bash
brew install ruby
```

安装完成后，设置 Ruby 环境变量，以便使用 Homebrew 安装的 Ruby 版本。将以下命令添加到你的 **`~/.bash_profile`** 或 **`~/.zshrc`** 文件中：

```bash
export PATH="/usr/local/opt/ruby/bin:$PATH"
```

然后执行 **`source ~/.bash_profile`** 或 **`source ~/.zshrc`** 使变更生效。

### 安装 Jekyll 和 Bundler

```bash
gem install --user-install bundler jekyll
```

将 RubyGems 的 bin 目录添加到 PATH 中。将以下命令添加到 **`~/.bash_profile`** 或 **`~/.zshrc`** 文件：

```bash
export PATH="$HOME/.gem/ruby/X.X.0/bin:$PATH"
```

**注意：** 将 **`X.X.0`** 替换为你安装的 Ruby 版本。


## **在 Linux 上安装**

首先更新系统包：

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev git
```

为了避免以 root 用户身份安装 RubyGems 包：

如果你使用的是 bash（大多数情况下的默认设置）：

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

如果你使用的是 zsh：

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### **安装 Jekyll 和 bundler**

```bash
gem install jekyll bundler
```

## **在 Windows 上安装**
我也不会，建议用WSL（Windows Subsystem for Linux）。

## **在本地部署此网站**

### **克隆此仓库**

```bash
git clone https://github.com/hingsli/1x-web-certificate-gkd.git
```

然后安装依赖项：

```bash
cd 1x-web-certificate-gkd
bundle
```

### **Jekyll 命令**

运行你的站点：

```bash
bundle exec jekyll serve --config _config.yml,_config_dev.yml
```
打开 **`localhost:4000`**查看网站。

构建你的站点：

```bash
JEKYLL_ENV=production bundle exec jekyll b
```

部署的网页文件会输出到 **`_site`** 文件夹。

## **创建文章**

### 命名约定

Jekyll 对页面和文章使用了一套命名约定

在 **`_posts`** 目录下创建文件，格式为：

```sql
YEAR-MONTH-DAY-title.md
```

例如：

```yaml
2024-03-23-git-tutorial.md
2024-03-24-php-fundamentals.md
```

文章的“header”部分位于文件顶部，比如：

```markdown
---
layout: post
title: "如何开发和部署此网站"
date: 2024-03-30 17:01:34 -0700
categories: jekyll
---
```

### 本地链接文件

从 asset 中链接图片：

```markdown
![一个截图](/assets/screenshot.webp)
```

链接到文件：

```markdown
... 你可以在这里 [下载 PDF](/assets/diagram.pdf) 。
```

去到 [Jekyll 网站](https://jekyllrb.com/docs/posts/)上查看更多文章格式规则。

## **使用 Markdown**

[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
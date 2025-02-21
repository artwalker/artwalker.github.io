---  
title: Jeklly GitHubPages Blog  
date: 2025-02-21 14:09:25 +0800  
categories: [blog]  
tags: [blog]  
--- 
# 1. 安装Ruby
更新并安装依赖
```bash
sudo apt update
sudo apt install -y git build-essential libssl-dev libreadline-dev zlib1g-dev rbenv libyaml-dev ruby3.0-dev
```
克隆 rbenv 和 ruby-build
```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

添加 rbenv 到 PATH 并初始化
```bash
echo "export PATH=\"$PATH\"" >> ~/.bashrc
```

安装并设置 Ruby 版本
```bash
rbenv install 3.2.0
rbenv global 3.2.0
echo 'eval "$(rbenv init - bash)"' >> ~/.bashrc
```

重新加载 .bashrc
```bash
source ~/.bashrc
```

显示 Ruby 版本
```bash
ruby -v
```
安装jekyll
```bash
gem -v
sudo gem install jekyll bundler
```

打开 ~/.bashrc 文件进行编辑
```bash
nano ~/.bashrc
```

在文件末尾添加以下内容
```bash
export PATH="/usr/local/bin:$PATH"
```
# 2. 博客设置
首先使用git clone拉取自己的博客仓库，然后进入项目根目录文件夹中，运行命令：
```bash
bundle install
jekyll -v
```
启动本地服务器
```bash
bundle exec jekyll serve
```
设置头像及修改用户名需要修改这个文件：_config.yml
```yml
时区：
timezone: Asia/Shanghai
title: Think Different - Do Great # the main title

tagline: Artist && Computer Engineer # it will display as the sub-title

description: >- # used by seo meta and the atom feed
  Artist && Computer Engineer

# Fill in the protocol & hostname for your site.
# e.g. 'https://username.github.io', note that it does not end with a '/'.
url: "www.novax.fun"

github:
  username: artwalker # change to your github username

twitter:
  username: EthanWang999 # change to your twitter username

social:
  # Change to your full name.
  # It will be displayed as the default author of the posts and the copyright owner in the Footer
  name: EthanWang
  email: xinxingwang@acm.org # change to your email address
  links:
    # The first element serves as the copyright owner's link
    - https://x.com/username # change to your twitter homepage
    - https://github.com/username # change to your github homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username
# the avatar on sidebar, support local or CORS resources
avatar: ./assets/avatar.jpg
```
# 3. 如何发布Post
> 注意md文档格式后面的换行

文档的标题格式：2024-07-06-0-Diffing-Files.md
md文档首行需要填入如下内容：
```md
---
title: 0 Diffing Files  
date: 2024-07-06 21:35:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
```
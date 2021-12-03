## 使用 Usage

将这一行代码加入 `<head>` 或 `<body>`，即可展现出效果：
```xml
<script src="https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget@latest/autoload.js"></script>
```
如果网站启用了 PJAX，由于看板娘不必每页刷新，因此要注意将相关脚本放到 PJAX 刷新区域之外。

换句话说，如果你是小白，或者只需要最基础的功能，就只用把这一行代码，连同前面加载 Font Awesome 的一行代码，一起放到 html 的 `<head>` 中即可。  
对于用各种模版引擎（例如 Nunjucks，Jinja 或者 PHP）生成的页面，也要自行修改，方法类似，只是可能略为麻烦。以 [Hexo](https://hexo.io) 为例，需要在主题相关的 ejs 或 njk 模版中正确配置路径，才可以加载。

**但是！我们强烈推荐自己进行配置，否则很多功能是不完整的，并且可能产生问题！**  
如果你有兴趣自己折腾的话，请看下面的详细说明。

### Using CDN

要自定义有关内容，可以把这个仓库 Fork 一份，然后进行修改。这时，使用方法对应地变为
```xml
<script src="https://cdn.jsdelivr.net/gh/username/live2d-widget@latest/autoload.js"></script>
```
将此处的 `username` 替换为你的 GitHub 用户名。为了使 CDN 的内容正常刷新，需要创建新的 git tag 并推送至 GitHub 仓库中，否则此处的 `@latest` 仍然指向更新前的文件。此外 CDN 本身存在缓存，因此改动可能需要一定的时间生效。相关文档：
- [Git Basics - Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [Managing releases in a repository](https://help.github.com/en/github/administering-a-repository/managing-releases-in-a-repository)

### Self-host

你也可以直接把这些文件放到服务器上，而不是通过 CDN 加载。

- 如果你能够通过 `ssh` 访问你的主机，请把整个仓库克隆到服务器上。执行：
  ```bash
  cd /path/to/your/webroot
  # Clone this repository
  git clone https://github.com/stevenjoezhang/live2d-widget.git
  ```
- 如果你的主机无法用 `ssh` 连接（例如一般的虚拟主机），请选择 `Download ZIP`，然后通过 `ftp` 等方式上传到主机上，再解压到网站的目录下。
- 如果你是通过 Hexo 等工具部署的静态博客，请在博客源文件（即 `source`）目录下，执行前述的 `git clone` 命令。重新部署博客时，相关文件就会自动上传到对应的路径下。为了避免这些文件被 Hexo 插件错误地修改，可能需要设置 `skip_render`。

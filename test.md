---
title: hexo 配置站点文件详解
date: 2020-05-09 22:50:00
categories:
	- note
tags: 
	- hexo

---

> 本文会对hexo的站点配置文件，进行详细的说明
>
> 主要参考[hexo官方文档](https://hexo.io/zh-cn/docs/configuration)

<!--more-->

内容顺序与配置文件一致

#### Site

| 参数          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| `title`       | 网站标题                                                     |
| `subtitle`    | 网站副标题                                                   |
| `description` | 网站描述                                                     |
| `keywords`    | 网站的关键词。使用半角逗号 `,` 分隔多个关键词。              |
| `author`      | 您的名字                                                     |
| `language`    | 网站使用的语言。对于简体中文用户来说，使用不同的主题可能需要设置成不同的值，请参考你的主题的文档自行设置，常见的有 `zh-Hans`和 `zh-CN`。 |
| `timezone`    | 网站时区。Hexo 默认使用您电脑的时区。请参考 [时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) 进行设置，如 `America/New_York`, `Japan`, 和 `UTC` 。一般的，对于中国大陆地区可以使用 `Asia/Shanghai`。 |

其中，`description`主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。`author`参数用于主题显示文章的作者。

#### URL

| 参数                         | 描述                                                         | 默认值                      |
| :--------------------------- | :----------------------------------------------------------- | :-------------------------- |
| `url`                        | 网址                                                         |                             |
| `root`                       | 网站根目录                                                   |                             |
| `permalink`                  | 文章的 [永久链接](https://hexo.io/zh-cn/docs/permalinks) 格式 | `:year/:month/:day/:title/` |
| `permalink_defaults`         | 永久链接中各部分的默认值                                     |                             |
| `pretty_urls`                | 改写 [`permalink`](https://hexo.io/zh-cn/docs/variables) 的值来美化 URL |                             |
| `pretty_urls.trailing_index` | 是否在永久链接中保留尾部的 `index.html`，设置为 `false` 时去除 | `true`                      |
| `pretty_urls.trailing_html`  | 是否在永久链接中保留尾部的 `.html`, 设置为 `false` 时去除 (*对尾部的 `index.html`无效*) | `true`                      |

**网站存放在子目录**

如果您的网站存放在子目录中，例如 `http://yoursite.com/blog`，则请将您的 `url` 设为 `http://yoursite.com/blog` 并把 `root` 设为 `/blog/`

#### Directory

|                |                                                              |                  |
| :------------- | :----------------------------------------------------------- | :--------------- |
| 参数           | 描述                                                         | 默认值           |
| `source_dir`   | 资源文件夹，这个文件夹用来存放内容。                         | `source`         |
| `public_dir`   | 公共文件夹，这个文件夹用于存放生成的站点文件。               | `public`         |
| `tag_dir`      | 标签文件夹                                                   | `tags`           |
| `archive_dir`  | 归档文件夹                                                   | `archives`       |
| `category_dir` | 分类文件夹                                                   | `categories`     |
| `code_dir`     | Include code 文件夹，`source_dir` 下的子目录                 | `downloads/code` |
| `i18n_dir`     | 国际化（i18n）文件夹                                         | `:lang`          |
| `skip_render`  | 跳过指定文件的渲染。匹配到的文件将会被不做改动地复制到 `public` 目录中。您可使用 [glob 表达式](https://github.com/micromatch/micromatch#extended-globbing)来匹配路径。 |                  |

例如：

```
skip_render: "mypage/**/*"
# 将会直接将 `source/mypage/index.html` 和 `source/mypage/code.js` 不做改动地输出到 'public' 目录
# 你也可以用这种方法来跳过对指定文章文件的渲染
skip_render: "_posts/test-post.md"
# 这将会忽略对 'test-post.md' 的渲染
```

#### writing

| 参数                    | 描述                                                         | 默认值    |
| :---------------------- | :----------------------------------------------------------- | :-------- |
| `new_post_name`         | 新文章的文件名称                                             | :title.md |
| `default_layout`        | 预设布局                                                     | post      |
| `auto_spacing`          | 在中文和英文之间加入空格                                     | false     |
| `titlecase`             | 把标题转换为 title case                                      | false     |
| `external_link`         | 在新标签中打开链接                                           | true      |
| `external_link.enable`  | 在新标签中打开链接                                           | `true`    |
| `external_link.field`   | 对整个网站（`site`）生效或仅对文章（`post`）生效             | `site`    |
| `external_link.exclude` | 需要排除的域名。主域名和子域名如 `www` 需分别配置            | `[]`      |
| `filename_case`         | 把文件名称转换为 (1) 小写或 (2) 大写                         | 0         |
| `render_drafts`         | 显示草稿                                                     | false     |
| `post_asset_folder`     | 启动 [Asset 文件夹](https://hexo.io/zh-cn/docs/asset-folders) | false     |
| `relative_link`         | 把链接改为与根目录的相对位址                                 | false     |
| `future`                | 显示未来的文章                                               | true      |
| `highlight`             | 代码块的设置                                                 |           |
| `highlight.enable`      | 开启代码块高亮                                               | `true`    |
| `highlight.auto_detect` | 如果未指定语言，则启用自动检测                               | `false`   |
| `highlight.line_number` | 显示行数 *Enabling this option will also enable `wrap` option* | `true`    |
| `highlight.tab_replace` | 用 n 个空格替换 tabs；如果值为空，则不会替换 tabs            | `''`      |
| `highlight.wrap`        | Wrap the code block in [<table>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table) | `true`    |
| `highlight.hljs`        | Use the `hljs-*` prefix for CSS classes                      | `false`   |

**相对地址**

默认情况下，Hexo 生成的超链接都是绝对地址。例如，如果您的网站域名为 `example.com`,您有一篇文章名为 `hello`，那么绝对链接可能像这样：`http://example.com/hello.html`，它是**绝对**于域名的。相对链接像这样：`/hello.html`，也就是说，无论用什么域名访问该站点，都没有关系，这在进行反向代理时可能用到。通常情况下，建议使用绝对地址。

#### Home page setting

| 参数                       | 描述                                       | 默认值 |
| -------------------------- | ------------------------------------------ | ------ |
| `index_generator.path`     | 表示主页的路径                             | `''`   |
| `index_generator.per_page` | 主页展示多少个posts的文章                  | 10     |
| `index_generator.order_by` | posts文章展示顺序，-date表示展示最新的文章 | -date  |

#### 分类 & 标签

| 参数               | 描述     | 默认值          |
| :----------------- | :------- | :-------------- |
| `default_category` | 默认分类 | `uncategorized` |
| `category_map`     | 分类别名 |                 |
| `tag_map`          | 标签别名 |                 |

#### 日期 / 时间格式

Hexo 使用 [Moment.js](http://momentjs.com/) 来解析和显示时间

| 参数                   | 描述                                                         | 默认值       |
| :--------------------- | :----------------------------------------------------------- | :----------- |
| `date_format`          | 日期格式                                                     | `YYYY-MM-DD` |
| `time_format`          | 时间格式                                                     | `HH:mm:ss`   |
| `use_date_for_updated` | 启用以后，如果 Front Matter 中没有指定 `updated`， [`post.updated`](https://hexo.io/zh-cn/docs/variables#页面变量) 将会使用 `date` 的值而不是文件的创建时间。在 Git 工作流中这个选项会很有用 | `true`       |

#### 分页 pagination

| 参数             | 描述                                | 默认值 |
| :--------------- | :---------------------------------- | :----- |
| `per_page`       | 每页显示的文章量 (0 = 关闭分页功能) | `10`   |
| `pagination_dir` | 分页目录                            | `page` |

#### 扩展

| 参数             | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| `theme`          | 当前主题名称。值为`false`时禁用主题                          |
| `theme_config`   | 主题的配置文件。在这里放置的配置会覆盖主题目录下的 `_config.yml` 中的配置 |
| `deploy`         | 部署部分的设置                                               |
| `meta_generator` | [Meta generator](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta#属性) 标签。 值为 `false` 时 Hexo 不会在头部插入该标签 |

#### 覆盖主题配置

通常情况下，Hexo 主题是一个独立的项目，并拥有一个独立的 `_config.yml` 配置文件。
你可以在站点的 `_config.yml` 配置文件中配置你的主题，这样你就不需要 fork 一份主题并维护主题独立的配置文件。

以下是一个覆盖主题配置的例子：

```
# _config.yml
theme_config:
  bio: "My awesome bio"
# themes/my-theme/_config.yml
bio: "Some generic bio"
logo: "a-cool-image.png"
```

最终主题配置的输出是：

```bash
{
  bio: "My awesome bio",
  logo: "a-cool-image.png"
}
```


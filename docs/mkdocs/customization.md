# 主题定制

项目的文档跟项目一样，多种多样，丰富多彩；使用 `Material for MkDocs` 开始让项目文档变得更漂亮。当然，我们总会遇到为了保持项目展示的独特性而需要对文档布局结构等做调整的时候。

## 添加素材文件

[MkDocs] 提供了不同的方法来定制已有主题，如果想对Material主题做微调，请将CSS或者JS文件放入 `docs` 目录。

[MkDocs]: https://www.mkdocs.org

### 额外的 CSS 样式

如果你想对文档里面某些元素的颜色或者指定元素的间距等做微调，你可以引入一个单独的额外样式文件。最简单的方法是在 `docs` 目录下创建新建一个样式文件：

``` { .sh .no-copy }
.
├─ docs/
│  └─ stylesheets/
│     └─ extra.css
└─ mkdocs.yml
```

然后，在 `mkdocs.yml` 中添加下面这行配置：

``` yaml
extra_css:
  - stylesheets/extra.css
```

### 添加额外的js

如果你想集成其他的语法高亮组件或者添加一些自定义逻辑到主题中，在 `docs` 目录下创建一个新的 JS 文件：

``` { .sh .no-copy }
.
├─ docs/
│  └─ javascripts/
│     └─ extra.js
└─ mkdocs.yml
```

然后在 `mkdocs.yml`:

``` yaml
extra_javascript:
  - javascripts/extra.js
```

## 扩展主题

如果你想改变生成的 HTML 源码（例如 添加或者移除某些部分），你可以对主题进行扩展。MkDocs支持[主题扩展]，这是一个非常方便的不需要从源码从头编译 Material而实现改变 Material主题部分内容的方法。

  [主题扩展]: https://www.mkdocs.org/user-guide/customizing-your-theme/#using-the-theme-custom_dir

### Material主题的目录结构

在 `mkdocs.yml` 中启用MkDocs的Material主题，然后新建目录 `overrides`，并通过 [`custom_dir`][custom_dir] 指向它，配置内容如下：

``` yaml
theme:
  name: material
  custom_dir: overrides
```

!!! 注意 "主题扩展的前置条件"

    为了使用 [`custom_dir`][custom_dir] 配置扩展主题，MkDocs 的 Material主题需要提前通过pip安装并在mkdocs.yml中通过名称进行指定使用，如果只是从 git 目录中 clone 下来Material的源码将不起作用。

为了覆盖Material主题中的文件，`overrides` 目录中的文件需要跟Material主题中的目录结构保持一致，`overrides` 目录下文件将覆盖Material主题中相同路径和名称的文件。同样，资源文件也可以放在 `overrides` 目录中：

Material主题目录结构：

``` { .sh .no-copy }
.
├─ .icons/                             # Bundled icon sets
├─ assets/
│  ├─ images/                          # Images and icons
│  ├─ javascripts/                     # JavaScript files
│  └─ stylesheets/                     # Style sheets
├─ partials/
│  ├─ integrations/                    # Third-party integrations
│  │  ├─ analytics/                    # Analytics integrations
│  │  └─ analytics.html                # Analytics setup
│  ├─ languages/                       # Translation languages
│  ├─ actions.html                     # Actions
│  ├─ alternate.html                   # Site language selector
│  ├─ comments.html                    # Comment system (empty by default)
│  ├─ consent.html                     # Consent
│  ├─ content.html                     # Page content
│  ├─ copyright.html                   # Copyright and theme information
│  ├─ feedback.html                    # Was this page helpful?
│  ├─ footer.html                      # Footer bar
│  ├─ header.html                      # Header bar
│  ├─ icons.html                       # Custom icons
│  ├─ language.html                    # Translation setup
│  ├─ logo.html                        # Logo in header and sidebar
│  ├─ nav.html                         # Main navigation
│  ├─ nav-item.html                    # Main navigation item
│  ├─ pagination.html                  # Pagination (used for blog)
│  ├─ palette.html                     # Color palette toggle
│  ├─ post.html                        # Blog post excerpt
│  ├─ progress.html                    # Progress indicator
│  ├─ search.html                      # Search interface
│  ├─ social.html                      # Social links
│  ├─ source.html                      # Repository information
│  ├─ source-file.html                 # Source file information
│  ├─ tabs.html                        # Tabs navigation
│  ├─ tabs-item.html                   # Tabs navigation item
│  ├─ tags.html                        # Tags
│  ├─ toc.html                         # Table of contents
│  ├─ toc-item.html                    # Table of contents item
│  └─ top.html                         # Back-to-top button
├─ 404.html                            # 404 error page
├─ base.html                           # Base template
├─ blog.html                           # Blog index page
├─ blog-archive.html                   # Blog archive index page
├─ blog-category.html                  # Blog category index page
├─ blog-post.html                      # Blog post page
└─ main.html                           # Default page
```

  [custom_dir]: https://www.mkdocs.org/user-guide/configuration/#custom_dir
  [name]: https://www.mkdocs.org/user-guide/configuration/#name

### 替换局部模板文件

替换局部模板文件直接替换上述Material主题目录结构中 `partials` 目录下对应的模板文件即可。举例来说，如果想替换主题中的 `footer.html` 模板，在项目的 `overrides` 目录下创建 `footer.html` 模板文件即可：

``` { .sh .no-copy }
.
├─ overrides/
│  └─ partials/
│     └─ footer.html
└─ mkdocs.yml
```

这样MkDocs就会使用新的模板文件渲染主题，所有的模板文件都可以这样替换。

### 替换模板中的代码块(推荐)

除了替换局部模板文件，还可以替换(或者扩展)模板中的代码块，此处的代码块是指在模板文件中预定义的实现指定特性的代码占位块。为了替换代码块，首先在 `overrides` 目录下创建 `main.html` 文件：

``` { .sh .no-copy }
.
├─ overrides/
│  └─ main.html
└─ mkdocs.yml
```

如果我们想替换站点标题，添加如下行到 `main.html` ：

``` html
{% extends "base.html" %}

{% block htmltitle %}
  <title>Lorem ipsum dolor sit amet</title>
{% endblock %}
```

如果你想在主题原有内容上添加新的内容而不是完全替换它（扩展内容），可以在原来的代码块中使用 {{super}} 来包含主题的原有内容。这个在添加新的三方脚本文件的时候尤其有用。例如：

``` html
{% extends "base.html" %}

{% block scripts %}
  <!-- Add scripts that need to run before here -->
  {{ super() }}
  <!-- Add scripts that need to run afterwards here -->
{% endblock %}
```

下面是整个Material主题预定义的代码块：

| 代码块名称         | 用法                                                     |
| :---------------- | :------------------------------------------------------- |
| `analytics`       | 集成 Google Analytics 功能                                |
| `announce`        | 公告栏(announcement bar)                                  |
| `config`          | JS配置(JavaScript application config)                     |
| `container`       | 页面主要内容容器(main content container)                   |
| `content`         | 页面主要内容(main content)                                 |
| `extrahead`       | 空块用于添加自定义meta标签                                  |
| `fonts`           | 页面字体定义(font definitions)                             |
| `footer`          | 页脚导航和版权声明(footer with navigation and copyright)   |
| `header`          | 顶部固定导航条(fixed header bar)                           |
| `hero`            | Wraps the hero teaser (if available)                      |
| `htmltitle`       | Wraps the `<title>` tag                                   |
| `libs`            | header中 JS 库（JavaScript libraries (header) ）           |
| `outdated`        | 版本提示(version warning)                                  |
| `scripts`         | 底部 JS 代码块(JavaScript application (footer))            |
| `site_meta`       | head中 meta 标签块                                         |
| `site_nav`        | 站点导航及其内容(site navigation and table of contents)     |
| `styles`          | 样式块(style sheets (also extra sources))                  |
| `tabs`            | TAB导航(tabs navigation (if available))                    |

alabaster 默认主题
####################################

`alabaster <https://alabaster.readthedocs.io/en/latest/>`_ 是一个视觉上简洁的，响应性的，可配置的 Sphinx 文档主题。它是 Sphinx1.3 版本安装时的依赖项，并被选为默认主题。

alabaster 的行为和风格可以通过多种方式进行自定义：

- 自定义样式
- 主题样式

自定义样式表
************************************

如果需要修改 alabaster 的默认 CSS 样式，可以按如下方式提供自定义 CSS 样式表：

- 创建任意的 css 的文件（通常放在 _static/ 目录中）。
- 在 html_static_path 选项中添加该文件的路径或所在的目录。

主题选项
************************************

alabaster 的主要配置是 conf.py 文件中的 html_theme_options 变量，如果不存在可自定义添加该变量。例如：

::

    html_theme_options = {
        'logo': 'logo.png',
        'github_user': 'bitprophet',
        'github_repo': 'alabaster',
    }

以下小节详细介绍了可用的此类选项，包括有关行为的说明。

基础
====================================

与文本显示、徽标（logo）等相关的设置。所有参数请参见： `theme.conf <https://github.com/bitprophet/alabaster/blob/master/alabaster/theme.conf>`_

body_text_align
    body 的文本对齐设置。

canonical_url
    基础的网页链接，该值必须以 / 结尾。

description
    关于项目的文本描述，显示在徽标下面。

description_font_style
    用于描述文本的样式。

fixed_sidebar
    是否固定侧边栏的位置。

logo
    项目 logo，使用相对路径（$PROJECT/_static/）。

logo_name
    设置为 true，以文本形式在徽标下插入项目的名称。

logo_text_align
    设置徽标使用的文本对齐方式

page_width
    设置页面的宽度。

sidebar_width
    设置侧边栏的宽度。

服务链接或横幅
====================================

第三方服务（GitHub、Travis-CI 等）和相关徽章或横幅。

analytics_id
    作者的 Google Analytics ID 以启用跟踪。

badge_branch
    设置在 Travis、CodeCov 等徽章中使用哪个分支。

codecov_button
    true，false 或者是 Github 风格的 "account/repo" 字符串，用于在侧边栏中显示“构建状态”按钮。如果 true，则使用 github\_(user|repo) 设置。

donate_url
    通用/任意捐赠服务的 url；显示基本的“捐赠”徽章/盾牌。

github_banner
    true 或 false，是否在页面右上角应用“Fork me on GitHub”横幅。如果 true，需要同时设置 github_user 和 github_repo。

github_button
    true 或 false，是否链接到您的 Github。如果 true，需要同时设置 github_user 和 github_repo。

github_repo
    GitHub 仓库名

github_user
    GitHub 用户名

travis_button
    true，false 或者是 Github 风格的 "account/repo" 字符串，用于显示侧边栏中的“构建状态”按钮。如果 true，则使用 github\_(user|repo) 设置。

非服务侧边栏控件
====================================

与服务链接没有直接关系的侧栏相关选项。

extra_nav_links
    将链接名映射到链接目标的字典，链接将添加在主侧边栏导航下方的 UL 中。用于 Sphinx 文档树外的静态链接。

show_related
    布尔值控制侧边栏是否显示“下一个/上一个/相关”辅助导航。默认为 false，因为在许多网站上这些元素是多余的。

sidebar_includehidden
    布尔值决定 TOC 侧栏是否应该包含隐藏的 toctree 元素。默认为true。


页眉/页脚选项
====================================

哪些元素应出现在页眉和/或页脚中，或对其进行修改。

show_powered_by
    布尔值控制 Powered by Sphinx N.N.N. & Alabaster M.M.M 页脚的内容。为 true，显示在版权信息中。

show_relbars
    true 或 false，用于显示 next 和 previous 主页内容上方和下方的链接。如果只想显示一个，则可以通过 show_relbar_top 和 show_relbar_bottom 设置。

样式颜色
====================================

这些应该是完全合格的 CSS 颜色说明符，例如 #004B6B 或 #444。列表中的前几项是用作其他许多项的默认值的“全局”颜色；更新这些项以对配色方案进行彻底更改。可以根据需要使用更精细的设置来覆盖。

anchor
    段落链接符号 ¶ 的前景色（鼠标悬停在标题上时显示的符号）

anchor_hover_bg
    鼠标悬停在标题上时的背景色，背景颜色 anchor 文本。

anchor_hover_fg
    鼠标悬停在标题上时的前景色。

body_text
    主要内容文本。

code_highlight
    在代码块中使用 :emphasize-lines: 时的高亮颜色。

footer_text
    页脚文本（包括链接）。

footnote_bg
    页脚块的背景。

footnote_border
    页脚块的边框。

gray_1
    深灰色。

gray_2
    浅灰色。

gray_3
    中灰色。

link_hover
    主体链接，鼠标悬停。

link
    未悬停的链接。

narrow_sidebar_bg
    侧边栏强制放到页面底部时的背景颜色。

narrow_sidebar_fg
    侧边栏强制放到页面底部时的文本颜色。

narrow_sidebar_link
    侧边栏强制放到页面底部时的链接颜色。

note_bg
    note 的背景色。

note_border
    note 的边框色。

pink_1
    浅粉色。

pink_2
    中粉色。

pre_bg
    预格式化文本块（包括代码片段）的背景。

relbar_border
    包含下一个和上一个链接的栏与页面其余内容之间的边框颜色。

seealso_bg
    seealso 背景色。

seealso_border
    seealso 的边框色。

sidebar_header
    侧边栏的标题。

sidebar_hr
    侧边栏水平分隔符的颜色。

sidebar_link
    侧边栏链接（没有悬停变量）。适用于标题和文本链接。

sidebar_list
    侧边栏列表项目符号和未链接文本的前景色。

sidebar_link_underscore
    侧边栏链接的下划线。

sidebar_search_button
    搜索字段“提交”按钮的背景色。

sidebar_text
    侧边栏段落文本。


字体
====================================

设置字体的大小和样式。

caption_font_size
    文本的字体大小。

caption_font_family
    文本的字体样式。

code_font_size
    代码块文本的字体大小。

code_font_family
    代码块文本的字体样式。默认为 'Consolas', 'Menlo', 'DejaVu Sans Mono', 'Bitstream Vera Sans Mono', monospace

font_size
    正文文本的字体大小。

font_family
    正文文本的字体样式。

head_font_family
    标题的字体样式。默认为 'Garamond', 'Georgia', serif


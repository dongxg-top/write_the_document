reStructuredText 指令
####################################

指令块是以指令标记和内容组成的文字块。指令标记以 **..** 开头（后紧跟一个空格），再加上指令类型和两个冒号组成，例如： ``.. image::`` 。

指令块应用于指令标记之后（即同一行），并包括所有随后的缩进行。指令块中还可以包括选项和参数，用于调整默认值。有关语法细节，请参阅 `reStructuredText 标记规范 <https://docutils.sourceforge.io/docs/ref/doctree.html>`_ 中的指令一节。

指令块和段落之间要用空行分开。

图片
************************************

使用 image 在文件中插入图片。

::

    .. image:: ../img/picture.jpg
       :height: 100px
       :width: 200 px
       :alt: alternate text
       :align: right

还可以使用 figure 生成带说明的图片。

::

    .. figure:: ../img/picture.jpg
       :scale: 50 %
       :alt: alternate text

        ▲ 图片说明文本

image 和 figure 支持的选项：

- alt 图片的 alt 说明
- height 图片的高度，支持使用的单位：px、em、mm、cm
- width 图片的宽度，支持使用的单位：px、em、mm、cm
- scale 图片的比例（默认：100%）
- align 图片的对齐方式，支持 top、middle、bottom、left、center、right
- target 使图片成为一个超链接，也可以链接到锚点或脚注等

替换引用
************************************

替换引用是用定义的指令替换对应的文字或图片，替换文本不能以空格开头或结尾，定义指令格式参考 :ref:`行内标记 <inline_markup>` 。

::

    这是 Pythond Logo: |logo| ，我的最喜欢的语言是: |name| 。

    .. |logo| image:: https://www.python.org/static/img/python-logo.png
    .. |name| replace:: Python

.. hint::

    image 和 figure 暂不支持行内添加图片（小图标），但是可以使用“替换引用”来插入行内图片，需要注意图片的尺寸一定要小。

更强大的表格
************************************

指令扩展了表格的功能，方便在文档中添加更强大的表格。

带标题的表格
====================================

用 table 指令可以更详细的设置表格，如为表格添加标题、设置表格宽度、设置表格对齐。

::

    .. table:: 表格的标题
        :width: 300px
        :align: center

        =====  =====
        A      not A
        =====  =====
        False  True
        True   False
        =====  =====

逗号分隔的表格
====================================

用 csv-table 指令来创建使用 CSV（以逗号分隔）数据格式的表格。

::

    .. csv-table:: Frozen Delights!
        :header: "Treat", "Quantity", "Description"
        :widths: 15, 10, 30

        "Albatross", 2.99, "On a stick!"
        "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
        crunchy, now would it?"
        "Gannet Ripple", 1.99, "On a stick!"

带图片的表格
====================================

Sphinx 支持在表格中插入图片，通常不建议这么做，以免表格过于复杂。

::

    +--------------------------------+-----------------------+
    | Symbol                         | Meaning               |
    +================================+=======================+
    | .. image:: ../img/picture.jpg  | Campground            |
    |    :scale: 50 %                |                       |
    +--------------------------------+-----------------------+
    | .. image:: ../img/picture.jpg  | Lake                  |
    +--------------------------------+-----------------------+

标记主题
************************************

标记主题用于文档中的突出显示，并且带有标题文字。通常，显示为文档中的偏移块或使用不同的背景颜色。

标记指令包括：注意（attention）、小心（caution）、危险（danger）、错误（error）、提示（hint）、重要（important）、注释（note）、技巧（tip）、警告（warning）。

文档使用时建议只使用 note、hint、attention、danger 四种类型。

::

    .. hint::

        这是一段提示文本

当前文件目录
************************************

当前文件目录用于在当前文件中插入本文件的目录，并自动生成连接。

::

    .. contents:: Table of Contents
        :depth: 2

当前文件目录支持的选项：

- depth 指定目录深度，默认为无限深度
- local 隐藏当前文件的主标题

插入文件内容
************************************

建议在文档中使用 :doc:`sphinx_cross_referencing` ，而不是将其它文件插入到当前文件。插入文件内容多用于在文档中插入自定义的代码内容，例如，使用 `输出原始内容`_ 在文档中加入 JavaScript 脚本，如果脚本需要加入多个文件，每次都使用 raw 添加即麻烦又不便于维护脚本。可以将脚本写入单独的文件中，然后在每个文件中插入脚本文件。

::

    .. include:: ./path/gifffer.rst


插入文件内容支持的选项：

- start-line 指定插入文件的起始行数
- end-line 指定插入文件的结束行数，不包含结束行
- encoding 源文件的编码格式，如 ASCII、UTF-8
- number-lines 添加行号，可指定起始行号
- tab-width 选项指定制表符的宽度

.. attention::

    如果插入的文包含章节结构，那么标题修饰符必须与主文档的标题修饰符相匹配。

输出原始内容
************************************

raw 指令用于将原始内容直接传递到指定的输出格式（使用 make 命令构建的格式）。如果输出格式和指令定义格式不相同，会忽略 raw 指令的内容。

在 HTML 网页输出中添加视频：

::

    .. raw:: html

        <video src="../clamp.mp4" controls="controls">
        抱歉！您的浏览器不支持视频播放。
        </video>

.. attention::

    raw 指令是一种权宜之计，不应该被过度使用或滥用。raw 指令将文档与特定的输出格式绑定在一起，会使文档不易移植。

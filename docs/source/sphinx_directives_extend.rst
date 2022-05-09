Sphinx 扩展指令
####################################

Sphinx 扩展了标准的 reStructuredText（reST）语法，使其增加了很多功能，例如：目录、代码块语法高亮等。

目录
************************************

由于 reStructuredText 没有组织目录的功能，因此 Sphinx 使用自定义指令来组织文档的目录树（TOC 树）。

toctree 指令将在当前位置插入一个目录树，目录树使用相对文档名来组织。文档名使用 ``/`` 作为路径分隔符（不能以正斜杠开头），并且不包含文件扩展名。

目录树可以在文档中出现多次，并且可以在一个文件中使用多种目录格式。

.. hint::

    文档中的所有文件必须出现在某些 toctree 指令中，如果 Sphinx 找到未包含到目录中的文件，会发出警告，这意味着无法通过标准导航访问到此文件。

::

    .. toctree::
        :maxdepth: 2
        :numbered: 3
        :glob:
        :caption: 目录

        welcome
        All about strings <strings>
        usage/started
        recipe/*
        The colors <http://www.url.com>
        ...

    .. toctree::
        :hidden:

        doc_1
        doc_2


自定义目录标题
====================================

默认情况下，目录中的标题是读取文档标题后自动生成的。可以自定义目录中的标题，也可以在目录中加入外部超链接。

上面例子中，第二行为 strings 文档自定义标题 “All about strings”，而不是使用文档的标题。第四行为 The colors 标题自定义 url 链接。


选项和参数
====================================

目录指令支持的选项和参数：

- maxdepth 选项设置目录树的深度（默认值 1），即目录中嵌套标题的深度。
- numbered 选项设置文档标题的自动编号，默认会为所有标题添加编号。也可以指定深度。
- caption 选项设置目录的标题。
- titlesonly 选项设置在目录只显示文档的标题，适用于一个文档中有多个 H1 标题时。该选项没有参数。
- glob 选项设置在目录添加文件时，支持 ``*`` 匹配，将结果按字母顺序插入到目录中。该选项没有参数。
- reversed 反转目录中条目的顺序，通常配合 glob 选项使用。该选项没有参数。
- hidden 选项用于隐藏目录，

.. hint::

    目录在每种输出格式中都会发生变化，例如，输出网页（HTML）文件时，构建器将目录视为超链接的集合；输出单个文件（手册页）时，构建器将目录替换为文档的内容。

另类标题
************************************

小标题
====================================

rubric 指令创建一个段落小标题（粗体文本行），该标题不会添加到目录节点中。

::

    .. rubric:: 小标题文字

居中的小标题
====================================

centered 指令创建一个居中的小标题，该标题不会添加到目录节点中。

::

    .. centered:: LICENSE AGREEMENT

代码块语法高亮
************************************

reStructuredText 只能用于 Python 代码的高亮，Sphinx 扩展了该功能，使其支持更多的编程语言。Sphinx 的语法高亮由 `Pygments <https://pygments.org/>`_ 模块提供。

自定义语言代码高亮
====================================

在文件的任意位置使用 highlight 指令进行自定义语言代码高亮。在当前文件中，highlight 指令之后的代码块都将被定义，直到遇到下一个 highlight 指令。

highlight 指令支持 Pygments 支持的所有编程语言，常用的有：

- none（不使用代码高亮）
- default（类似于 Python）
- guess（让 Pygments 根据内容猜测语言，只适用于某些识别良好的语言）
- python
- ruby
- c

如果使用所选语言高亮显示失败，将会回退到 none 值（不使用代码高亮）。

::

    .. highlight:: python
        :linenothreshold: 5

linenothreshold 选项为代码块生成行号，上边的示例将为超过五行的所有代码块生成行号。

多语言代码高亮
====================================

code-block 指令将编程语言名称作为参数，可以对每个代码块进行设置，并且 code-block 指令的设置优先级高于 highlight 指令。

::

    .. code-block:: JavaScript
        :caption: Ajax 请求示例
        :lineno-start: 10
        :emphasize-lines: 3,5

        function displayFullName() {
        var request = new XMLHttpRequest();
        request.open("GET", "https://www.baidu.com");
        request.onreadystatechange = function() {
            if(this.readyState === 4 && this.status === 200) {
            document.getElementById("result").innerHTML = this.responseText;
            }
        };
        request.send();
        }

code-block 指令支持更多的选项对代码块进行设置：

- linenos 选项设置为代码块生成行号。
- lineno-start 选项为第一行设置行号数。使用用后，linenos 选项会自动激活
- emphasisize-lines 选项用于强调特定的行。
- caption 选项定义代码块的标题
- dedent 选项设置从代码块中删除缩进字符的个数

插入代码文件
====================================

literalinclude 指令用于将代码文件中的内容插入到文档的代码块，适用于插入长的代码块。

::

    .. literalinclude:: example.py
        :emphasize-lines: 12,15-18

literalinclude 指令支持 code-block 指令的所有选项，并且额外增加了几个选项：

- language 选项指定代码语言
- tab-width 选项指定制表符的宽度
- encoding 源文件的编码格式，如 ASCII、UTF-8
- lines 选项指定要插入文件的行，例如：``1,3,5-10,20-`` 包括第 1、3、5 到 10 行和第 20 行到最后一行
- start-after 选项指定要插入文件开始的行，可以单独使用也可以配合 end-before 选项使用
- end-before 选项指定要插入文件结束的行，可以单独使用
- diff 选项用于对比两个文件，类似于 diff 命令的输出

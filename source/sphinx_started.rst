Sphinx 快速使用
####################################

`Sphinx <https://www.sphinx-doc.org/en/master/index.html>`_ 是一个文档生成工具，用于将一组 reStructuredText 源文件组织成一个文档（如：HTML、PDF），并自动生成交叉引用、索引等。

reStructuredText 是一种轻量级纯文本标记语言，也被简称为：RST 或 reST，以 ``.rst`` 为扩展名的文件。

安装
************************************

Sphinx 是用 Python 编写的，可以使用 pip 快速安装：

::

    pip install -U sphinx

创建文档
************************************

为了简化创建文档的过程，Sphinx 提供了一个脚本工具，使用该工具创建文档时，会问几个文档配置的问题。运行脚本工具:

::

    sphinx-quickstart project_name

    # 是否分离源目录和构建目录
    > Separate source and build directories (y/n) [n]: y

    # 设置文档名称
    > Project name: 技术文档写作指南
    # 设置作者名
    > Author name(s): glenn
    # 支持多版本发布，直接回车跳过
    > Project release []:

    # 文档语言
    > Project language [en]: zh_CN

编辑文档
************************************

sphinx-quickstart 脚本工具会在文档 source 目录下创建 conf.py 配置文件和 index.rst 主文件。

.. hint::

    index.rst 文件相当于文档的“目录树”（或“目录根”）。


为文档新建内容文件，例如：Welcome.rst。

编辑 index.rst 主文件，在 ``.. toctree::`` 下添加文档目录，文档名使用 ``/`` 作为路径分隔符，并且不包含文件扩展名。

::

    .. toctree::
        :maxdepth: 2

        welcome
        usage/started
        ...

构建文档
************************************

sphinx-quickstart 脚本工具会在文档目录下创建了一个 Makefile 和一个 make.bat。通过运行 make 来构建文档。例如：

::

    # 构建 HTML 文档
    make html

    # 构建 PDF 文档
    make latexpdf

同时，可以使用 sphinx-build 命令更详细的自定义构建内容。请参见 `官网 <https://www.sphinx-doc.org/en/master/man/sphinx-build.html>`_

::

    # 自定义构建时输出的目录，最后一个参数
    sphinx-build -b html document/source ~/doc


优化文档
************************************

支持中文搜索
====================================

Sphinx 默认不支持中文搜索，需要安装中文分词扩展来支持中文搜索。

::

    pip install jieba

修改 conf.py 配置文件，在最后添加：

::

    html_search_language = 'zh'

.. hint::

    最好先安装 jieba 分词模块，然后在安装 sphinx。经测试有时会出现搜索不显示内页详情的情况。


修改主题
====================================

安装 html 主题。

::

    pip install sphinx_rtd_theme

修改 conf.py 配置文件中的相应项。

::

    html_theme = 'sphinx_rtd_theme'

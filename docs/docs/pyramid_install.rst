..
    Installing Pyramid
    =========================

Pyramid のインストール
======================

..
    This is a quick guide to getting Pyramid set up, it should be good enough
    for most use cases. If you run into some problem and need more detailed help
    or if you are using a different platform, please consult our
    `detailed installation guide
    <http://docs.pylonsproject.org/projects/pyramid/1.0/narr/install.html>`_.

このドキュメントは、Pyramid 環境を構築するクイックガイドです。ほとんどのユースケースにおいて十分な内容だと思います。もし実行して何か問題があり、もっと詳細なヘルプが必要になったり、または他の環境で利用しているなら、 `詳細なインストールガイド <http://docs.pylonsproject.org/projects/pyramid/1.0/narr/install.html>`_ を調べてみてください。

..
    Before You Install
    ------------------

インストールの前に
------------------

..
    You will need Python version 2.4 or better to
    run Pyramid. Pyramid doesn't run on Python 3 yet, but we're working
    on it. `Get Python now <http://www.python.org/download/>`_.

Pyramid を実行するには Python バージョン 2.4 以上が必要になります。Pyramid はまだ Python 3 では動作しませんが、我々はその対応にまさに取り組んでいます。 `最新の Python をダウンロードします <http://www.python.org/download/>`_ 。

..
    Pyramid is known to run on all popular Unix-like systems such as
    Linux, MacOS X, and FreeBSD as well as on Windows platforms.  It is also
    known to run on Google's App Engine and :term:`Jython`.

Pyramid は、Linux, MacOS X, FreeBSD といった一般的な Unix ライクなシステムと Windows プラットフォーム上で実行できます。さらに Google App Engine と :term:`Jython` でも動くことが確認されています。

..
    It is best practice to install Pyramid into a "virtual"
    Python environment in order to obtain isolation from any "system"
    packages you've got installed in your Python version.  This can be
    done by using the :term:`virtualenv` package.  Using a virtualenv will
    also prevent Pyramid from globally installing versions of
    packages that are not compatible with your system Python.

インストールされている Python バージョン毎に独立した "システム" の環境を構築するには、"仮想的な" Python 環境に Pyramid をインストールするのがベストプラクティスです。これは :term:`virtualenv` パッケージを利用して行います。virtualenv を利用することで、システムの Python とは互換性のないパッケージのバージョンがグローバルにインストールされるのを防げます。

..
    To install virtualenv you will need setuptools.  Once you've got
    setuptools installed, you should install the :term:`virtualenv` package
    using the ``easy_install`` command.

virtualenv をインストールするには setuptools が必要です。setuptools をインストールしたら、 ``easy_install`` コマンドから :term:`virtualenv` をインストールしましょう。

.. code-block:: text

   $ easy_install virtualenv


..
    Installing Pyramid Into the Virtual Python Environment
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

仮想 Python 環境に Pyramid をインストールする
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..
    After you've got your ``env`` virtualenv installed, you may install
    Pyramid itself using the following commands from within the
    virtualenv (``env``) directory:

``env`` という virtualenv 環境を作成したら、virtualenv (``env``) ディレクトリ内から次のコマンドを実行して Pyramid をインストールすると良いです。

.. code-block:: text

   $ bin/easy_install pyramid

..
    This command will take longer than the previous ones to complete, as it
    downloads and installs a number of dependencies.

このコマンドを実行すると、 virtualenv をインストールするよりは少し時間がかかります。Pyramid をダウンロードして、たくさんの依存パッケージがインストールされるからです。

..
    What Gets Installed
    -------------------

どんなパッケージがインストールされたか
--------------------------------------

..
    When you ``easy_install`` Pyramid, various Zope libraries,
    various Chameleon libraries, WebOb, Paste, PasteScript, and
    PasteDeploy libraries are installed.

``easy_install`` Pyramid を実行すると、種々多様な Zope ライブラリ、Chameleon ライブラリ、WebOb、Paste、PasteScript、PasteDeploy ライブラリがインストールされます。

..
    Additionally, as chronicled in :ref:`project_narr`, PasteScript (aka
    *paster*) templates will be registered that make it easy to start a
    new Pyramid project.

さらに :ref:`project_narr` 物語のように、簡単に新たな Pyramid プロジェクトを始められるように、PasteScript (別名 *paster*) テンプレートが登録されます。

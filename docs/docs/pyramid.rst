Pyramid ドキュメント
====================

..
    Pyramid Documentation
    =====================

..
    Getting Started
    ---------------

はじめに
--------

..
    If you are new to Pyramid, we have a few resources that can help you get up to
    speed right away:

Pyramid を初めて使う方にも、すぐに理解して開発できるようになる情報があります。

..
    * Check out  our `FAQ <http://docs.pylonsproject.org/faq/pyramid.html>`_.

* `FAQ <http://docs.pylonsproject.org/faq/pyramid.html>`_ を確認してください。

..
    * For help getting Pyramid set up, try the `install guide
      <pyramid_install.html>`_.

* Pyramid 環境を構築するには `インストールガイド <pyramid_install.html>`_ を試してください。

..
    * Coming from Pylons?  Start with :ref:`Akhet <akhet-desc>`.

* Pylons からやってきた？ :ref:`Akhet <akhet-desc>` から始めてください。

..
    * To get the feel of how a Pyramid web application is created, go to the 
      `quick tutorial <pyramid_quick_tutorial.html>`_ page. 

* Pyramid の Web アプリケーション開発を実際にやってみるには `クイックチュートリアル <pyramid_quick_tutorial.html>`_ へ行ってください。

..
    * Like learning by example? Check out to the `wiki tutorial
      <http://docs.pylonsproject.org/projects/pyramid/1.0/tutorials/wiki2/index.html>`_.

* サンプルで学ぶのがお好み？ `wiki チュートリアル <http://docs.pylonsproject.org/projects/pyramid/1.0/tutorials/wiki2/index.html>`_ を調べてください。

..
    * Need help?  See :ref:`support-desc`.

* 助けが必要？ :ref:`support-desc` を参照してください。

..
    Main Documentation
    ------------------

メインドキュメント
------------------

..
    * `Pyramid documentation 1.0 </projects/pyramid/1.0/>`_ (`PDF
      <http://static.pylonsproject.org/pyramid-1.0.pdf>`_) (`Epub
      <http://static.pylonsproject.org/pyramid-1.0.epub>`_) is narrative and API
      documentation for Pyramid's currently released version.  If you are using
      an unrealeased version of Pyramid you might need to consult the `Pyramid
      development documentation </projects/pyramid/dev/>`_.

* `Pyramid ドキュメント 1.0 </projects/pyramid/1.0/>`_ (`PDF <http://static.pylonsproject.org/pyramid-1.0.pdf>`_) (`Epub <http://static.pylonsproject.org/pyramid-1.0.epub>`_) は、物語風に構成されていて、それは Pyramid の現在のリリースバージョン向けの API ドキュメントです。もし Pyramid のリリースされていないバージョンを使っているなら `Pyramid 開発版ドキュメント </projects/pyramid/dev/>`_ を調べる必要があるかもしれません。

..
    * `The Pyramid Cookbook
      <http://docs.pylonsproject.org/projects/pyramid_cookbook/dev/>`_ presents
      topical, practical usages of Pyramid.  The cookbook is unfinished.

* `Pyramid クックブック <http://docs.pylonsproject.org/projects/pyramid_cookbook/dev/>`_ は、Pyramid の使用方法の中でも、関心が高く、実用的な応用例を紹介します。クックブックは未完成です。

..
    Pyramid Add-On Documentation
    ----------------------------

Pyramid アドオンドキュメント
----------------------------

..
    Pyramid supports extensibility through add-ons.  The following add-ons are
    officially endorsed by the Pylons Project, and their documentation is hosted
    here.

Pyramid は、アドオンによる拡張機能をサポートします。次のアドオンは公式に Pylons プロジェクトが承認したもので、そういったアドオンのドキュメントもここにホスティングされています。

..
    * `pyramid_beaker </projects/pyramid_beaker/dev/>`_: Beaker session backend
      plug-in.

* `pyramid_beaker </projects/pyramid_beaker/dev/>`_: Beaker セッションのバックエンドプラグイン

  .. - Maintained by: Ben Bangert, Chris McDonough

  - メンテナンス: Ben Bangert, Chris McDonough

  .. - Version Control: https://github.com/Pylons/pyramid_beaker

  - バージョン管理: https://github.com/Pylons/pyramid_beaker

..
    * `pyramid_chameleon_genshi </projects/pyramid_chameleon_genshi/dev/>`_:
      template renderer for `Chameleon's Genshi implementation
      <http://chameleon.repoze.org/docs/latest/genshi.html>`_.

* `pyramid_chameleon_genshi </projects/pyramid_chameleon_genshi/dev/>`_: `Chameleon の Genshi 実装 <http://chameleon.repoze.org/docs/latest/genshi.html>`_ のテンプレートレンダラー

  .. - Maintained by: Chris McDonough

  - メンテナンス: Chris McDonough

  .. - Version Control: https://github.com/Pylons/pyramid_chameleon_genshi

  - バージョン管理: https://github.com/Pylons/pyramid_chameleon_genshi

..
    * `pyramid_handlers </projects/pyramid_handlers/dev/>`_: analogue of
      Pylons-style "controllers" for Pyramid.

* `pyramid_handlers </projects/pyramid_handlers/dev/>`_: Pyramid の Pylons スタイルな "コントローラー" のようなもの

  .. - Maintained by: Ben Bangert, Chris McDonough

  - メンテナンス: Ben Bangert, Chris McDonough

  .. - Version Control: https://github.com/Pylons/pyramid_handlers

  - バージョン管理: https://github.com/Pylons/pyramid_handlers

..
    * `pyramid_jinja2 </projects/pyramid_jinja2/dev/>`_: `Jinja2
      <http://jinja.pocoo.org/>`_ template renderer for Pyramid

* `pyramid_jinja2 </projects/pyramid_jinja2/dev/>`_: Pyramid の `Jinja2 <http://jinja.pocoo.org/>`_ テンプレートレンダラー

  .. - Maintained by: Rocky Burt

  - メンテナンス: Rocky Burt

  .. - Version Control: https://github.com/Pylons/pyramid_jinja2

  - バージョン管理: https://github.com/Pylons/pyramid_jinja2

..
    * `pyramid_mailer </projects/pyramid_mailer/dev/>`_: a package for the
      Pyramid framework to take the pain out of sending emails.

* `pyramid_mailer </projects/pyramid_mailer/dev/>`_: メール送信の煩わしさから逃れるための Pyramid フレームワークのパッケージ

  .. - Maintained by:  Dan Jacobs

  - メンテナンス: Dan Jacobs

  .. - Version Control: https://bitbucket.org/danjac/pyramid_mailer

  - バージョン管理: https://bitbucket.org/danjac/pyramid_mailer

..
    * `pyramid_rpc </projects/pyramid_rpc/dev/>`_: RPC service add-on for
      Pyramid, supports XML-RPC in a more extensible manner than `pyramid_xmlrpc`
      with support for JSON-RPC and AMF.

* `pyramid_rpc </projects/pyramid_rpc/dev/>`_: JSON-RPC と AMF をサポートする `pyramid_xmlrpc` よりも拡張性の高い XML-RPC をサポートする Pyramid の RPC サービスのアドオン

  .. - Maintained by: Ben Bangert

  - メンテナンス: Ben Bangert

  .. - Version Control: https://github.com/Pylons/pyramid_rpc

  - バージョン管理: https://github.com/Pylons/pyramid_rpc

..
    * `pyramid_tm </projects/pyramid_tm/dev/>`_: Centralized transaction 
      management for Pyramid applications (without middleware).

* `pyramid_tm </projects/pyramid_tm/dev/>`_: (ミドルウェアなしで) Pyramid アプリケーションのトランザクション管理を一元化

  .. - Maintained by: Rocky Burt

  - メンテナンス: Rocky Burt

  .. - Version Control: https://github.com/Pylons/pyramid_tm

  - バージョン管理: https://github.com/Pylons/pyramid_tm

..
    * `pyramid_who </projects/pyramid_who/dev/>`_: Authentication policy for 
      pyramid using repoze.who 2.0 API.

* `pyramid_who </projects/pyramid_who/dev/>`_ : repoze.who 2.0 API を利用する Pyramid の認証ポリシー

  .. - Maintained by: Chris McDonough, Tres Seaver

  - メンテナンス: Chris McDonough, Tres Seaver

  .. - Version Control: https://github.com/Pylons/pyramid_who

  - バージョン管理: https://github.com/Pylons/pyramid_who

..
    * `pyramid_xmlrpc </projects/pyramid_xmlrpc/dev/>`_: XML-RPC add-on for
      Pyramid

* `pyramid_xmlrpc </projects/pyramid_xmlrpc/dev/>`_ : Pyramid の XML-RPC のアドオン

  .. - Maintained by: Chris McDonough

  - メンテナンス: Chris McDonough

  .. - Version Control: https://github.com/Pylons/pyramid_xmlrpc

  - バージョン管理: https://github.com/Pylons/pyramid_xmlrpc

..
    * `pyramid_zcml </projects/pyramid_zcml/dev/>`_: Zope Configuration Markup
      Language configuration support for Pyramid.

* `pyramid_zcml </projects/pyramid_zcml/dev/>`_: Pyramid の ZCML (Zope Configuration Markup Language) サポート

  .. - Maintained by: Chris McDonough

  - メンテナンス: Chris McDonough

  .. - Version Control: https://github.com/Pylons/pyramid_zcml

  - バージョン管理: https://github.com/Pylons/pyramid_zcml

..
    Pyramid Development Environment Documentation
    ---------------------------------------------

Pyramid の開発環境マニュアル
----------------------------

..
    Development environments are packages which use Pyramid as a core, but offer
    alternate services and scaffolding.  Each development environment presents a
    set of opinions and a "personality" to its users.  Although users of a
    development environment can still use all of the services offered by the
    Pyramid core, they are usually guided to a more focused set of opinions
    offered by the development environment itself.  Development environments
    often have dependencies beyond those of the Pyramid core.

開発環境は、コアに Pyramid を使っているパッケージですが、複数のサービスとスキャフォールドを提供しています。それぞれの開発環境は、そのユーザーの "個性" と意見を集約したものを提供します。開発環境のユーザーは、Pyramid のコアが提供するサービス全てを利用できますが、そういったサービスは通常、開発環境自体が提供する、ユーザーたちの意見を集約したものへ導かれます。開発環境は、多くの場合、Pyramid のコア以上の依存関係があります。

.. _akhet-desc:

..
    * `Akhet </projects/akhet/dev/>`_: Akhet is an application scaffolding for
      Pyramid that's closer to the Pylons 1 style than Pyramid's built-in
      scaffolding. The manual also tries to be a gentler introduction to Pyramid
      for those from a Pylons-ish background.

* `Akhet </projects/akhet/dev/>`_: Akhet は、Pyramid の組み込みスキャフォールドよりも Pylons 1 スタイルに近い Pyramid のアプリケーションスキャフォールドです。マニュアルもまた、Pylons 風の背景から、Pylons スタイルの開発者のために Pyramid への穏やかな導入になるようにしています。

  .. - Maintained by: Mike Orr

  - メンテナンス: Mike Orr

  .. - Version Control: https://bitbucket.org/sluggo/akhet

  - バージョン管理: https://bitbucket.org/sluggo/akhet

..
    * `Khufu Project <http://khufuproject.github.com/>`_: Khufu is an application
      scaffolding for Pyramid that provides an environment to work with Jinja2 and
      SQLAlchemy.

* `Khufu Project <http://khufuproject.github.com/>`_: Khufu は Pyramid のアプリケーションスキャフォールドです。それは Jinja2 と SQLAlchemy を連携する環境を提供します。

  .. - Maintained by: Rocky Burt

  - メンテナンス: Rocky Burt

  .. - Version Control: https://github.com/khufuproject

  - バージョン管理: https://github.com/khufuproject


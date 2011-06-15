Pylons プロジェクトドキュメント
===============================

..
    The Pylons Project Documentation
    ================================

..
    The Pylons Project maintains the Pyramid web framework as well as additional
    packages intended for use with Pyramid. This is the home for the
    documentation for all of these projects.

Pylons プロジェクトでは、Pyramid という Web フレームワークとそれと連携することを目的とした追加のパッケージも一緒にメンテナンスしています。ここはそういったプロジェクト全てのドキュメントホームとなるページです。

..
    Documentation Index
    -------------------

ドキュメント の目次
-------------------

..
    Documentation sources for subprojects within the Pylons Project are listed
    below.

Pylons プロジェクトのサブプロジェクトのドキュメントは次になります。

.. toctree::
   :maxdepth: 1

   docs/pyramid
   docs/pylons
   docs/libraries

.. _support-desc:

..
    Support
    -------

サポート
--------

..
    Development questions related to Pylons projects can be discussed on the 
    `pylons-discuss mail list <http://groups.google.com/group/pylons-discuss/>`_.

Pylons プロジェクトに関連する開発の質問は `pylons-discuss メーリングリスト <http://groups.google.com/group/pylons-discuss/>`_ で議論できます。

..
    On IRC, Pylons developers are generally available on the ``#pylons`` channel
    on the `Freenode IRC Network <http://freenode.net/>`_.

IRC だと、普通 Pylons 開発者は `Freenode IRC Network <http://freenode.net/>`_ の ``#pylons`` チャンネルにいます。

..
    .. topic:: Using Support Wisely

.. topic:: 賢くサポートを利用する

   .. Before asking a technical question on the maillist(s) or in IRC, please
      make sure to try the following things (paraphrased from `Before You Ask
      <http://www.catb.org/~esr/faqs/smart-questions.html#before>`_):

   メーリングリストや IRC で技術的な質問をする前に、次のようなこと (`質問する前に <http://www.catb.org/~esr/faqs/smart-questions.html#before>`_ を言い換えたもの) を確認するようにしてください。

   .. - Try to find an answer by reading the manual.

   - マニュアルに答えが書いてないか探してみてください。

   .. - Try to find an answer by searching the maillist archives.

   - メーリングリストのアーカイブに答えがないか検索してみてください。

   .. - Try to find an answer by searching the Web.

   - Web を検索して答えが見つからないか調べてみてください。

   .. - Try to find an answer by inspection or experimentation.

   - インスペクションを行ったり、実験したりして答えを探してみてください。

   .. - If you're a programmer, try to find an answer by reading the source
        code.

   - プログラマだったら、ソースコードを読んで答えを見つけようとしてください。

   .. After exhausing these avenues, it's completely appropriate to ask a
      question on the Pylons-devel maillist or #pylons IRC channel.  When you
      ask your question, please describe what you've learned from the efforts
      above, as it will help the developers focus on answering your question
      quickly.  It also helps tremendously if you are able to provide a code or
      configuration snippet that makes the problem easily repeatable.

   ここで紹介した方法を試したなら、Pylons-devel メーリングリストや IRC の #pylons チャンネルで質問しても良い類いの質問だということです。質問するときは、回答する開発者たちが、すぐに質問の要点を把握して回答しやすいように、上述した方法から実際にやってみて分かったことを説明してください。さらに、もし簡単にその質問の内容を再現できるコードや設定のスニペットを提供できるなら、それは大いに役立ちます。

FAQ
---

..
    For Pylons users coming from Pylons 1 or repoze.bfg the change to a new core
    package might raise some questions regarding how to proceed, what it means
    for existing applications.

repoze.bfg や Pylons 1 を使っていた Pylons ユーザーには、新たなコアパッケージの変更は、既存のアプリケーションをどうやって継続利用するか、その変更はどういう意味があるかといった質問を抱くかもしれません。

.. toctree::
   :maxdepth: 1

   faq/pylonsproject
   faq/pyramid

..
    Podcasts
    --------

ポッドキャスト
--------------

..
    Subscribe to the Pylons Podcasts.  Pylons Podcasts are a series of audio
    podcasts from developers of the Pylons Project.  You can either subscribe in
    iTunes or Rhythmbox (or your favorite audio client) using the Feed URL below,
    or listen to individual podcasts.

Pylons ポッドキャストを購読してください。Pylons ポッドキャストは、Pylons プロジェクトの開発者が語るオーディオポッドキャストのシリーズです。次のフィード URL から iTunes や Rhythmbox (または好みのオーディオクライアント) で購読するか、もしくは個々にポッドキャストを聞くか、どちらでも構いません。

..
    `Feed URL (RSS/iTunes) <http://static.repoze.org/casts/pylons.xml>`_

`フィード URL (RSS/iTunes) <http://static.repoze.org/casts/pylons.xml>`_

.. toctree::
   :maxdepth: 1

   podcasts

..
    Promote
    -------

推進
----

..
    If you want to promote The Pylons Project and it's related technologies or your
    own work made with our tools.

もし Pylons プロジェクトを推進しようという気があるなら、その関連技術か、取り組んでいる作業を我々のツールで開発しているよね。

.. toctree::
    :maxdepth: 1

    promote/logos
    promote/badges
    promote/desktops

..
    Contributing
    ------------

貢献
----

..
    The Pylons Project welcomes contributors.  Please read the following
    documentation about how the Pylons Project functions, coding styles expected
    for contributions, and the community standards we expect everyone to abide
    by.

Pylons プロジェクトは、手伝ってくれる人を歓迎します。次のドキュメントを読んで、Pylons プロジェクトの仕組み、期待されるコーディングスタイル、コミュニティ規約に貢献者みんなが従ってくれると思っています。

.. toctree::
   :maxdepth: 1

   community/conduct
   community/contributing
   community/codestyle
   community/testing
   community/featuresbugs

..
    Denials
    -------

拒絶
----

..
    Don't worry, none of these are actually true. We swear!

心配しないで。この内容はどれも実際には該当しないと我々は誓うよ！

.. toctree::
    :maxdepth: 1
    
    denials/pyramid


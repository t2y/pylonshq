..
    Pylons Project FAQ
    ==================

Pylons プロジェクト FAQ
=======================

..
    How does "The Pylons Project" relate to Pylons-the-web-framework?
    -----------------------------------------------------------------

"Pylons プロジェクト" は Pylons ウェブフレームワークとどういう関係なのか？
------------------------------------------------------------------------

..
    The Pylons Project was founded by the people behind the Pylons web framework
    to develop web application framework technology in Python. Rather than
    focusing on a single web framework, the Pylons Project will develop a
    collection of related technologies.

Pylons プロジェクトは、Python でウェブアプリケーションフレームワークの技術を開発するために Pylons ウェブフレームワークの背後にいる人たちによって設立されました。単一のウェブフレームワークに重点を置いているというよりは、Pylons プロジェクトは関連する一連の技術を開発しています。

..
    The first package from the Pylons Project will be the Pyramid web framework.
    Other packages will be added to the collection over time, including
    higher-level components, applications and other frameworks which rely
    on a particular persistence mechanism (Pyramid does not). Ben Bangert, the
    Pylons web framework project lead, is already aiming to develop layers above
    the core web framework.

Pylons プロジェクトで使う最初のパッケージは、Pyramid というウェブフレームワークになるでしょう。より高いレベルのコンポーネント、アプリケーション、特に (Pyramid にはない) データの永続化の仕組みをサポートするフレームワークを含め、時間とともにその他のパッケージ群として追加される予定です。Ben Bangert は、Pylons ウェブフレームワークのプロジェクトリーダーであり、既にコアのウェブフレームワークの上位レイヤーの開発を目標に定めています。

..
    "The Pylons Project" was chosen to reflect the shared core ethos with the
    Pylons web framework: an overall effort combining the best parts from
    different projects.

"Pylons プロジェクト" は、Pylons ウェブフレームワークで共有された理念を反映することが望まれています。様々なプロジェクトから最高の部品を組み合わせるのに全ての努力を惜しみません。

..
    Why not just continue developing the Pylons 1.0 code-base?
    ----------------------------------------------------------

Pylons 1.0 のコードベースの開発を継続しないのはどうしてなのか？
---------------------------------------------------------------

..
    Unfortunately, the Pylons 1.0 code-base has hit a point of diminishing returns
    in flexibility and extendability. Due to the use of `sub-classing
    <http://be.groovie.org/post/1347858988/why-extending-through-subclassing-a-frameworks>`_
    , extensive, sometimes confusing, use of Stacked Object Proxy globals, and
    issues with configuration organization, attempts to re-factor or re-design the
    existing ``pylons`` core weren't working out.

残念ながら、Pylons 1.0 のコードベースの柔軟性と拡張性は、収穫逓減の域に達しています。 `サブクラス化 <http://be.groovie.org/post/1347858988/why-extending-through-subclassing-a-frameworks>`_ の副作用により、広範囲で時には混乱をもたらし、StackedObjectProxy のグローバルな利用、設定の構成による課題など、既存の ``pylons`` コアのリファクタリングや再設計しようとする試みはうまく行きませんでした。

..
    Over the course of several months, serious attempts were made to re-write
    sections of the ``pylons`` core. After realizing that Pylons users would have
    to put in extensive effort to port their existing applications, and that
    Pylons 2 was looking more and more like ``repoze.bfg``, continued development
    seemed a waste of development effort.

数ヶ月にわたり、 ``pylons`` コアのセクションを書き直そうという真剣な試みが行われました。そして、Pylons ユーザーが既存のアプリケーションを移行するには多大な労力が必要になると気付いてから、Pylons 2 は、徐々に ``repoze.bfg`` によく似てきて、開発を継続するのが労力の無駄に思われました。

..
    Ben Bangert started collaborating with Chris McDonough to bring the
    ``repoze.bfg`` routes functionality up to par with the stand-alone
    `Routes <http://routes.groovie.org>`_ project. Further development showed that
    the two projects had much in common, and the developers shifted from building
    Pylons 2 on top of BFG and towards a full merger.

Ben Bangert は、実用的なレベルに達していた `Routes <http://routes.groovie.org>`_ という独立したプロジェクトを ``repoze.bfg`` に持ち込もうと Chris McDonough と共同で取り組み始めました。さらに、2つのプロジェクトが多くの共通点をもっていることが示され、開発者たちは BFG の上に Pylons 2 を作るよりも完全な合併へ向けて移行しました。

..
    What does the Pylons Project mean for Pylons-the-web-framework?
    ---------------------------------------------------------------

Pylons プロジェクトは Pylons ウェブフレームワークにとって何なのか？
-------------------------------------------------------------------

..
    The Pylons web framework 1.x line will continue to be maintained, though not
    enhanced. We will provide a package that allows Pylons 1.x applications and
    Pyramid applications to run in the same interpreter. The future of
    Pylon-style web application development is Pyramid.  See also
    :ref:`should_i_port`.

Pylons ウェブフレームワーク 1.x 系はメンテナンスを継続しますが、機能拡張はしません。私たちは、Pylons 1.x アプリケーションと Pyramid アプリケーションが同じインタープリターで実行できるパッケージを提供します。Pylons スタイルのウェブアプリケーション開発の未来は Pyramid です。 :ref:`should_i_port` もご覧ください。

..
    What does the Pylons Project mean for repoze.bfg?
    -------------------------------------------------

Pylons プロジェクトは repoze.bfg にとって何なのか？
---------------------------------------------------

..
    The Pyramid codebase is derived almost entirely from ``repoze.bfg``. Some
    changes have been made for the sake of Pylons compatibility, but those
    used to development with ``repoze.bfg`` will find Pyramid very familiar. By
    merging ``repoze.bfg`` with the philosophically-similar Pylons framework,
    both gain a dramatically expanded audience.

Pyramid のコードベースは、ほぼ完全に ``repoze.bfg`` から来ています。Pylons の互換性のために少しの変更が行われていますが、 ``repoze.bfg`` での開発に慣れたユーザーは、Pyramid にとても親近感を抱くでしょう哲学的によく似た Pylons フレームワークと ``repoze.bfg`` の合併によって、双方のプロジェクトは劇的にユーザー数を拡大させました。

..
    What does this mean for the Repoze project?
    -------------------------------------------

これは Repoze プロジェクトにとってどうなのか？
----------------------------------------------

..
    The Repoze project will continue to exist. Repoze will be able to regain its
    original focus: bringing Zope technologies to WSGI. The popularity of BFG as
    its own web framework hindered this goal.

Repoze プロジェクトは、そのまま存在し続けます。Repoze は、Zope の技術を WSGI へ持ち込むという当初の原点を取り戻せます。独自のウェブフレームワークとして BFG の人気がこの目標を妨げていました。

..
    Why should I care about The Pylons Project?
    -------------------------------------------

Pylons プロジェクトについて注意すべきことはあるのか？
-----------------------------------------------------

..
    This really is a good question. We hope that people are attracted at
    first by the spirit of the thing. It takes humility to sacrifice a
    little sovereignty and work together. The opposite, forking or splintering
    of projects, is much more common in the open source world.  We feel there is a
    limited amount of oxygen in the space of "top-tier Python web frameworks" and
    we don't do the Python community a service by over-crowding.

これは本当に良い質問です。私たちは、ユーザーたちがまず私たちの理念に惹き付けられることを願っています。それは支配権を少し犠牲にして謙虚さを取り、一緒に活動しようという狙いがあります。逆にプロジェクトの分岐や分裂は、オープンソースの世界ではよくあることです。私たちは、"一流の Python ウェブフレームワーク" の空間にある酸素には限りがあると感じていて、過剰な混雑は Python コミュニティへ貢献しません。

..
    We are a group of project leaders with experience going back to the start of
    Python web frameworks.  We aim to bring fresh ideas to classic problems.  We
    hope to combine a lot of hard-earned maturity into the development of a secure
    choice that developers and companies can bet on. Couple this with the humility
    and irreverence gained by surviving every stupid decision that could be
    imagined, and you've got a good basis for a team of developers.

私たちは、Python ウェブフレームワークの原点に戻ろうとしている経験豊富なプロジェクトリーダーのグループです。古典的な問題に対して新鮮なアイデアを持ち込もうとしています。私たちは、散々苦労して得たものを開発者や企業が利用するに値する安心できる選択肢の1つとして、この開発に組み合わせたいと考えています。想像される全ての愚かな決断を切り抜けることで得られた不遜さと謙虚さもこの開発に結び付け、まさに開発チームにとって優れた基本的な機能を手に入れました。

..
    Why is the Pylons Project different than other projects?
    --------------------------------------------------------

Pylons プロジェクトは、他のプロジェクトとどう違うのか？
-------------------------------------------------------

..
    Our mantra is: "Small, Documented, Tested, Extensible, Fast, Stable,
    Friendly". Everything we do, from Pyramid to the batteries we want to develop
    for later "batteries-included" projects, should retain these qualities.

私たちの信念は、"小さい、ドキュメントがある、テストされている、拡張性がある、高速、安定、友好的" です。後になって "付属の部品を含んだ" プロジェクトになるように、Pyramid から付属の部品まで含めた全ての開発において、この品質を維持する必要があります。

..
    What do you mean by "Friendly"?
    -------------------------------

"友好的" とは、どういう意味なのか？
-----------------------------------

..
    All of us have been around the block a few times. We've seen good
    communities and bad communities, effective communities and
    dysfunctional communities, arrogant ones and irreverant ones. We
    pride ourselves on constructive listening, telling the truth even when
    it makes us look bad, admitting when we're wrong, and attracting lots of
    people who actually like to help.

私たちみんなが、何度か経験してきて分かっていますね。私たちは、良いコミュニティや悪いコミュニティと出会い、生産性の高いコミュニティや機能不全に陥ったコミュニティを知り、横柄なコミュニティや無礼なコミュニティなど、多くのコミュニティを見てきました。私たちは、前向きに意見を聞き、時には自分たちが間違っていたと非を認めて真実を語り、実際に貢献したい多くの人を惹き付けることに誇りをもっています。

..
    What does the Pylons Project mean for Zope and Plone?
    -----------------------------------------------------

Pylons プロジェクトは、Zope と Plone にとって何なのか？
-------------------------------------------------------

..
    The repoze.bfg people came from the world of Zope and Plone. Paul, for
    example, was a co-founder of Zope and was at the first Python conference at
    NIST. Zope was a tremendous success in the first cycle, with some truly
    fresh ideas and a large commercial ecosystem. Plone continued that in a
    second cycle, with an even larger ecosystem and an obvious, out-of-the-box
    value proposition.

repoze.bfg の人たちは Zope と Plone の世界から来ました。例えば、Paul は、Zope の共同創立者であり、NIST で開催された最初の Python カンファレンスにいました。Zope は、本当に斬新なアイデアと大規模な商用エコシステムを形成し、最初のサイクルで驚異的な成功を収めました。Plone は、さらに大きなエコシステムと透明性をもち、全ての機能が含まれる価値の提案という第2のサイクルを継続しました。

..
    Since then, the cycle has moved on and focus has shifted to other projects. We
    love our Zope roots, the experience we gained helping establish the Zope
    Foundation and the Plone Foundation, and consulting experience we have on
    very large projects. But we want to take these experiences and start fresh
    together with Pylons, one of the clear winners of the last cycle, to work on
    something for the next cycle.

それ以来、このサイクルは先へ進み、その他のプロジェクトへ焦点が移ってきました。私たちは、Zope を根源として、Zope 財団 と Plone 財団の設立を支援したことから得られた経験と、かなり大規模なプロジェクトに携わっているというコンサルティングの経験をすごく気に入っています。それでも、私たちはこういった経験をまたやりたくて、Pylons プロジェクトを新鮮なメンバーと協力して始めます。それは、次のサイクルのための何かに繋がっていくように、最後のサイクルの明確な勝者の1人となるように。

..
    If you're doing Zope and Plone and have a project that fits their bulls-eye,
    use them. If you have something that could use those ideas for an alternate
    need, keep an eye on what we're doing.

Zope と Plone を使って大成功を収めているプロジェクトなら、そのまま使い続けてください。もし別の要求が出てきて次のサイクルへのアイデアになりそうなら、私たちがやっていることに注目してください。

..
    How do I participate?
    ---------------------

どうやって参加すれば良いのか？
------------------------------

..
    Join the Pylons-discuss and/or Pylons-dev maillists on google groups,
    or join the #pylons IRC channel on freenode.net.

Pylons-discuss や Google グループの Pylons-dev メーリングリストに参加してください。もしくは freenode.net の #pylons IRC チャンネルに入ってください。

..
    Where is the code?
    ------------------

コードはどこにあるのか？
------------------------

https://github.com/Pylons


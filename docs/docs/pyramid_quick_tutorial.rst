..
    Pyramid Quick Tutorial
    ======================

Pyramid クイックチュートリアル
==============================

..
    This tutorial is intended to provide you with a feel of how a Pyramid web
    application is created. The tutorial is very short, and focuses on the
    creation of a minimal application using common idioms.  For brevity, the
    tutorial uses a "single-file" application development approach instead of the
    more complex (but more common) "scaffolds" described in the main Pyramid
    documentation.

このチュートリアルは、Pyramid の Web アプリケーション開発を実際にやってみて体験することを目的としています。チュートリアルは、とても短く、一般的なイディオムを使って最小限のアプリケーションを開発することに重点を置いています。簡潔にするために、チュートリアルでは、メインの Pyramid ドキュメントで説明されている、より複雑な (とはいえ、そっちの方が一般的) "スキャフォールド" ではなく、"1 ファイル" のアプリケーション開発を行います。

..
    At the end of the tutorial, you'll have a minimal application which:

チュートリアルをやり遂げると、次のような最小限のアプリケーションが作成されます。

..
    - provides views to list, insert and close tasks

- タスクの表示、追加、完了のビューを提供する

..
    - uses route patterns to match your URLs to view code functions

- ビュー関数に対して URL をマッチさせるためにルートパターンを使う

..
    - uses Mako Templates to render your views

- ビューをレンダリングするのに Mako テンプレートを使う

..
    - stores data in an SQLite database

- SQLite データベースにデータを格納する

..
    Here's a screenshot of the final application:

これが最終的なアプリケーションのスクリーンショットです。

.. image:: pyramid_quick_tutorial.png

..
    Step 1 - Organizing The Project
    -------------------------------

手順 1 - プロジェクトを構成する
-------------------------------

.. note::

   .. For help getting Pyramid set up, try the `install guide
       <pyramid_install.html>`_.

   Pyramid 環境を構築するには `インストールガイド <pyramid_install.html>`_ をやってみてください。

..
    Before getting started, we will create the directory hierarchy needed for
    our application layout. Create the following directory layout on your
    filesystem:

始める前に、アプリケーションを配置するのに必要なディレクトリ階層を作成します。ファイルシステム上に次のディレクトリ構成で作成してください。

.. code-block:: text

    /tasks
        /static
        /templates

..
    Note that the ``tasks`` directory will not be used as a python package,
    it'll just serve as a container in which we can put our project.

``tasks`` ディレクトリは Python パッケージとしては使いません。このディレクトリは、単純にファイルを保存する目的に使います。

..
    Step 2 - Application Setup
    --------------------------

手順 2 - アプリケーションのセットアップ
---------------------------------------

..
    To begin our application, start by adding a Python source file named
    ``tasks.py`` to the ``tasks`` directory.  We'll add a few basic imports
    within the newly created file:

アプリケーション開発を始めるには、 ``tasks.py`` という名前で Python のソースファイルを ``tasks`` ディレクトリに追加することから始めます。新たに作成したこのファイルに標準ライブラリをインポートするプログラムを追加します。

.. code-block:: python

    import os
    import logging
    
    from pyramid.config import Configurator
       
    from paste.httpserver import serve

..
    Then we'll set up logging and the current working directory path:

それから logging やカレントワークディレクトリのパスを設定します。

.. code-block:: python
    
    logging.basicConfig()
    log = logging.getLogger(__file__)
    
    here = os.path.dirname(os.path.abspath(__file__))

..
    Finally, in a block that runs only when the file is executed, we'll configure
    the Pyramid application, obtain the WSGI app, and serve it.

最後に、このファイルが実行されたときのみ処理されるブロックに、Pyramid のアプリケーションと WSGI アプリケーションを生成して提供するように設定します。

.. code-block:: python
    
    if __name__ == '__main__':
        # settings 設定
        settings = {}
        settings['reload_all'] = True
        settings['debug_all'] = True
        # configuration 設定
        config = Configurator(settings=settings)
        # app サーバー
        app = config.make_wsgi_app()
        serve(app, host='0.0.0.0')

..
    We now have the basic project layout needed to run our application, but
    we still need to add database support, routing, views, and templates.

これでアプリケーションを実行するために必要なプロジェクトの配置ができました。但し、まだデータベースのサポート、ルーティング、ビュー、テンプレートを追加しなければなりません。

..
    Step 3 - Database And Schema
    ----------------------------

手順 3 - データベースとスキーマ
-------------------------------

..
    To make things straightforward, we'll use the widely installed SQLite
    database for our project. The schema for our tasks is simple: an **id**
    to uniquely identify the task, a **name** not longer than 100 characters, and
    a **closed** boolean to indicate if the task is closed or not.

開発作業を単純にするために、一般的によくインストールされている SQLite データベースをこのプロジェクトに使います。このタスクのスキーマはシンプルです。タスクを一意に識別する **id** 、100 文字以内の **name** 、タスクが完了しているかどうかを表す **closed** のブーリアン値です。

..
    Add to the ``tasks`` directory a file named ``schema.sql`` with the following
    content:

次の内容を含んだ ``schema.sql`` というファイルを ``tasks`` ディレクトリへ追加してください。

.. code-block:: sql

    CREATE TABLE IF NOT EXISTS tasks (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name CHAR(100) NOT NULL,
        closed BOOL NOT NULL
    );
    
    INSERT OR IGNORE INTO tasks (id, name, closed) VALUES (1, 'Start learning Pyramid', 0);
    INSERT OR IGNORE INTO tasks (id, name, closed) VALUES (2, 'Do quick tutorial', 0);
    INSERT OR IGNORE INTO tasks (id, name, closed) VALUES (3, 'Have some beer!', 0);

..
    Add a few more imports to the very top of the ``tasks.py`` file:

``tasks.py`` ファイルの最上部でさらにいくつかインポートします。

.. code-block:: python

    from pyramid.events import NewRequest
    from pyramid.events import subscriber
    from pyramid.events import ApplicationCreated
    from paste.httpserver import serve
    import sqlite3

..
    To make the process of creating the database slightly easier, rather than
    requiring a user to execute the data import manually with SQLite, we'll create
    a function that subscribes to a Pyramid system event for this purpose. By
    subscribing a function to the ``ApplicationCreated`` event, each time we'll
    start the application, our subscribed function will be executed.
    Consequently, our database will be created or updated as necessary when the
    application is started.

SQLite でユーザにデータベースの作成処理を読み込んで実行してもらうよりも、この作成処理の方が少しだけ簡単です。この目的のために Pyramid のシステムイベントに登録する関数を作成します。ある関数を ``ApplicationCreated`` イベントに対して登録すると、その登録された関数が実行されます。その結果として、アプリケーションの起動時に必要に応じて、データベースを作成する、または更新します。

.. code-block:: python
    
    @subscriber(ApplicationCreated)
    def application_created_subscriber(event):
        log.warn('Initializing database...')
        f = open(os.path.join(here, 'schema.sql'), 'r')
        stmt = f.read()
        settings = event.app.registry.settings
        db = sqlite3.connect(settings['db'])
        db.executescript(stmt)
        db.commit()
        f.close()

..
    We also need to make our database connection available to the application.
    We'll provide the connection object as an attribute of the application's
    request. By subscribing to the Pyramid ``NewRequest`` event we'll initialize
    a connection to the database when a Pyramid request begins.  It will be
    available as ``request.db``.  We'll arrange to close it down by the end of
    the request lifecycle using the ``request.add_finished_callback`` method.

また、アプリケーションから利用できるデータベースのコネクションも生成しなければなりません。アプリケーションのリクエストオブジェクトの属性として、コネクションオブジェクトを提供します。Pyramid の ``NewRequest`` イベントに登録することで、Pyramid リクエストの開始時に、データベースのコネクションが初期化されます。これは ``request.db`` として利用できます。 ``request.add_finished_callback`` メソッドを使って、リクエストのライフサイクルの最後にクローズするように修正します。

.. code-block:: python

    @subscriber(NewRequest)
    def new_request_subscriber(event):
        request = event.request
        settings = request.registry.settings
        request.db = sqlite3.connect(settings['db'])
        request.add_finished_callback(close_db_connection)

    def close_db_connection(request):
        request.db.close()

..
    To make those changes active, we'll have to specify the database location in
    the configuration settings and make sure our ``@subscriber`` decorator is
    scanned by the application at runtime using config.scan().

いま行った変更を有効にするには、settings の設定でデータベースの場所を指定する必要があります。そして ``@subscriber`` デコレータで実行時にアプリケーションを調べさせるのに config.scan() を使います。

.. code-block:: python

    if __name__ == '__main__':
        ...
        settings['db'] = os.path.join(here, 'tasks.db')
        ...
        config.scan()
        ...

..
    We now have the basic mechanism in place to create and talk to the database 
    in the application through ``request.db``.

これで ``request.db`` を通して、アプリケーションのデータベースを作成してやり取りする基本的な仕組みができました。

..
    Step 4 - View Functions And Routes
    ----------------------------------

手順 4 - ビュー関数とルート
---------------------------

..
    It's now time to expose some functionality to the world in the form of view
    functions. We'll start by adding a few imports to our ``tasks.py`` file.  In
    particular, we're going to import the ``view_config`` decorator, which will
    let the application discover and register views.

いよいよ、ビュー関数の形態で機能をインターネットへ公開するときがきました。 ``tasks.py`` ファイルにいくつかインポートすることから始めます。特に ``view_config`` デコレータをインポートして、アプリケーションにビューの検出と登録を行わせます。

.. code-block:: python

    ...
    from pyramid.exceptions import NotFound
    from pyramid.httpexceptions import HTTPFound
    from pyramid.session import UnencryptedCookieSessionFactoryConfig
    from pyramid.view import view_config
    ...

..
    We'll now add some view functions to our application for listing, adding, and
    closing todos. 

いまアプリケーションに対して、タスクの表示、追加、完了のビュー関数を追加しました。

..
    List View
    +++++++++

List ビュー関数
+++++++++++++++

..
    This view is intended to show all open entries, according to our ``tasks``
    table in the database. It uses the ``list.mako`` template available under the
    ``templates`` directory by defining it as the ``renderer`` in the
    ``view_config`` decorator. The results returned by the query are tuples but we
    convert them into a dictionary for easier accessibility within the template.
    The view function will pass a dictionary defining ``tasks`` to the
    ``list.mako`` template.

このビュー関数は、データベースの ``tasks`` テーブルから、オープンしている全てのエントリを表示するために呼ばれます。 ``view_config`` デコレータの ``renderer`` に ``list.mako`` を定義することで、 ``templates`` ディレクトリ配下の ``list.mako`` テンプレートが利用できます。そのクエリが返す結果はタプルですが、テンプレート内から扱いやすいようにそのタプルをディクショナリに変換します。ビュー関数は、 ``tasks`` を定義するディクショナリを ``list.mako`` テンプレートへ渡します。

.. code-block:: python

    @view_config(route_name='list', renderer='list.mako')
    def list_view(request):
        rs = request.db.execute("select id, name from tasks where closed = 0")
        tasks = [dict(id=row[0], name=row[1]) for row in rs.fetchall()]
        return {'tasks': tasks}

..
    When using the ``view_config`` decorator, it's important to specify a
    ``route_name`` to match a defined route, and a ``renderer`` if the function is
    intended to render a template. The view function should then return a
    dictionary defining the variables for the renderer to use.  Our ``list_view``
    above does both.

``view_config`` デコレータを使うとき、定義されたルートにマッチさせるために ``route_name`` を指定し、その関数がテンプレートをレンダリングするなら ``renderer`` を指定することが重要です。ビュー関数は、そのレンダラーが使用する変数を定義したディクショナリを返す必要があります。この ``list_view`` 関数はその両方を行います。

..
    New View
    ++++++++

New ビュー関数
++++++++++++++

..
    This view lets the user add new tasks to the application. If a ``name`` is
    provided to the form, a task is added to the database. Then an information
    message is flashed to be displayed on the next request, and the user's browser
    is redirected back to the *list_view*. If nothing is provided, a warning
    message is flashed and the *new_view* is displayed again.

このビュー関数は、アプリケーションに対して、ユーザへ新しいタスクを追加させます。もしフォームに ``name`` が提供されたら、データベースへタスクが追加されます。その後、次のリクエスト上に表示されるように通知メッセージが書き込まれます。そして、ユーザのブラウザは *list_view* へ戻るようにリダイレクトされます。もし何も提供されない場合、警告メッセージが書き込まれて、再度 *new_view* が表示されます。

.. code-block:: python

    @view_config(route_name='new', renderer='new.mako')
    def new_view(request):
        if request.method == 'POST':
            if request.POST.get('name'):
                request.db.execute('insert into tasks (name, closed) values (?, ?)',
                                   [request.POST['name'], 0])
                request.db.commit()
                request.session.flash('New task was successfully added!')
                return HTTPFound(location=request.route_url('list'))
            else:
                request.session.flash('Please enter a name for the task!')
        return {}

.. warning::

   ..  Be sure to use question marks when building SQL statements via
       ``db.execute``, otherwise your application will be vulnerable to SQL
       injection when using string formatting.

   ``db.execute`` 経由で SQL 文を構築するとき、クエスチョンマーク (?) を必ず使うようにしてください。そうしないと、文字列フォーマットを使うときに SQL インジェクションに対して脆弱なアプリケーションになってしまいます。

..
    Close View
    ++++++++++

Close ビュー関数
++++++++++++++++

..
    This view lets the user mark a task as closed, flashes a success message, and
    redirects back to the *list_view* page.

このビュー関数は、ユーザーにタスクを完了させます。処理が成功したメッセージを書き込み、 *list_view* ページへ戻るようにリダイレクトします。

.. code-block:: python

    @view_config(route_name='close')
    def close_view(request):
        task_id = int(request.matchdict['id'])
        request.db.execute("update tasks set closed = ? where id = ?", (1, task_id))
        request.db.commit()
        request.session.flash('Task was successfully closed!')
        return HTTPFound(location=request.route_url('list'))

..
    NotFound View
    +++++++++++++

NotFound ビュー関数
+++++++++++++++++++

..
    This view lets us customize the default ``NotFound`` view provided by Pyramid,
    by using our own template. The ``NotFound`` view is displayed by Pyramid when
    a URL cannot be mapped to a Pyramid view.  We'll add the template in a
    subsequent step.

このビュー関数は、Pyramid が提供するデフォルトの ``NotFound`` ビュー関数を、自分たちのテンプレートでカスタマイズします。Pyramid は、URL が Pyramid のビュー関数にマッピングできないときに ``NotFound`` ビューを表示します。このテンプレートを次の手順で追加します。

.. code-block:: python

    @view_config(context='pyramid.exceptions.NotFound',
                 renderer='notfound.mako')
    def notfound_view(self):
        return {}

..
    Adding Routes
    +++++++++++++

ルートを追加
++++++++++++

..
    We finally need to add some routing elements to our application configuration
    if we want our view functions to be matched to application URLs.

ビュー関数にアプリケーションの URL をマッチさせたい場合、最後はアプリケーション設定にルーティングの要素を追加する必要があります。

.. code-block:: python

    ...
    # ルート設定
    config.add_route('list', '/')
    config.add_route('new', '/new')
    config.add_route('close', '/close/{id}')
    ...

..
    We've now added functionality to the application by defining views exposed
    through the routes system.

これにより、ルートシステムを通じて、公開されるビュー関数を定義することで、アプリケーションに機能を追加しました。

..
    Step 5 - View Templates
    -----------------------

手順 5 - ビューテンプレート
---------------------------

..
    The views perform the work, but they need to render something that the web
    browser understands: **HTML**.  We have seen that the view configuration
    accepts a renderer argument with the name of a template. We'll use one of
    the default templating engines supported out of the box by Pyramid: *Mako
    Templates*.

ビュー関数はその処理を実行しますが、その実行結果はウェブブラウザが理解できる **HTML** のカタチにレンダリングする必要があります。前節では、renderer 引数でテンプレート名を受け取るビュー関数の設定をしました。Pyramid がサポートしていて、すぐに使えるデフォルトテンプレートエンジンの1つである *Mako Templates* を使います。

..
    We'll also use Mako template inheritance.  Template inheritance makes it
    possible to reuse a generic layout across multiple templates, easing layout
    maintenance and uniformity.

さらに Mako のテンプレート継承も使います。テンプレート継承は、複数のテンプレートにまたがって汎用的なレイアウトを再利用できるようにします。そして、レイアウトのメンテナンスや統一性をもたせるのも簡単に行えます。

..
    Create the following templates in the ``templates`` directory with the
    respective content:

``templates`` ディレクトリへ、それぞれ次のテンプレートを作成してください。

layout.mako
+++++++++++

..
    This template contains the basic layout structure that will be shared with
    other templates. Inside the body tag we've defined a block to display flash
    messages sent by the application and another block to display the content of
    the page inheriting this master layout by using the mako directive
    ``${next.body()}``.

このテンプレートは、他のテンプレートから共有される基本レイアウトの構造を含みます。body タグの内部でアプリケーションから送られた通知メッセージを表示するブロックと、mako ディレクティブ ``${next.body()}`` でこのマスターレイアウトを継承してページのコンテンツを表示する別のブロックを定義しました。

.. literalinclude:: pyramid_quick_tutorial/templates/layout.mako
   :language: html+mako

list.mako
+++++++++

..
    This template is used by the ``list_view`` view function.  This template
    extends the master ``layout.mako`` template by providing a listing of
    tasks. The loop uses the passed ``tasks`` dictionary sent from the
    ``list_view`` function using Mako syntax. We also use the
    ``request.route_url`` function to generate a url based on a route name and
    its arguments instead of statically defining the url path.

このテンプレートは、 ``list_view`` ビュー関数が使います。このテンプレートは、タスクの表示を提供することで、 ``layout.mako`` テンプレートのマスターを拡張します。このループは、Mako の構文で ``list_view`` 関数から送られた ``tasks`` ディクショナリを使います。また、静的に URL パスを定義するのではなく、ルート名とその引数に基づいた URL を生成する ``request.route_url`` を使います。

.. literalinclude:: pyramid_quick_tutorial/templates/list.mako
   :language: html+mako

new.mako
++++++++

..
    This template is used by the ``new_view`` view function.  The template
    extends the master ``layout.mako`` template by providing a basic form to add
    new tasks.

このテンプレートは、 ``new_view`` ビュー関数が使います。このテンプレートは、新たなタスクを追加する基本的なフォームを提供することで、 ``layout.mako`` テンプレートのマスターを拡張します。

.. literalinclude:: pyramid_quick_tutorial/templates/new.mako
   :language: html+mako

notfound.mako
+++++++++++++

..
    This template extends the master ``layout.mako`` template.  We use it as the
    template for our custom ``NotFound`` view.

このテンプレートは、 ``layout.mako`` テンプレートのマスターを拡張します。カスタム ``NotFound`` ビュー関数のテンプレートとして使います。

.. literalinclude:: pyramid_quick_tutorial/templates/notfound.mako
   :language: html+mako

..
    Configuring Template Locations
    ++++++++++++++++++++++++++++++

テンプレート置き場の設定
++++++++++++++++++++++++

..
    To make it possible for views to find the templates they need by renderer
    name, we now need to specify where the Mako templates can be found by
    modifying the application configuration settings in ``tasks.py``.

ビュー関数がレンダラー名で必要なテンプレートが見つけられるように、 ``tasks.py`` にあるアプリケーションの settings 設定を変更することで、Mako テンプレートを見つけられるパスを指定する必要があります。

.. code-block:: python

    ...
    settings['mako.directories'] = os.path.join(here, 'templates')
    ...

..
    Step 6 - Styling Your Templates
    -------------------------------

手順 6 - テンプレートのスタイル設定
-----------------------------------

..
    It's now time to add some styling to the application templates by adding a
    **CSS** file named ``style.css`` to the ``static`` directory with the
    following content:

ここでは ``static`` ディレクトリへ次の内容を含んだ ``style.css`` という **CSS** ファイルを追加することで、アプリケーションのテンプレートにスタイルを追加してみましょう。

.. literalinclude:: pyramid_quick_tutorial/static/style.css
   :language: css

..
    To cause this static file to be served by the application, we must add a
    "static view" directive to the application configuration:

この静的なファイルは、アプリケーションから提供されます。アプリケーションの設定に "静的なビュー" ディレクティブを追加する必要があります。

.. code-block:: python

    ...
    config.add_static_view('static', os.path.join(here, 'static'))
    ...

..
    Step 7 - Running The Application
    --------------------------------

手順 7 - アプリケーションの実行
-------------------------------

..
    We have now completed all steps needed to run the application in its final
    version. Before running it, here's the complete main code for ``tasks.py`` for
    review:

これで最終的なアプリケーションを実行するのに必要な全ての手順を完了しました。実行する前に、レビュー用途に ``tasks.py`` の完全なソースコードを記載します。

.. literalinclude:: pyramid_quick_tutorial/tasks.py
   :language: python

..
    And now let's run ``tasks.py``:

さぁ ``tasks.py`` を実行してみましょう。

.. code-block:: bash

    $ python tasks.py 
    WARNING:tasks.py:Initializing database...
    serving on 0.0.0.0:8080 view at http://127.0.0.1:8080

..
    Conclusion
    ----------

まとめ
------

..
    This introduction to Pyramid was inspired by **flask** and **bottle** 
    tutorials with the same minimalistic approach in mind. Big thanks Chris 
    McDonough, Carlos de la Guardia, and Casey Duncan for their support and 
    friendship.

Pyramid の入門チュートリアルは、 **flask** と **bottle** のチュートリアルからヒントを得て、同じように最小限のアプリケーション開発を意識していました。Chris McDonough, Carlos de la Guardia, Casey Duncan のサポートと友情に多大なる感謝の意を表します。

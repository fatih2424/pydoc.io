Pydoc
=====

:License: Apache Software License 2.0

Welcome to Pydoc.

Installation
------------

::
    
    git clone https://github.com/rtfd/pydoc.io
    cd pydoc.io
    pip install -r requirements/local.txt
    ./manage.py createsuperuser

Now, you can update the list of packages from Pypi::

    ./manage.py update_package_index

And build some examples::

    pip freeze | ./manage.py process_freeze

You should now be able to start a start:

    ./manage.py runserver

If you browse to http://localhost:8000 you should see a list of docs to view!

Basic Commands
--------------

Setting Up Your Users
^^^^^^^^^^^^^^^^^^^^^

* To create a **normal user account**, just go to Sign Up and fill out the form. Once you submit it, you'll see a "Verify Your E-mail Address" page. Go to your console to see a simulated email verification message. Copy the link into your browser. Now the user's email should be verified and ready to go.

* To create an **superuser account**, use this command::

    $ python manage.py createsuperuser

For convenience, you can keep your normal user logged in on Chrome and your superuser logged in on Firefox (or similar), so that you can see how the site behaves for both kinds of users.

Test coverage
^^^^^^^^^^^^^

To run the tests, check your test coverage, and generate an HTML coverage report::

    $ coverage run manage.py test
    $ coverage html
    $ open htmlcov/index.html

Running tests with py.test
~~~~~~~~~~~~~~~~~~~~~~~~~~

::

  $ py.test


Celery
^^^^^^

This app comes with Celery.

To run a celery worker:

.. code-block:: bash

    cd pydoc
    celery -A pydoc.core.tasks worker -l info

Please note: For Celery's import magic to work, it is important *where* the celery commands are run. If you are in the same folder with *manage.py*, you should be right.

Sentry
^^^^^^

Sentry is an error logging aggregator service. You can sign up for a free account at  https://getsentry.com/signup/?code=cookiecutter  or download and host it yourself.
The system is setup with reasonable defaults, including 404 logging and integration with the WSGI application.

You must set the DSN url in production.

===========
Nose plugin: Alembic Attrib
===========

Requirements
-------------

* nose
* alembic
* sqlalchemy

Install
-------

Install with pip::

    pip install nose-alembic-attrib

Quickstart
----------

Simply import the decorator and use as such::

    from nose_alembic_attrib import alembic_attr

    @alembic_attr(minimum_revision="4b9a79b051c6")
    def test_my_alembic_test(self):
        ...

    @alembic_attr(minimum_revision="5aa2dfb6e6a8")
    def test_my_alembic_test(self):
        ...

Assuming your alembic revision history looks like this::

    $> alembic history

    5aa2dfb6e6a8 -> 3830063c1b00 (head), my head revision
    4b9a79b051c6 -> 5aa2dfb6e6a8, my second revision
    None -> 4b9a79b051c6, my first revision

Running nosetest as follows will honour those minimum revision anotations::

    nosetest --with-alembicattrib --alembic-ini=alembic.ini


Options
-------

Options available:

* ``--with-alembicattrib``: Enable the plugin
* ``--alembic-ini=path/to/alembic.ini``: Assumed to be ``alembic.ini`` in the current dir by default
* ``--alembic-echo={True,False}``: Turn sqlalchemy engine echo on or off

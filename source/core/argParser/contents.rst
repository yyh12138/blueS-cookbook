argParser
=========

.. py:class:: ArgParser

    The class realize to parse parameters from command line by using ``app`` instance

    .. py:function:: __init__(appInstance)

        The constructor allows to keep a reference to the main application instance

        :param appInstance: The main application instance
        :type appInstance: core.app.App 

    .. py:function:: debug()

        This method allows to start debug mode by add ``--debug`` to the command line

    .. py:function:: quiet()

        This method allows to start quiet mode by add ``--quiet`` to the command line

    .. py:function:: verbosity()

        This method allows to start verbosity mode to set LOG_LEVEL by add ``--verbosity`` to the command line

    .. py:function:: create_module()

        This method allows to start create_module by add ``--create-module`` to the command line

    .. py:function:: create_scenario()

        This method allows to start create_scenario by add ``--create-scenario`` to the command line

    .. py:function:: list()

        This method allows to start list by add ``--list`` to the command line

    .. py:function:: launcher()

        This method allows to start launcher by using ``blues_launcher`` to the command line

    .. py:function:: run()

        This method start to run.

        - If no modules or scenarios have been provide, it will enter the loop method of core.app.App

        - If modules have been provide, it will start ``launcher`` method 






config
======

.. py:class:: Config

    The class is used to parse and create a configuration file in ``.cfg`` format

    .. py:function:: __init__(filename)

        The constructor allows to keep a reference to the configuration file and init a config parser

        :param str filename: The configuration file

    .. py:function:: generateData()

        This method allows to read a configuration file and store in the attribute ``datas``

        :raises ParsingError: If the configuration file is not formatted correctly

    .. py:function:: generateShortcuts()

        This method allows to read a configuration file and store in the attribute ``shortcuts``

        :raises ParsingError: If the configuration file is not formatted correctly

    .. py:function:: getShortcuts()

        This method allows to get the shortcuts

        :return: The shortcuts
        :rtype: dict

    .. py:function:: dataExists(moduleName, arg)

        This method allows to check if the arguments exists of the module

        :param str moduleName: The module name
        :param str arg: The argument name
        :return: True if the data exists, False otherwise
        :rtype: bool

    .. py:function:: getData(moduleName, arg)

        This method allows to get the datas

        :param str moduleName: The module name
        :param str arg: The argument name
        :return: The module's arguments
        :rtype: str
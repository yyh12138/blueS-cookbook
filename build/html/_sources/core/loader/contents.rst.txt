loader
=========

.. py:class:: Loader

    This class is used to dynamically load modules.

    .. py:function:: __init__()

        The constructor creates the modules list

    .. py:function:: getModulesNames()

        The method is used to get the list of modules names loaded.

        :return: The list of modules names loaded
        :rtype: list or str

    .. py:function:: load(moduleName)

        The method is used to load a module by its name. It returns the module loaded.

        :param str moduleName: The name of the module to load
        :return: The instance of the module loaded
        :rtype: core.module.module  

    .. py:function:: list(pattern="")

        The method returns the list of modules loaded by filtered.

        :param str pattern: The pattern to filter the list of modules loaded

        
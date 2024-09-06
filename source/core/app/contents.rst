app
===========

.. py:class:: App(Interpreter)

    The main class of the application.

    .. py:function:: __init__(quiet=False, homeDir='/home/usr/.blues', tempDir='/tmp/blues')
        
        The constructor allows to initialize the main attributes and software components used by the framework. 

        :param bool quiet: boolean indicating if blues has been launched in quiet mode.
        :param str homeDir: string indicating the location of the home directory.
        :param str tempDir: string indicating the location of the temporary directory.

    .. py:function:: start(task)

        Start the framework.

        :param str task: Task to start

    .. py:function:: stop(task)

        Stop the framework.

        :param str task: Task to stop

    .. py::function:: restart(task)

        Restart the framework.

        :param str task: Task name to restart

    .. py:function:: exit()

        Exit the framework.

    .. py:function:: tasks(pattern='')

        List the existing tasks available in the framework.

        :param str pattern: Filter

    .. py:function:: create_scenario()

        This method allows to interact with the user in order to easily generate an user scenario.

    .. py:function:: create_module()

        This method allows to interact with the user in order to easily generate a new module.

    .. py:function:: loop()

        This method loops the main interpreter preocess

    .. py:function:: clear()

        This method clears the screen

    .. py:function:: list(pattern='')

        This method lists the available modules

        :param str pattern: Filter

    .. py:function:: shortcuts(pattern='')

        This method lists the available shortcuts

        :param str pattern: Filter

    .. py:function:: _autocompleteModules()

        This method lists the available modules to autocompletes the modules

        :return: list of the available modules in string
        :rtype: str

    .. py:function:: load(moduleName:'!method:_autocompleteModules')

        This method allows to load a module according to its name.
        It allows to load a sequence of modules by using the pipe (``|``) symbol

        :param moduleName: name of the module (or sequence of modules) to load
        :type moduleName: str

        :Example:
        >>> app.load('ble_info')
        >>> app.load('ble_connect|ble_discover')

    .. py:function:: _autocompleteParameters()

        This method lists the parameters to set the modules

        :return: list of the available parameters in string
        :rtype: str

    .. py:function:: _set(name, value, modulesList)
        
        This method is a built-in method of set function with some detials

        :param str name: module's parameters name
        :param str value: module's parameters value
        :return: if setting is completed
        :rtype: bool

    .. py:function:: set(name, value)

        This method allows to set the parameters of the modules by ``_set`` method

        :param str name: module's parameters name
        :param str value: module's parameters value
        :raises SetParameterException(Exception): if the parameter is not set
        :raises NoModuleLoaded(SetParameterException): if no module is loaded
        :raises IncorrectPrarameter(SetParameterException): if the parameter is incorrect
        :raises MutipleModulesLoaded(SetParameterException): if multiple modules are loaded
        :Example:
        >>> app.set('INTERFACE', 'hci0')
        >>> app.set('ble_connect1.INTERFACE', 'hci0')

    .. py:function:: showargs()

        This method dispalys a chart describing the parameters of the loaded modules

    .. py:function:: args()

        This method is an alias of ``showargs``

    .. py:function:: info()

        This method displays the information of the loaded modules

    .. py:function:: run()

        This method runs the loaded modules with the parameters set.
        Run by ``module.execute()`` method



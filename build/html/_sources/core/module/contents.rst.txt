module
==========

.. py:class:: Module

    This class defines the standard behavior of a module. It is the base class for all modules.

    .. py:method:: __init__()

        This constructor inits the module.

    .. py:method:: out(success, output={})

        This method help to format the output of the module.

        :param bool success: True if the module has been executed successfully, False otherwise.
        :param output: The output of the module.
        :type output: dict of str
        :return: The formatted output of the module, like {"success": success, "output": output}
        :rtype: dict

    .. py:method:: ok(output={})

        This method is a shortcut to call :py:meth:`out` with success=True.

        :param output: The output of the module.
        :type output: dict of str
        :return: The formatted output of the module, like {"success": True, "output": output}
        :rtype: dict

    .. py:method:: nok()

        This method is a shortcut to call :py:meth:`out` with success=False.

        :return: The formatted output of the module, like {"success": False, "output": {}}
        :rtype: dict

    .. py:method:: init()

        It must be overloaded in order to define the parameters of module

    .. py:method:: prerun()

        It must be overloaded in order to define the actions to do before running the module

    .. py:method:: run()

        It must be overloaded in order to define the actions to do when running the module

    .. py:method:: postrun()

        It must be overloaded in order to define the actions to do after running the module

    .. py:method:: execute()

        This method is the main method to call to run the module. It calls :py:meth:`prerun`, :py:meth:`run` and :py:meth:`postrun` in the right order.

        :raise KeyboardInterrupt: If the user wants to stop the execution of the module
        :raise EOFError: If the module is not correctly initialized

    .. py:method:: info()

        This method helps to format the output of the module

        :return: The formatted output of the module, like {"name": name, "type": type, "description": description, "dependencies": dependencies}
        :rtype: dict

    .. py:method:: watchKeyboard()

        This method allows to register a callback if a key is pressed by ``on_release`` method

    .. py:method:: key(key)

        This method is called when a key is pressed.
        It raises the scenario signal ``onkey``

        :param str key: The pressed key name
    
    .. py:method:: loadScenario()

        This method helps to load a scenario and load key related signals

        :return: If the scenario is loaded
        :rtype: bool
        :raise ScenarioNotFoundError: If the scenario file is not found


.. py:class:: WirelessModule(Module)

    This class defines the standard behavior of a wireless module. It inherits from ``core.module.Module``.
    It adds a couple of Emitters and Receivers

    .. py:method:: __init__()

        This constructor inits the module

    .. py:method:: registerEmitter(cls, technology, emitter=None)

        This method allows to link an emitter for a specific technology.

        :param str technology: The technology of the emitter
        :param emitter: The emitter to register
        :type emitter: :py:class:`libs.wireless.Emitter`

    .. py:method:: registerReceiver()

        This method allows to link a receiver for a specific technology

        :param str technology: The technology of the receiver
        :param receiver: The receiver to register
        :type receiver: :py:class:`libs.wireless.Receiver`

    .. py:method:: getEmitter(interface="")

        This method returns the emitter instance by ``technology``

        :param str interface: The interface of the emitter
        :return: The emitter of the module
        :rtype: :py:class:`libs.wireless.Emitter`

    .. py:method:: getReceiver()

        This method returns the receiver instance by ``technology``

        :param str interface: The interface of the receiver
        :return: The receiver of the module
        :rtype: :py:class:`libs.wireless.Receiver`
scenario
==========

.. py:class:: Scenario

    This class a scenario, which can customize the behavior of a module without modifying its code

    .. py:method:: __init__(name="", module=None)

        This constructor inits the scenario

        :param str name: The name of the scenario
        :param module: The module to apply the scenario
        :type module: :py:class:`core.module.Module`

    .. py:method:: receiveSignal(signal, *args, **kwargs)

        This method is called when a signal is received

        :param str signal: The signal to receive
        :param args: The arguments of the signal
        :param kwargs: The keyword arguments of the signal
        :return: If the signal is received
        :rtype: bool

    .. py:method:: scenarioSignal(argument)

        It is a decorator allowing to link a module's method to scenario signal and run the related method

        :param str argument: signal name



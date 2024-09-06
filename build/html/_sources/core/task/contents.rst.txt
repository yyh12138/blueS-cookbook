task
==========

.. py:class:: task(mutiprocessing.Process)

    This class define a background task, it inherits from ``multiprocessing.Process``. 
    It provides a friendly API to run a given function in background

    .. py:function:: __init__(function, name, args=[], kwargs={})

        The constructor inits the task with the target function, and inits the attributes.

        :param function function: The function to run in background
        :param str name: The name of the current task
        :param list args: The list of unamed arguments
        :param dict kwargs: The dictionary of named arguments

    .. py:function:: run()

        The method runs the target function in background. 

        The standard output is automatically redirected to a temporary file, named ``<taskName>-<taskPID>.out``.

    .. py:function:: stop()

        The method stops the current task.

    .. py:function:: start()

        The method starts the current task.

    .. py:function:: toList()

        The method returns a list representing the current task. 
        The list is [PID, name, state, outputFileName]

        :return: list representing the current task
        :rtype: list or str

    


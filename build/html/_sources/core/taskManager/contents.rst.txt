taskManager
============

.. py:class:: TaskManager

    This class is a manager to manipulate the background tasks

    .. py:method:: __init__()

        This constructor inits the task manager

    .. py:method:: addTask(function, name="", args=[], kwargs={})

        This method adds a new background task to the task manager.
        If a task already exists, it will be suffixed by a number

        :param function function: The function to add
        :param str name: The name of the task
        :param list args: The list of the unamed arguments
        :param dict kwargs: The dictionary of the named arguments
        :return: The name of task
        :rtype: str

    .. py:method:: startTask(name)

        This method starts an existing task

        :param str name: The name of the task
        :return: If the task is started
        :rtype: bool

    .. py:method:: stopTask(name)

        This method stops an existing task

        :param str name: The name of the task
        :return: If the task is stopped
        :rtype: bool

    .. py:method:: restartTask(name)

        This method restarts an existing task

        :param str name: The name of the task
        :return: If the task is restarted
        :rtype: bool

    .. py:method:: stopAllTasks()

        This method stops all the tasks

    .. py:method:: getTaskPID(name)

        This method returns the PID of the task

        :param str name: The name of the task
        :return: The PID of the task
        :rtype: int

    .. py:method:: getTaskState(name)

        This method returns the state of the task

        :param str name: The name of the task
        :return: The state of the task
        :rtype: str

    .. py:method:: getTasksList(pattern="")

        This method returns the list of the tasks

        :param str pattern: The pattern to filter the tasks
        :return: The list of the existing tasks
        :rtype: list


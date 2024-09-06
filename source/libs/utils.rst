utils
==============

.. py:method:: getHomeDir()

    Returns the home directory

.. py:method:: addTask(function, name="", args=[], kwargs={})

    Adds a task to the task queue.
    It uses ``core.taskManager.addTask``

    :param function function: The function to be executed
    :param str name: The name of the task
    :param list args: The unamed arguments to be passed to the function
    :param dict kwargs: The named arguments to be passed to the function
    :return: The task name
    :rtype: str

.. py:method:: startTask(name)

    Starts a task from the task queue.
    It uses ``core.taskManager.startTask``

    :param str name: The name of the task

.. py:method:: stopTask(name)

    Stops a task from the task queue.
    It uses ``core.taskManager.stopTask``

    :param str name: The name of the task

.. py:method:: stopAllTasks()

    Stops all tasks from the task queue.
    It uses ``core.taskManager.stopAllTasks``

.. py:method:: loadModule(name)

    Loads a module from the modules directory.
    It uses ``core.loader.load``

    :param str name: The name of the module

.. py:method:: exitBlues()

    Exits the blues

.. py:method:: wait(second=1, minute=0, hour=0)

    Waits for a certain amount of time

    :param int second: The number of seconds to wait
    :param int minute: The number of minutes to wait
    :param int hour: The number of hours to Waits

.. py:method:: now()

    Returns the current time

.. py:method:: isRoot()

    Returns True if the user is root

    :return: If the user is root
    :rtype: bool

.. py:method:: isNumber(theString)

    Returns True if the string is a number

    :param str theString: The string to be checked
    :return: If the string is a number
    :rtype: bool

.. py:method:: isPrintable(theString)

    Returns True if the string is printable

    :param str theString: The string to be checked
    :return: If the string is printable
    :rtype: bool

.. py:method:: isHexadecimal(theString)

    Returns True if the string is a hex

    :param str theString: The string to be checked
    :return: If the string is a hex
    :rtype: bool

.. py:method:: booleanArg(arg)

    Returns the boolean value of the boolean string

    :param str arg: The argument
    :return: The boolean value of the argument
    :rtype: bool
    :Example:
        >>> utils.booleanArg("yes")
        True

.. py:method:: integerArg(arg)

    Returns the integer value of the argument

    :param str arg: The argument
    :return: The integer value of the integer string
    :rtype: int
    :Example:
        >>> utils.integerArg("0x1234")
        4660

.. py:method:: addressArg(arg)

    Returns the address value of the address string

    :param str arg: The argument
    :return: The address value of the address string
    :rtype: int
    :Example:
        >>> utils.addressArg("0a:0b:0c:0d:00:00")
        "0A:0B:0C:0D:00:00"

.. py:method:: getRandomAddress()

    Returns a random address

    :return: A random address
    :rtype: str


    



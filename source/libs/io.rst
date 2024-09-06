io
=========

.. py:class:: VerbosityLevels(IntEnum)

    This class provide an enum of avaliable verbosity levels, ``NONE``, ``NO_INFO_AND_WARNING``, ``NO_INFO``, ``ALL``


.. py:method:: banner()

    This method print the banner

    :return: The banner
    :rtype: str

.. py:method:: colorCode(color)

    This method return the color code of the given color

    :param str color: The color
    :return: The color code
    :rtype: str

.. py:method:: colorize(message, color)

    This method colorize the message with the given color

    :param str message: The message to colorize
    :param str color: The color
    :return: The colorized message
    :rtype: str

.. py:method:: enterPinCode(message="Enter pin code: ", maxLength=6)

    This method ask to enter a pin code

    :param str message: The message to display
    :param int maxLength: The maximum length of the pin code
    :return: The pin code
    :rtype: str

.. py:method:: success(message)

    This method print a success message, like ``[SUCCESS] message``

    :param str message: The message to print
    :return: The message
    :rtype: str

.. py:method:: info(message)

    This method print an info message, like ``[INFO] message``

    :param str message: The message to print
    :return: The message
    :rtype: str

.. py:method:: fail(message)

    This method print a fail message, like ``[FAIL] message``

    :param str message: The message to print
    :return: The message
    :rtype: str

.. py:method:: warning(message)

    This method print a warning message, like ``[WARNING] message``

    :param str message: The message to print
    :return: The message
    :rtype: str

.. py:method:: displayPacket(packet)

    This method display the given packet, like ``[PACKET] packet``

    :param scapy packet: The packet to display
    :return: The packet
    :rtype: scapy packet

.. py:method:: ask(prompt, default="", final=": ")

    This method ask user a question, like ``[QUESTION] prompt: `` 

    :param str prompt: The question
    :param str default: The default value
    :param str final: The final character
    :return: The answer
    :rtype: str

.. py:method:: chart(columnsName, content, title="")

    This method print a chart

    :param list columnsName: The columns name
    :param list content: The content
    :param str title: The title
    :Example:
        >>> io.chart(["Name", "Age"], [["John", 25], ["Doe", 30]], "Users")

.. py:method:: progress(count, total=100, suffix="")

    This method print a progress bar

    :param int count: The current count
    :param int total: The total count
    :param str suffix: The suffix
    :return: If the progress is complete
    :rtype: bool
    :Example:
        >>> io.progress(100, 100, "Complete")
        )))))))))))))))))))))))))) Complete
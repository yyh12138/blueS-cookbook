interpreter
===========

.. py:class:: Interpreter

    The class is used to be inherited. Each method lists in list ``availableCommands``. 
    If the parameters have no default value in method, the parameters is mandatory in the interpreter. Else, the parameters is optional.

    Every parameter can be automatically autocompleted if the ``autocompletion`` mode is enabled.
    
    * You can provide a list: 

    :Example:
        def my_cmd(self, arg1, arg2:["value1", "value2"]="value1"):
            pass

    * You can provide a string indicating a method using the syntax ``!method:<methodName>`` or ``!function:<functionName>``:

    :Example:
        def _autocompleteMyCmd(self):
            return ["value"+str(i) for i in range(10)]

        def my_cmd(self,my_parameter:"!method:_autocompleteMyCmd"="value1"):
            pass

    * You can provide a string indicating a file path using the syntax ``!file``:

    :Example:
        def my_cmd(self,my_parameter:"!file"="path1"):
            pass

    The name of the parameters are displayed when user types a known command if the ``suggestion`` mode is enabled.

    In one word, you can type enter to accept the suggestion or autocomplete the name of the parameter.

    .. py:function:: __init__(prompt=io.colorize(" ~~> ", "cyan"), suggestion=True, autocompletion=True)

        The constructor inits the interpreter and set availableCommands, suggestion mode and autocompletion mode. 

        :param str prompt: The prompt to display when waiting for user input.
        :param bool suggestion: Enable or disable the suggestion mode.
        :param bool autocompletion: Enable or disable the autocompletion mode.

    .. py:function:: loop()

        The method is the main interaction loop by running ``suggestion``, ``autocompletion`` and ``evaluateScript``

    .. py:function:: evaluateScript(script)

        The method is used to evaluate a script. The script is a string containing one or more commands separated by a newline.

        It splits the string provided by the user using the delimiter ``;`` and calls the method ``evaluateCommand``
		on each command found.

        :param str script: The script to evaluate

    .. py:function:: evaluateCommand(command)

        The method is used to evaluate a command by using ``getattr(self, opcode)(*arguments)``. The opcode is in ``avaliabeCommands``, and interpreter will call ``self.opcode(*arguments)`` if opcode is found in ``availableCommands``.

        :param command: The command to evaluate
        :type command: str or list


att_server
============

.. py:class:: ATT_Attribute

    This class describes an ATT attribute

    .. py:method:: __init__(self, handle=None, value=None, type=None, permissions=None)

        :param int handle: The handle of the attribute
        :param bytes value: The value of the attribute
        :param type: The type of the attribute
        :type type: int or bytes or hex or string
        :param permissions: The permissions of the attribute
        :type permissions: int or list or string

    .. py:method:: __str__()

        :return: A string representation of the ATT attribute

.. py:class:: ATT_Database

    This class describes an ATT database.
    It can manipulate the ATT attributes

    .. py:method:: __init__()

        Init the attributes list

    .. py:method:: show()

        Print the ATT list, like [``Attribute handle``, ``Attribute type``, ``Attribute value``]

    .. py:method:: showService()

        Print the services list, like [``Start handle``, ``End handle``, ``UUID16``, ``UUID128``, ``Name``]

    .. py:method:: showCharacteristics(startHandle, endHandle, title="Characteristics")

        Print the characteristics list, like [``Declaration handle``, ``Value handle``, ``UUID16``, ``UUID128``, ``Name``, ``Permissions``, ``Value``, ``Descriptors``]

    .. py:method:: showGATT()

        Print the GATT list, actually run the ``showServices`` and ``showCharacteristics`` methods

    .. py:method:: setAttribute(handle=None, value=None, type=None, permissions=None)

        Add an attribute to the database

        :param int handle: The handle of the attribute
        :param bytes value: The value of the attribute
        :param type: The type of the attribute
        :type type: int or bytes or hex or string
        :param permissions: The permissions of the attribute
        :type permissions: int or list or string
        :Example:
            >>> db = ATT_Database()
            >>> db.setAttribute(handle=1, value=b'\x00\x18', type="Primary Service", permissions=["Read"])
            >>> db.show()

    .. py:method:: getNextHandle()

        Get the next handle available in the database

        :return: The next handle available
        :type: int
    
    .. py:method:: read(handle)

        This method reads the value of the attribute with the given handle

        :param int handle: The handle of the attribute to read
        :return: The value of the attribute, like (``existing``, ``writable``, ``value``)
        :type: tuple of (bool, bool, btyes)

    .. py:method:: write(handle, value)

        This method writes the value of the attribute with the given handle

        :param int handle: The handle of the attribute to write
        :param bytes value: The value to write
        :return: The value of the attribute, like (``existing``, ``writable``, ``value``)
        :type: tuple of (bool, bool, bytes)

    .. py:method:: readByType(start, end, type)

        This method reads the value of the attribute with the given type

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :param type: The type of the attribute to read
        :type type: int or string
        :return: The value of the attribute, like [{"attributeHandle": 1, "value": b"\x00\x18"}, {...}]
        :type: list of dict

    .. py:method:: readByGroupType(start, end, type)

        This method reads the value of the attribute with the given group type

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :param type: The type of the attribute to read
        :type type: int or string
        :return: The value of the attribute, like [{"attributeHandle": 1, "endGroupHandle": 2, "value": b"\x00\x18"}, {...}]
        :type: list of dict

    .. py:method:: findInformation(start, end)

        This method finds the information of the attribute

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :return: The value of the attribute, like [{"attributeHandle": 1, "type": b"\x01"}, {...}]
        :type: list of dict

    .. py:method:: findByTypeValue(start, end, type, value)

        This method finds the attribute by type and value

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :param type: The type of the attribute to read
        :type type: int or string
        :param bytes value: The value of the attribute to read
        :return: The value of the attribute, like [{"attributeHandle": 1, "endGroupHandle": 2}, {...}]
        :type: list of dict


.. py:class:: ATT_Server 

    This class implements an ATT server, and uses ``ATT_Database`` to store the attributes

    .. py:method:: __init__(self, database=None, mtu=23)

        :param database: The database to use
        :type database: libs.ble_utils.attserver.ATT_Database
        :param int mtu: The MTU size

    .. py:method:: addAttribute(handle=None, value=None, type=None, permissions=None)

        Add an attribute to the database by using the ``setAttribute`` method of the database

        :param int handle: The handle of the attribute
        :param bytes value: The value of the attribute
        :param type: The type of the attribute
        :type type: int or bytes or hex or string
        :param permissions: The permissions of the attribute
        :type permissions: int or list or string

    .. py:method:: setMtu(mtu)

        Set the MTU size

        :param int mtu: The MTU size

    .. py:method:: read(handle)

        This method reads the value of the attribute with the given handle by using the ``read`` method of the database

        :param int handle: The handle of the attribute to read
        :return: (``success``, ``value`` or ``error code``)
        :type: tuple of (bool, bytes or int)

    .. py:method:: readBlob(handle, offset)

        This method implements the read blob request by using the ``read`` method of the database

        :param int handle: The handle of the attribute to read
        :param int offset: The offset of the attribute to read
        :return: (``success``, ``value`` or ``error code``)
        :type: tuple of (bool, bytes or int)

    .. py:method:: writeCommand(handle, value)

        This method implements the write command by using the ``write`` method of the database

        :param int handle: The handle of the attribute to write
        :param bytes value: The value to write
        :return: (``success``, None)
        :type: tuple of (bool, None)

    .. py:method:: writeRequest(handle, value)

        This method implements the write request by using the ``write`` method of the database

        :param int handle: The handle of the attribute to write
        :param bytes value: The value to write
        :return: (``success``, ``error code``)
        :type: tuple of (bool, int)

    .. py:method:: readByType(start, end, type)

        This method reads the value of the attribute with the given type by using the ``readByType`` method of the database

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :param type: The type of the attribute to read
        :type type: int or string
        :return: (``success``, ``value`` or ``error code``)
        :type: tuple of (bool, list of dict)

    .. py:method:: readByGroupType(start, end, type)

        This method reads the value of the attribute with the given group type by using the ``readByGroupType`` method of the database

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :param type: The type of the attribute to read
        :type type: int or string
        :return: (``success``, ``value`` or ``error code``)
        :type: tuple of (bool, list of dict)

    .. py:method:: findInformation(start, end)

        This method finds the information of the attribute by using the ``findInformation`` method of the database

        :param int start: The start handle of the attribute to read
        :param int end: The end handle of the attribute to read
        :return: (``success``, ``value`` or ``error code``)
        :type: tuple of (bool, list of dict)


.. py:class:: GATT_Server(ATT_Server)

    This class inherits from ``ATT_Server`` and provides the GATT server

    .. py:method:: addPrimaryService(uuid, handle=None, permissions=["Read"])

        Add a primary service to the database by using the ``setAttribute`` method of the database

        :param uuid: The UUID of the service
        :type uuid: int or bytes or hex or string
        :param int handle: The handle of the service
        :param permissions: The permissions of the service
        :type permissions: int or list or string

    .. py:method:: addSecondaryService(uuid, handle=None, permissions=["Read"])

        Add a secondary service to the database by using the ``setAttribute`` method of the database

        :param uuid: The UUID of the service
        :type uuid: int or bytes or hex or string
        :param int handle: The handle of the service
        :param permissions: The permissions of the service
        :type permissions: int or list or string

    .. py:method:: addCharacteristic(uuid, value=b"", declarationHandle=None, valueHandle=None, permissions=["Read", "Write"])

        This method adds a characteristic to the database by using the ``addAttribute`` method

        :param bytes uuid: The UUID of the descriptor
        :param bytes value: The value of the descriptor
        :param int handle: The handle of the descriptor

    .. py:method:: addDescriptor(uuid, value=b"", handle=None, permissions=["Read", "Write", "Notify"])

        This method adds a descriptor to the database by using the ``addAttribute`` method

        :param bytes uuid: The UUID of the descriptor
        :param bytes value: The value of the descriptor
        :param int handle: The handle of the descriptor




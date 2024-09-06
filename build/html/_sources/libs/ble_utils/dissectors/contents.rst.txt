dissectors
===============

.. py:class:: PermissionsFlag(Dissector)

    This class provides the permissions flag dissector. 
    The permissions can be: ``Indicate``, ``Write``, ``Read``, ``Notify``, ``Broadcast``, ``Write Without Response``, ``Authenticated Signed Writes``, ``Extended Properties``
    
    permissions <===> data

    :Example:
        >>> PermissionsFlag(data=bytes.fromhex("0a")).permissions
        ['Write', 'Read']
        >>> PermissionsFlag(permissions=["Write", "Read"]).data
        "0a"

    .. py:method:: dissect()

        Dissect the permissions flag in content

    .. py:method:: build()

        Build the permissions flag in data

.. py:class:: UUID(Dissector)

    This class provides the UUID dissector.
    The uuid can be displayed: ``16-bit``, ``128-bit``, ``Name`` based on ``libs.bt_utils.assigned_numbers.ASSIGNED_NUMBERS``

    name/UUID16/UUID128 in content <===> data

    :Example:
        >>> UUID(data=bytes.fromhex("1800")).name
        "Generic Access"
        >>> UUID(name="Generic Access").data.hex()
        "1800"

    .. py:method:: dissect()

        Dissect the UUID in ``content["UUID16"]``, ``content["UUID128"]`` and ``content["name"]``

    .. py:method:: build()

        Build the UUID in data


.. py:class:: CharacteristicDeclaration(Dissector)

    This class provides the characteristic declaration dissector.
    The characteristic declaration can be displayed: ``UUID``, ``permissionsFlag``, ``valueHandle``

    UUID/permissionsFlag/valueHandle in content <===> data

    :Example:
        >>> CharacteristicDeclaration(data=bytes.fromhex("2a00000302")).valueHandle
        3
        >>> CharacteristicDeclaration(data=bytes.fromhex("2a00000302")).permissionsFlag.permissions
        ['Read']
        >>> CharacteristicDeclaration(UUID("Device Name"), PermissionsFlag(["Read"]), 3).data.hex()
        "2a00000302"

    .. py:method:: dissect()

        Dissect the characteristic declaration in ``content["UUID"]``, ``content["permissionsFlag"]`` and ``content["valueHandle"]``

    .. py:method:: build()

        Build the characteristic declaration in data

.. py:class:: CharacteristicsDescriptor(Dissector)

    This class provides the characteristics descriptor dissector.
    The characteristics descriptor can be displayed: ``UUID``

    UUID content <===> data
    
    :Example:
        >>> CharacteristicsDescriptor(data=bytes.fromhex("2901"))
        "0000"
        >>> CharacteristicsDescriptor(data=bytes.fromhex("2902")).UUID.name
        "Client Characteristic Configuration"
        >>> CharacteristicsDescriptor(UUID("Client Characteristic Configuration"), "0000").data.hex()
        "29020000"

    .. py:method:: dissect()

        Dissect the characteristics descriptor in ``content["UUID"]``

    .. py:method:: build()

        Build the characteristics descriptor in data


.. py:class:: Service(Dissector)

    This class provides the service dissector.
    The service can be displayed: ``UUID``

    UUID/startHandle/endHandle in content <===> data

    :Example:
        >>> Service(data=bytes.fromhex("1800")).UUID
        UUID(128bits:00001800-0000-1000-8000-00805f9b34fb, 16bits:0x1800, name:Generic Access )
        >>> Service(UUID=UUID(UUID16=0x1800)).data.hex()
        "1800"

    .. py:method:: dissect()

        Dissect the service in ``content["UUID"]``

    .. py:method:: build()

        Build the service in data


.. py:class:: InputOutputCapability(Dissector)

    This class provides the input output capability dissector.
    The input output capability can be displayed: ``display``, ``yesno``, ``Keyboard``

    display/yesno/keyboard in content <===> data

    :Example:
        >>> InputOutputCapability(display=True, yesno=False, keyboard=True).data.hex()
        "04"
        >>> InputOutputCapability(data=data=bytes.fromhex("04"))
        Input Output Capability(0x4,keyboard:yes|yesno:no|display:yes)

    .. py:method:: dissect()

        Dissect the input output capability in content

    .. py:method:: build()

        Build the input output capability in data

.. py:class:: AuthReqFlag(Dissector)

    This class provides the authentication request flag dissector.
    The authentication request flag can be displayed: ``bonding``, ``mitm``, ``secureConnections``, ``keypress``, ``ct2``

    bonding/MITM/secureConnections/keypress/CT2 in content <===> data

    :Example:
        >>> AuthReqFlag(bonding=True, mitm=True).data.hex()
        "05"
        >>> AuthReqFlag(data=data=bytes.fromhex("05"))
        AuthReq Flag(0x5,bonding:yes|mitm:yes|secureConnections:no|keypress:no|ct2:no)

    .. py:method:: dissect()

        Dissect the authentication request flag in content

    .. py:method:: build()

        Build the authentication request flag in data

.. py:class:: KeyDistributionFlag(Dissector)

    This class provides the key distribution flag dissector.
    The key distribution flag can be displayed: ``encKey``, ``idKey``, ``signKey``, ``linkKey``

    encKey/idKey/signKey/linkKey in content <===> data

    :Example:
        >>> KeyDistributionFlag(idKey=True,encKey=True).data.hex()
        "03"
        >>> KeyDistributionFlag(data=bytes.fromhex("03"))
        Key Distribution Flag(0x3,encKey:yes|idKey:yes|signKey:no|linkKey:no)

    .. py:method:: dissect()

        Dissect the key distribution flag in content

    .. py:method:: build()

        Build the key distribution flag in data
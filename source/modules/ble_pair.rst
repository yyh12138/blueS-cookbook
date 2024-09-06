ble_pair
==================

.. py:class:: ble_pair(module.WirelessModule)

    .. py:method:: init()

        Initialize the BLE pairing module

        :args:
            - INTERFACE: "hci0"
            - MODE: "master"
            - PIN: "123456"
            - ACTIVATE: "yes"
            - ADDR_TYPE: ""
            - ADDR: ""
            - LTK: ""
            - EDIV: ""
            - RAND: ""
            - IRK: ""
            - CSRK: ""
            - KEYBOARD: "no"
            - YESNO: "no"
            - DISPLAY: "yes"
            - CT2: "no"
            - MITM: "no"
            - BONDING: "no"
            - SECURE_CONNECTIONS: "no"
            - KEYPRESS: "no"

    .. py:method:: pinToTemporaryKey(pin)

        Convert the pin to temporary key

        :param str pin: The pin to convert
        :returns: The temporary key
        :rtype: bytes

    .. py:method:: pairingMethodSelection()

        Select the pairing method by io capabilities

        :returns: The pairing method
        :rtype: str

    .. 
            

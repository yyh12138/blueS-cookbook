ble_replay
===================

.. py:class:: replayPacket(BLEPacket)

    .. py:method:: __init__(packet, source)

        Initialize the replay packet. replayPacket = <packet, source, type>

        :param BLEPacket packet: The BLE packet to replay
        :param str source: The source of the packet. It can be "master" or "slave"


.. py:class:: ble_replay()

    This class provides the BLE device master to restore packets and act replay attacks

    .. py:method:: init()

        Initialize the BLE replay

        :args: 
            - INTERFACE: "hci0"
            - MODE: "master"
            - PIN: "000000"
            - TARGET: ""
            - GCONNECTION_TYPE: "random"
            - ADDR: ""
            - ADDR_TYPE: "random"
            - ADVERTISING_STRATEGY: "preconnect"
            - SHOW_SCANNING: "yes"
            - SCENARIO: ""

    .. py:method:: prerun()

        This method inits the interpreter and regists the CMD, such as ``clear``, ``exit``, ``connect``, ``showPackets``, ``disconnect``, ``replay``, ``exchangeMTURequest``, ``pair_lp``, ``pair_sc``

    .. py:method:: clear()

        Clear the screen

    .. py:method:: exit()

        Exit the BLE replay interpreter

    .. py:method:: disconnect()

        Disconnect the BLE master device

    .. py:method:: connect()

        Connect the BLE master device by excuting ``ble_connect``
    
    .. py:method:: showPackets()

        This method shows the packets from packet buffer

    .. py:method:: replay()

        This method replays the packets from packet buffer

    .. py:method:: exchangeMTURequest(mtu)

        This method sends the exchange MTU request

        :param int mtu: The MTU value

    .. py:method:: pair_lp()

        This method starts pairing by excuting ``ble_pair``

    .. py:method:: pair_sc()

        This method starts pairing by excuting ``ble_sc_pair``

    .. py:method:: run()

        This method inits the BLE replay and enter into interpreter loop

    
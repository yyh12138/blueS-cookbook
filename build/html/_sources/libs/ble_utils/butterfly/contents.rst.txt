butterfly
============

.. py:class:: BLEButterflyDevice(wireless.ButterflyDevice)

    This class represents a BLE Butterfly device, which inherit the ``ButterflyDevice``

    .. py:method:: setAccessAddress(accessAddress)

        :param bytes accessAddress: The access address to set

    .. py:method:: getAccessAddress()

        :return bytes: The access address

    .. py:method:: getCrcInit()

        :return bytes: The CRCInit to set

    .. py:method:: getChannelMap()

        :return bytes: The channel map to set
    
    .. py:method:: getHopInterval()

        :return bytes: The hop interval to set

    .. py:method:: getHopIncrement()

        :return bytes: The hop increment to set

    .. py:method:: setChannel(channel=37)

        :param int channel: The channel to set

    .. py:method:: getChannel()

        This method returns the current channel by ``Butterfly_Get_Channel_Command``

        :return int: The channel

    .. py:method:: setScanInterval(seconds=1)

        :param int seconds: The scan interval to set

    .. py:method:: setScan(enable=True)

        This method starts to sniff advertisements by ``sniffAdvertisements``

        :param bool enable: The scan to set

    .. py:method:: sniffAdvertisements(address, channel)

        This method sniffs advertisements by ``_setChannel(channel)``, ``_setFilter(address)`` and ``_setFollowMode(False)``

        _setChannel runs ``Butterfly_Set_Channel_Command``
        _setFilter runs ``Butterfly_Set_Filter_Command``
        _setFollowMode runs ``Butterfly_Set_Follow_Mode_Command``

        :param bytes address: The address to sniff
        :param int channel: The channel to sniff

    .. py:method:: restartsniffMode()

        This method restarts the sniff mode by ``sniffNewConnections``

    .. py:method:: sniffNewConnections(address, channel)

        This method sniffs new connections by ``_setChannel(channel)``, ``_setFilter(address)`` and ``_setFollowMode(True)``

        _setChannel runs ``Butterfly_Set_Channel_Command``
        _setFilter runs ``Butterfly_Set_Filter_Command``
        _setFollowMode runs ``Butterfly_Set_Follow_Mode_Command``

        :param bytes address: The address to sniff
        :param int channel: The channel to sniff

    .. py:method:: setHijacking(target="master", enable=True)

        This method starts to hijack a connection by ``hijackConnection``.

        If the hijack target is slave, it will inject LL_TERMINATE_IND by ``Butterfly_Start_Attack_Command(0x02)``.

        If the hijeck target is master, it will inject LL_CONNECTION_UPDATE_REQ by ``Butterfly_Start_Attack_Command(0x03)``.

        :param str target: The target to hijack
        :param bool enable: The hijack to set

    .. py:method:: setMitm(enable=True)

        This method starts a MitM attack targeting an established connection. 
        
        It will inject LL_CONNECTION_UPDATE_REQ by ``Butterfly_Start_Attack_Command(0x04)``.

        :param bool enable: The mitm to set

    .. py:method:: getCurrentConnection()

        This method returns the access address, like function ``getAccessAddress``

        :return bytes: The access address

    .. py:method:: isSynchronized()

        This method checks if the device is synchronized

        :return bool: if the device is synchronized

    .. py:method:: recv()

        This method run the ``recv`` method of ``ButterflyDevice``.

        If the received packet is Butterfly_BLE_Packet, it will return the data packet. If it is BTLE_CONNECT_REQ, it will synchronize the new connection.

        If the received packet is Butterfly_Notification_Hdr, it is the notification packet and return None. 

        Notification contains: 

            -  1. connection report: connection lost, attack running, attack success, attack failed 
            -  2. inejct report: inject success, inject failed
            -  3. debug report: debug message

        :return packet: The received data
        :rtype: libs.wireless_utils.packets.Packet

    .. py:method:: send(packet)

        This method send packet to the butterfly. 

        If the packet is payload packet, it will send by ``_internalCommand``.

        If it is synchronized, it will send ``Butterfly_Start_Attack_Command(0x01)`` by ``_injectPacket``.

    .. py:method:: init()

        This method inits the params, set scan interval, select BLE controller and enable it.


.. py:class:: BLEButterflySubDevice(wireless.Device)

    This subDevice is as a software proxy to interact with the butterfly device. 

    We can use only one physical ButteRFly Device to interact with the two roles (master and slave) involved in the targeted connection simultaneously by modified WinOffset and WinSize fields in the LL_CONN_UPDATE_IND.
    
    .. py:method:: __init__(interface)

        This method inits subDevice, like butterfly0:sub0 as master and butterfly0:sub1 as slave.

    .. py:method:: isConnected()

        This method checks if the device is connected

        :return bool: if the device is connected

    .. py:method:: recv()

        This method get packet from packet queue

        :return packet: The received data
        :rtype: libs.wireless_utils.packets.Packet

    .. py:method:: send(packet)

        This method sends playload packet to the butterfly

    .. py:method:: init()

        This method inits the packet queue
    
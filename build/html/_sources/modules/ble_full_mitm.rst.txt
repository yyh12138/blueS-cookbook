ble_full_mitm
===================


.. py:class:: BLEMitmStage(IntEnum)

    This class defines five MITM stages: SCAN, CLONE, WAIT_CONNECTION, ACTIVE_MITM, STOP

.. py:class:: ble_full_mitm

    This class is used to demonstrate the MITM attack on BLE devices. 
    It uses 2 hci sockets, hci0 is used to scan, connect and clone the slave, hci1 is used to advertise and connect to the master

    .. py:method:: init()

        This method initializes the class

        :args:
            - INTERFACE1: "hci0"
            - INTERFACE2: "hci1"
            - TARGET: "xx:xx:xx:xx:xx:xx"
            - CONNECTION_TYPE: "random"
            - SLAVE_SPOFFING: "yes"
            - MITM_STRATEGY: "preconnect"
            - SHOW_SCANNING: "yes"
            - LTK: ""
            - INTERFACE: ""

    .. py:method:: registerEvents()

        This method registers the events and the callback functions

    .. py:method:: run()

    .. py:method:: scanStage(packet)

        This method scans for the target device. 
        If it collects the ADV_IND and SCAN_RSP, it will start the clone stage

        :param packet: The adv packet
        :type packet: libs.ble_utils.packets.Packet.BLEAdvertisement

    .. py:method:: cloneStage(address, data, dataResponse, intervalMin, intervalMax, addrType)

        This method clones the target device on hci1 and sets the advertising parameters to connect to the master

        :param str address: The address of the target device
        :param bytes data: The data of the target device
        :param bytes dataResponse: The data response of the target device
        :param int intervalMin: The minimum interval of the target device
        :param int intervalMax: The maximum interval of the target device
        :param str addrType: The address type of the target device

    .. py:method:: forwardToSlave(packet)

        This method forwards the packets to the slave by hci0

        :param packet: The packet to forward
        :type packet: libs.ble_utils.packets.Packet.BLEPacket

    .. py:method:: forwardToMaster(packet)

        This method forwards the packets to the master by hci1

        :param packet: The packet to forward
        :type packet: libs.ble_utils.packets.Packet.BLEPacket

    .. py:method:: readRequest(packet)

        This method gets the read request from the master and forwards packets to the slave
 
        :param packet: The packet to handle
        :type packet: libs.ble_utils.packets.Packet.BLEReadRequest

    .. py:method:: readRespnse(packet)

        This method gets the read response from the slave and forwards packets to the master

        :param packet: The packet to handle
        :type packet: libs.ble_utils.packets.Packet.BLEReadResponse

    .. py:method:: readByGroupTypeRequest(packet)

        This method gets the read by group type request from the master and forwards packets to the slave

        :param packet: The packet to handle
        :type packet: libs.ble_utils.packets.Packet.BLEReadByGroupTypeRequest

    .. py:method:: readByGroupTypeResponse(packet)

        This method gets the read by group type response from the slave and forwards packets to the master.
        This method should send response to the master with one attribute

        :param packet: The packet to handle
        :type packet: libs.ble_utils.packets.Packet.BLEReadByGroupTypeResponse
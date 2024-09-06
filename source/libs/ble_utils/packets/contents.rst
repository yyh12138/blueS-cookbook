packets
=================

.. py:class:: BLESniffingParameters(wireless.AdditionalInformations)

    This class attach the BLE packets by sniffer

    .. py:method:: __init__(rssi=None, rssi_min=0, rssi_max=0, rssi_avg=0, rssi_count=0, clk_100ns=0, clk_high=0, direction=None, channel=None, frequency=None, rawPacket=None)

        :param float rssi: RSSI value
        :param float rssi_min: Minimum RSSI value
        :param float rssi_max: Maximum RSSI value
        :param float rssi_avg: Average RSSI value
        :param int rssi_count: RSSI count
        :param float clk_100ns: Clock 100ns value
        :param float clk_high: Clock hight value
        :param str direction: Direction of the received packet (``"master->slave"`` or ``"slave->master"``)
        :param int channel: Channel of the received packet
        :param float frequency: Frequency of the received packet
        :param str rawPacket: Raw packet

.. py:class:: BLEPacket(wireless.Packet)

    blues BLE packet. It is the base class for all blues BLE packets

.. py:class:: BLEControlPDU(BLEPacket)

.. py:class:: BLEEncryptedPacket(BLEPacket)

    This class needs to init encrypted data and connection handle

.. py:class:: BLEEmptyPDU(BLEPacket)

.. py:class:: BLEExchangeMTURequest(BLEPacket)

    This class needs to init mtu and connection handle

.. py:class:: BLEExchangeMTUResponse(BLEPacket)

    This class needs to init mtu and connection handle

.. py:class:: BLEConnect(BLEPacket)

    This class needs to init dstAddr, srcAddr, type (responserType), initiatorType

.. py:class:: BLEConnectResponse(BLEPacket)

    This class needs to init dstAddr, srcAddr, type, success, role (role of initiator), interval

.. py:class:: BLEDisconnect(BLEPacket)

    This class needs to connection handle

.. py:class:: BLEConnectionCancel(BLEPacket)

.. py:class:: BLEAdvertisement(BLEPacket)

    This class needs to init addr, type (``ADV_IND``, ...), addrType, data, intervalMin, intervalMax

    .. py:method:: getRawDatas()

        :return: Raw datas
        :rtype: bytes

.. py:class:: BLEAdvInd(BLEAdvertisement)

    This class needs to init addr, addrType, data

.. py:class:: BLEAdvDirectInd(BLEAdvertisement)

.. py:class:: BLEAdvNonConnInd(BLEAdvertisement)

.. py:class:: BLEScanRequest(BLEAdvertisement)

    This class (``SCAN_REQ``) needs to init srcAddr, arcAddrType, dstAddr, dstAddrType

.. py:class:: BLEScanResponse(BLEAdvertisement)

    This class (``SCAN_RSP``) needs to init addr, addrType, data

.. py:class:: BLEConnectRequest(BLEAdvertisement)

    This class (``CONNECT_REQ``) needs to init srcAddr, srcAddrType, dstAddr, dstAddrType, intervalMin, intervalMax, latency, timeout, channelMap, hop, sca

.. py:class:: BLEFindInformationRequest(BLEPacket)

    This class needs to init connection handle, startHandle, endHandle

.. py:class:: BLEFindInformationResponse(BLEPacket)

    This class needs to init connection handle, format, data, attributes

There are many other ble-related classes in the module, but they are not documented here.
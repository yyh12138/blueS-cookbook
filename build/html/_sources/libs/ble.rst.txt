ble
==========

.. py:class:: BLEHCIDevice(bt.BtHCIDevice)

    This class is a device that can communicate with an HCI device to use Bluetooth Low Energy.
    The interface is ``hciX`` where X is the number of the device

    .. py:method:: getCurrentConnectionMode()

        This method return the current connection mode, ``ranodm`` or ``public``

        :return: The current connection mode
        :rtype: str

    .. py:method:: init()

        This method init the bluetooth device by send HCI CMD

    .. py:method:: getMode()
        
        This method return the current mode of bluez.
        There are three mode: ``NORMAL``, ``SCANNING`` and ``ADVERTISING``

        :return: The current mode
        :rtype: str

    .. py:method:: setAddress(address, random=False)

        This method set the BD address of bluez, if possible

        :param str address: New BD address
        :param bool random: If the address is random
        :return: If the address is set
        :rtype: bool

    .. py:method:: setChannelMap(channelMap=0x1fffffffff)

        This method set the channel map of bluez

        :param int channelMap: The new channel map
        :return: If the channel map is set
        :rtype: bool

    .. py:method:: setScan(enable=True, passive=False)

        This method set the scan mode of bluez

        :param bool enable: If the scan is enable
        :param bool passive: If the scan is passive, like no ``SCAN_REQ``
        :return: If the scan is set
        :rtype: bool

    .. py:method:: setAdvertising(enable=True)

        This method set the advertising mode of bluez. 
        You have to set advertising params (:py:meth:: `setAdvertisingParameters`) before advertising

        :param bool enable: If the advertising is enable
        :return: If the advertising is set
        :rtype: bool

    .. py:method:: updateConnectionParameters(minInterval=0, maxInterval=0, latency=0, timeout=0, minCe=0, maxCe=0xFFFF)

        This method update the connection parameters of bluez.
        It is used when bluez receives a ``BLEConnectionParameterUpdateRequest``

        :param int minInterval: The new minimum connection interval
        :param int maxInterval: The new maximum connection interval
        :param int latency: The new connection latency
        :param int timeout: The new connection timeout
        :param int minCe: The new minimum event length
        :param int maxCe: The new maximum event length

    .. py:method:: setScanningParameters(data=b"")

        This method set the scanning parameters of bluez.
        It is used when bluez receives a ``BLEScanRequest``

    .. py:method:: setAdvertisingParameters(type="ADV_IND", destAddr="00:00:00:00:00:00", data=b"", intervalMin=200, intervalMax=210, daType="public", oaType="public")

        This method set the advertising parameters of bluez.
        
        :param str type: The type of advertising
        :param str destAddr: The destination address
        :param bytes data: The advertising data
        :param int intervalMin: The minimum advertising interval
        :param int intervalMax: The maximum advertising interval
        :param str daType: The destination address type (public or random)
        :param str oaType: The origan address type (public or random)

    .. py:method:: getAddressMode()

        This method return the current address mode of bluez, ``random`` or ``public``

        :return: The current address mode
        :rtype: str

    .. py:method:: encryptLink(rand=b"\x00\x00\x00\x00\x00\x00\x00\x00", ediv=0, ltk = b"\x00"*16)

        This method encrypt the link with the given parameters

        :param bytes rand: The random number
        :param int ediv: The EDIV
        :param bytes ltk: The LTK
        :return: If the link is encrypted
        :rtype: bool


.. py:class:: BLEEmitter(wireless.Emitter)

    This class is an emitter that can emit BLE packets

    .. py:method:: __init__(interface="hci0")
        
        This method create a BLE Device as an emitter by interface

        :param str interface: The interface of the device

    .. py:method:: convert(packet)

        This method convert the blues packet to scapy packet

        :param bytes packet: The packet to convert
        :return: The scapy packet
        :rtype: scapy.all.packet


.. py:class:: BLEReceiver(wireless.Receiver)

    This class is a receiver that can receive BLE packets

    .. py:method:: __init__(interface="hci0")
        
        This method create a BLE Device as a receiver by interface

        :param str interface: The interface of the device

    .. py:method:: convert(packet)

        This method convert the scapy packet to blues packet

        :param bytes packet: The packet to convert
        :return: The scapy packet
        :rtype: scapy.all.packet
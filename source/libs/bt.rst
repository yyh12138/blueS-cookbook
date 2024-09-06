bt
=============

.. py:class:: BtHCIDevice(wireless.Device)

    This class is a device that can communicate with an HCI device to use Bluetooth.
    The interface is ``hciX`` where X is the number of the device

    .. py:method:: __init__(interface)

        :param str interface: The interface of the device

    .. py:method:: init()

        This method init the bluetooth device by send HCI CMD

    .. py:method:: _createSocket()

        This method create a bluetooth user socket (from ``scapy.all.BluetoothUserSocket``) to communicate with the HCI device

        :return: If the socket is created
        :rtype: bool
        :raises BluetoothSocketError: If the socket can't be created

    .. py:method:: isUp()

        This method check if the bluetooth device is ready
    
    .. py:method:: send(data)

        This method use socket to send a packet to the HCI device

        :param data: The packet to send
        :type data: scapy cmd packet

    .. py:method:: recv()

        This method use socket to receive a packet from the HCI device

        :return: The packet received
        :rtype: scapy cmd packet
        :raises OSError: If the socket can't find a socket

    .. py:method:: _internalCommand(cmd, noResponse=False)

        This method send a command to the HCI device and wait for the response

        :param cmd: The command to send
        :type cmd: scapy cmd packet
        :param bool noResponse: If the command don't need a response
        :return: The response
        :rtype: scapy cmd packet
        :raises BluetoothCommandError: If the response is an error

    .. py:method:: getCurrentHandle()

        This method return the current handle.
        If no connection is established, it will return -1

        :return: The current handle
        :rtype: int

    .. py:method:: getConnections()

        This method returns a list of couple, like (handle, address) for the current connections

        :return: The list of connections' info
        :rtype: list
        :Example:
            >>> device.getConnections()
            [{'handle': 0, 'address': '00:11:22:33:44:55'}, {'handle': 1, 'address': '00:11:22:33:44:56'}]

    .. py:method:: getAddressByHandle(handle)
        
        This method returns the address of the device with the given handle

        :param int handle: The handle of the device
        :return: The address of the device
        :rtype: str

    .. py:method:: getCurrentConnection()

        This method returns the address of the device with the current handle

        :return: The address of the device
        :rtype: str

    .. py:method:: switchConnection(address)

        This method switch the current connection to the device with the given address

        :param str address: The address of the device
        :return: If the switch is successful
        :rtype: bool

    .. py:method:: isConnected()

        This method returns if the device is connected

        :return: If the device is connected
        :rtype: bool

    .. py:method:: setLocalName(name)

        This method set the local name of the HCI device

        :param str name: The name to set
        :return: If the name is set
        :rtype: bool

    .. py:method:: getLocalName()

        This method returns the local name of the HCI device

        :return: The local name
        :rtype: str

    .. py:method:: getManufacturer()

        This method returns the manufacturer of the HCI device

        :return: The manufacturer
        :rtype: str

    .. py:method:: isAddressChangeable()

        This method returns if the address of the HCI device can be changed

        :return: If the address can be changed
        :rtype: bool

    .. py:method:: getAddress()

        This method returns the address of the HCI device

        :return: The address
        :rtype: str

    .. py:method:: setAddress(address)

        This method set the BD address, if possible

        :param str address: New BD address
        :return: If the address is set
        :rtype: bool
        :Example:
            >>> device.setAddress('00:11:22:33:44:55')
            [INFO] Changing HCI Device (hci0) Address to: 00:11:22:33:44:55
            [SUCCESS] BD Address successfully modified !
            True
            >>> device.getAddress()
            '00:11:22:33:44:55'


.. py:class:: BluetoothEmitter(wireless.Emitter)

    This class is an emitter for the bluetooth. 
    It can instantiate a HCI device

    .. py:method:: __init__(interface="hci0")

        :param str interface: The interface of the device

    .. py:method:: convert(p)

        This method convert a blues packet to a scapy packet

        :param p: The packet to convert
        :type p: libs.wireless_utils.packets.Packet


.. py:class:: BluetoothReceiver(wireless.Receiver)

    This class is a receiver for the bluetooth. 
    It can instantiate a HCI device

    .. py:method:: __init__(interface="hci0")

        :param str interface: The interface of the device

    .. py:method:: convert(p)

        This method convert a scapy packet to a blues packet

        :param p: The packet to convert
        :type p: scapy.all.packet

    .. py:method:: stop()

        This method stop the receiver
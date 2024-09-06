ble_discover
===================

.. py:class:: ble_discover(module.WirelessModule)

    This class provides the BLE discovery

    .. py:method:: init()

        Initialize the BLE discovery

        :args: 
            - INTERFACE: "hci0"
            - START_HANDLE: "0X0001"
            - END_HANDLE: "0xFFFF"
            - WHAT: "all"
            - FILTER: ""
            - FILTER_BY: ""
            - ATT_FILE: ""
            - GATT_FILE: "/tmp/gatt.cfg"
    
    .. py:method:: checkCapabilities()

        Check the capabilities of the BLE discovery by using ``libs.wireless_utils.device.Device.hasCapabilities()``

        :returns: If the BLE discovery is supported
        :rtype: bool

    .. py:method:: exportAttributes(attributes)

        Export the attributes of the BLE discovery and write in file
        :param dict attributes: The attributes to export

    .. py:method:: exportGATT(datas)

        Export the GATT datas of the BLE discovery and write in file
        :param dict datas: The GATT datas to export

    .. py:method:: receive(types, retry=None)

        This method receives the blues packets from queue by using ``libs.wireless.Receiver.next()``

        :param list types: The types of the packets to receive
        :param int retry: The number of retry to receive the packets
        :returns: The received packets
        :rtype: libs.wireless_utils.packets.Packet

    .. py:method:: serviceToString(service)

        Convert the service to string

        :param dict service: The service to convert
        :returns: The service converted
        :rtype: str

    .. py:method:: servicesDiscovery(uuid, startHandle=0x0001, endHandle=0xFFFF)

        Discover the services

        :param str uuid: The UUID of the services to discover
        :param int startHandle: The start handle of the services to discover
        :param int endHandle: The end handle of the services to discover
        :returns: The discovered services
        :rtype: list of services (``libs.ble_utils.dissectors.Service``)

    .. py:method:: allServicesDiscovery(startHandle=0x0001, endHandle=0xFFFF)

        Discover all the services by running primary services and secondary services discovery function

        :param int startHandle: The start handle of the services to discover
        :param int endHandle: The end handle of the services to discover
        :returns: The discovered services
        :rtype: list of services (``libs.ble_utils.dissectors.Service``)

    .. py:method:: characteristicsDiscovery(startHandle=0x0001, endHandle=0xFFFF)

        Discover the characteristics

        :param int startHandle: The start handle of the characteristics to discover
        :param int endHandle: The end handle of the characteristics to discover
        :returns: The discovered characteristics
        :rtype: list of dict (values like ``libs.ble_utils.dissectors.CharacteristicDeclaration``...)

    .. py:method:: attributesDiscovery(startHandle=0x0001, endHandle=0xFFFF)

        Discover the attributes

        :param int startHandle: The start handle of the attributes to discover
        :param int endHandle: The end handle of the attributes to discover
        :returns: The discovered attributes
        :rtype: list of dict
    
    .. py:method:: characteristicDescriptorDiscovery(startHandle=0x0001, endHandle=0xFFFF)

        Discover the characteristics descriptors

        :param int startHandle: The start handle of the characteristics descriptors to discover
        :param int endHandle: The end handle of the characteristics descriptors to discover
        :returns: The discovered characteristics descriptors
        :rtype: list of dict (values like ``libs.ble_utils.dissectors.CharacteristicsDescriptor``...)

    .. py:method:: printCharacteristics(characteristics, title="Characteristics")


    .. py:method:: applyFilter(attributes)

        Apply the filter on the attributes. The ``FILTER_BY`` is used to filter the attributes (``type`` or ``value``)

        :param list attributes: The attributes to filter
        :returns: The filtered attributes
        :rtype: list of dict

    .. py:method:: run()

        Run the BLE discovery

        :returns: If the BLE discovery is ok, see ``core.module.Module.ok()``
        :rtype: dict
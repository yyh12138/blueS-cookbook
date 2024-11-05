ble_sniff
===================

.. py:class:: ble_sniff(module.WirelessModule)

    This class provides the BLE device as a sniffer. It can jam[not realized], sniff(sniff advertisements, sniff connection[not realized]) and hijack.

    .. py:method:: init()

        Initialize the BLE sniffer

        :args: 
            - INTERFACE: "butterfly0"
            - INTERFACEA: ""
            - INTERFACEB: ""
            - SNIFFING_MODE: "newConnections"
            - TARGET: ""
            - CHANNEL: "37"
            - HIJACKING_MASTER: "no"
            - HIJACKING_SLAVE: "yes"
            - ACCESS_ADDRESS: ""
            - CRC_INIT: ""
            - CHANNEL_MAP: ""
            - LTK: ""
            - SCENARIO: ""

    .. py:method:: onPacket(packet)

        This method displays the packet

    .. py:method:: run()

        This method inits the emitter and receiver, checks the capabilities of the inerface.
        Finally, it enters the sniffing mode: ``existingConnections``, ``newConnections`` or ``advertisements``

    .. py:method:: sniffNewConnections(target, channel)

        This method sniffs new connections in channel 36, 37 or 38 by ``sniffNewConnections`` function from nRF52840Dongle.
        When the receiver is synchronized, it will hijack slave by ``setHijacking`` function from nRF52840Dongle.

        :param str target: the target address
        :param str channel: the channel number

    .. py:method:: sniffExistingConnections(receiver, accessAddress, crcInit, channelMap)

        This method can set jamming by ``setJamming`` function or not, and calls ``sniffExistingConnections`` function from Ubertooth One.

        :param receiver: the receiver
        :type receiver: libs.ble_utils.butterfly.BLEButterflyDevice

    .. py:method:: sniffAdvertisements(target, channel)

        This method sniffs advertisements in channels by ``sniffAdvertisements`` function from nRF52840Dongle

        :param str target: the target address
        :param str channel: the channel number




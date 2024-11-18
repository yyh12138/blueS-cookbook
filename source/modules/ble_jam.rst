ble_jam
================

.. py:class:: ble_jam(module.WirelessModule)

    This class jam the BLE connection

    .. py:method:: init()

        This method will initialize the BLE jam module.
        JAMMING_MODE is in ``advertisements``, ``newConnections``, ``existingConnections``

        :args:
            - INTERFACE: "butterfly0"
            - TARGET: ""
            - CHANNEL: "37"
            - JAMMING_MODE: "advertisements"
            - ACCESS_ADDRESS: ""
            - CRC_INIT: ""

    .. py:method:: run()

        This method will start the BLE jam module by excuting ``ble_sniff``

    .. py:method:: jamAdvertisements()

        This method uses emiter's jamAdvertisements to jam the channel by ``JAMMING_MODE``="advertisements" 

    .. py:method:: jamNewConnections()

        This method excutes ``ble_sniff`` by ``JAMMING``=yes,  ``HIJACKING``=no, ``SNIFFING_MODE``="newConnections"

    .. py:method:: jamExistingConnections()

        This method excutes ``ble_sniff`` by ``JAMMING``=yes,  ``HIJACKING``=no, ``SNIFFING_MODE``="existingConnections"
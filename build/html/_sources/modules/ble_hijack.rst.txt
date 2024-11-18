ble_hijack
==============
.. py:class:: ble_hijack(module.WirelessModule)

    This class hijack the BLE connection

    .. py:method:: init()

        This method will initialize the BLE hijack module

        :args:
            - INTERFACE: "butterfly0"
            - TARGET: ""
            - CHANNEL: "37"
            - HIJACKING_MODE: "newConnections"
            - ROLE: "slave"
            - ACCESS_ADDRESS: ""
            - CRC_INIT: ""

    .. py:method:: run()

        This method will start the BLE hijack module by excuting ``ble_sniff`` with ``HIJACKING_SLAVE``=yes, ``JAMMING``=no


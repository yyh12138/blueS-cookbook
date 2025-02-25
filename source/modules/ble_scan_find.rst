ble_scan_find
================

.. py:class:: ble_scan_find(module.WirelessModule)

    This class scans the BLE device and return immediately if find

    .. py:method:: init()

        This method will initialize the BLE module.

        :args:
            - INTERFACE: "hci0"
            - MASTER_TYPE: "random"
            - TARGET: ""
            - SLAVE_TYPE: "random"
            - DURATION: "400"
    
    .. py:method:: run()

        This method receive all advertisement and filter the BD address, return when find
ble_disconnect
================

.. py:class:: ble_disconnect(module.WirelessModule)

    This class disconnect the BLE device

    .. py:method:: init()

        This method will initialize the BLE module.

        :args:
            - INTERFACE: "hci0"
            - TARGET: ""
            - SLAVE_TYPE: "random"
    
    .. py:method:: run()

        This method sens the disconnect command to the BLE device
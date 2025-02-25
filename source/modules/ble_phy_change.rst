ble_phy_change
================

.. py:class:: ble_phy_change(module.WirelessModule)

    This class changes the PHY of the BLE connection.

    .. py:method:: init()

        This method will initialize the BLE module.

        ``PART`` has 4 options: "timeout", "length", "chm", "interval"

        :args:
            - INTERFACE: "hci0"
            - MASTER_TYPE: "random"
            - TARGET: ""
            - SLAVE_TYPE: "random"
    
    .. py:method:: run()

        This method runs ``Sweyntooth`` changePHY function
ble_pkt_fuzz
================

.. py:class:: ble_pkt_fuzz(module.WirelessModule)

    This class fuzzes packets and see how many packets can be affected

    .. py:method:: init()

        This method will initialize the BLE module.

        ``PART`` has 4 options: "timeout", "length", "chm", "interval"

        :args:
            - INTERFACE: "sweyntooth"
            - MASTER_TYPE: "random"
            - TARGET: ""
            - SLAVE_TYPE: "random"
            - SUSTAINABLE: "100"
    
    .. py:method:: run()

        This method runs ``Sweyntooth`` fuzzPackets function
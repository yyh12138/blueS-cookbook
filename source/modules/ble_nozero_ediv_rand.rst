ble_nozero_ediv_rand
==========================
.. py:class:: ble_nozero_ediv_rand(module.WirelessModule)

    This class will send a recryption start request with a non-zero ediv and a rand. And it uses the pairing module

    .. py:method:: init()

        This method will initialize the BLE nozero ediv rand module.

        :args:
            - INTERFACE: "hci0"
            - ACTIVATE: "yes"
            - ADDR_TYPE: "random"
            - TARGET: ""
            - CONNECTION_TYPE: "random"


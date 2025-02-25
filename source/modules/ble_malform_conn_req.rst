ble_malform_conn_req
================

.. py:class:: ble_malform_conn_req(module.WirelessModule)

    This class sends malform connection request by well-designed

    .. py:method:: init()

        This method will initialize the BLE module.

        ``PART`` has 4 options: "timeout", "length", "chm", "interval"

        :args:
            - INTERFACE: "sweyntooth"
            - MASTER_TYPE: "random"
            - TARGET: ""
            - SLAVE_TYPE: "random"
            - PART: "timeout"
    
    .. py:method:: run()

        This method runs ``Sweyntooth`` malformConnRequest function
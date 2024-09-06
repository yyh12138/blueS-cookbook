ble_connect
===========

.. py:class:: ble_connect(module.WirelessModule)

    This class provides the BLE connection

    .. py:method:: init()

        Initialize the BLE connection

        :args: 
            - INTERFACE: "hci0"
            - TARGET: "xx:xx:xx:xx:xx:xx"
            - CONNECTION_TYPE: "public"
            - TIMEOUT: "10"
    
    .. py:method:: checkCapabilities()

        Check the capabilities of the BLE connection by using ``libs.wireless_utils.device.Device.hasCapabilities()``

        :returns: If the BLE connection is supported
        :rtype: bool

    .. py:method:: run()

        Run the BLE connection

        :returns: If the BLE connection is ok, see ``core.module.Module.ok()``
        :rtype: dict
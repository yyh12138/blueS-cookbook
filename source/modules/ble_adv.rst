ble_adv
===========

.. py:class:: ble_adv(module.WirelessModule)

    This class provides the BLE advertising

    .. py:method:: init()

        Initialize the BLE advertising

        :args: 
            - INTERFACE: "hci0"
            - ADVERTISING_TYPE: "ADV_IND"
            - ADVERTISING_DATA: ""
            - SCANNING_DATA: ""
            - ADVERTISING_ADDRESS: ""
            - DESTINATION_ADDRESS: ""
            - ADVERTISING_ADDRESS_TYPE: "public"
            - DESTINATION_ADDRESS_TYPE: "public"
            - INTERNAL_MIN: "200"
            - INTERNAL_MAX: "210"
            - ENABLE: "yes"
            - TIME: "0"
    
    .. py:method:: checkCapabilities()

        Check the capabilities of the BLE advertising by using ``libs.wireless_utils.device.Device.hasCapabilities()``

        :returns: If the BLE advertising is supported
        :rtype: bool

    .. py:method:: run()

        Run the BLE advertising

        :returns: If the BLE advertising is ok, see ``core.module.Module.ok()``
        :rtype: dict
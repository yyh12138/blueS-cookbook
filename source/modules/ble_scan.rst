ble_scan
=============

.. py:class:: ble_scan(module.WirelessModule)

    This class provides the BLE scan

    .. py:method:: init()

        Initialize the BLE scan

        :args: 
            - INTERFACE: "hci0"
            - TARGET: ""
            - TIMEOUT: "10"
            - DISPLAY: "address, name, company, flags, data"

    .. py:method:: checkCapabilities()

        Check the capabilities of the BLE connection by using ``libs.wireless_utils.device.Device.hasCapabilities()``

        :returns: If the BLE connection is supported
        :rtype: bool

    .. py:method:: scan(packet)

        If the packet is ``SCAN_RSP`` or ``SCAN_IND``, put the packet instance in the queue

    .. py:method:: updateDevices()

        This method updates the devices list and display

    .. py:method:: displayDevices()

        Display the devices list, label is in ``address``, ``name``, ``company``, ``flags``, ``data``

    .. py:method:: run()

        Run the BLE scan

        :returns: If the BLE connection is ok, see ``core.module.Module.ok()``
        :rtype: dict

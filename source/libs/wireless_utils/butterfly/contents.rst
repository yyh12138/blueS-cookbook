butterfly
=============

.. py:class:: ButterflyDevice(wireless.Device)

    This device is used to sniff, jam and inject BLE. 
    The interface is ``butterflyX``, it is same like ``hciX``

    .. py:method:: __init__(self, interface)

        :param str interface: The name of the device, like butterfly0

    .. py:method:: isUp()

        This method checks if the device is up.

        :return bool: if the device is up

    .. py:method:: init()

        This method initializes the device.
    
    .. py:method:: send(command)

        This method sends a command by ``write`` in ``NRF_DRV_USBD_EPOUT1`` and return the ``Butterfly_Message`` by ``read`` in ``NRF_DRV_USBD_EPIN1``
    
    .. py:method:: recv()

        This method returns the ``Butterfly_Message`` by ``read`` in ``NRF_DRV_USBD_EPIN1``

    .. py:method:: close()

        This method disables the controller by sending a ``Bufferfly_Disable_Controller_Command``

    .. py:method:: getFirmwareVersion()

        This method returns the firmware version by sending a ``Bufferfly_Get_Firmware_Version_Command``
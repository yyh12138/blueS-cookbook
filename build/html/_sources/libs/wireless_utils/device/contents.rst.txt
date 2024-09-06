device
=========

.. py:class:: Device

    This class communicates with a hardware device.
    Each device must inherit from this class, and implement the following methods: 
    :py:meth:`init()`, :py:meth:`isUp()`, :py:meth:`send(packet)`, :py:meth:`recv()`, :py:meth:`close()`.

    Each device has a unique name, which is a string stored in ``INTERFACE`` attribute

    .. py:method:: __init__(self, interface)

        :param str interface: The name of the device

    .. py:method:: get(cls, interface)

        This method returns the only one instance with the given name

        :param str interface: The name of the device
        :return Device: The device with the given name
        :rtype: Device

    .. py:method:: subscribe(subscriber)

        This method registers a subscribing function to the device

        :param function subscriber: The subscribing function

    .. py:method:: publish(event, *args, **kwargs)

        This method publishes an event, if the emitter/receiver subscribe and implements the event 

        :param str event: The name of the event
        :param str args: The unamed arguments of the event
        :param dict kwargs: The named arguments of the event

    .. py:method:: hasCapabilities(*capability)

        This method checks if the device has the given capabilities

        :param str *capability: The name of the capability
        :return bool: if the device has the given capabilities
        :Example:
            >>> device.capabilities = ['SNIFFING', 'CHANGING_ADDRESS', 'CONNECTING']
            >>> device.hasCapabilities('SNIFFING', 'CHANGING_ADDRESS')
            True
        
    .. py:method:: isUp()

        This method checks if the device is up.
        It must be implemented by the child class

        :return bool: if the device is up

    .. py:method:: init()

        This method initializes the device.
        It must be implemented by the child class

    .. py:method:: send(data)

        This method sends data to the device.
        It must be implemented by the child class

        :param bytes data: The data to send

    .. py:method:: recv()

        This method receives data from the device.
        It must be implemented by the child class

        :return bytes: The received data

    .. py:method:: close()

        This method closes the device.
        It must be implemented by the child class


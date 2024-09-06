wireless
========

.. py:class:: Emitter(PacketQueue)

    This class allows user to send data (``blues.libs.wireless_utils.packets.Packet``). 
    It is an abstract class which must implement the ``convert(packet)`` method. 
    The method converts a blues packet to a raw packet.

    .. py:method:: __init__(interface, packetType=Packet, deviceType=Device)

        This constructor inits an emitter

        :param str interface: the interface to use
        :param packetType: the packet type to use
        :type packetType: blues.libs.wireless_utils.packets.Packet
        :param deviceType: the device type to use
        :type deviceType: blues.libs.wireless_utils.device.Device

    .. py:method:: isTransmitting()

        This method returns True if the emitter is transmitting, False otherwise.

        :return: If the emitter is isTransmitting
        :rtype: bool

    .. py:method:: convert(packet)

        This method converts a blues packet to a raw packet.
        It must be overloaded by the child class

        :param packet: the packet to convert
        :type packet: blues.libs.wireless_utils.packets.Packet
        :return: the raw packet
        :rtype: bytes

    .. py:method:: convertBluesPacketToRaw(data)

        This method is an alias for the ``convert`` method.

        :param packet: the packet to convert
        :type packet: blues.libs.wireless_utils.packets.Packet
        :return: the raw packet
        :rtype: bytes

    .. py:method:: _task()

        This method implements by default.
        It gets a blues packet from the queue and uses ``Device`` to send

    .. py:method:: send(*packets)

        This method sends a blues packet or a list

        :param *packets: the packet(s) to send
        :type *packets: blues.libs.wireless_utils.packets.Packet

    .. py:method:: sendp(*packets)

        This method is an alias for the ``send`` method.

    .. py:method:: stop()

        This method stops the emitter and close the device

.. py:class:: Receiver(PacketQueue)

    This class allows user to receive data (``blues.libs.wireless_utils.packets.Packet``).
    It is an abstract class which must implement the ``convert(packet)`` method.
    The method converts a raw packet to a blues packet

    .. py:method:: __init__(interface, packetType=Packet, deviceType=Device)

        This constructor inits a receiver

        :param str interface: the interface to use
        :param packetType: the packet type to use
        :type packetType: blues.libs.wireless_utils.packets.Packet
        :param deviceType: the device type to use
        :type deviceType: blues.libs.wireless_utils.device.Device

    .. py:method:: isReceiving()

        This method returns True if the receiver is receiving.

        :return: If the receiver is isReceiving
        :rtype: bool

    .. py:method:: convert(data)

        This method converts a raw packet to a blues packet.
        It must be overloaded by the child class

        :param data: the raw packet to convert
        :type data: bytes
        :return: the packet
        :rtype: blues.libs.wireless_utils.packets.Packet

    .. py:method:: convertRawToBluesPacket(data)

        This method is an alias for the ``convert`` method.

        :param data: the raw packet to convert
        :type data: bytes
        :return: the packet
        :rtype: blues.libs.wireless_utils.packets.Packet

    .. py:method:: _task()

        This method implements by default, like a watchdog.
        It gets a raw packet from the device, converts it to a blues packet and puts it in the queue

    .. py:method:: skip(timeout=None)

        This method skips the receiver for a given time

        :param float timeout: the time to skip

    .. py:method:: clean()

        This method cleans the blues packets in queue

    .. py:method:: next(timeout=None)

        This method returns the next blues packet in queue

        :param float timeout: the time to wait
        :return: the next packets
        :rtype: blues.libs.wireless_utils.packets.Packet

    .. py:method:: recvive(nb=1, loop=False, timeout=None)

        This method provides an iterator to receive blues packets in queue

        :param int nb: the number of packets to receive
        :param bool loop: if True, the method will loop until the number of packets is received
        :param float timeout: the time to wait
        :return: the blues packets
        :rtype: blues.libs.wireless_utils.packets.Packet


    .. py:method:: onEvent(event="*", callback=None, args=[], kwargs={}, background=True)

        This method attach a callback to an reveiving event, triggered when receive some special blues packets 

        :param str event: the format how the event received
        :Example(event):
            - *\**: each packet received will trigger the callback
            - *n*: every n packets received will trigger the callback
            - *packetType*: each ``packetType`` received will trigger the callback
        :param function callback: the callback to attach
        :param list args: the unamed arguments to pass to the callback
        :param dict kwargs: the named arguments to pass to the callback
        :param bool background: if True, the callback will be executed in background
        
        :Example:
            def show(packet, value):
                io.info("The receiving packet: " + packet)
                io.info("The value: " + value)
            >>> receiver.onEvent("BLEConnectRequest", callback=show, args=["yyy"]) # show the packet and value when a BLEConnectRequest received

    .. py:method:: stop()

        This method stops the receiver and close the device
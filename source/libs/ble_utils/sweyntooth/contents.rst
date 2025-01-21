sweyntooth
============

.. py:class:: SweyntoothDevice(wireless.Device)

    This class represents a BLE device by Sweyntooth, which inherit the ``Device``

    .. py:method:: setAccessAddress(accessAddress)

        :param bytes accessAddress: The access address to set

    .. py:method:: getAccessAddress()

        :return bytes: The access address

    .. py:method:: set_nesnsn(value)

        :param bytes value: nesn & sn value to set

    .. py:method:: recv()

        This method receives the packet by ``_recv``

        :return bytes: The packet

    .. py:method:: send(packet)

        This method sends the packet by ``_send``

        :param bytes packet: The packet to send

    .. py:method:: connection(slaveAddr, masterAddrType="random", running=100)

        This method connects to the device

        :param string slaveAddr: The slave address to connect
        :param str masterAddrType: The master address type to connect
        :param int running: The running times to connect

    .. py:method:: fuzzPackets(slaveAddr, masterAddrType="random", running=100)

        This method fuzzes packets and sends to the connection device

        :param string slaveAddr: The slave address to fuzz
        :param str masterAddrType: The master address type to fuzz
        :param int running: The running times to fuzz
    
    .. py:method:: malformConnRequest(slaveAddr, masterAddrType="random", running=50, part="length")

        This method malforms connection request packets and tries to connect

        :param string slaveAddr: The slave address to malform
        :param str masterAddrType: The master address type to malform
        :param int running: The running times to malform
        :param str part: The part to malform, such as length, interval, timeout, chM

    .. py:method:: readATTOverfloe(slaveAddr, masterAddrType="random", running=50)

        This method reads ATT overflow packets and tries to connect

        :param string slaveAddr: The slave address to read
        :param str masterAddrType: The master address type to read
        :param int running: The running times to read

    .. py:method:: mutipleVersions(slaveAddr, masterAddrType="random", running=50)

        This method sends multiple versions packets to the connection device

        :param string slaveAddr: The slave address to send
        :param str masterAddrType: The master address type to send
        :param int running: The running times to send

    .. py:method:: packetLengthChange(slaveAddr, masterAddrType="random", running=50, length=10)

        This method changes the packet length and sends to the connection device

        :param string slaveAddr: The slave address to change
        :param str masterAddrType: The master address type to change
        :param int running: The running times to change

    .. py:method:: invalidSequence(slaveAddr, masterAddrType="random", running=200)

        This method sends mutiple packets while inits the anchor point to the connection device

        :param string slaveAddr: The slave address to send
        :param str masterAddrType: The master address type to send
        :param int running: The running times to send

    .. py:method:: changePHY(slaveAddr, masterAddrType="random", running=50)

        This method changes the PHY and sends to the connection device

        :param string slaveAddr: The slave address to change
        :param str masterAddrType: The master address type to change
        :param int running: The running times to change
    
ble_pair
==================

.. py:class:: ble_pair(module.WirelessModule)

    This class provides the BLE LP pairing

    .. py:method:: init()

        Initialize the BLE pairing module

        :args:
            - INTERFACE: "hci0"
            - MODE: "master"
            - PIN: "123456"
            - ACTIVATE: "yes"
            - ADDR_TYPE: ""
            - ADDR: ""
            - LTK: ""
            - EDIV: ""
            - RAND: ""
            - IRK: ""
            - CSRK: ""
            - KEYBOARD: "no"
            - YESNO: "no"
            - DISPLAY: "yes"
            - CT2: "no"
            - MITM: "no"
            - BONDING: "no"
            - SECURE_CONNECTIONS: "no"
            - KEYPRESS: "no"

    .. py:method:: pinToTemporaryKey(pin)

        Convert the pin to temporary key

        :param str pin: The pin to convert
        :returns: The temporary key
        :rtype: bytes

    .. py:method:: pairingMethodSelection()

        Select the pairing method by io capabilities

        :returns: The pairing method
        :rtype: str

    .. py:method:: slavePairingFailed(pkt)

        If the pairing failed, print the error

        :param pkt: The blues packet
        :type pkt: libs.ble_utils.packet.Packet

    .. py:method:: slavePairingRequest(pkt)

        This method sends the master pairing request

    .. py:method:: slavePairingResponse(pkt)

        This method chooses pairing method and generate the master random and TK

    .. py:method:: slavePairingConfirm(pkt)

        This method sends master pairing random pkt

    .. py:method:: slavePairingRandom(pkt)

        This method checks the slave confirm and generates LTK

    .. py:method:: slaveEncryptionInformation(pkt)

        This method print LTK received

    .. py:method:: slaveMasterIdentification(pkt)

        This method print EDIV and RAND received

    .. py:method:: slaveIdentityInformation(pkt)

        This method print IRK received

    .. py:method:: slaveIdentityAddressInformation(pkt)

        This method print address received

    .. py:method:: slaveSigningInformation(pkt)

        This method print CSRK received
            
    .. py:method:: keyDistribution(type="initiator")

        This method sends key: ``LTK``, ``IRK``, ``CSRK``

        :param: str type: The role distributes the keys

    .. py:method:: run()

        Run the LP pairing

        :returns: If the BLE connection is ok, see ``core.module.Module.ok()``
        :rtype: dict

ble_sc_pair
===================

.. py:class:: ble_sc_pair(module.WirelessModule)

    This class implements the BLE Secure Connections Pairing feature

    .. py:method:: init()

        This method initializes the BLE Secure Connections Pairing feature

        :args:
            - INTERFACE: "hci0"
            - MODE: "master"
            - PIN: "000000"
            - ACTIVE: "yes"
            - ADDR_TYPE: "public"
            - ADDR: ""
            - KEYBOARD: "no"
            - YESNO: "no"
            - DISPLAY: "yes"
            - CT2: "no"
            - MITM: "no"
            - BONDING: "no"
            - KEYPRESS: "no"
            - TARGET: ""
            - CONNECTION_TYPE: "random"

    .. py:method:: run()

        This method runs the BLE Secure Connections Pairing feature before ``ble_connect``

    .. py:method:: pairingMethodSelection()

        This method selects the pairing method by devices IO capabilities and print

    .. py:method:: slaveSecurityRequest(pkt)

        This method receives the security request from slave and sends security request to master

    .. py:method:: slavePairingResponse(pkt)

        This method receives the pairing response from slave and sends public key to master

    .. py:method:: slavePublicKey(pkt)

        This method receives the public key from slave and sends confirm to master if pairing method is PasskeyEntry

    .. py:method:: slavePairingConfirm(pkt)

        This methods receives the confirm from slave and sends random to master.
        It generates Nonce

    .. py:method:: slavePairingRandom(pkt)

        This method receives the random from slave and verify confirm value.
        It sends DHKeyCheck

    .. py:method:: slavePairingDHKeyCheck(pkt)

        This method receives the DHKeyCheck from slave and verify DHKey.
        It sends start encryption.

    .. py:method:: slavePairingFailed(pkt)

        This method print the error if the pairing failed

    .. py:method:: slaveIdentityInformation(pkt)

        This method print IRK received

    .. py:method:: slaveIdentityAddressInformation(pkt)

        This method print address received

    .. py:method:: slaveSigningInformation(pkt)

        This method print CSRK received

    .. py:method:: slaveKeyEncryptionChange(pkt)

        This method means encryption finished successfully
            
    .. py:method:: keyDistribution(type="initiator")

        This method sends key: ``IRK``, ``CSRK``

        :param: str type: The role distributes the keys


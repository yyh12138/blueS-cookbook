crypto
============

.. py:class:: BLECrypto

    This class provides a set of cryptographic functions that are used in the BLE protocol.

    .. py:method:: crackTemporaryKey(r,  preq, pres, iat, initiatorAddress, rat, responderAddress, confirm)

        This method calculates the temporary key that is used in the pairing process.

        :param bytes r: Random number
        :param bytes preq: Pairing request
        :param bytes pres: Pairing response
        :param bytes iat: Initiator address type
        :param str initiatorAddress: Initiator address
        :param bytes rat: Responder address type
        :param str responderAddress: Responder address
        :param bytes confirm: Confirm value
        :return: PIN code
        :rtype: int

        :Example:
            >>> random = bytes.fromhex("abb692ebfd4601f4aad3aea40f7da5fc")[::-1]
			>>> pairingRequest = bytes.fromhex("01030005100001")[::-1]
			>>> pairingResponse = bytes.fromhex("02000005100001")[::-1]
			>>> initiatorAddress = "08:3E:8E:E1:0B:3E"
			>>> initiatorAddressType = b"\x00"
			>>> responderAddress = "78:C5:E5:6E:DD:E8"
			>>> responderAddressType = b"\x00"
			>>> confirm = bytes.fromhex("febb983ed78020e13d685bc8418d2c5d")[::-1]
			>>> BLECrypto.crackTemporaryKey(random,pairingRequest,pairingResponse, initiatorAddressType,initiatorAddress,responderAddressType,responderAddress,confirm)
			0

    .. py:method:: generateRandom(size=16)

        This method generates a random number of a given size.

        :param int size: Size of the random number
        :return: Random number
        :rtype: bytes

        :Example:
            >>> BLECrypto.generateRandom(3).hex()
            'e7bbc9'

    .. py:method:: e(key, plaintext)

        This method encrypts a plaintext using a key, implements the security function :math: `E`

        :param bytes key: encrypted key
        :param bytes plaintext: Plaintext
        :return: Encrypted text
        :rtype: bytes

    .. py:method:: em1(key, ciphertext)

        This method encrypts a plaintext using a key, implements the security function :math: `E_{-1}`

        :param bytes key: encrypted key
        :param bytes ciphertext: encrypted text
        :return: Decrypted text
        :rtype: bytes

    .. py:method:: s1(key, randMaster, randSlave)

        This method implements the security function :math: `S1`

        :param bytes key: encrypted key
        :param bytes randMaster: Random number of the master
        :param bytes randSlave: Random number of the slave
        :return: generated text
        :rtype: bytes

    .. py:method:: c1(key, rand, payloadRequest, payloadResponse, initiatorAddressType, initiatorAddress, responderAddressType, responderAddress)

        This method implements the security function :math: `C1`

        :param bytes key: encrypted key
        :param bytes rand: Random number
        :param bytes payloadRequest: Payload request
        :param bytes payloadResponse: Payload response
        :param bytes initiatorAddressType: Initiator address type, b"\x00" for public address and b"\x01" for random address
        :param str initiatorAddress: Initiator address
        :param bytes responderAddressType: Responder address type
        :param str responderAddress: Responder address
        :return: generated confirm value
        :rtype: bytes

    ..py:method:: c1m1(key, rand, payloadRequest, payloadResponse, initiatorAddressType, initiatorAddress, responderAddressType, responderAddress)

        This method implements the security function :math: `C1_{-1}`

        :param bytes key: encrypted key
        :param bytes rand: Random number
        :param bytes payloadRequest: Payload request
        :param bytes payloadResponse: Payload response
        :param bytes initiatorAddressType: Initiator address type, b"\x00" for public address and b"\x01" for random address
        :param str initiatorAddress: Initiator address
        :param bytes responderAddressType: Responder address type
        :param str responderAddress: Responder address
        :return: generated confirm value
        :rtype: bytes


.. py:class:: BLELinkLayerCrypto

    This class provides a API to manipuate the LL encryption used by ``BLEReceiver``. It shouldn't be used directly.

    .. py:method:: __init__(ltk)

        This method inits some security parameters

    .. py:method:: provideLTK(ltk)

        Set LTK in the single instance

        :param bytes ltk: Long term key

    .. py:method:: getInstance()

        Get the single instance of the class

        :return: Single instance of the class
        :rtype: BLELinkLayerCrypto

    .. py:method:: displayDetails()

        Print the parameters of the class

    .. py:method:: setMasterValues(skd, iv)

        This method sets session key disversifier and initialization vector from master

    .. py:method:: setSlaveValues(skd, iv)

        This method sets session key disversifier and initialization vector from slave

    .. py:method:: encrypt(playload, masterToSlave=True)

        This method encrypts a payload

        :param bytes playload: Payload to encrypt
        :param bool masterToSlave: If the payload is from master to slave
        :return: Encrypted payload, 2 btyes of playload + ciphertext + message integrity check (MIC)
        :rtype: bytes

    .. py:method:: tryToDecrypt(playload)

        This method tries to decrypt a payload

        :param bytes playload: Payload to decrypt
        :return: Decrypted payload
        :rtype: tuple of (bytes, bool)

    .. py:method:: decrypt(playload, masterToSlave=True)

        This method decrypts a payload

        :param bytes playload: Payload to decrypt
        :return: Decrypted payload
        :rtype: tuple of (bytes, bool)

    .. py:method:: incrementMasterCount()

        This method increments the master count

    .. py:method:: incrementSlaveCount()

        This method increments the slave count
sc_crypto
===========

.. py:class:: CryptoUtils

    This class provides a set of crypto tools

    .. py:method:: generateRandom(size=16)

        This method generates a random number of a given size.

        :param int size: Size of the random number
        :return: Random number
        :rtype: bytes

        :Example:
            >>> CryptoUtils.generateRandom(3).hex()
            'e7bbc9'

    .. py:method:: getRandomAddress()

        This method generates a random address.

        :return: Random address
        :rtype: str

    .. py:method:: reverseOrder(value)

        This method reverses the order of the bytes.

        :param bytes value: Value to reverse
        :return: Reversed value
        :rtype: bytes

        :Example:
            >>> CryptoUtils.reverseOrder(b"\x01\x02\x03").hex()
            '030201'

.. py:class:: BLECryptoSC

    This class provides a set of cryptographic functions that are used in the BLE protocol for secure connections

    .. py:method:: f4(U, V, X, Z)

        This method calculates the confirm value by f4 function.
        A sends to B

        :param bytes U: PKax (256 bits)
        :param bytes V: PKbx value (256 bits)
        :param bytes X: Na/ra/Nai for numeric comparison (128 bits)
        :param bytes Z: 0/0/rai for numeric comparison (8 bits)
        :return: confirm value
        :rtype: bytes

    .. py:method:: f5(W, N1, N2, A1, A2)

        This method calculates the keys' value by f5 function.
        A sends to B

        :param bytes W: DHKey (256 bits)
        :param bytes N1: A Nonce (128 bits)
        :param bytes N2: B Nonce (128 bits)
        :param bytes A1: A address (56 bits)
        :param bytes A2: B address (56 bits)
        :return: (MacKey, LTK)
        :rtype: tuple

    .. py:method:: f6(W, N1, N2, R, IOcap, A1, A2)

        This method calculates the DHKey value by f6 function.
        A sends to B

        :param bytes W: A MacKey (256 bits)
        :param bytes N1: A Nonce (128 bits)
        :param bytes N2: B Nonce (128 bits)
        :param bytes R: 0/ra/rb (128 bits)
        :param bytes IOcap: IO capabilities (24 bits)
        :param bytes A1: A address (56 bits)
        :param bytes A2: B address (56 bits)
        :return: DH Key
        :rtype: bytes

    .. py:method:: g2(U, V, X, Y)

        This method calculates the numeric comparison value by g2 function.
        A sends to B

        :param bytes U: PKax (256 bits)
        :param bytes V: PKbx (256 bits)
        :param bytes X: Na (128 bits)
        :param bytes Y: Nb (128 bits)
        :return: numeric comparison value
        :rtype: bytes


.. py:class:: SCCryptoInstance

    This class provides a instance with some parameters for secure connections

    .. py:method:: __init__()

        This method initializes some SC pairing parameters

    .. py:method:: generateDHKeyPair()

        This method generates a DH key pair and returns the X and Y coordinate for the public key.
        A sends to B
        :return: X and Y corrdinates for public key
        :rtype: tuple of (orderPubKeyX, orderPubKeyY)

    .. py:method:: generateDHSharedSecret(U, V)

        This method generates a DH shared secret. It adds DHKey to the instance.
        A sends to B.
        
        :param bytes U: PKbx (256 bits)
        :param bytes V: PKby (256 bits)
    
    .. py:method:: generateLocalNonce()
        
        This method generates a local nonce. It adds Na to the instance

        :return: local nonce
        :rtype: bytes

    .. py:method:: generateConfirmValue(keyX=None, remoteKeyX=None, localNonce=None, rbi=b"\x00")

        This method generates a confirm value. It adds local confirm to the instance

        :param bytes rbi: passkey bytes
        :return: confirm value
        :rtype: bytes

    .. py:method:: verifyConfirmValue(orderRemoteNonce, orderConfirm, keyX=None, rbi=b"\x00")

        This method verifies the confirm value

        :param bytes orderRemoteNonce: remote nonce
        :param bytes orderConfirm: remote confirm
        :param bytes rbi: passkey bytes
        :return: If the confirm value is correct
        :rtype: bool

    .. py:method:: generateCompareValueInitiator(orderRemoteNonce)

        This method generates a compare value for the final step of the SC numeric comparison

        :param bytes orderRemoteNonce: remote nonce (128 bits)
        :return: 6-digit compare value
        :rtype: int

    .. py:method:: generateCompareValueResponder(orderRemoteNonce)

        This method generates a compare value for the final step of the SC numeric comparison

        :param bytes orderRemoteNonce: remote nonce (128 bits)
        :return: 6-digit compare value
        :rtype: int
        
    .. py:method:: deriveLTKInitiator(localAddress, remoteAddress, localAddressType, remoteAddressType, orderRemoteNonce)

        This method derives the LTK and MacKey

        :param bytes localAddress: local address
        :param bytes remoteAddress: remote address
        :param int localAddressType: local address type
        :param int remoteAddressType: remote address type
        :param bytes orderRemoteNonce: remote nonce

    .. py:method:: deriveLTKResponder(localAddress, remoteAddress, localAddressType, remoteAddressType, orderRemoteNonce)

        This method derives the LTK and MacKey

        :param bytes localAddress: local address
        :param bytes remoteAddress: remote address
        :param int localAddressType: local address type
        :param int remoteAddressType: remote address type
        :param bytes orderRemoteNonce: remote nonce
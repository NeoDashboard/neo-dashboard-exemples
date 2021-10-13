# Verify/Sign message
Here you can find some example of how to verify a message signed by Neoline with neo-mambe Python module

## Sign message
Neoline N3 documentation: `https://neoline.io/dapi/N3.html`
>
    await neolineN3.signMessage({
        message: 'Hello world'
    });

## Verify message
Neo-mamba repository: `https://github.com/CityOfZion/neo-mamba`
>
    from neo3.core import cryptography
    
    def _verify_signature(message, signature, pubkey, salt):
        message = bytes(salt+message, 'utf-8')
        message = binascii.hexlify(message)
        len_mess = hex(int(len(message) / 2))[2:]
        message = bytes(len_mess, 'utf-8') + message
        message = bytes('010001f0', 'utf-8') + message + bytes('0000', 'utf-8')
    
        res = cryptography.verify_signature(
            binascii.unhexlify(message),
            binascii.unhexlify(signature),
            binascii.unhexlify(pubkey),
            cryptography.ECCCurve.SECP256R1
        )
    
        return res
        

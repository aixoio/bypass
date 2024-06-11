# Protocol

Bypass is a tool built to bypass internet censorship. This document is an overview of the protocol that bypass uses to combat internet censors.

## Connecting

We will start by talking about connecting to a server without hiding the fact that your using bypass.

The client will need the server's public key to start connecting and the server will need the client's
public key.

First the client will send a packet to the server to start the connection.
Then the server will reply with a packet encrypted with the client's public in this packet will be a
random 8 byte sequence. Once the client gets this packet it will sing the data with it's private key will then encrypt the signature using the server's public key and then it will send the encrypted signature to the server.

The server will then check is the signature is valid if it is **not** the server will send a unencrypted packet back to the client with a byte being `0b00000000` and then it will close the connection, but if the
signature is valid the server will send back a byte with `0b00000001` (unencrypted) to tell the client it has been authenticated.

Now that the server has verified the client, the client must verify the server. First the client will send
the server a packet with 8 random bytes and the server will sign the 8 bytes with it's private key and
will encrypt the signature and send it back to the client for the client to verify.

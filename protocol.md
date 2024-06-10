# Protocol

Bypass is a tool built to bypass internet censorship. This document is an overview of the protocol that bypass uses to combat internet censors.

## Connecting

We will start by talking about connecting to a server without hiding the fact that your using bypass.

The client will need the server's public key to start connecting and the server will need the client's
public key.

First the client will send a packet to the server to start the connection.
Then the server will reply with a packet encrypted with the client's public in this packet will be a
random 8 byte sequence. Once the client gets this packet it will sing the data with it's private key will then encrypt the signature using the server's public key and then it will send the encrypted signature to the server.

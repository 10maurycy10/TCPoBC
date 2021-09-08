# Transmission Control Protocol over Block Chain

TCPoBC is protocol to transfer TCP datagrams in a cryptographically verifiable 
manner, while allowing a distributed non-fungible record of all
datagrams ever sent.

## Prerequisites

Sending a TCPoBC datagram requires the 4096 bit RSA public key [note: specify format] of the 
destination host, and a 4096 bit private RSA key. [note: what format?].

## format of a TCPoBC datagram

    32 bits     : complete SHA-1 hash of last (globally) transmitted datagram
    4096 bits   : key of the destination host
    64 bits     : unix time when the process of sending started
    64 bits     : length of the payload TCP datagram in bytes
    N bytes     : the payload TCP datagram
    4096 bits   : signature of the sender for _all_ preceding values
    64 bits     : nonce value generated when sending

all values little endian

## process of sending a TCPoBC datagram

all fields other than the nonce are populated.
then the sender must find a value for the nonce that makes the SHA-1 hash of the SHA-1 hash of the 
datagram be lower that the difficulty value at the time. Next the sender will distribute the datagram
as quickly as posable to a selection of user defined repositories.

## receiving a TCPoBC datagram

when a datagram is uploaded a host must check if the destination key the hosts key, if yes then the 
datagram is passed to the hosts TCP handier.

## determination of difficulty value

[TODO: fill this in]

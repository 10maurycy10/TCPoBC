# Transmission Control Protocol over Block Chain

TCPoBC is protocol to transfer TCP datagrams in a cryptographicy verifiable 
maner, while mantioning allowing a distributed non-fungable recorod of all
datagrams eversent.

## Prerequisits

Sending a TCPoBC datagram requires the 4096 bit RSA public key [note: specify format] of the 
destination host, and a 4096 bit pivate RSA key. [note: what format?].

## format of a TCPoBC datagram

32 bits 	: complete SHA-1 hash of last (globaly) transmited datagram
4096 bits	: key of the destination host
64 bits		: unix time when the proces of sending started
64 bits 	: length of the payload TCP datagram in bytes
N bytes 	: the payload TCP datagram
4096 bits	: siganture of the sender for _all_ precidng values
64 bits		: nonce value generated when senfing

all valuse litle endian

## proces of sending a TCPoBC datagram

all feilds other than the nonce are populated.
then the sender must find a value for the nonce that makes the SHA-1 hash of the SHA-1 hash of the 
datagram be lower that the dificulty value at the time. Next the sender will distrubute the datagram
as quickly as posable to a selection of user defined repositorys.

## reciving a TCPoBC datagram

when a datagram is uploaded a host must check if the destination key the hosts key, if yes then the 
datagram is to be interprated and passed to the hosts TCP hander.

## determination of dificulty value

[TODO: fill this in]

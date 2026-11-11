# MAC Addresses

A runt is any frame smaller than 64 bytes.

A giant is any frame larger than 1518 bytes.

## ETHERNET (DIX) FRAME

D = DEC (Digital Equipment Company)
I = Intel
X = Xerox

Total Frame Size: 64 - 1518 bytes

```
+----------+------+------+------+----------------------+------+
| Preamble |  DA  |  SA  | Type | Data (+ Padding)     | FCS  |
+----------+------+------+------+----------------------+------+
|    8     |  6   |  6   |  2   |      46 - 1500       |  4   |
+----------+------+------+------+----------------------+------+
```

Preamble:
  7 bytes = 10101010 repeated
  1 byte  = 10101011 (Start Frame Delimiter)

DA   = Destination Address (MAC)
SA   = Source Address (MAC)
Type = Upper-layer protocol identifier
       Examples:
         0x0800 = IPv4
         0x0806 = ARP
         0x86DD = IPv6

Data Field:
  46 - 1500 bytes
  Padding added if payload is less than 46 bytes

FCS:
  Frame Check Sequence (CRC)


=================================================================

## IEEE 802.3 FRAME

Total Frame Size: 64 - 1518 bytes

```
+----------+-----+------+------+--------+----------------------+------+
| Preamble | SFD |  DA  |  SA  | Length | 802.2 Header & Data  | FCS  |
+----------+-----+------+------+--------+----------------------+------+
|    7     |  1  |  6   |  6   |   2    |      46 - 1500       |  4   |
+----------+-----+------+------+--------+----------------------+------+
```

Preamble:
  7 bytes = 10101010 repeated

SFD (Start Frame Delimiter):
  1 byte = 10101011

DA     = Destination Address (MAC)
SA     = Source Address (MAC)
Length = Length of LLC payload

802.2 Header:
  LLC (Logical Link Control)
  Identifies upper-layer protocol

FCS:
  Frame Check Sequence (CRC)


KEY DIFFERENCE
---------------

Ethernet II (DIX)
    Uses TYPE field
    |
    +--> Indicates protocol directly
         IPv4, ARP, IPv6, etc.

IEEE 802.3
    Uses LENGTH field
    |
    +--> Requires 802.2 LLC header
         to determine upper-layer protocol



---

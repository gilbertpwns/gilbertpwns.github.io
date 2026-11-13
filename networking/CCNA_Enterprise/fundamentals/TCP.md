# TCP - Transmission Control Protocol

Connection-oriented protocol

```
+------------------------------------------------------------------+
|                         L2/L3 Headers                            |
+------------------------------------------------------------------+
| TCP Source Port Number     | TCP Destination Port Number         |
+------------------------------------------------------------------+
|                        Sequence Number                           |
+------------------------------------------------------------------+
|                    Acknowledgment Number                         |
+----------+--------+----------------+-----------------------------+
| Hdr      | Resvd  | Control  |    Window Size                    |
| Length   |        | Flags    |                                   |
+----------+--------+----------------+-----------------------------+
| TCP Checksum                 |  Urgent Pointer                   |
+------------------------------------------------------------------+
|                     TCP Options (if any)                         |
+------------------------------------------------------------------+
|                             Payload                              |
+------------------------------------------------------------------+
```

## Three-way Handshake

One of the most important fundamental concepts in networking in my opinion.


---

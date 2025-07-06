---
description: >-
  Packets are chunks of bytes (data) sent/received through the network, ordered
  and organized in packages with an unique ID (opcode) to exchange information
  between client and server through protocols.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Packets

Packets are chunks of bytes (data) sent/received through the network, ordered and organized in packages with an unique ID (opcode) to exchange information between client and server through protocols.

### Protocols

* [Global](global.md)
* [Gateway](gateway.md) (GatewayServer)
* [Download](download.md) (DownloadServer)
* [Agent](agent.md) (AgentServer & SR\_GameServer)

### Message Types

The first 4 Most Signifcant Bits (MSB) of the opcode indicates the message type of the packet.

```
// (MSB)                                                                        (LSB)
// | 15  | 14 | 13 | 12 | 11 | 10 | 09 | 08 | 07 | 06 | 05 | 04 | 03 | 02 | 01 | 00 |
// |     MsgType        |                              ID                           |
```

| MsgType | Signal | Module / Operation |
| ------- | ------ | ------------------ |
| 0       | NoDir  |                    |
| 1       | NoDir  | Data               |
| 2       | NoDir  | Global             |
| 3       | NoDir  | Agent              |
| 4       | Req    |                    |
| 5       | Req    | Handshake          |
| 6       | Req    | Global, Gateway    |
| 7       | Req    | Agent              |
| 8       | Ack    |                    |
| 9       | Ack    | Handshake          |
| A       | Ack    | Local, Gateway     |
| B       | Ack    | Agent              |
| C       | Req    |                    |
| D       | Req    |                    |
| E       | Req    |                    |
| F       | Req    |                    |


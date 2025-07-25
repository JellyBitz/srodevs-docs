---
hidden: true
---

# Global Packets

Packets used when communicating with any server (globally used).

<table data-full-width="true"><thead><tr><th width="100">Opcode</th><th width="215">Direction ( Client / Server )</th><th>Name</th></tr></thead><tbody><tr><td>0x5000</td><td>-</td><td>GLOBAL_HANDSHAKE_CHALLENGE</td></tr><tr><td>0x9000</td><td>C > S</td><td>GLOBAL_HANDSHAKE_ACCEPT</td></tr><tr><td>0x2001</td><td>S > C</td><td><a href="global_module_identification.md">GLOBAL_MODULE_IDENTIFICATION</a></td></tr><tr><td>0x2002</td><td>C > S</td><td><a href="global_module_keep_alive.md">GLOBAL_MODULE_KEEP_ALIVE</a></td></tr><tr><td>0x6003</td><td>C > S</td><td>GLOBAL_MODULE_CERTIFICATION_REQ</td></tr><tr><td>0xA003</td><td>S > C</td><td>GLOBAL_MODULE_CERTIFICATION_ACK</td></tr><tr><td>0x2005</td><td>S > C</td><td>GLOBAL_MODULE_UPDATE_STATE</td></tr><tr><td>0x6005</td><td>S > C</td><td>GLOBAL_MODULE_UPDATE_STATE_REQ</td></tr><tr><td>0x6008</td><td>C > S</td><td>GLOBAL_MODULE_RELAY_REQ</td></tr><tr><td>0xA008</td><td>S > C</td><td>GLOBAL_MODULE_RELAY_ACK</td></tr><tr><td>0x600D</td><td>-</td><td>GLOBAL_MASSIVE_MESSAGE</td></tr></tbody></table>

{% hint style="info" %}
Here the concept of **Client** also applies for all **Server** modules.
{% endhint %}

### Diagram

<figure><img src="../../.gitbook/assets/packets-global-diagram.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
For more info, visit [A Guide to Silkroad's Security](../../client/a-guide-to-silkroads-security.md)
{% endhint %}

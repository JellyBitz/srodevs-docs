---
hidden: true
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

# Download Packets

Packets used when communicating with DownloadServer.

<table><thead><tr><th width="100">Opcode</th><th width="215">Direction ( Client / Server )</th><th>Name</th></tr></thead><tbody><tr><td>0x6004</td><td>C > S</td><td>DOWNLOAD_FILE_REQ</td></tr><tr><td>0x1001</td><td>S > C</td><td>DOWNLOAD_FILE_CHUNK</td></tr><tr><td>0xA004</td><td>S > C</td><td>DOWNLOAD_FILE_COMPLETE</td></tr></tbody></table>

### Diagram

<figure><img src="../.gitbook/assets/packets-download-diagram.png" alt=""><figcaption></figcaption></figure>

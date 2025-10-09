---
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
  metadata:
    visible: true
---

# AGENT\_CHAT\_REQ

* Opcode `0x7025`
* Direction `C > S`

```csharp
1   byte    ChatType
1   byte    ChatWindow.RowIndex
if(ChatType == ChatType.Private)
{
    2   ushort  Receiver.Length
    *   string  Receiver
}
2   ushort  Message.Length
*   string  Message
```

***

### ChatType

```csharp
public enum ChatType : byte
{
    ///<summary>
    /// General chat visible to nearby entities
    ///</summary>
    All = 1,
    
    ///<summary>
    /// $
    ///</summary>
    Private = 2,
    
    ///<summary>
    /// General (GM) chat visible to nearby entities
    ///</summary>
    AllGM = 3,
    
    ///<summary>
    /// #
    ///</summary>
    Party = 4,
    
    ///<summary>
    /// @
    ///</summary>
    Guild = 5, 
    
    ///<summary>
    /// Global chatting scroll item
    ///</summary>
    Global = 6,
    
    ///<summary>
    /// ~
    ///</summary>
    Notice = 7,
    
    ///<summary>
    /// While stall window
    ///</summary>
    Stall = 9, 
    
    ///<summary>
    /// %
    ///</summary>
    Union = 11,
    
    ///<summary>
    /// SN_TALK_QNO_EU_EASTEU_21_14
    ///</summary>
    NPC = 13,
    
    ///<summary>
    /// &
    ///</summary>
    Academy = 16
}
```

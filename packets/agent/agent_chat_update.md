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

# AGENT\_CHAT\_UPDATE

* Opcode `0x3026`&#x20;
* Direction `S > C`

```csharp
1   byte    ChatType
if( ChatType == ChatType.All ||
    ChatType == ChatType.AllGM ||
    ChatType == ChatType.NPC )
{
    4   uint    Message.Sender.UniqueID
}
else if( ChatType == ChatType.PM ||
         ChatType == ChatType.Party ||
         ChatType == ChatType.Guild ||
         ChatType == ChatType.Global ||
         ChatType == ChatType.Stall ||
         ChatType == ChatType.Union ||
         ChatType == ChatType.Accademy )        
{
    2   ushort  Message.Sender.Name.Length
    *   string  Message.Sender.Name
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
    PM = 2,
    
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
    /// While in stall window
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
    Academy = 16,
}
```

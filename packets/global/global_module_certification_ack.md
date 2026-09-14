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
  tags:
    visible: true
  actions:
    visible: true
---

# GLOBAL\_MODULE\_CERTIFICATION\_ACK

* Opcode `0xA003`
* Direction `S > C`
* Massive&#x20;

```csharp
1   byte    Result
if( Result == 0x01 )
{
    // Check SRO_CERTIFICATION for reference

    // Module
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        1   byte    Module.ID
        64  char[]  Module.Name
    }
    1   byte    unkByte02                //2

    // Content
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        1   byte    Content.ID
        64  char[]  Content.Name
    }
    1   byte    unkByte02                //2

    // Division
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        1   byte    Division.ID
        32  char[]  Division.Name
        256 char[]  Division.DbConfig
        2   ushort  Division.GlobalManagerID
    }
    1   byte    unkByte02                //2

    // Farm
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        1   byte    Farm.ID
        1   byte    Farm.DivisionID
        32  char[]  Farm.Name
        256 char[]  Farm.DbConfig
    }
    1   byte    unkByte02                //2

    // FarmContent
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        1   byte    FarmContent.FarmID
        1   byte    FarmContent.ContentID
        4   uint    mem_ptr_to_FarmContent
    }
    1   byte    unkByte02                //2

    // Shard
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        2   ushort  Shard.ID
        1   byte    Shard.FarmID
        1   byte    Shard.ContentID
        32  char[]  Shard.Name           // Name sent to players
        256 char[]  Shard.DbConfig
        256 char[]  Shard.LogDBConfig
        2   ushort  Shard.MaxCapacity
        2   ushort  Shard.ShardManagerID
        4   uint    mem_ptr_to_FarmContent
        1   byte    Shard.IsOperational
        2   ushort  Shard.CurrentCapacity
    }
    1   byte    unkByte02                //2

    // ServerMachine
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        4   uint    ServerMachine.ID
        1   byte    ServerMachine.DivisionID
        32  char[]  ServerMachine.Name
        16  char[]  ServerMachine.PublicIP
        16  char[]  ServerMachine.PrivateIP
        2   ushort  ServerMachine.MachineManagerID
    }
    1   byte    unkByte02                //2

    // ServerBody
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        2   ushort  ServerBody.ID
        1   byte    ServerBody.DivisionID
        1   byte    ServerBody.FarmID
        2   ushort  ServerBody.ShardID
        4   uint    ServerBody.ServerMachineID
        1   byte    ServerBody.ModuleID
        1   byte    ServerBody.ModuleType
        2   ushort  ServerBody.CertifierID
        2   ushort  ServerBody.Port
        4   uint    ServerBody.State    // See "ServerBodyState"
        4   uint    mem_ptr_to_Module;
        4   uint    mem_ptr_to_Shard;
        4   uint    mem_ptr_to_Division;
        4   uint    mem_ptr_to_Farm;
        4   uint    mem_ptr_to_Shard;
    }
    1   byte    unkByte02                //2

    // ServerCord
    1   byte    unkByte01                //0
    while(true)
    {
        1   bool    CanRead
        if(!CanRead)
            break

        4   uint    ServerCord.ID
        2   ushort  ServerCord.ChildID
        2   ushort  ServerCord.ParentID
        1   byte    ServerCord.BindType  // See "ServerCordBindType"
        4   uint    ServerCord.State     // See "ServerCordState"
        4   uint    ServerCord.ConnectionSession
    }
    1   byte    unkByte02                //2

}
```

***

### ServerBodyState

```cs
public enum ServerBodyState : uint
{
    None = 0,
    Wait = 1,
    Busy = 2,
    Cert = 3,
    Gray = 4,
    Blue = 5,
    Red = 6,
    Exit = 7,
    Hide = 8,
}
```

### ServerCordBindType

```cs
public enum ServerCordBindType : byte
{
    Public = 0,
    Private = 1,
}
```

### ServerCordState

```cs
public enum ServerCordState : uint
{
    /// <summary>
    /// Gray DOTTED
    /// </summary>
    Blind = 0,
    /// <summary>
    /// Blue
    /// </summary>
    Established = 2,
}
```

{% hint style="info" %}
References:

* [https://www.elitepvpers.com/forum/sro-coding-corner/4930839-complete-certification-format.html](https://www.elitepvpers.com/forum/sro-coding-corner/4930839-complete-certification-format.html)
* [https://www.elitepvpers.com/forum/sro-pserver-guides-releases/4114834-release-replace-certification.html](https://www.elitepvpers.com/forum/sro-pserver-guides-releases/4114834-release-replace-certification.html)
{% endhint %}

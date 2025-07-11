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
---

# GATEWAY\_PATCH\_ACK

* Opcode `0xA100`
* Direction `S > C`&#x20;
* Massive

***

```csharp
1   byte    Result
if(Result == 0x02)
{
    1   byte    PatchErrorCode
    if(PatchErrorCode == PatchErrorCode.Update)
    {
        2   ushort  DownloadServer.IP.Length
        *   string  DownloadServer.IP
        2   ushort  DownloadServer.Port
        4   uint    LatestVersion
        
        while(true)
        {
            1   bool CanRead
            if(!CanRead)
                break;
            
            4   uint    File.ID
            2   ushort  File.Name.Length
            *   string  File.Name
            2   ushort  File.Path.Length
            *   string  File.Path         // .PK2 name as root path if IsPacked
            4   uint    File.Size
            1   bool    File.IsPacked     // To be packed into .PK2
        }
    }
}
```

***

### PatchErrorCode

```csharp
public enum PatchErrorCode : byte
{
    /// <summary>
    /// UILM_MSG_DETECTED_ABNORMAL_MODULE
    /// <para>Invalid client. Program will be terminated.</para>
    /// </summary>
    InvalidVersion = 1,

    /// <summary>
    /// BSObj Plugin: can't create file transfer manager! Maybe pack file corrupted or someone is already accessing it now... try a few minutes later"
    /// </summary>
    Update = 2,

    /// <summary>
    /// UILM_MSG_GATEWAY_NOT_IN_SERVICE
    /// <para>The server is undergoing inspection or updates. Connect to %swww.silkroadonline.net for more information.</para>
    /// </summary>
    NotInService = 3,

    /// <summary>
    /// UILM_MSG_DETECTED_ABNORMAL_MODULE
    /// <para>Invalid client. Program will be terminated.</para>
    /// </summary>
    AbnormalModule = 4,

    /// <summary>
    /// UILM_MSG_DETECTED_PATCH_DIABLE
    /// <para>You have to install the full version. Move to official website to dowload the full version?</para>
    /// </summary>
    PatchDisabled = 5,
}
```

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

# AGENT\_CHARACTER\_SELECTION\_RENAME\_ACK

* Opcode `0xB450`
* Direction `S > C`

```csharp
1   byte    RenameAction
1   byte    Result
if(Result == 0x02)
{
    2   ushort  RenameErrorCode  // Depends on RenameAction, see below
}
```

***

### CharacterSelectionRenameErrorCode

```csharp
public enum CharacterSelectionRenameErrorCode : ushort
{
    #region CharacterRename

    /// <summary>
    /// This ID already exists.
    /// </summary>
    UIO_MSG_ERROR_ID = 6,

    /// <summary>
    /// Invalid character name.
    /// </summary>
    UIO_SMERR_NOT_ALLOWED_CHARNAME = 7,

    #endregion CharacterRename

    #region GuildRename

    /// <summary>
    /// The selected guild name already exsists.
    /// </summary>
    UIIT_MSG_GUILDERR_SAME_GUILDNAME_EXIST = 6,

    /// <summary>
    /// The guild name cannot be created.
    /// </summary>
    UIIT_MSG_GUILD_NOT_CREATE = 7,

    /// <summary>
    /// Unknown error.
    /// </summary>
    //UIIT_MSG_PARTYERR_UNKNOWN_ERROR = 2, 3, 4, 5,

    #endregion GuildRename
}
```

{% hint style="info" %}
See also:

* [CharacterSelectionRenameAction](agent_character_selection_rename_req.md#characterselectionrenameaction)
{% endhint %}

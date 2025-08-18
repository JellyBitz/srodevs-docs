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

# AGENT\_CHARACTER\_SELECTION\_RENAME\_REQ

* Opcode `0x7450`
* Direction `C > S`&#x20;

```csharp
1   byte    RenameAction
if( RenameAction == CharacterSelectionRenameAction.CharacterRename ||
    RenameAction == CharacterSelectionRenameAction.GuildRename )
{
    2   ushort  CurName.Length
    *   string  CurName
    2   ushort  NewName.Length
    *   string  NewName
}
else if( RenameAction == CharacterSelectionRenameAction.GuildNameCheck )
{
    2   ushort  Name.Length
    *   string  Name
}
```

***

### CharacterSelectionRenameAction

```csharp
public enum CharacterSelectionRenameAction : byte
{
    CharacterRename = 1,
    GuildRename = 2,
    GuildNameCheck = 3
}
```

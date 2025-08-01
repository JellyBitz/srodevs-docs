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

# AGENT\_CHARACTER\_SELECTION\_ACTION\_REQ

* Opcode `0x7007`
* Direction `C > S`

```csharp
1   byte    Action
if(Action == CharacterSelectionAction.Create)
{
	2   ushort  Name.Length
	*   string  Name
	4   uint    RefObjID
	1   byte    Scale
        // (MSB)                               (LSB)
        // | 07 | 06 | 05 | 04 | 03 | 02 | 01 | 00 |
        // |   Scale.Height    |   Scale.Volume    |
	4   uint    RefItemID	// EQUIP_SLOT_MAIL
	4   uint    RefItemID	// EQUIP_SLOT_PANTS
	4   uint    RefItemID	// EQUIP_SLOT_BOOTS
	4   uint    RefItemID	// EQUIP_SLOT_WEAPON
}
else if(Action == CharacterSelectionAction.Delete || 
        Action == CharacterSelectionAction.CheckName || 
        Action == CharacterSelectionAction.Restore)
{
	2   ushort  Name.Length
	*   string  Name
}
```

***

### CharacterSelectionAction

```csharp
public enum CharacterSelectionAction : byte
{
    Create = 1,
    List = 2,
    Delete = 3,
    CheckName = 4,
    Restore = 5,
}
```

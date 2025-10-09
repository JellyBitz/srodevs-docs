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

# AGENT\_CHARACTER\_SELECTION\_ACTION\_ACK

* Opcode `0xB007`
* Direction `S > C`

```csharp
1   byte    Action
1   byte    Result
if(Result == 0x01)
{
    if(Action == CharacterSelectionAction.List)
    {
        1   byte    CharacterCount
        foreach(CharacterCount)
        {
            // Character
            4   uint    RefObjID
            2   ushort  Name.Length
            *   string  Name
            1   byte    Scale
            1   byte    CurLevel
            8   ulong   ExpOffset
            2   ushort  Strength
            2   ushort  Intelligence
            2   ushort  StatPoint
            4   uint    CurHP 
            4   uint    CurMP

            1   bool    isDeleting
            if(isDeleting)
            {
                4   uint    DeletingTime  // Minutes
            }

            // Guild & Academy
            1   byte    GuildMemberClass
            1   bool    IsGuildRenameRequired
            if(IsGuildRenameRequired)
            {
                2   ushort  CurGuildName.Length
                *   string  CurGuildName
            } 
            1   byte    AcademyMemberClass

            // Items
            1   byte    ItemCount
            foreach(ItemCount)
            {
                4   uint    Item.RefItemID
                1   byte    Item.Plus
            }
            1   byte    AvatarItemCount
            foreach(AvatarItemCount)
            {
                4   uint    AvatarItem.RefItemID
                1   byte    AvatarItem.Plus
            }
        }
    }
}
else if(Result == 0x02)
{
    2   ushort  ErrorCode
}

```

***

{% hint style="info" %}
See also:

* [CharacterSelectionAction](agent_character_selection_action_req.md#characterselectionaction)
{% endhint %}

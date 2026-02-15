# AGENT\_CHAT\_ACK

* Opcode `0xB025`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 2)
{
    2   ushort  ChatErrorCode    
}
1   byte    ChatType
1   byte    ChatWindow.RowIndex
```

***

### ChatErrorCode

<pre class="language-csharp"><code class="lang-csharp"><strong>public enum ChatErrorCode : ushort
</strong>{
    /// &#x3C;summary>
    /// Cannot find [%s].
    /// &#x3C;/summary>
    UIIT_CHATERR_CANT_FIND_TARGET = 3,

    /// &#x3C;summary>
    /// [%s]'s whisper function is turn off.
    /// &#x3C;/summary>
    UIIT_CHATERR_YOU_ARE_SQUELCHED = 0x2006,

    /// &#x3C;summary>
    /// Invalid chat command.
    /// &#x3C;/summary>
    UIIT_CHATERR_INVALID_COMMAND = 0x2008,

    /// &#x3C;summary>
    /// Not in the party status.
    /// &#x3C;/summary>
    UIIT_CHATERR_NOT_A_PARTY_MEMBER = 0x200A,

    /// &#x3C;summary>
    /// Cannot use the Ally Chat because the selected guild is not your ally.
    /// &#x3C;/summary>
    UIIT_CHATERR_ALLIANCE_PERMISSION_DENIED = 0x200B,

    /// &#x3C;summary>
    /// Chat Restricted: %d seconds
    /// &#x3C;/summary>
    UIIT_STT_CANT_CHATTING = 0x200D,

    /// &#x3C;summary>
    /// You do not have union chatting authority, so you cannot chat.
    /// &#x3C;/summary>
    UIIT_MSG_GUILD_UNION_CHAT_LIMIT = 0x200E
}
</code></pre>

{% hint style="info" %}
See also:

* [ChatType](agent_chat_req.md#chattype)
{% endhint %}

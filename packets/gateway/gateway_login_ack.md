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

# GATEWAY\_LOGIN\_ACK

* Opcode `0xA102`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 0x01)
{
    4   uint    QueueID
    2   ushort  AgentServer.IP.Length
    *   string  AgentServer.IP
    2   ushort  AgentServer.Port
}
else if(Result == 0x02)
{
    1   byte    LoginErrorCode
    if(LoginErrorCode == LoginErrorCode.InvalidCredentials)
    {
        // Username/Password error
        4   uint    MaxAttempts
        4   uint    CurAttempts
    }
    else if(LoginErrorCode == LoginErrorCode.Blocked)
    {
        1   byte    LoginBlockType
        if(LoginBlockType == LoginBlockType.Punishment)
        {
            2   ushort  Reason.Length
            *   string  Reason
            2   ushort  EndDate.Year
            2   ushort  EndDate.Month
            2   ushort  EndDate.Day
            2   ushort  EndDate.Hour
            2   ushort  EndDate.Minute
            2   ushort  EndDate.Second
            2   ushort  EndDate.Microsecond
        }
    }
}
else if(Result == 0x03) // Custom message, not supported by every client
{
    // Not looked into this yet
    1   byte    unkByte0
    1   byte    unkByte1
    2   ushort  Message.Length
    *   string  Message
    2   ushort  unkUShort0
}
```

***

### LoginErrorCode

```csharp
public enum LoginErrorCode
{
    /// <summary>
    /// <para>UIIT_STT_GLOBAL_PASSWORD_INPUT_ERROR</para>
    /// Password entry has failed %d out of %d times.
    /// </summary>
    InvalidCredentials = 1,

    /// <summary>
    /// Depends on subtype <see cref="LoginBlockType"/>
    /// </summary>
    Blocked = 2,

    /// <summary>
    /// <para>UIO_MSG_ERROR_OVERLAP</para>
    /// This user is already connected. The user may still be connected because of an error that forced the game to close. Please try again in 5 minutes.
    /// </summary>
    AlreadyConnected = 4,
    /// <summary>
    /// <para>UIO_MSG_ERROR_SERVER_BUSY_CONNECT_IMPOSSIBILE</para>
    /// The server is full, please try again later.
    /// </summary>
    ServerIsFull = 6,

    /// <summary>
    /// Cannot connect to the server because access to the current IP has exceeded its limit.
    /// </summary>
    IPLimit = 0xB,

    /// <summary>
    /// <para>TRANSLATION MISSING</para>
    /// 사용기간이 만료되어 서버에 접속할 수 없습니다. (This period has expired, you can not connect to the server.)
    /// </summary>
    UIIO_CLIENT_START_CONTENT_FAIL_BILLING_FAILED = 0xC,

    /// <summary>
    /// Billing server error occurred.
    /// </summary>
    UIIO_CLIENT_START_CONTENT_FAIL_BILLING_RELATED = 0xD,

    /// <summary>
    /// Only adults over the age of 18 are allowed to connect to the server.
    /// </summary>
    UIIO_SMERR_ADULT_ONLY_SERVER = 0xE,

    /// <summary>
    /// Only users over the age of 12 are allowed to connect to the server.
    /// </summary>
    UIIO_SMERR_TEENOVER_ONLY_SERVER = 0xF,

    /// <summary>
    /// Adults over the age of 18 are not allowed to connect to the Teen server.
    /// </summary>
    UITT_TEENSERVER_ERRMGS_ADULT = 0x10,
}
```

### LoginBlockType

```csharp
public enum LoginBlockType
{
    /// <summary>
    /// <para>UIO_MSG_ERROR_ACCOUNT_STOP</para>
    /// This account has been blocked according to the Terms of Service and cannot be accessed to play the game.
    /// Blocking reason:
    /// Completion time:
    /// </summary>
    Punishment = 1,

    /// <summary>
    /// <para>UIO_MSG_ERROR_ACCOUNT_CONNECT_IMPOSSIBILE</para>
    /// Cannot connect to the server because the server is now in inspection.
    /// </summary>
    AccountInspection = 2,

    /// <summary>
    /// <para>UIO_MSG_ERROR_THERE_IS_NO_ACCOUNT_INFO</para>
    /// ID is found, but the needed details are not found.\nFill in the needed information at Silkroad homepage to connect to the game.
    /// <para>SimpleMessageBox -> opens website</para>
    /// </summary>
    NoAccountInfo = 3,

    /// <summary>
    /// <para>UIO_MSG_ERROR_GRATIS_USER_BLOCKED</para>
    /// Cannot connect because the free service is over.
    /// </summary>
    FreeServiceOver = 4,
}
```


# AGENT\_LOGIN\_AUTH\_ACK

* Opcode `0xA103`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 0x02)
{
    1   byte    AuthenticationErrorCode
}
```

***

### AuthenticationErrorCode

```csharp
public enum AuthenticationErrorCode : byte
{
    /// <summary>
    /// <para>UIO_MSG_ERROR_SEVER_CONNECT</para>
    /// Failed to connect to the server.
    /// </summary>
    ConnectionErrorC9 = 1,
    ConnectionErrorC10 = 2,
    
    /// <summary>
    /// <para>UIO_MSG_ERROR_SERVER_BUSY_CONNECT_IMPOSSIBILE</para>
    /// The server is full, please try again later.
    /// </summary>
    ServerIsFull = 4,

    /// <summary>
    /// <para>UIO_MSG_ERROR_CONTENT_FAIL_INSUFFICIENT_IP</para>
    /// Cannot connect to the server because access to the current IP has exceeded its limit.
    /// </summary>
    IPLimit = 5,
}
```

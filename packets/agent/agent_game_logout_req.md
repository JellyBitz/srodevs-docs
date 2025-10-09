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

# AGENT\_GAME\_LOGOUT_REQ

* Opcode `0x7005`;
* Direction `C > S`

```csharp
1   byte    LogoutMode
```
***
### LogoutMode
```csharp
public enum LogoutMode : byte
{
    /// <summary>
    /// Go to Process.CPSQuit
    /// </summary>
    Exit = 1, 
    
    /// <summary>
    /// Go to Process.CPSRestart
    /// </summary>
    Restart = 2,
}
```

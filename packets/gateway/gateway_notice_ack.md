# GATEWAY\_NOTICE\_ACK

* Opcode `0xA104`&#x20;
* Direction `S > C`

```csharp
1   byte    NoticeCount
foreach(NoticeCount)
{
    // Notice (Launcher News)
    2   ushort  Subject.Length
    *   string  Subject
    2   ushort  Article.Length
    *   string  Article
    2   ushort  DateTime.Year
    2   ushort  DateTime.Month
    2   ushort  DateTime.Day
    2   ushort  DateTime.Hour
    2   ushort  DateTime.Minute
    2   ushort  DateTime.Second
    4   int     DateTime.Nanosecond
}
```

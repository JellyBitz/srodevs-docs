---
hidden: true
---

# SILKCFG

Contains the most basic configurations to start the game.

{% tabs %}
{% tab title="File Structure" %}
```csharp
4   uint    Version //3
if (Version < 4)
{
    4   uint    unkUInt01               //1
    4   uint    WindowResolution.Width
    4   uint    WindowResolution.Height
    1   byte    GraphicType1            // 0 = Low, 1 = Middle, 2 = High, 3 = Large, 4 = Unchanged
    1   byte    Brightness              // 0 = Very Dark, 1 = Dark, 2 = Normal, 3 = Bright, 4 = Very Bright
    1   byte    unkByte01
    1   bool    IsSoundEnabled
    1   byte    unkByte02               // Language tab index?
    if (Version == 3)
    {
        1   byte    GraphicType2
        1   byte    GraphicTypeIndex    //1 or 2
    }
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct WindowResolution
{
    u32 Width;
    u32 Height;
};
enum GraphicType : u8
{
    Low = 0,
    Middle = 1,
    High = 2,
    Large = 3,
    Unchanged = 4
};
enum Brightness : u8
{
    VeryDark = 0,
    Dark = 1,
    Normal = 2,
    Bright = 3,
    VeryBright = 4
};
struct SilkCfg
{
    u32 Version;
    u32 unkUInt01;
    WindowResolution Resolution;
    GraphicType GraphicType1;
    Brightness Brightness;
    u8 unkByte01;
    u8 IsSoundEnabled;
    u8 unkByte02;
    if (Version == 3)
    {
        GraphicType GraphicType2;
        u8 GraphicTypeIndex;
    }
};

SilkCfg file @ 0;
```
{% endtab %}
{% endtabs %}

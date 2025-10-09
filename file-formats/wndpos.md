---
hidden: true
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

# WndPos

Contains the layout position from some game windows inside the client window.

{% tabs %}
{% tab title="File Structure" %}
```csharp
4   uint    Version        //3
4   uint    WindowCount    // Not used, number is hardcoded.. see below.
4   uint    Client.Width
4   uint    Client.Height
foreach(WindowCount)
{
    // Window
    4   uint    X
    4   uint    Y
}

//Window[0] = GDR_MAINPOPUP
//Window[1] = GDR_STORE
//Window[2] = GDR_STORAGEROOM
//Window[3] = GDR_EXCHANGE
//Window[4] = GDR_WORLDMAP
//Window[5] = GDR_COS_WND
//Window[6] = GDR_GAMEGUIDE
//Window[7] = GDR_ALCHEMYBOX
//Window[8] = GDR_AUTO_POTION
//Window[9] = GDR_EXT_QUICK_SLOT
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct Window
{
    u32 X;
    u32 Y;
};

struct WndPos
{
    u32 Version;
    u32 WindowCount;
    u32 ClientWidth;
    u32 ClientHeight;
    Window Windows[WindowCount];
};

WndPos file @ 0;
```
{% endtab %}
{% endtabs %}

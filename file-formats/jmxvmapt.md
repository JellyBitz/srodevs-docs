---
hidden: true
---

# JMXVMAPT

Represent the baked lightmap texture from terrain associated.\
Also includes a simplified map used to check if an object is inside shadow.

{% tabs %}
{% tab title="File Structure" %}
```csharp
12   char[]  Signature      //JMXVMAPT1001

9216 byte[]  ShadowMap      // 96x96 tiles, each 20 units same as terrain mesh
4    int     TextureLength  // (+8) It counts TextureLength and TextureType bytes
4    int     TextureType    // https://docs.microsoft.com/en-us/windows/win32/direct3d9/d3dresourcetype
*    byte[]  Texture        // https://learn.microsoft.com/en-us/windows/win32/direct3ddds/dx-graphics-dds
```
{% endtab %}

{% tab title="ImHex" %}
```cpp
#pragma array_limit 4294967296

struct JMXVMAPT
{
    char Signature[12];
    u8 ShadowMap[96*96];
    u32 TextureLength;
    u32 TextureType;
    u8 Texture[TextureLength-8];
};

JMXVMAPT file @ 0;
```
{% endtab %}
{% endtabs %}



<br>

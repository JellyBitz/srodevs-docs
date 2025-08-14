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

# JMXV2DTI

Contains a list with all the 2D tile info used for the map terrain.

{% hint style="info" %}
This file is not binary, it's read line by line.
{% endhint %}

{% tabs %}
{% tab title="File Structure" %}


<pre class="language-csharp"><code class="lang-csharp"><strong>*   string  Signature  //JMXV2DTI1001
</strong></code></pre>

```csharp
*   string  TileCount
```

```csharp
foreach(TileCount)
{
    *   string  Tile // Split by empty spaces, see format below
}
```

| Column   | Format      | Description                                                                                                                                                                                   |
| -------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ID       | {0:00000}   |                                                                                                                                                                                               |
| Type     | 0x{1:X8}    | [#tiletype](jmxv2dti.md#tiletype "mention")                                                                                                                                                   |
| Category | "{2}"       |                                                                                                                                                                                               |
| Filename | "{3}"       | \*.ddj                                                                                                                                                                                        |
| ? Grass  | \{{0},{1\}} | <p>First value indicates and index from object.ifo<br>Second value indicates grass amount which is randomly placed on the tile.<br></p><p><em>Multiple grass per tile is possible.</em></p> |



***

### TileType

```csharp
public enum TileType: int
{
    Dirt = 0,
    Sand = 1,
    Ashfield = 2,
    Stone = 3,
    Metal = 4,
    Wood = 5,
    Mud = 6,
    Water = 7,
    DeepWater = 8,
    Snow = 9,
    Grass = 10,
    LongGrass = 11,
    Forest = 12,
    Cloud = 13
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
import std.mem;
import std.string;

struct Textline
{
    char value[while(std::mem::read_string($, 1) != "\n")];
    padding[1];
};

struct TileEntry
{
    char Id[while(std::mem::read_string($, 1) != " ")];
    padding[1];
    char Type[while(std::mem::read_string($, 1) != " ")];
    padding[2];
    char Category[while(std::mem::read_string($, 1) != "\"")];
    padding[3];
    char File[while(std::mem::read_string($, 1) != "\"")];
    if(std::mem::read_string($+1, 1) != "\n")
    {
        padding[2];
        char GrassInfo[while(std::mem::read_string($, 1) != "\n")];
        padding[1];
    }
    else
    {
        padding[2];
    }
};

struct JMXV2DTI
{
    Textline Signature;
    Textline TileCount;
    TileEntry TileEntries[std::string::parse_int(TileCount.value,10)];
};

JMXV2DTI file @ 0;
```
{% endtab %}
{% endtabs %}

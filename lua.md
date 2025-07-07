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

# LUA

[LUA](https://www.lua.org/about.html) is used as an scripting language extension to handle interactions between NPC and players.

| SRO version | LUA version |
| ----------- | ----------- |
| 188         | 5.1         |
| 230+        | 5.3         |

### Compilers

* [https://luabinaries.sourceforge.net/](https://luabinaries.sourceforge.net/)

### Decompilers

* [https://luadec.metaworm.site/](https://luadec.metaworm.site/)
* [https://github.com/viruscamp/luadec](https://github.com/viruscamp/luadec)
* [https://github.com/HansWessels/unluac](https://github.com/HansWessels/unluac)

## API Functions

#### LuaInsertQuest

Registers a function to be used for quests.

| Parameter    | Type     | Description                                 |
| ------------ | -------- | ------------------------------------------- |
| TypeId       | `int`    |                                             |
| Filename     | `string` | Filename with the function to be registered |
| FunctionName | `string` | Function name to be registered              |

{% tabs %}
{% tab title="Example" %}
```lua
LuaInsertQuest(1,"quest.sct","QNO_SD_RE_001")
```
{% endtab %}
{% endtabs %}

#### LuaInsertNpc

Links the NPC to execute the current function.

| Parameter | Type                | Description                 |
| --------- | ------------------- | --------------------------- |
| Count     | `int`               | Number of NPCs to be linked |
| Codenames | `*args` as `string` | Codenames from NPCs         |

{% tabs %}
{% tab title="Example" %}
```lua
LuaInsertNpc(3,"NPC_CH_EVENT_KISAENG1","NPC_CH_EVENT_KISAENG2","NPC_CH_EVENT_KISAENG3")
```
{% endtab %}
{% endtabs %}

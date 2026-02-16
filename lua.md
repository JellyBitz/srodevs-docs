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

#### LuaInsertEvent

Registers a function to be used as an event.

| Parameter    | Type     | Description                                 |
| ------------ | -------- | ------------------------------------------- |
| Type         | `int`    | (1)                                         |
| Filename     | `string` | Filename with the function to be registered |
| FunctionName | `string` | Function name to be registered              |

{% tabs %}
{% tab title="Example" %}
```lua
LuaInsertEvent(1,"event.sct","QEV_LEVEL_CH_POTION")
```
{% endtab %}
{% endtabs %}

#### LuaInsertQuest

Registers a function to be used for quests.

| Parameter    | Type     | Description                                 |
| ------------ | -------- | ------------------------------------------- |
| Type         | `int`    | (1)                                         |
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
LuaInsertNpc(3,
    "NPC_CH_EVENT_KISAENG1",
    "NPC_CH_EVENT_KISAENG2",
    "NPC_CH_EVENT_KISAENG3"
)
```
{% endtab %}
{% endtabs %}

#### LuaInsertDropItem

Registers an item drop globally for all monsters.

| Parameter     | Type                           | Description                    |
| ------------- | ------------------------------ | ------------------------------ |
| Count         | `int`                          | Number of NPCs to be linked    |
| Codenames     | `*args` as `string`            | Codenames from NPCs            |
| Probabilities | `*args` as `int` in `[0, 100]` | Drop probability in percentage |

{% tabs %}
{% tab title="Example" %}
```lua
LuaInsertDropItem(2,
    "ITEM_ETC_MOON_GEM",100,
    "ITEM_ETC_MOON_POT",100
)
```
{% endtab %}
{% endtabs %}

#### SetEventOne

Set text from the first talking action at NPC.

| Parameter | Type     | Description                     |
| --------- | -------- | ------------------------------- |
| EventID   | `int`    | Unique identifier for the event |
| Codename  | `string` | Codename for text reference     |
| Unk01     | `int`    | (1)                             |
| Unk02     | `int`    | (1)                             |
| Unk03     | `int`    | (1)                             |

{% tabs %}
{% tab title="Example" %}
```lua
EventID = 40008
SetEventOne(EventID,"SN_QEV_LEVEL_CH_POTION",1,1,0)
```
{% endtab %}
{% endtabs %}

#### SetEventTwo

Set a text list from all possible talking actions at NPC.

| Parameter | Type                | Description                   |
| --------- | ------------------- | ----------------------------- |
| Count     | `int`               | Number of codenames to be set |
| Codenames | `*args` as `string` | Codenames for text references |

{% tabs %}
{% tab title="Example" %}
```lua
SetEventTwo(2,
    "SN_TALK_QEV_LEVEL_CH_POTION_B",
    "SN_TALK_COMMON_EXIT"
)
```
{% endtab %}
{% endtabs %}


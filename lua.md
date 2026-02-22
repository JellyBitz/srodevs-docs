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
| Type         | `int`    | `1`                                         |
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
| Type         | `int`    | `1`                                         |
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
| Count         | `int`                          | Number of items to be linked   |
| Codenames     | `*args` as `string`            | Codenames from items           |
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
| Unk01     | `int`    | `1`                             |
| Unk02     | `int`    | `1`                             |
| Unk03     | `int`    | `1`                             |

{% tabs %}
{% tab title="Example" %}
```lua
EventID = 40008
SetEventOne(EventID,"SN_QEV_LEVEL_CH_POTION",1,1,0)
```
{% endtab %}
{% endtabs %}

#### SetEventTwo

Set a list for all possible talking actions at NPC.

| Parameter       | Type                | Description                   |
| --------------- | ------------------- | ----------------------------- |
| Count           | `int`               | Number of codenames to be set |
| ActionCodenames | `*args` as `string` | Codenames for text references |

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

#### InsertPayItemCodeName

Register items to be rewarded or exchanged in the process.

| Parameter | Type                | Description                          |
| --------- | ------------------- | ------------------------------------ |
| Count     | `int` in `[0, 120]` | Number of items to be set for reward |
| Codenames | `*args` as `string` | Codename of the items                |

{% tabs %}
{% tab title="Example" %}
```lua
InsertPayItemCodeName(3,
    "ITEM_ETC_E051123_AGILITY_SCROLL",
    "ITEM_ETC_E051123_EVATION_SCROLL",
    "ITEM_ETC_E051123_HIT_SCROLL"
)
```
{% endtab %}
{% endtabs %}

#### InsertPayItemRatio

Register reward ratio for items registered with [InsertPayItemCodeName](lua.md#insertpayitemcodename).

| Parameter     | Type               | Description                                    |
| ------------- | ------------------ | ---------------------------------------------- |
| Count         | `int`              | Number of probabilities to be set              |
| Probabilities | `*args` as `float` | Percentage values, the summatory should be 100 |

{% tabs %}
{% tab title="Example" %}
```lua
InsertPayItemRatio(3,
    32.5, -- ITEM_ETC_E051123_AGILITY_SCROLL
    32.5, -- ITEM_ETC_E051123_EVATION_SCROLL
    35 -- ITEM_ETC_E051123_HIT_SCROLL
)
```
{% endtab %}
{% endtabs %}

#### InsertMenuStringList

Links all event types at NPC to be used with their dialog text reference to be used as menu.

| Parameter      | Type                | Description                |
| -------------- | ------------------- | -------------------------- |
| NpcCodename    | `string`            | Codename from NPC          |
| EventCount     | `int`               | Number of events to be set |
| EventCode      | `*args` as `string` | Code from event type       |
| DialogCodename | `*args` as `string` | Codename from dialog text  |

{% tabs %}
{% tab title="Example" %}
```lua
InsertMenuStringList("NPC_CH_EVENT_KISAENG1", 5,
    "EVENT_MENUSTRING_GREETING","SN_NPC_CH_EVENT_KISAENG1_QS",
    "EVENT_MENUSTRING_REQUEST_ACCEPT_QUEST","SN_TALK_QEV_CH_EVENT_KISAENG_GLOBAL2011_2_A",
    "EVENT_MENUSTRING_NOT_ACHIEVED","SN_TALK_QEV_CH_EVENT_KISAENG_GLOBAL2011_2_E",
    "EVENT_MENUSTRING_INVENTORY_FULL","SN_TALK_QEV_CH_EVENT_KISAENG_GLOBAL2011_2_D",
    "EVENT_MENUSTRING_ACHIEVED","SN_TALK_QEV_CH_EVENT_KISAENG_GLOBAL2011_2_C"
)
```
{% endtab %}
{% endtabs %}

#### LuaInsertFunctionStringList

Register callback function which handles all the NPC talking process.

| Parameter    | Type     | Description             |
| ------------ | -------- | ----------------------- |
| Unk01        | `int`    | `1`                     |
| Unk01        | `string` | `"CONVERSATION_SINGLE"` |
| FunctionName | `string` | Callback function name  |

{% tabs %}
{% tab title="Example" %}
```lua
CONVERSATION_SINGLE = 0 -- Not sure if this is even required
LuaInsertFunctionStringList(1,"CONVERSATION_SINGLE","KISAENG_LETTER_THANKS_Conversation")

-- ...

function KISAENG_LETTER_THANKS_Conversation(ConversationState,NpcCodename)
    if ConversationState == CONVERSATION_START then
        -- code here
    elseif ConversationState == CONVERSATION_RESPONSE then
        -- code here
    end
end
```
{% endtab %}
{% endtabs %}

#### LuaNpcHandlerNum

Returns the unique identifier from NPC executing the talking process.

| Return | Type  | Description           |
| ------ | ----- | --------------------- |
| NpcUID | `int` | NPC unique identifier |

{% tabs %}
{% tab title="Example" %}
```lua
npcUID = LuaNpcHandlerNum()
```
{% endtab %}
{% endtabs %}

#### LuaShowMenu

Sets up the dialog and talking actions from [SetEventTwo](lua.md#seteventtwo) to be shown at the next callback from [LuaInsertFunctionStringList](lua.md#luainsertfunctionstringlist).

| Parameter     | Type  | Description                                                 |
| ------------- | ----- | ----------------------------------------------------------- |
| Type          | `int` | Dialog type[^1] to be shown                                 |
| ActionsOffset | `int` | Index from actions where the menu begins                    |
| ActionsLength | `int` | Number of actions to show at menu, starting from the offset |
| NpcUID        | `int` | NPC unique identifier to use                                |

{% tabs %}
{% tab title="Example" %}
```lua
SetEventTwo(3,
    "SN_TALK_QEV_LEVEL_CH_POTION_A", -- index: 0
    "SN_TALK_QEV_LEVEL_CH_POTION_B", -- index: 1
    "SN_TALK_COMMON_EXIT" -- index: 2
)

-- ...

MENUTYPE_GREETING = 5
-- Show Menu as => [ SN_TALK_QEV_LEVEL_CH_POTION_B, SN_TALK_COMMON_EXIT ]
menuOffset = 1
menuLength = 2
LuaShowMenu(MENUTYPE_GREETING,EventID,menuOffset,menuLength,LuaNpcHandlerNum())
```
{% endtab %}
{% endtabs %}

#### LuaGetEventMenuResponse

Get the player action response from menu.

| Return   | Type  | Description                        |
| -------- | ----- | ---------------------------------- |
| Response | `int` | Action index but shifted/reversed? |

{% tabs %}
{% tab title="Example" %}
```lua
SetEventTwo(3,
    "SN_TALK_QEV_LEVEL_CH_POTION_A", -- index: 0
    "SN_TALK_QEV_LEVEL_CH_POTION_B", -- index: 1
    "SN_TALK_COMMON_EXIT" -- index: 2
)

-- ...

function GetActionResponseIndex()
    return LuaGetEventMenuResponse()-TALK_RESPONSE_LIST_BASE
end

-- ...

response = GetActionResponseIndex()
if response == 0 then -- SN_TALK_QEV_LEVEL_CH_POTION_A
    -- code here
elseif response == 1 then -- SN_TALK_QEV_LEVEL_CH_POTION_B
    -- code here
else -- SN_TALK_COMMON_EXIT
    -- code here
end
```
{% endtab %}
{% endtabs %}

#### LuaSetCurPage

Sets the page number used to track the loop process through the callback from [LuaInsertFunctionStringList](lua.md#luainsertfunctionstringlist). Generally used before [LuaShowMenu](lua.md#luashowmenu).

| Parameter  | Type  | Description           |
| ---------- | ----- | --------------------- |
| PageNumber | `int` | Page number to be set |

{% tabs %}
{% tab title="Example" %}
```lua
pageNumber = 1
LuaSetCurPage(pageNumber)
```
{% endtab %}
{% endtabs %}

#### LuaGetCurPage

Gets the page number used to track the loop process through the callback from [LuaInsertFunctionStringList](lua.md#luainsertfunctionstringlist).

| Return     | Type  | Description         |
| ---------- | ----- | ------------------- |
| PageNumber | `int` | Current page number |

{% tabs %}
{% tab title="Example" %}
```lua
currentPage = LuaGetCurPage()
if currentPage == 1 then
    -- code here
elseif currentPage == 2 then
    -- code here
else
    -- code here
end
```
{% endtab %}
{% endtabs %}

#### LuaTerminateMenu

Stops the talking loop process from [LuaInsertFunctionStringList](lua.md#luainsertfunctionstringlist).

{% tabs %}
{% tab title="Example" %}
```lua
LuaTerminateMenu()
```
{% endtab %}
{% endtabs %}

#### LuaEventInQuireSameItem

Check inventory items from player talking, used also to count.

| Parameter    | Type     | Description                      |
| ------------ | -------- | -------------------------------- |
| Unk01        | `int`    | `0`                              |
| ItemCodename | `string` | Codename of the item to search   |
| SearchType   | `int`    | Type[^2] of the searching method |
| Unk01        | `int`    | `-1,0` Maybe default result?     |

| Return       | Type  | Description                                     |
| ------------ | ----- | ----------------------------------------------- |
| SearchResult | `int` | Item slot or count, depends on searching method |

{% tabs %}
{% tab title="Example" %}
```lua
function GetSlotFromItem(Codename)
    return LuaEventInQuireSameItem(0,Codename,INQUIRE_SAMEITEM_OP_FIND_FIRST_SLOT,-1)
end

-- ...

slot = GetSlotFromItem("ITEM_CH_BLADE_01_A")
if slot >= 0 then
    -- item found
end
```
{% endtab %}
{% endtabs %}

#### LuaGetCountEmptyInventory

Counts all empty slots found in the inventory of the player talking.

| Parameter | Type  | Description                                |
| --------- | ----- | ------------------------------------------ |
| Unk01     | `int` | `0` Maybe slot offset where search begins? |
| Unk02     | `int` | `-1` Maybe default result?                 |

| Return | Type  | Description                       |
| ------ | ----- | --------------------------------- |
| Count  | `int` | Count of empty slots in inventory |

{% tabs %}
{% tab title="Example" %}
```lua
emptySlotCount = LuaGetCountEmptyInventory(0,-1)
-- Confirm there is an empty slot
if emptySlotCount > 1 then
    -- code here
end
```
{% endtab %}
{% endtabs %}

#### LuaAddItem\_EXT

Add an item to the inventory of the player talking.

| Parameter      | Type              | Description                                                                             |
| -------------- | ----------------- | --------------------------------------------------------------------------------------- |
| EventID        | `int`             | Unique identifier for the event                                                         |
| Unk01          | `int`             | `0`                                                                                     |
| Amount         | `int`             | Amount of items                                                                         |
| ReasonType     | `int`             | Reason type[^3] of adding                                                               |
| RandomizeStats | `int` in `[0, 1]` | Indicator to apply random stats if item is equipable                                    |
| Unk02          | `int`             | `0` Maybe plus?                                                                         |
| ItemIndex      | `int`             | Index[^4] of the item list set at [InsertPayItemCodeName](lua.md#insertpayitemcodename) |

{% tabs %}
{% tab title="Example" %}
```lua
InsertPayItemCodeName(3,
    "ITEM_ETC_E051123_AGILITY_SCROLL", -- index: 1
    "ITEM_ETC_E051123_EVATION_SCROLL", -- index: 2
    "ITEM_ETC_E051123_HIT_SCROLL" -- index: 3
)

-- ...

emptySlotCount = LuaGetCountEmptyInventory(0,-1)
-- Confirm there is an empty slot
if emptySlotCount > 1 then
    -- Add (5) pieces of "ITEM_ETC_E051123_EVATION_SCROLL"
    index = 2
    pieces = 5
    LuaAddItem_EXT(EventID,0,pieces,SYSOP_REASON_EVENT,0,0,index)
end
```
{% endtab %}
{% endtabs %}

#### LuaDelItem\_EXT

Delete an item from the inventory of the player talking.

| Parameter  | Type  | Description                 |
| ---------- | ----- | --------------------------- |
| Unk01      | `int` | `0`                         |
| Slot       | `int` | Slot of the item            |
| Amount     | `int` | Amount of items             |
| ReasonType | `int` | Reason type[^3] of deletion |
| Unk02      | `int` | `0`                         |

{% tabs %}
{% tab title="Example" %}
```lua
function GetSlotFromItem(Codename)
    return LuaEventInQuireSameItem(0,Codename,INQUIRE_SAMEITEM_OP_FIND_FIRST_SLOT,-1)
end

-- ...

slot = GetSlotFromItem("ITEM_CH_BLADE_01_A")
if slot >= 0 then
    -- item found
    LuaDelItem_EXT(0,slot,1,SYSOP_REASON_DRAINED,0)
end
```
{% endtab %}
{% endtabs %}

[^1]: ```lua
    MENUTYPE = {
        GREETING = 5,
        ACHIEVED = 3,
        ACHIEVED = 1
    }
    ```

[^2]: ```lua
    0 = INQUIRE_SAMEITEM_OP_FIND_FIRST_SLOT -- First inventory slot to find
    1 = INQUIRE_SAMEITEM_OP_COUNT_FIRST_ITEM -- Count stack from first inventory slot to find
    2 = INQUIRE_SAMEITEM_OP_COUNT_ALL_SAMEITEM -- Count all inventory items found
    ```

[^3]: ```lua
    0 = SYSOP_REASON_QUEST
    1 = SYSOP_REASON_EVENT
    2 = SYSOP_REASON_DRAINED
    3 = SYSOP_REASON_WITHDRAW
    4 = SYSOP_REASON_ALCHEMY_REINFORCE
    5 = SYSOP_REASON_FLEAMARKET_NETWORK
    6 = SYSOP_REASON_SIEGE
    255 = SYSOP_REASON_INVALID
    ```

[^4]: LUA list index paradigm starts from 1

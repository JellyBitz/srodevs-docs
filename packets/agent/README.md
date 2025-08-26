---
hidden: true
---

# Agent Packets

Packets used when communicating with AgentServer (dispatched to ShardManager or GameServer).

<table data-full-width="true">
<thead>
<tr>
<th width="100">Opcode</th>
<th width="215">Direction (Client / Server)</th>
<th>Name</th>
</tr>
</thead>
<tbody>
<tr><td>0x6103</td><td>C > S</td><td><a href="agent_login_auth_req.md">AGENT_LOGIN_AUTH_REQ</a></td></tr>
<tr><td>0xA103</td><td>S > C</td><td><a href="agent_login_auth_ack.md">AGENT_LOGIN_AUTH_ACK</a></td></tr>
<tr><td>0x7007</td><td>C > S</td><td><a href="agent_character_selection_action_req.md">AGENT_CHARACTER_SELECTION_ACTION_REQ</a></td></tr>
<tr><td>0xB007</td><td>S > C</td><td><a href="agent_character_selection_action_ack.md">AGENT_CHARACTER_SELECTION_ACTION_ACK</a></td></tr>
<tr><td>0x7001</td><td>C > S</td><td><a href="agent_character_selection_join_req.md">AGENT_CHARACTER_SELECTION_JOIN_REQ</a></td></tr>
<tr><td>0xB001</td><td>S > C</td><td><a href="agent_character_selection_join_ack.md">AGENT_CHARACTER_SELECTION_JOIN_ACK</a></td></tr>
<tr><td>0x7450</td><td>C > S</td><td><a href="agent_character_selection_rename_req.md">AGENT_CHARACTER_SELECTION_RENAME_REQ</a></td></tr>
<tr><td>0xB450</td><td>S > C</td><td><a href="agent_character_selection_rename_ack.md">AGENT_CHARACTER_SELECTION_RENAME_ACK</a></td></tr>
<tr><td>0x34A5</td><td>S > C</td><td>AGENT_CHARACTER_DATA_BEGIN</td></tr>
<tr><td>0x3013</td><td>S > C</td><td>AGENT_CHARACTER_DATA_CHUNK</td></tr>
<tr><td>0x34A6</td><td>S > C</td><td>AGENT_CHARACTER_DATA_END</td></tr>
<tr><td>0x3056</td><td>S > C</td><td><a href="agent_character_exp_update.md">AGENT_CHARACTER_EXP_UPDATE</a></td></tr>
<tr><td>0x304E</td><td>S > C</td><td>AGENT_CHARACTER_INFO_UPDATE</td></tr>
<tr><td>0x70A7</td><td>C > S</td><td><a href="agent_character_bodystate_req.md">AGENT_CHARACTER_BODYSTATE_REQ</a></td></tr>
<tr><td>0x3012</td><td>C > S</td><td>AGENT_GAME_READY</td></tr>
<tr><td>0x300C</td><td>S > C</td><td>AGENT_GAME_NOTIFY</td></tr>
<tr><td>0x3080</td><td>-</td><td>AGENT_GAME_INVITE</td></tr>
<tr><td>0x7005</td><td>C > S</td><td><a href="agent_game_logout_req.md">AGENT_GAME_LOGOUT_REQ</a></td></tr>
<tr><td>0xB005</td><td>S > C</td><td><a href="agent_game_logout_ack.md">AGENT_GAME_LOGOUT_ACK</a></td></tr>
<tr><td>0x7006</td><td>C > S</td><td><a href="agent_game_logout_cancel_req.md">AGENT_GAME_LOGOUT_CANCEL_REQ</a></td></tr>
<tr><td>0xB006</td><td>S > C</td><td><a href="agent_game_logout_cancel_ack.md">AGENT_GAME_LOGOUT_CANCEL_ACK</a></td></tr>
<tr><td>0x300A</td><td>S > C</td><td><a href="agent_game_logout_success.md">AGENT_GAME_LOGOUT_SUCCESS</a></td></tr>
<tr><td>0x7025</td><td>C > S</td><td><a href="agent_chat_req.md">AGENT_CHAT_REQ</a></td></tr>
<tr><td>0xB025</td><td>S > C</td><td><a href="agent_chat_ack.md">AGENT_CHAT_ACK</a></td></tr>
<tr><td>0x3026</td><td>S > C</td><td><a href="agent_chat_update.md">AGENT_CHAT_UPDATE</a></td></tr>
<tr><td>0x302D</td><td>S > C</td><td>AGENT_CHAT_RESTRICT</td></tr>
<tr><td>0x7021</td><td>C > S</td><td><a href="agent_entity_movement_req.md">AGENT_ENTITY_MOVEMENT_REQ</a></td></tr>
<tr><td>0xB021</td><td>S > C</td><td><a href="agent_entity_movement_ack.md">AGENT_ENTITY_MOVEMENT_ACK</a></td></tr>
<tr><td>0x7024</td><td>C > S</td><td><a href="agent_entity_rotation_req.md">AGENT_ENTITY_ROTATION_REQ</a></td></tr>
<tr><td>0xB024</td><td>S > C</td><td><a href="agent_entity_rotation_ack.md">AGENT_ENTITY_ROTATION_ACK</a></td></tr>
<tr><td>0xB070</td><td>S > C</td><td><a href="agent_entity_skill_cast_begin.md">AGENT_ENTITY_SKILL_CAST_BEGIN</a></td></tr>
<tr><td>0xB071</td><td>S > C</td><td><a href="agent_entity_skill_cast_end.md">AGENT_ENTITY_SKILL_CAST_END</a></td></tr>
<tr><td>0x3CA2</td><td>S > C</td><td><a href="agent_quest_script.md">AGENT_QUEST_SCRIPT</a></td></tr>
<tr><td>0x2209</td><td>S > S</td><td>AGENT_RELAY_CLIENT_MESSAGE</td></tr>
</tbody>
</table>

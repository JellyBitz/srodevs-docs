---
hidden: true
---

# Agent Packets

Packets used when communicating with AgentServer (dispatched to ShardManager or GameServer).

| Opcode  | Direction (Client / Server) | Name |
|--------|----------------------------|------|
| 0x6103 | C > S                      | [AGENT_LOGIN_AUTH_REQ](agent_login_auth_req.md) |
| 0xA103 | S > C                      | [AGENT_LOGIN_AUTH_ACK](agent_login_auth_ack.md) |
| 0x7007 | C > S                      | [AGENT_CHARACTER_SELECTION_ACTION_REQ](agent_character_selection_action_req.md) |
| 0xB007 | S > C                      | [AGENT_CHARACTER_SELECTION_ACTION_ACK](agent_character_selection_action_ack.md) |
| 0x7001 | C > S                      | [AGENT_CHARACTER_SELECTION_JOIN_REQ](agent_character_selection_join_req.md) |
| 0xB001 | S > C                      | [AGENT_CHARACTER_SELECTION_JOIN_ACK](agent_character_selection_join_ack.md) |
| 0x7450 | C > S                      | [AGENT_CHARACTER_SELECTION_RENAME_REQ](agent_character_selection_rename_req.md) |
| 0xB450 | S > C                      | [AGENT_CHARACTER_SELECTION_RENAME_ACK](agent_character_selection_rename_ack.md) |
| 0x34A5 | S > C                      | AGENT_CHARACTER_DATA_BEGIN |
| 0x3013 | S > C                      | AGENT_CHARACTER_DATA_CHUNK |
| 0x34A6 | S > C                      | AGENT_CHARACTER_DATA_END |
| 0x3056 | S > C                      | [AGENT_CHARACTER_EXP_UPDATE](agent_character_exp_update.md) |
| 0x304E | S > C                      | AGENT_CHARACTER_INFO_UPDATE |
| 0x70A7 | C > S                      | [AGENT_CHARACTER_BODYSTATE_REQ](agent_character_bodystate_req.md) |
| 0x3012 | C > S                      | AGENT_GAME_READY |
| 0x300C | S > C                      | AGENT_GAME_NOTIFY |
| 0x3080 | -                          | AGENT_GAME_INVITE |
| 0x7005 | C > S                      | [AGENT_GAME_LOGOUT_REQ](agent_game_logout_req.md) |
| 0xB005 | S > C                      | [AGENT_GAME_LOGOUT_ACK](agent_game_logout_ack.md) |
| 0x7006 | C > S                      | AGENT_GAME_LOGOUT_CANCEL_REQ |
| 0xB006 | S > C                      | AGENT_GAME_LOGOUT_CANCEL_ACK |
| 0x300A | S > C                      | AGENT_GAME_LOGOUT_SUCCESS |
| 0x7025 | C > S                      | [AGENT_CHAT_REQ](agent_chat_req.md) |
| 0xB025 | S > C                      | [AGENT_CHAT_ACK](agent_chat_ack.md) |
| 0x3026 | S > C                      | [AGENT_CHAT_UPDATE](agent_chat_update.md) |
| 0x302D | S > C                      | AGENT_CHAT_RESTRICT |
| 0x7021 | C > S                      | [AGENT_ENTITY_MOVEMENT_REQ](agent_entity_movement_req.md) |
| 0xB021 | S > C                      | [AGENT_ENTITY_MOVEMENT_ACK](agent_entity_movement_ack.md) |
| 0x7024 | C > S                      | [AGENT_ENTITY_ROTATION_REQ](agent_entity_rotation_req.md) |
| 0xB024 | S > C                      | [AGENT_ENTITY_ROTATION_ACK](agent_entity_rotation_ack.md) |
| 0xB070 | S > C                      | [AGENT_ENTITY_SKILL_CAST_BEGIN](agent_entity_skill_cast_begin.md) |
| 0xB071 | S > C                      | [AGENT_ENTITY_SKILL_CAST_END](agent_entity_skill_cast_end.md) |
| 0x3CA2 | S > C                      | [AGENT_QUEST_SCRIPT](agent_quest_script.md) |
| 0x2209 | S > S                      | AGENT_RELAY_CLIENT_MESSAGE |

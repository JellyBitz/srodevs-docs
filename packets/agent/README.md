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
---

# Agent Packets

Packets used when communicating with AgentServer (dispatched to ShardManager or GameServer).

<table data-full-width="true"><thead><tr><th width="100">Opcode</th><th width="215">Direction ( Client / Server )</th><th>Name</th></tr></thead><tbody><tr><td>0x6103</td><td>C > S</td><td><a href="agent_login_auth_req.md">AGENT_LOGIN_AUTH_REQ</a></td></tr><tr><td>0xA103</td><td>S > C</td><td><a href="agent_login_auth_ack.md">AGENT_LOGIN_AUTH_ACK</a></td></tr><tr><td>0x7007</td><td>C > S</td><td>AGENT_CHARACTER_SELECTION_ACTION_REQ</td></tr><tr><td>0xB007</td><td>S > C</td><td>AGENT_CHARACTER_SELECTION_ACTION_ACK</td></tr><tr><td>0x7001</td><td>C > S</td><td>AGENT_CHARACTER_SELECTION_JOIN_REQ</td></tr><tr><td>0xB001</td><td>S > C</td><td>AGENT_CHARACTER_SELECTION_JOIN_ACK</td></tr><tr><td>0x7450</td><td>C > S</td><td>AGENT_CHARACTER_SELECTION_RENAME_REQ</td></tr><tr><td>0xB450</td><td>S > C</td><td>AGENT_CHARACTER_SELECTION_RENAME_ACK</td></tr><tr><td>0x34A5</td><td>S > C</td><td>AGENT_CHARACTER_DATA_BEGIN</td></tr><tr><td>0x3013</td><td>S > C</td><td>AGENT_CHARACTER_DATA_CHUNK</td></tr><tr><td>0x34A6</td><td>S > C</td><td>AGENT_CHARACTER_DATA_END</td></tr><tr><td>0x3056</td><td>S > C</td><td>AGENT_CHARACTER_EXP_UPDATE</td></tr><tr><td>0x304E</td><td>S > C</td><td>AGENT_CHARACTER_INFO_UPDATE</td></tr><tr><td>0x70A7</td><td>C > S</td><td>AGENT_CHARACTER_BODYSTATE_REQ</td></tr><tr><td>0x3012</td><td>C > S</td><td>AGENT_GAME_READY</td></tr><tr><td>0x300C</td><td>S > C</td><td>AGENT_GAME_NOTIFY</td></tr><tr><td>0x3080</td><td>-</td><td>AGENT_GAME_INVITE</td></tr><tr><td>0x7005</td><td>C > S</td><td>AGENT_GAME_LOGOUT_REQ</td></tr><tr><td>0xB005</td><td>S > C</td><td>AGENT_GAME_LOGOUT_ACK</td></tr><tr><td>0x7006</td><td>C > S</td><td>AGENT_GAME_LOGOUT_CANCEL_REQ</td></tr><tr><td>0xB006</td><td>S > C</td><td>AGENT_GAME_LOGOUT_CANCEL_ACK</td></tr><tr><td>0x300A</td><td>S > C</td><td>AGENT_GAME_LOGOUT_SUCCESS</td></tr><tr><td></td><td></td><td></td></tr><tr><td>0x2209</td><td>S > S</td><td>AGENT_RELAY_CLIENT_MESSAGE</td></tr></tbody></table>

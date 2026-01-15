---
title: JBClawd
created: 2026-01-15T09:15:00+01:00
owner: self
---

## Bot Details

| Field | Value |
|-------|-------|
| **Name** | JBClawd |
| **Port** | 18789 |
| **URL** | http://localhost:18789 |
| **Launchd File** | ~/Library/LaunchAgents/com.clawdbot.jbclawd.plist |
| **Start Script** | ~/.config/bj_launchd/jbclawd-start.sh |
| **Working Directory** | ~/.clawdbot/agents/main |
| **Workspace** | /Users/bjesuiter/.config/clawdbot-workspaces/jbclawd |

## Restart Command

```bash
launchctl kickstart -k gui/501/com.clawdbot.jbclawd
```

## Update/Restart Procedure

1. Pull latest changes:
   ```bash
   cd ~/Develop/clawdbot && git pull
   npm i && npm run build
   ```

2. Restart via launchd:
   ```bash
   launchctl kickstart -k gui/501/com.clawdbot.jbclawd
   ```

## Notes
- Uses fish shell via fnm's default Node.js version
- Config: `~/.clawdbot/`
- Logs: `~/.clawdbot/logs/gateway.log`
- Gateway token stored in `CLAWDBOT_GATEWAY_TOKEN` env var

---

## JBPhoenix

| Field | Value |
|-------|-------|
| **Name** | JBPhoenix |
| **Port** | 18800 |
| **URL** | http://localhost:18800 |
| **Launchd File** | `~/Library/LaunchAgents/com.clawdbot.phoenix.plist` |
| **Working Directory** | `~/.clawdbot-phoenix/` |

### Restart Command

```bash
launchctl kickstart -k gui/501/com.clawdbot.jbphoenix
```

### Update/Restart Procedure

1. Pull latest changes (if needed):
   ```bash
   cd ~/Develop/clawdbot && git pull && npm i && npm run build
   ```

2. Restart via launchd:
   ```bash
   launchctl kickstart -k gui/501/com.clawdbot.jbphoenix
   ```

### Notes
- Uses fish shell
- Logs: `~/.clawdbot-phoenix/logs/gateway.log`
- Config: `~/.clawdbot-phoenix/`


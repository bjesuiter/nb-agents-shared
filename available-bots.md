---
title: JBClawd
created: 2026-01-15T09:15:00+01:00
owner: self
---

## LaunchAgent Naming Scheme

The app manages a per‑user LaunchAgent labeled `com.clawdbot.gateway` (or `com.clawdbot.<profile>` when using `--profile` / `CLAWDBOT_PROFILE`).

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

### Recommended (Non-Interactive)
```bash
clawdbot update --restart
```

### Manual Fallback
```bash
cd ~/Develop/clawdbot && git pull && pnpm i && pnpm build
launchctl kickstart -k gui/501/com.clawdbot.gateway
```

## Notes
- Uses fish shell via fnm's default Node.js version
- Config: `~/.clawdbot/`
- Logs: `~/.clawdbot/logs/gateway.log`
- Gateway token stored in `CLAWDBOT_GATEWAY_TOKEN` env var
- LaunchAgent label: `com.clawdbot.gateway` (default profile)

---

## JBPhoenix

| Field | Value |
|-------|-------|
| **Name** | JBPhoenix |
| **Port** | 28800 |
| **URL** | http://localhost:28800 |
| **Launchd File** | ~/Library/LaunchAgents/com.clawdbot.jbphoenix.plist |
| **Start Script** | ~/.config/bj_launchd/jbphoenix-start.sh |
| **Working Directory** | ~/.clawdbot-jbphoenix/ |
| **Workspace** | /Users/bjesuiter/.config/clawdbot-workspaces/jbphoenix |

### Restart Command

```bash
launchctl kickstart -k gui/501/com.clawdbot.jbphoenix
```

### Update/Restart Procedure

#### Recommended (Non-Interactive)
```bash
clawdbot --profile jbphoenix update --restart
```

#### Manual Fallback
```bash
cd ~/Develop/clawdbot && git pull && pnpm i && pnpm build
launchctl kickstart -k gui/501/com.clawdbot.jbphoenix
```

### Notes
- Uses fish shell via fnm's default Node.js version
- Config: `~/.clawdbot-jbphoenix/clawdbot.json`
- Logs: `~/.clawdbot-jbphoenix/logs/gateway.log`
- Gateway token stored in `CLAWDBOT_GATEWAY_TOKEN` env var
- LaunchAgent label: `com.clawdbot.jbphoenix` (custom profile)


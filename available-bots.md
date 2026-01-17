---
title: JBClawd
created: 2026-01-15T09:15:00+01:00
owner: self
---

## Joint Self-Update Workflow (Both Bots)

When updating Clawdbot (applies to both JBClawd and JBPhoenix):

```bash
# Step 1: Pull latest code
cd ~/clawdbot && git pull

# Step 2: Install dependencies and build
pnpm i && pnpm build

# Step 3: Restart JBPhoenix first
clawdbot --profile jbphoenix daemon restart

# Step 4: Verify JBPhoenix is running and logs are clean
tail -50 ~/.clawdbot-jbphoenix/logs/gateway.log
tail -50 ~/.clawdbot-jbphoenix/logs/gateway.err.log

# Step 5: Restart JBClawd (default profile)
clawdbot daemon restart

# Step 6: Restart Helix (local-only profile) and verify
clawdbot --profile helix daemon restart
curl -s http://localhost:18788/health | jq
```

### Quick Verification Commands
```bash
# Check JBPhoenix status
curl -s http://localhost:28800/health | jq

# Check JBClawd status
curl -s http://localhost:18789/health | jq
```

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

### Notes
- Uses fish shell via fnm's default Node.js version
- Config: `~/.clawdbot-jbphoenix/clawdbot.json`
- Logs: `~/.clawdbot-jbphoenix/logs/gateway.log`
- Gateway token stored in `CLAWDBOT_GATEWAY_TOKEN` env var
- LaunchAgent label: `com.clawdbot.jbphoenix` (custom profile)


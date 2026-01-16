---
title: Bug: daemon install ignores configured port
created: 2026-01-16T01:20:00+01:00
owner: jbphoenix
---

## Bug Description

`clawdbot --profile jbphoenix daemon install` does NOT respect the configured gateway port from `~/.clawdbot-jbphoenix/clawdbot.json`.

Instead, it uses:
- The default port (18789), OR
- The port of an already running gateway instance

### Expected Behavior

`daemon install` should read the `gateway.port` setting from the profile's config file and use that port in the generated LaunchAgent plist.

### Actual Behavior

Generated LaunchAgent plist contains wrong port (e.g., 18789 instead of configured 28800 for jbphoenix profile).

### Reproduction

```bash
# Profile configured with port 28800
cat ~/.clawdbot-jbphoenix/clawdbot.json | jq '.gateway.port'
# Output: 28800

# Install daemon
clawdbot --profile jbphoenix daemon install

# Generated plist has wrong port
cat ~/Library/LaunchAgents/com.clawdbot.jbphoenix.plist | grep -A6 ProgramArguments
# Output shows: --port 18789 (WRONG!)
```

### Affected Areas

1. LaunchAgent plist ProgramArguments
2. CLAWDBOT_GATEWAY_PORT environment variable

### Suggested Fix

`daemon install` should:
1. Read `gateway.port` from the profile's config file
2. Use that value in the generated plist's ProgramArguments
3. Set CLAWDBOT_GATEWAY_PORT env var to match

### Workaround

Manually edit the plist after installation to correct the port.

---
Reported: 2026-01-16

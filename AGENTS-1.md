
# AGENTS.md - Instructions for Agents 

## Available agents on m1mini 

## helix 

Description: local only bot, no telegram or other external channels connected 
Port: 18789
Restart: clawdbot daemon restart

## jbclawd

Description: Main Bot via telegram 
Port: 27800
Restart: clawdbot --profile jbclawd daemon restart 

## jbphoenix

Description: Rescue Bot for telegram 
Port: 28800
Restart: clawdbot --profile jbphoenix daemon restart

## Update rules for m1mini system 

1. check you are on the right system with `hostname` shell command 
2. Run `git pull` in ~/clawdbot 
3. Run `pnpm i && pnpm build` in ~/.clawdbot 
4. Restart the bots in that order: jbphoenix, helix, jbclawd 
- 

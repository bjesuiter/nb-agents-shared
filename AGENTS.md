---
title: agents-shared Notebook Rules
owner: system
---

## File: available-bots.md

Contains infrastructure details for all agents (JBClawd, JBPhoenix).

**Contents:**
- Bot name, port, URL
- Launchd file location
- Start script path
- Working directory & workspace
- Restart commands
- Update procedure

**Purpose:** Each agent can look up how to restart or update the other agent.

## Usage

- Read at session start to know active agents
- Update when infra changes
- JBClawd section: self-referential
- JBPhoenix section: cross-agent reference

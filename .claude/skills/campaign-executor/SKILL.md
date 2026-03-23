---
name: campaign-executor
description: |
  Execute email campaigns autonomously with rate limiting and compliance checks.
  Handles batch sending, delay management, and delivery tracking.
  Use this skill when the outreach-manager delegates actual campaign execution.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Campaign Executor Skill

Executes email campaigns with rate limiting, compliance checks, and delivery tracking.

## When to Use This Skill

This skill is called by the outreach-manager to execute approved campaigns. It handles:
- Batch email sending with configurable delays
- Rate limit enforcement (daily/hourly limits)
- Bounce and delivery tracking
- Campaign pause/resume functionality

## Execution Flow

1. Load campaign configuration from `campaigns/active/`
2. Verify all recipients have been QA-checked
3. Send emails in batches using the gmail-adapter
4. Log results to `campaigns/logs/`
5. Move completed campaigns to `campaigns/completed/`

## Script

```bash
python .claude/scripts/send_campaign.py --campaign-id <ID>
```

## Rate Limits

- Default: 100 emails/day, 50/batch, 60s delay between sends
- Configurable via `.env` overrides

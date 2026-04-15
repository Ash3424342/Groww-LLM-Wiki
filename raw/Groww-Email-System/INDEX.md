# Groww Email System — Project Index

> **Status**: In Progress (Phase 2 of 5)
> **Last updated**: 2026-04-03
> **Owner**: Ashish Chhabra (Growth Engagement, Groww)

## Quick links

- [[PROJECT_STATE]] — Current build status, what's done, what's next
- [[ARCHITECTURE]] — Three-layer system design (tokens → blocks → recipes)
- [[CHANGELOG]] — Every change logged with date and context
- [[DESIGN_TOKENS]] — Locked color, typography, spacing values
- [[BLOCK_CATALOG]] — All email section blocks with params
- [[RECIPE_CATALOG]] — Email recipes (JSON configs)
- [[CHART_AGENT]] — Chart image generation pipeline
- [[DECISIONS]] — Key architectural decisions and why
- [[CLAUDE_CODE_CONTEXT]] — Paste this into Claude Code to resume any session
- [[SCREENSHOTS_ANALYZED]] — All reference emails cataloged
- [[OPEN_ISSUES]] — Known bugs, visual mismatches, TODO items

## What is this project?

A system that generates **email-ready HTML and chart PNG images** for Groww and 915 brand email campaigns. Instead of building each email from scratch (which took 6 iterations last time), emails are assembled from reusable blocks using JSON recipes.

**Architecture**: Design tokens → Reusable section blocks → JSON recipes → Assembler engine → Final HTML

**Two sub-projects**:
1. `groww-creative-mcp` — MCP server with email assembly tools
2. `chart-image-agent` — Python CLI that generates retina PNG chart cards

## File locations

| Component | Path |
|-----------|------|
| MCP Server | `/Users/ashishch/Downloads/To Build/groww-creative-mcp/` |
| Chart Agent | `/Users/ashishch/Downloads/To Build/chart-image-agent/` |
| MCP Config | `~/.mcp.json` |
| This vault | `/Users/ashishch/Desktop/Groww/Groww-Email-System/` |

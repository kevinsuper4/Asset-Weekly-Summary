---
name: asset-weekly-summary
description: Generate the Chinese “资产优选周会纪要” from DingTalk data. Use when the user asks to create, update, or standardize an 资产优选/选品周会 weekly summary using 钉钉日历, AI听记, and the group “策略🐮--客户受益才是王道”; especially when applying the fixed meeting-window, product-research, business-support, and capability-improvement rules for 选品周会.
---

# Asset Weekly Summary

## Overview

Generate a concise weekly summary for “资产优选周会纪要 yyyy/mm/dd” by combining:

- DingTalk calendar times for exact-title “选品周会”.
- Group research notes from “策略🐮--客户受益才是王道” only for `1、产品调研`.
- Selected “选品周会” AI minutes mainly for `2、业务支持` and `3、能力提升`.

Use the `dws` skill for DingTalk operations. Every `dws` command must include `--format json`.

Read [summary-rules.md](references/summary-rules.md) before drafting the final weekly summary.

## Workflow

1. Find the meeting window from DingTalk calendar:
   - Query calendar events around the current date.
   - Keep only events whose `summary` is exactly `选品周会`.
   - Current meeting = today’s exact-title `选品周会`.
   - Previous meeting = the exact-title `选品周会` immediately before the current meeting.
   - Window = previous meeting start time to current meeting start time.
   - Exclude similarly named events such as `稳健选品周会`.

2. Get product research notes from the group:
   - Find the group whose title is exactly `策略🐮--客户受益才是王道`.
   - Default target userIds: `478908,039953,364115,363555,392507,283083,531366,542895`.
   - If the user gives a different list, use the user’s list.
   - Prefer sender-based retrieval (`chat message list-by-sender`) over keyword search.
   - Filter to the target group and the meeting window.
   - Keep only research-note-style messages. Exclude prior weekly-summary content, business battlefield summaries, casual discussion, replies, and non-research forwards.

3. Parse product research:
   - Extract product/fund name from the first title line.
   - Extract the shortest usable conclusion from fields like `结论`, `核心结论`, or `调研结论`; for “整体评价” paragraphs, summarize the product decision in one short clause.
   - Classify into the three fixed product-research branches and their child tracks using [summary-rules.md](references/summary-rules.md).
   - Merge products in the same child track into one line: `赛道：产品1（结论）、产品2（结论）`.

4. Select AI minutes for non-product sections:
   - If the user specifies an AI minutes item, use that specified item.
   - If the user does not specify one, read the most recent AI minutes whose title is exactly `选品周会`.
   - Use the selected AI minutes mainly to draft:
     - `2、业务支持`
     - `3、能力提升`
   - Make these two sections concise but not empty. Use one compact sentence for a simple section; use at most 2 short bullets only when a section has clearly separate points.
   - Do not mention personal names in these two sections; use roles or teams only when necessary.
   - Exclude product research items, product-specific conclusions, and market views from these two sections. Keep only business progress, rules/processes, operational support, data/tool capability, staffing, and workflow improvements.
   - Do not use AI minutes product-research content for `1、产品调研` unless the user explicitly changes the rule.

5. Draft the final summary:
   - Keep conclusions concise.
   - Preserve the three product-research big branches even if a branch has no child line.
   - Do not write empty child tracks.
   - Use the exact output structure in [summary-rules.md](references/summary-rules.md).

## DWS Tips

- Calendar list has only time-range filters; query a practical range, then filter exact `summary` locally.
- If a wide calendar query times out, retry once with `--verbose`, then narrow the date range.
- If `dws` fails with a local panic like `chat_permission_grant flag redefined`, create a temporary `DWS_CONFIG_DIR`/`DWS_CACHE_DIR` copy and remove the conflicting IM service from the temp cache only. Do not modify the real `~/.dws`.

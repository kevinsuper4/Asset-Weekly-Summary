# 资产优选周会纪要规则

## Output Template

```text
资产优选周会纪要 yyyy/mm/dd

1、产品调研

偏股金选：
赛道：产品1（结论）、产品2（结论）

稳健金选/货架：
赛道：产品1（结论）、产品2（结论）

余额宝/攒着：
余额宝/攒着：产品1（结论）、产品2（结论）

2、业务支持

余额宝战场：...
  - ...
  - ...

稳健战场：...
  - ...
  - ...

权益战场：...
  - ...
  - ...

黑卡理财师：...
  - ...
  - ...

3、能力提升

...
  - ...
  - ...
```

## Time Window

- Calendar event title must be exactly `选品周会`.
- Current meeting is today’s exact-title `选品周会`.
- Previous meeting is the exact-title `选品周会` immediately before today’s current meeting.
- Group research window is `[previous meeting start, current meeting start]`.
- Exclude events whose names merely contain the phrase, such as `稳健选品周会`.

## Product Research Sources

- Use the group `策略🐮--客户受益才是王道` only for `1、产品调研`.
- Do not use previous weekly-summary content found in the group.
- Keep only messages that look like product research notes, usually with title + `整体评价`/`概览`/`结论`/`核心结论`/`调研结论`/`市场适应性`/`Alpha`/`风险点`/`调研感受`.
- Exclude business-summary lines, casual chat, operational coordination, and non-research forwards.
- Use AI minutes mainly for `2、业务支持` and `3、能力提升`.

## AI Minutes Selection

- If the user specifies an AI minutes item, use the specified item.
- If the user does not specify one, read the most recent AI minutes whose title is exactly `选品周会`.
- Draft `2、业务支持` and `3、能力提升` mainly from the selected AI minutes.
- Make `2、业务支持` and `3、能力提升` concise but useful. Prefer one compact sentence under each battlefield/capability theme; use at most 2 short bullets only when the points are clearly separate.
- Do not mention personal names in `2、业务支持` or `3、能力提升`; use roles or teams only when necessary.
- Avoid over-splitting into many bullets.
- Do not include product research products, product-specific conclusions, fund manager views, asset allocation opinions, funding/market trend judgments, or market观点 in `2、业务支持` or `3、能力提升`.
- Keep non-product sections focused on business support, rules/process progress, operational coordination, data/tool capability, staffing, and workflow improvement.
- Do not use AI minutes product-research content for `1、产品调研` unless the user explicitly changes that rule.

## Product Research Structure

Always keep the three big branches:

1. `偏股金选`
2. `稳健金选/货架`
3. `余额宝/攒着`

Do not write child tracks that have no product research.

### 偏股金选

Use for equity funds. Child tracks are the equity赛道 inferred from the research note, such as:

- `成长`
- `科技`
- `均衡`
- `制造`
- `医药`
- `能涨抗跌`

When multiple products share one track, write one merged line:

```text
成长：融通转型三动力（成长备选关注）、景顺长城品质投资（备选关注）
```

### 稳健金选/货架

Child tracks are:

- `定期+`
- `收益+`
- `求赚`
- `周周宝`

Classification rules:

- If the message/title/fields involve `周周宝`, classify as `周周宝`.
- If they involve `定期+`, classify as `定期+`.
- If they involve `收益+` or `求稳`, classify as `收益+`.
- Within this stable branch, if none of `定期+`, `收益+`, `求稳`, or `周周宝` appears, classify as `求赚`.

Important: products involving the `求稳` field are `收益+` products.

### 余额宝/攒着

Use for balance/cash-management products involving `余额宝`, `攒着`, `货币`, or related money-market product research.

Write one merged child line:

```text
余额宝/攒着：华泰紫金货币增利（...）、国泰利是宝（...）
```

## Wording

- Keep each conclusion short, preferably one clause.
- Remove detailed reasoning, performance statistics, and long risk narratives unless necessary for the conclusion.
- Prefer product names without manager names or product codes unless needed to disambiguate.
- Keep Chinese punctuation and the user’s section numbering style.

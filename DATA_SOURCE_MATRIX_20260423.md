# ACC102 Data Source Matrix - 20260423

## Objective

Lock a free-first, authority-aware, engineering-stable data source plan for the project.

## Source Matrix

| DATA_LAYER | RECOMMENDED_SOURCE | AUTHORITY_LEVEL | COST_LEVEL | ENGINEERING_STABILITY | ROLE |
| --- | --- | --- | --- | --- | --- |
| STOCK_UNIVERSE | Official CSI constituent source exported to CSV | High | Free | High | primary |
| DAILY_PRICE | Tushare `pro_bar` adjusted daily data | Medium-High | Free if student points available | High | primary |
| DAILY_BASIC | Tushare `daily_basic` | Medium-High | Free if student points available | High | primary |
| MONEYFLOW | Tushare `moneyflow` | Medium-High | Free if student points available | High | primary |
| MARGIN_DETAIL | Tushare `margin_detail` | Medium-High | Free if student points available | High | primary |
| STK_LIMIT | Tushare `stk_limit` | Medium-High | Free if student points available | High | primary |
| SHARE_FLOAT | Tushare `share_float` | Medium-High | Free if student points available | High | primary |
| FINA_INDICATOR | Tushare `fina_indicator` by single stock | Medium-High | Usually still acceptable | Medium | optional |
| BOND_YIELD | AKShare `bond_gb_zh_sina` | Medium | Free | Medium | optional |

## Mainline Recommendation

### Recommended Mainline V1

- Use official source once to build `universe_YYYYMMDD.csv`
- Use Tushare for core daily and feature layers
- Use AKShare only for macro supplement
- Keep finance and macro as optional layers until core pipeline is stable

### Why This Mainline

- best balance between free access and structured retrieval
- easiest to explain in README and reflection
- strong enough for Track 4 without overspending
- keeps the MVP focused on volatility rather than data over-collection

## Free-First Paths

### Path A - Recommended

- Official constituent CSV
- Tushare with student points
- AKShare supplement

Pros:

- strong engineering structure
- low cost
- easier feature completeness

Risks:

- requires user account setup and token handling

### Path B - Backup

- Official constituent CSV
- AKShare-only simplified pipeline

Pros:

- no Tushare dependency
- fully free

Risks:

- some fields less convenient or less stable
- weaker traceability story for certain feature layers
- likely requires scope reduction

## Must-Have APIs For MVP

- price adjusted daily
- daily basic metrics
- stock universe source

## Strongly Recommended APIs For Better Score

- moneyflow
- margin_detail
- stk_limit
- share_float

## Optional APIs

- fina_indicator
- bond yield
- broader macro variables

## Decision Gates

### Gate 1 - Stock Universe

Options:

- CSI 300 official constituents
- curated liquid stock pool

Recommendation:

- CSI 300 official constituents

### Gate 2 - Data Access Route

Options:

- Tushare student-free route
- AKShare-only route

Recommendation:

- Tushare student-free route if eligible

## Current Decision Status

- STOCK_UNIVERSE: curated liquid stock pool selected
- DATA_ACCESS_ROUTE: AKShare-only route selected
- NOTE: upgrade to A + A remains reserved after lightweight MVP is stable

# System Pitch — Ogallala Groundwater Early-Warning Agent

## The user
Groundwater Conservation District (GCD) staff and agricultural extension
officers in the Texas Panhandle (e.g., North Plains GCD, Panhandle GCD) who
need to track aquifer depletion trends at the county/district level, plus
policymakers who allocate conservation funding based on those trends.

## The problem
The Ogallala Aquifer is depleting faster than recharge across the
Panhandle, but the data that would reveal this early — well-level readings
(USGS, TWDB), agricultural water-use and irrigation records (USDA, TWDB),
and precipitation data — is fragmented across agencies, inconsistent in
format, and rarely synthesized into an actionable signal until depletion is
already severe. Decision-makers currently react to crisis-level data rather
than catching unsustainable withdrawal trends early enough to intervene
(irrigation efficiency programs, water-right adjustments, crop-mix
incentives).

## Why this system can take all twelve layers
- **Loop / patterns**: a recurring agent loop that pulls new readings, reasons about trend deviation, and decides whether to escalate.
- **Tools**: API/data-pull tools for TWDB, USGS, USDA sources.
- **MCP**: exposing the data pipeline and ledger as MCP tools/resources for other agents or a dashboard to query.
- **Context**: multi-year trend windows per well/district; compaction as history grows.
- **Memory**: persistent state of prior alerts, false positives, district-specific baselines.
- **Multi-agent**: a data-collection agent, a forecasting agent, an adversarial-review agent (stress-testing forecasts before they go out), and a communication agent — mirroring the 5-agent architecture already designed for the parallel Killgore rural-hospital early-warning system.
- **Evaluation**: backtesting forecasts against known historical depletion events; golden cases from documented past drawdown periods.
- **Deployment**: served as a scheduled/triggered pipeline with a rollback path if a data source format changes.

## Biggest risk
Data-source instability — TWDB or USGS changing reporting formats or API
structure mid-project. This is a data-cleaning problem, not a
project-ending one, provided the ingestion layer is built to detect and
flag schema drift rather than silently failing (same mitigation approach
already used in the Killgore project's Phase 1 quality pipeline).

---

## PEAS specification

| Element | Specification |
|---|---|
| **Performance measure** | Lead time between an alert and the point of critical/unsustainable depletion; precision/recall of alerts (false-positive rate districts can tolerate); actionability as judged by GCD staff |
| **Environment** | Texas Panhandle counties overlying the Ogallala Aquifer; public data sources (TWDB, USGS, USDA); partially observable (data lags, gaps) and dynamic (seasonal, multi-year trends) |
| **Actuators** | Alert reports, dashboard updates, and recommendation summaries delivered to GCD staff and policymakers |
| **Sensors** | API/data pulls: TWDB well-level readings, USGS groundwater data, USDA agricultural water-use data, precipitation/weather data |

## PEAS → nine components mapping

| PEAS element | Maps to component(s) |
|---|---|
| Environment | Foundation (what data/model it stands on), Perception (what it reads from that environment) |
| Sensors | Perception, Tools (how data is pulled and validated) |
| Actuators | Governance & human interface (who receives/approves an alert), Runtime (how/when it's delivered) |
| Performance measure | Evaluation (how forecast quality is checked and failures are caught) |

*(Planning, Memory & context, and Coordination round out the remaining
components — these describe internal reasoning/architecture rather than
mapping directly to a single PEAS element, and should be addressed in your
Design Analysis and later ADRs.)*

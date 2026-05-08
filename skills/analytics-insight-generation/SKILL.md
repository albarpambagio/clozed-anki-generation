---
name: analytics-insight-generation
description: Generate structured business insights from data analysis using the SCAN framework. Use when analyzing data findings, writing insights logs, or translating analytical results into actionable business recommendations.
---

# Analytics Insight Generation

Transform raw findings into structured, actionable business insights using the SCAN framework.

## SCAN Framework

### S — Summarize

Lead with the key finding in one sentence:

```
[Finding]: [Specific number/trend] — [Business implication]
```

### C — Context

Explain why this matters:
- What's the baseline or benchmark?
- Is this better or worse than expected?
- What time period does it cover?

### A — Analyze

Dig deeper into the finding:
- What factors explain this pattern?
- What segments are driving the trend?
- Is this a one-time event or ongoing pattern?

### N — Note

Document caveats and next steps:
- Data limitations affecting this insight
- Further investigation needed
- Recommended actions

## Insight Categorization

Organize findings into three types:

### Market Context (Background)
Insights that explain "why" but aren't directly actionable:
- Seasonal patterns
- Market concentration
- Behavioral trends

### Further Investigation (Signal)
Observations worth exploring but needing more data:
- Anomalies that might be noise or signal
- Correlations without established causation
- Segments too small for confident conclusions

### Actionable Recommendations (Priority)
Specific, targeted actions with expected impact:
- Who to target
- What to do
- Expected outcome (quantified)

## Recommendation Template

```markdown
#### [Title] ([Priority])

**Target:** [Who or what this addresses]
- [Customer segment, region, category]

**Actions:**
- [Specific, concrete actions]

**Expected Impact:**
- [Quantified outcome with assumptions]
```

## Insights Log Template

```markdown
# Insights Log

## Key Metrics
| Metric | Value | Benchmark | Trend |
|--------|-------|-----------|-------|
| [Metric] | [Value] | [Comparison] | [Up/Down/Stable] |

## Top Findings

### Finding 1: [Title]
- **Summary**: [One sentence]
- **Context**: [Why it matters]
- **Analysis**: [What drives it]
- **Recommendation**: [What to do]

### Finding 2: [Title]
- **Summary**: [One sentence]
- ...
```

## North Star Metrics

Define the single most important metric that guides decisions:

```
North Star = [Metric] ([Value])
Stakeholder Team = [Who owns it]
Levers = [Actions they can take]
```

Decompose it to understand drivers:

```
Revenue = Order Volume × AOV
  ↓               ↓
Marketing       Pricing
```

When revenue dips, ask:
- Fewer orders? → Marketing issue
- Lower prices? → Pricing issue

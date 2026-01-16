# Event Ontology Generation Template

## Purpose
Generate semantic knowledge graphs for equity analysis using [[wikilinks]] syntax compatible with InfraNodus visualization.

## Core Principles

### 1. Network Structure (Not Trees)
- **AVOID**: Hub-and-spoke patterns where everything connects to one central node
- **CREATE**: Distributed networks with multiple interconnected clusters
- **TARGET**: Graph density where most nodes have 2-4 connections

### 2. Relationship Types

| Code | Meaning | Use Case |
|------|---------|----------|
| `[causes]` | Direct causation | Revenue growth → Stock appreciation |
| `[enables]` | Makes possible | Technology → New products |
| `[threatens]` | Poses risk | Competition → Margin pressure |
| `[dependentOn]` | Prerequisite | Growth → Consumer spending |
| `[supports]` | Reinforces | Moat → Pricing power |
| `[opposes]` | Works against | Regulation → Expansion |
| `[temporallyPrecedes]` | Time sequence | Q1 earnings → Q2 guidance |
| `[correlatesWith]` | Co-movement | Interest rates → Multiples |
| `[amplifies]` | Increases effect | Network effects → Growth |
| `[mitigates]` | Reduces impact | Diversification → Risk |

### 3. Entity Categories to Include

**Company-Specific**:
- Revenue streams
- Product lines
- Key executives
- Strategic initiatives
- Competitive advantages

**Market Factors**:
- Industry trends
- Competitor actions
- Supply chain dynamics
- Customer segments

**Macro Factors**:
- Interest rates
- Economic indicators
- Regulatory environment
- Geopolitical factors

**Catalyst Events**:
- Earnings releases
- Product launches
- M&A activities
- Management changes

## Generation Rules

### Minimum Requirements
- **Standard Analysis**: 15-20 relationship statements
- **Detailed Analysis**: 25-35 relationship statements

### Balance Requirements
- At least 40% bullish pathways
- At least 30% bearish/risk pathways
- At least 20% neutral/structural connections
- Include both short-term and long-term relationships

### Structural Patterns to Include

**Causal Chains** (A → B → C):
```
[[Interest Rate Hikes]] causes [[Multiple Compression]] [causes]
[[Multiple Compression]] threatens [[Stock Price]] [threatens]
```

**Feedback Loops** (A ↔ B):
```
[[Revenue Growth]] enables [[R&D Investment]] [enables]
[[R&D Investment]] supports [[Revenue Growth]] through innovation [supports]
```

**Triangular Relationships**:
```
[[Consumer Sentiment]] affects [[iPhone Sales]] [causes]
[[iPhone Sales]] drives [[Services Attach Rate]] [enables]
[[Services Attach Rate]] supports [[Recurring Revenue]] [supports]
[[Recurring Revenue]] mitigates [[Consumer Sentiment]] volatility [mitigates]
```

## Output Format

```
[[Entity A]] relation description [[Entity B]] [relationCode]
```

**Rules**:
- One statement per line
- Both entities in [[wikilinks]]
- Natural language description between entities
- Relation code in [brackets] at end
- No blank lines between statements

## Quality Checklist

Before finalizing Event Ontology:
- [ ] 15+ relationship statements (25+ for detailed)
- [ ] No single entity appears in >30% of statements
- [ ] Both bullish and bearish pathways included
- [ ] Macro and micro factors connected
- [ ] Temporal sequence of catalysts captured
- [ ] Can be directly pasted into InfraNodus

## Example: Complete Ontology (NVDA)

```
[[AI Demand]] enables [[Data Center Revenue]] growth [enables]
[[Data Center Revenue]] supports [[Gross Margin Expansion]] [supports]
[[Gross Margin Expansion]] causes [[EPS Beat]] expectations [causes]
[[EPS Beat]] amplifies [[Investor Sentiment]] [amplifies]
[[Investor Sentiment]] correlates with [[Valuation Multiple]] [correlatesWith]
[[China Export Ban]] threatens [[Revenue Diversification]] [threatens]
[[Revenue Diversification]] depends on [[Gaming Recovery]] [dependentOn]
[[Gaming Recovery]] correlates with [[Consumer Spending]] [correlatesWith]
[[Consumer Spending]] depends on [[Employment Levels]] [dependentOn]
[[Competition from AMD]] opposes [[Market Share]] dominance [opposes]
[[Market Share]] enables [[Pricing Power]] [enables]
[[Pricing Power]] supports [[Gross Margin Expansion]] [supports]
[[Blackwell Architecture]] temporally precedes [[Next Gen Adoption]] [temporallyPrecedes]
[[Next Gen Adoption]] enables [[Data Center Revenue]] acceleration [enables]
[[Automotive Segment]] diversifies [[Revenue Concentration]] risk [mitigates]
[[Supply Chain Constraints]] threatens [[Production Volume]] [threatens]
[[Production Volume]] depends on [[TSMC Capacity]] [dependentOn]
[[TSMC Capacity]] correlates with [[Geopolitical Risk]] [correlatesWith]
[[Geopolitical Risk]] threatens [[Supply Chain Stability]] [threatens]
[[Software Ecosystem (CUDA)]] supports [[Competitive Moat]] [supports]
[[Competitive Moat]] enables [[Pricing Power]] sustainability [enables]
```

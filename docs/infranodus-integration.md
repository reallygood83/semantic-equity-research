# InfraNodus Integration Guide

## Overview

[InfraNodus](https://infranodus.com) is a text network analysis tool that visualizes ideas as knowledge graphs. The Semantic Equity Research plugin generates output specifically formatted for InfraNodus compatibility.

---

## Quick Start

### Step 1: Generate Report

```bash
/semantic-research AAPL
```

### Step 2: Locate Event Ontology Section

Find Section 9 in the output:

```
### 9. 🕸️ EVENT ONTOLOGY

[[iPhone Revenue]] depends on [[Consumer Spending]] for growth [dependentOn]
[[Consumer Spending]] correlates with [[Interest Rate Policy]] [correlatesWith]
...
```

### Step 3: Copy to InfraNodus

1. Go to [InfraNodus.com](https://infranodus.com)
2. Create new graph or open existing
3. Paste the ontology statements
4. Click "Add to Graph"

### Step 4: Analyze

InfraNodus will:
- Generate network visualization
- Identify topic clusters
- Find structural gaps
- Suggest new connections

---

## Understanding the Output

### [[Wikilinks]] Format

Entities in double brackets become **nodes**:
```
[[iPhone Revenue]]
[[Consumer Spending]]
[[Interest Rates]]
```

### Relation Codes

Text between entities plus codes become **edges**:
```
[[A]] relation description [[B]] [relationCode]
```

| Code | Edge Type | Visualization |
|------|-----------|---------------|
| `[causes]` | Causal | Directional arrow |
| `[enables]` | Enabling | Directional arrow |
| `[correlatesWith]` | Correlation | Bidirectional |
| `[opposes]` | Opposition | Different color |

---

## Advanced Usage

### Combining Multiple Analyses

Generate ontologies for related stocks:
```bash
/semantic-research AAPL
/semantic-research MSFT
/semantic-research GOOGL
```

Combine in single InfraNodus graph to see:
- Cross-company relationships
- Shared risk factors
- Competitive dynamics

### Gap Analysis

InfraNodus identifies **structural gaps**—areas where connections are missing.

**How to interpret**:
- Gap between Tech and Macro clusters → Analysis may underweight macro factors
- Gap between Bull and Bear pathways → Need more balance
- Isolated nodes → Underexplored factors

### Cluster Analysis

InfraNodus groups related nodes into **topic clusters**.

**Typical equity analysis clusters**:
- Financial metrics
- Growth catalysts
- Risk factors
- Macro environment
- Competitive dynamics

**Healthy analysis** shows connections between clusters, not isolated silos.

---

## InfraNodus Features for Equity Analysis

### 1. Network Statistics

| Metric | Meaning for Analysis |
|--------|---------------------|
| Modularity | How siloed are your analysis areas? |
| Density | How interconnected is your thesis? |
| Central Nodes | What factors dominate your thinking? |
| Betweenness | What factors bridge different areas? |

### 2. AI Gap Bridging

InfraNodus can suggest connections between clusters:
> "Consider connecting [[Interest Rates]] to [[iPhone Demand]] via [[Consumer Credit]]"

Use these suggestions to expand your analysis.

### 3. Research Questions

Based on gaps, InfraNodus generates research questions:
> "How might [[Geopolitical Risk]] affect [[Supply Chain]]?"

These become inputs for deeper analysis.

---

## Best Practices

### Do's

✅ **Include macro connections**
```
[[Fed Policy]] affects [[Valuation Multiples]] [correlatesWith]
```

✅ **Balance bull and bear**
```
[[AI Growth]] enables [[Revenue Expansion]] [enables]
[[Competition]] threatens [[Margin Sustainability]] [threatens]
```

✅ **Create chains, not stars**
```
A → B → C → D  (Good: Chain)
A → B, A → C, A → D  (Bad: Star)
```

### Don'ts

❌ **Avoid single hub**
```
# Bad: Everything connects to one node
[[AAPL]] has [[Strong Brand]] [hasAttribute]
[[AAPL]] has [[Large Cash]] [hasAttribute]
[[AAPL]] has [[Services Growth]] [hasAttribute]
```

❌ **Avoid vague relations**
```
# Bad: Unclear relationship
[[Revenue]] is related to [[Profit]] [relatedTo]

# Good: Specific relationship
[[Revenue Growth]] enables [[Operating Leverage]] which supports [[Profit Expansion]] [enables]
```

---

## Troubleshooting

### Graph Too Dense

**Problem**: Too many connections, hard to read

**Solution**:
- Filter by relation type
- Focus on one cluster
- Increase minimum connection threshold

### Graph Too Sparse

**Problem**: Disconnected nodes, no patterns

**Solution**:
- Add more relationship statements
- Include transitional connections
- Check for missing macro-micro links

### Clusters Don't Make Sense

**Problem**: Groupings seem random

**Solution**:
- Review entity naming consistency
- Ensure similar concepts use same terms
- Add explicit bridge statements

---

## Export Options

InfraNodus exports to:
- **PNG/SVG**: For presentations
- **CSV**: For further analysis
- **JSON**: For programmatic access

### Integration with Other Tools

Export InfraNodus graph → Import to:
- Obsidian (via JSON)
- Neo4j (via CSV)
- Gephi (via GEXF)

---

## MCP Integration (Advanced)

If you have the InfraNodus MCP server configured:

```bash
# Generate and analyze in one step
/semantic-research AAPL --infranodus-analyze
```

This will:
1. Generate Event Ontology
2. Create InfraNodus graph via MCP
3. Return gap analysis results
4. Suggest additional research questions

**MCP Tools Available**:
- `InfraNodus:generate_knowledge_graph`
- `InfraNodus:generate_content_gaps`
- `InfraNodus:generate_research_questions`

---

## Resources

- [InfraNodus Documentation](https://infranodus.com/docs)
- [Cognitive Variability Framework](https://infranodus.com/about/cognitive-variability)
- [Network Analysis for Text](https://noduslabs.com/cases/text-network-analysis/)

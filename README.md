# Semantic Equity Research

> **Institutional-grade stock analysis enhanced with semantic knowledge graphs, critical thinking frameworks, and cognitive bias detection.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blue.svg)](https://claude.ai)

## Overview

Semantic Equity Research is a Claude Code plugin that transforms standard equity analysis into a comprehensive 11-section research report. By integrating semantic knowledge graph techniques from InfraNodus with traditional financial analysis, this plugin reveals hidden connections and challenges assumptions that conventional analysis misses.

### What Makes This Different?

| Traditional Analysis | Semantic Equity Research |
|---------------------|--------------------------|
| Linear narrative | Network of interconnected factors |
| Implicit assumptions | Explicit assumption inventory |
| Single perspective | Cognitive state awareness |
| Static catalysts | Dynamic event relationships |

## Features

### 📊 Core Analysis (Sections 1-8)
- Executive Summary with investment rating
- Fundamental Analysis with peer comparison
- Catalyst Analysis with timeline
- Valuation & Price Targets (Bull/Base/Bear scenarios)
- Risk Assessment with position sizing
- Technical Context with key levels
- Market Positioning
- Insider Signals

### 🕸️ Semantic Enhancement (Sections 9-11)

**9. Event Ontology**
- Knowledge graph in [[wikilinks]] format
- 15-25 relationship statements
- Compatible with [InfraNodus](https://infranodus.com) visualization
- Reveals hidden catalyst connections

**10. Critical Assumptions Check**
- 5+ hidden assumptions surfaced
- Devil's Advocate questioning
- Pre-Mortem failure scenarios
- Warning signs to monitor

**11. Cognitive State Alert**
- 4-state classification (BIASED/FOCUSED/DIVERSIFIED/DISPERSED)
- Bias detection checklist
- Narrative dominance analysis
- Actionable recommendations

## Installation

### Claude Code CLI

```bash
# Clone the repository
git clone https://github.com/reallygood83/semantic-equity-research.git

# Copy to Claude commands directory
cp -r semantic-equity-research/commands/* ~/.claude/commands/
```

### Manual Installation

1. Download this repository
2. Copy `commands/semantic-research.md` to `~/.claude/commands/`
3. Optionally copy `config/prompts/` for template references

## Usage

### Basic Analysis

```bash
/semantic-research AAPL
```

Generates complete 11-section analysis of Apple Inc.

### Detailed Analysis

```bash
/semantic-research NVDA --detailed
```

Enhanced analysis with:
- 25+ Event Ontology relationships
- 8+ Critical Assumptions
- Extended Pre-Mortem scenarios

### Korean Stocks

```bash
/semantic-research 005930.KS
```

Includes Korea-specific considerations (exchange rate, chaebol governance, etc.)

## Output Example

### Event Ontology Sample (AAPL)

```
[[iPhone Revenue]] depends on [[Consumer Spending]] for growth [dependentOn]
[[Consumer Spending]] correlates with [[Interest Rate Policy]] [correlatesWith]
[[Services Revenue]] mitigates [[iPhone Cyclicality]] [mitigates]
[[AI Integration]] supports [[iPhone Upgrade Cycle]] acceleration [supports]
[[China Sales]] depends on [[Geopolitical Stability]] [dependentOn]
[[Vision Pro Launch]] enables [[Spatial Computing Ecosystem]] development [enables]
```

### Cognitive State Alert Sample

```
**This Analysis Classification**: 🟡 FOCUSED

**Reasoning**: The analysis has a strong bullish thesis centered on AI
integration, with moderate acknowledgment of risks. Counter-narratives
(China exposure, premium pricing limits) are mentioned but not deeply explored.

**Bias Alerts**:
- [x] Recency Bias: Heavy emphasis on recent AI announcements
- [x] Authority Bias: Multiple Goldman Sachs citations without questioning
- [ ] Anchoring: Not detected

**Recommendation for Reader**:
> "Expand your China risk analysis. Consider what happens if AI features
underdeliver on initial promise."
```

## InfraNodus Integration

The Event Ontology output can be directly pasted into [InfraNodus.com](https://infranodus.com) for:

1. **Network Visualization**: See how catalysts interconnect
2. **Gap Analysis**: Find missing connections
3. **Cluster Identification**: Group related factors
4. **AI Insights**: Generate additional perspectives

### How to Use

1. Generate report with `/semantic-research TICKER`
2. Copy the Event Ontology code block
3. Paste into InfraNodus text input
4. Analyze the resulting knowledge graph

## Methodology

See [docs/methodology.md](docs/methodology.md) for detailed explanation of:
- Cognitive Variability Framework
- Ontology Generation Principles
- Critical Perspective Methodology
- Bias Detection Techniques

## File Structure

```
semantic-equity-research/
├── .claude-plugin/
│   ├── marketplace.json      # Plugin metadata
│   └── plugin.json           # Configuration
├── commands/
│   └── semantic-research.md  # Main command (11 sections)
├── config/prompts/
│   ├── event-ontology.md     # Ontology generation rules
│   ├── critical-assumptions.md # Assumption surfacing
│   └── cognitive-alert.md    # Cognitive state detection
├── docs/
│   ├── methodology.md        # Theoretical background
│   └── infranodus-integration.md
├── examples/sample_reports/
├── README.md
└── LICENSE
```

## Requirements

- Claude Code CLI or Claude Desktop
- Web search capability (for real-time data)
- Optional: InfraNodus account for visualization

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

### Areas for Improvement

- Additional relation codes for ontology
- Industry-specific templates
- Localization (Korean, Japanese, etc.)
- Additional cognitive frameworks

## Credits

- **Base Framework**: Inspired by [claude-equity-research](https://github.com/quant-sentiment-ai/claude-equity-research)
- **Semantic Methods**: Based on [InfraNodus](https://infranodus.com) cognitive variability framework
- **Critical Thinking**: Adapted from structured analytic techniques

## License

MIT License - see [LICENSE](LICENSE) for details.

## Disclaimer

**This plugin is for educational and informational purposes only.** It does not constitute financial advice. All investments carry risk. AI-generated analysis may contain errors. Always conduct your own research and consult qualified professionals before making investment decisions.

---

Made with 🧠 semantic thinking

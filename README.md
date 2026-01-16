# Semantic Equity Research

> **Institutional-grade stock analysis enhanced with semantic knowledge graphs, cognitive frameworks, InfraNodus integration, and multi-language support.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blue.svg)](https://claude.ai)
[![Version](https://img.shields.io/badge/version-1.1.0-green.svg)]()

## Overview

Semantic Equity Research is a Claude Code plugin that transforms standard equity analysis into a comprehensive 11-section research report. By integrating semantic knowledge graph techniques from InfraNodus with traditional financial analysis, this plugin reveals hidden connections and challenges assumptions that conventional analysis misses.

### What Makes This Different?

| Traditional Analysis | Semantic Equity Research |
|---------------------|--------------------------|
| Linear narrative | Network of interconnected factors |
| Implicit assumptions | Explicit assumption inventory |
| Single perspective | Cognitive state awareness |
| Static catalysts | Dynamic event relationships |
| Manual InfraNodus | **Automatic MCP integration** |
| English only | **Multi-language output (KO/EN/JA/ZH)** |

## New in v1.1.0

### 🌐 Multi-Language Support
- **Analysis**: Always performed in English for data accuracy
- **Output**: Automatically translated to your preferred language
- **Default**: Korean (한국어)
- **Options**: English, Japanese (日本語), Chinese (中文)

### 🕸️ InfraNodus MCP Integration
- Automatic knowledge graph creation from Event Ontology
- Content gap analysis for investment blind spots
- AI-generated research questions
- No manual copy-paste required

### 📁 Smart Folder Management
- Set output folder once, auto-save all subsequent reports
- No repeated folder prompts within session

---

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

### 🆕 12. InfraNodus Visualization (semantic-infra only)
- Interactive knowledge graph link
- Content gaps (investment blind spots)
- AI-generated research questions
- Network statistics

---

## Installation

### Claude Code CLI

```bash
# Clone the repository
git clone https://github.com/reallygood83/semantic-equity-research.git

# Copy to Claude commands directory
cp -r semantic-equity-research/commands/* ~/.claude/commands/
```

### InfraNodus MCP Setup (Optional)

For automatic InfraNodus integration, add to `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "infranodus": {
      "command": "npx",
      "args": ["-y", "infranodus-mcp-server"],
      "env": {
        "INFRANODUS_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

Get your API key at [InfraNodus.com](https://infranodus.com/settings/api)

---

## Usage

### Basic Analysis (Korean output - default)

```bash
/semantic-research AAPL
```

Generates complete 11-section analysis of Apple Inc. in Korean.

### English Output

```bash
/semantic-research AAPL --lang=en
```

### Japanese Output

```bash
/semantic-research TSLA --lang=ja
```

### Chinese Output

```bash
/semantic-research MSFT --lang=zh
```

### Detailed Analysis

```bash
/semantic-research NVDA --detailed
```

Enhanced analysis with:
- 25+ Event Ontology relationships
- 8+ Critical Assumptions
- Extended Pre-Mortem scenarios

### With InfraNodus Integration

```bash
/semantic-infra AAPL
```

or

```bash
semantic-infra: AAPL
```

Creates automatic knowledge graph + content gap analysis.

### Korean Stocks

```bash
/semantic-research 005930.KS
```

Includes Korea-specific considerations (exchange rate, chaebol governance, etc.)

### Custom Output Folder

```bash
/semantic-infra PLTR --folder=/path/to/your/folder
```

---

## Language Workflow

```
┌─────────────────────────────────────────────────┐
│  1. Analysis: Always in English                 │
│     - WebSearch in English for accuracy         │
│     - Data collection in source language        │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│  2. Translation: To user's preferred language   │
│     - Korean (default)                          │
│     - English, Japanese, Chinese available      │
│     - Technical terms kept in original          │
└─────────────────────────────────────────────────┘
```

---

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

---

## InfraNodus Integration

### Automatic (with MCP)

Use `/semantic-infra TICKER` to automatically:

1. Generate 11-section analysis
2. Create InfraNodus knowledge graph
3. Analyze content gaps
4. Generate research questions
5. Add Section 12 with visualization link

### Manual

1. Generate report with `/semantic-research TICKER`
2. Copy the Event Ontology code block
3. Paste into InfraNodus text input
4. Analyze the resulting knowledge graph

---

## File Structure

```
semantic-equity-research/
├── .claude-plugin/
│   ├── marketplace.json           # Plugin metadata
│   └── plugin.json                # Configuration (v1.1.0)
├── commands/
│   ├── semantic-research.md       # Main command (11 sections)
│   └── semantic-research-infranodus.md  # InfraNodus integration (12 sections)
├── config/prompts/
│   ├── event-ontology.md          # Ontology generation rules
│   ├── critical-assumptions.md    # Assumption surfacing
│   └── cognitive-alert.md         # Cognitive state detection
├── docs/
│   ├── methodology.md             # Theoretical background
│   └── infranodus-integration.md
├── examples/sample_reports/
├── README.md
└── LICENSE
```

---

## Requirements

- Claude Code CLI or Claude Desktop
- Web search capability (for real-time data)
- Optional: InfraNodus MCP server for automatic integration
- Optional: InfraNodus account for manual visualization

---

## Version History

### v1.1.0 (2026-01-17)
- **NEW**: Multi-language support (ko, en, ja, zh)
- **NEW**: InfraNodus MCP automatic integration
- **NEW**: `/semantic-infra` command with Section 12
- **NEW**: Smart folder management (set once, auto-save)
- **CHANGE**: Korean is now default output language
- **CHANGE**: Analysis always in English, then translated

### v1.0.0 (2026-01-15)
- Initial release with 11-section analysis
- Event Ontology with wikilinks
- Critical Assumptions Check
- Cognitive State Alert

---

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

### Areas for Improvement

- Additional relation codes for ontology
- Industry-specific templates
- Additional languages (Spanish, German, etc.)
- Additional cognitive frameworks

---

## Credits

- **Base Framework**: Inspired by [claude-equity-research](https://github.com/quant-sentiment-ai/claude-equity-research)
- **Semantic Methods**: Based on [InfraNodus](https://infranodus.com) cognitive variability framework
- **Critical Thinking**: Adapted from structured analytic techniques

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Disclaimer

**This plugin is for educational and informational purposes only.** It does not constitute financial advice. All investments carry risk. AI-generated analysis may contain errors. Always conduct your own research and consult qualified professionals before making investment decisions.

---

Made with 🧠 semantic thinking | 한국어 지원 🇰🇷

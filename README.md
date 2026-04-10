# Trading Indicator Stack

A complete quantitative trading system: custom Pine Script indicators → automated Python trading bot → adaptive learning engine → web dashboard → full autonomous trading operation.

## 🎯 Project Vision

**Short-term:** Fix and enhance 3 core Pine Script indicators for 1-min small cap scalping.  
**Medium-term:** Build 2-3 new indicators (S/R, Reversal/Future, Dashboard).  
**Long-term:** Full Python trading bot with Webull API, adaptive learning engine, web dashboard (lightweight-charts-python), and eventual Lightspeed migration.

## Trading Style
- Long only
- 1-minute scalping
- Small cap top gainers (premarket through 11am ET)
- Use WAE+iTrend for momentum/volume entries
- Confirm with Adaptive Trailing Stop + HTF1/HTF2 alignment

## Existing Core Indicators
1. **WAE+JMAiTrend+IVR+URE+Trail v5.9** — Signal/entry indicator
2. **Multi-TF Scalper Edition v2** — Multi-timeframe confirmation
3. **JMA Adaptive Trailing Stop – Ehlers Cycle Edition v3.0** — Adaptive exit
4. **Quintuple Oscillator Heatmap – RSX+ROC+FVE+BFF+SDO** — Momentum consensus
5. **Reversal Regime Stack** — Reversal/regime detection

## Planned Builds
- **Phase 1:** Fix WAE trailing stop, A/B Zone in Multi-TF, Quint optimization + divergences
- **Phase 2:** Composite S/R indicator, Reversal/Future/Exit indicator
- **Phase 3:** Backtesting & optimization
- **Phase 4:** Python trading bot (Webull API)
- **Phase 5:** Adaptive learning engine
- **Phase 6:** Web dashboard (lightweight-charts-python + React)
- **Phase 7:** Scanner + full automation
- **Phase 8:** Go live + Lightspeed migration

## Project Structure
```
trading-indicator-stack/
├── docs/                    # Strategy, architecture, personal notes
├── indicators/
│   ├── existing/            # Live TradingView indicators
│   ├── source/              # Original building blocks
│   ├── ideas/               # Reference scripts to analyze
│   └── builds/              # New/modified indicators (v1, v2, v3)
├── analysis/                # Research findings & backtest results
├── bot/                     # Python trading bot
│   ├── core/                # Engine, signal processor, risk manager
│   ├── broker/              # Webull (now) + Lightspeed (future)
│   ├── learning/            # Adaptive learning engine
│   ├── api/                 # Webhook receiver + dashboard API
│   └── scheduler/           # Premarket scan, session manager
├── dashboard/               # Web dashboard (React + lightweight-charts)
├── scripts/                 # Utility scripts
└── CHECKLIST.md             # Master project checklist (129 items)
```

## 📊 Progress
See [CHECKLIST.md](CHECKLIST.md) for detailed progress tracking across all 8 phases.
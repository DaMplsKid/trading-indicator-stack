# 🏗️ TRADING INDICATOR STACK — MASTER CHECKLIST

## Vision
Build a complete quantitative trading system: custom Pine Script indicators → automated Python trading bot → adaptive learning engine → web dashboard (lightweight-charts-python) → full autonomous trading operation.

## Architecture
```
Phase 1-3:  TradingView (Pine) = Brain + Eyes
Phase 4-6:  TradingView (Pine) = Eyes + Brain  |  Python = Hands + Memory + Analytics
Phase 7+:   Python = Brain + Eyes (lightweight-charts) + Hands + Memory + Learning
            TradingView = Second monitor for quick visual checks
```

## Legend
- ⬜ Not started
- 🟡 In progress
- ✅ Complete
- ❌ Blocked / Skipped
- 🔒 Requires previous phase completion

---

# PHASE 0: PROJECT SETUP & DOCUMENTATION
> Goal: Organize the repo so AI agents can work effectively
> Timeline: Now

## 0.1 Repository Structure
- ✅ Create GitHub repo (DaMplsKid/trading-indicator-stack)
- ✅ Push 5 existing indicators to `indicators/existing/`
- ✅ Push source folders (Multi TF, Quint, Signal) to `indicators/source/`
- ✅ Push ideas folders (Dashboard, Divergences, Future, Misc, S/R) to `indicators/ideas/`
- ✅ Update README with full project vision and structure
- ⬜ Create full folder structure (bot, dashboard, docs/notes, analysis, scripts)
- ⬜ Push folder structure: `git add . && git commit -m "Phase 0: Create full project folder structure" && git push`

## 0.2 Create Empty Note Templates
> Purpose: Placeholder markdown files for each indicator. Fill in content BEFORE working on each indicator in Phase 1.
- ⬜ Create `docs/notes/wae_signal_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/multitf_scalper_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/quintuple_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/reversal_regime_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/trailing_stop_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/composite_sr_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/reversal_future_notes.md` (headers only, content TBD)
- ⬜ Create `docs/notes/dashboard_notes.md` (headers only, content TBD)
- ⬜ Push templates: `git add . && git commit -m "Phase 0: Add note templates" && git push`

## 0.3 Save Research Findings to Repo
- ⬜ Create `analysis/deep_analysis_results.md` — paste full PART I-VI research findings
- ⬜ Create `analysis/divergence_analysis.md` — paste divergence deep dive findings
- ⬜ Create `analysis/master_strategy.md` — paste Master Build Strategy from chat
- ⬜ Push: `git add . && git commit -m "Phase 0: Add research analysis docs" && git push`

## 0.4 Clean Up Duplicates
- ⬜ Delete `indicators/ideas/future/@version=6.txt` (duplicate of Neural Network Buy and Sell Signals.txt)
  - Command: `Remove-Item "indicators\ideas\future\@version=6.txt"`
- ⬜ Delete `indicators/ideas/future/K Clustering.txt` (duplicate of support_and_resistance/ version)
  - Command: `Remove-Item "indicators\ideas\future\K Clustering.txt"`
- ⬜ Push: `git add . && git commit -m "Phase 0: Remove duplicate files" && git push`

## 0.5 Convert Word Doc to Markdown
- ⬜ Open `docs/Complete Indicator Tracking, Thought...docx` in Word
- ⬜ Copy ALL text content
- ⬜ Create `docs/indicator_tracking_master.md` and paste (fix formatting as needed)
- ⬜ Push: `git add . && git commit -m "Phase 0: Convert Word doc to markdown" && git push`

## 0.6 Add Any Additional Indicators to Review
> Do this whenever you find new indicators you want analyzed
- ⬜ Copy new scripts to appropriate `indicators/ideas/` subfolder
- ⬜ Create a notes `.md` file for each explaining why you picked it
- ⬜ Push and request a research session to analyze

## 0.7 Create Architecture Docs
- ⬜ Create `docs/architecture/system_overview.md` — high-level diagram (Pine → Webhook → Python → Broker → Dashboard)
- ⬜ Create `docs/architecture/data_flow.md` — how data moves through the system
- ⬜ Create `docs/architecture/api_design.md` — webhook JSON format, dashboard API endpoints
- ⬜ Push: `git add . && git commit -m "Phase 0: Add architecture docs" && git push`

---

# PHASE 1: SHORT-TERM — Fix & Enhance Core 3 Indicators
> Goal: Get WAE Signal, Multi-TF Scalper, and Quintuple production-ready
> Timeline: After Phase 0
> Prerequisite: Fill in the specific notes file BEFORE starting each task
> Note: Don't fight Pine's 64-plot limit. Build what works. Python removes all limits later.

## 1.1 Fix WAE Trailing Stop
> The WAE v5.9 trailing stop needs to match the one in Multi-TF Scalper Edition v2

### Prep (do before launching any agent):
- ⬜ Fill in `docs/notes/trailing_stop_notes.md` with:
  - What's wrong with the current WAE trailing stop (be specific)
  - Open both indicators on same TradingView chart and screenshot differences
  - Describe desired behavior: "When price does X, the trailing stop should do Y"
  - Reference specific settings/inputs that need to match
- ⬜ Push notes: `git add . && git commit -m "Phase 1: Add trailing stop notes" && git push`

### Build:
- 🔒 Launch coding agent PR: "Read `docs/notes/trailing_stop_notes.md` for context. Extract the JMA Adaptive Trailing Stop function from `indicators/existing/multitf_scalper_v4.pine` and replace the trailing stop in `indicators/existing/wae_jma_itrend_ivr_ure_trail_v59.pine`. Ensure all parameters match. Save to `indicators/builds/v1/wae_signal_v6.0.pine`"
- 🔒 Review PR diff — verify trailing stop logic matches
- 🔒 Copy to TradingView Pine Editor → compile → check for errors
- 🔒 Load on 1-min chart with recent small cap gainer
- 🔒 Compare: does trailing stop now match Multi-TF version visually?
- 🔒 If issues: document in notes, launch fix PR
- 🔒 Merge PR when confirmed working

## 1.2 Solidify A Zone/B Zone Entry Criteria (Multi-TF Scalper)
> Define and code clear A Zone (high conviction) vs B Zone (moderate) entry grades

### Prep:
- ⬜ Fill in `docs/notes/multitf_scalper_notes.md` with:
  - Your definition of "A Zone" — what HTF alignment, oscillator state, volume condition
  - Your definition of "B Zone" — what's different from A Zone
  - 3-5 example trades: "This was A Zone because..." / "This was B Zone because..."
  - What indicator should SHOW differently for A vs B (colors? labels? alert text?)
  - Any screenshots of A Zone vs B Zone setups
- ⬜ Push notes

### Build:
- 🔒 Launch research session: "Read `indicators/existing/multitf_scalper_v4.pine` and `docs/notes/multitf_scalper_notes.md`. Analyze current entry logic. Propose code changes for A/B Zone classification."
- 🔒 Discuss findings in chat — refine A/B definitions
- 🔒 Launch coding agent PR to implement A/B Zone logic
- 🔒 Test on 1-min chart with 5+ recent trades
- 🔒 Verify: past A Zone trades labeled A? B Zone labeled B?
- 🔒 Iterate until classifications match your mental model
- 🔒 Save to `indicators/builds/v1/multitf_scalper_v3.pine`
- 🔒 Merge PR

## 1.3 Optimize Quintuple Oscillator
> Reduce compute load by 50-70% to make room for divergences

### Prep:
- ⬜ Fill in `docs/notes/quintuple_notes.md` with:
  - How long does Quint currently take to load? (rough seconds)
  - Does it ever timeout or fail?
  - Which visual elements are ESSENTIAL (Dots, Diamonds, heatmap colors, etc.)
  - Which could you lose if it helps performance
  - Divergence plans: how you want to use Dots/Diamonds for TP/breakeven
- ⬜ Push notes

### Build:
- 🔒 Launch coding agent PR:
  1. Replace 5 individual KDE distributions → 1 composite KDE on `consensus_score`
  2. Replace 5 individual peak/trough scans → 1 composite peak/trough
  3. Reduce `densityRange` 300→100, bins 200→100
  4. Reduce `max_bars_back` 5000→2500
  5. Ensure Dots fire at equivalent composite thresholds
  6. Ensure Diamonds fire at equivalent composite thresholds
  7. Save to `indicators/builds/v1/quintuple_optimized_v2.pine`
- 🔒 Test: load BOTH old and new Quint on same chart, compare
- 🔒 Measure load time: old vs new
- 🔒 Verify no visual regressions
- 🔒 Merge PR

## 1.4 Add Divergences to Optimized Quint
> Add divergence module using freed compute headroom

### Build:
- 🔒 Launch coding agent PR:
  1. Compute `avgQuintZ = (rsx_z + roc_z + fve_z + bff_z + sdo_z) / 5`
  2. Apply SA-EMA from `indicators/ideas/divergences/Dynamic Z-Score Divergence.txt`
  3. Implement Immediate Divergence Detection from `indicators/ideas/divergences/Divergence IQ.txt` (lines 586-689)
  4. Use composite peak/trough as divergence anchor pivots
  5. Add optional `request.security("30S")` for LTF divergence with toggle
  6. Display signals as labels (bull div = green ▲, bear div = red ▼)
  7. Add input group 'Divergence Settings'
  8. Save to `indicators/builds/v1/quintuple_divergence_v2.pine`
- 🔒 Test on 1-min small cap: do divergences fire at logical reversal points?
- 🔒 Test 30-sec LTF: fires earlier than 1-min mode?
- 🔒 Verify indicator loads within acceptable time
- 🔒 Merge PR

## 1.5 Review for Additional Enhancements
- 🔒 Launch research session: "Read all three v1 builds + all idea files. Identify enhancements that add value without significant compute cost."
- 🔒 Discuss findings in chat
- 🔒 Implement approved enhancements via coding agent PRs
- 🔒 Final test: all 3 v1 builds running together on same chart

---

# PHASE 2: MEDIUM-TERM — Build New Indicators
> Goal: Build Composite S/R and Reversal/Future/Exit indicators
> Timeline: After Phase 1 complete and tested
> Note: Pine Script dashboard DEFERRED — web dashboard in Phase 6 is superior (no plot limits, no compute limits)

## 2.1 Composite S/R + Market Structure Indicator
### Prep:
- ⬜ Fill in `docs/notes/composite_sr_notes.md` with:
  - S/R methods to include (ORB, BOS/CHOCH, K-Clustering, Institutional Levels CNN, Range Detection, Linear Regression, Divergence Zones)
  - Priority when levels overlap
  - Visual preferences (colors, line styles, zone fills, labels)
  - Session filtering preferences
- ⬜ Push notes

### Build:
- 🔒 Launch research session to design architecture
- 🔒 Discuss in chat, refine design
- 🔒 Launch coding agent PR
- 🔒 Save to `indicators/builds/v2/composite_sr_v1.pine`
- 🔒 Test alongside v1 indicators
- 🔒 Iterate and merge

## 2.2 Reversal/Future/Exit Regime Indicator
### Prep:
- ⬜ Fill in `docs/notes/reversal_future_notes.md` with:
  - How this works with entry indicators (what triggers exit?)
  - What "exit" means (full? partial? trail to breakeven?)
  - Preferred methods (HMM, Monte Carlo, K-Cluster, Neural Network)
  - Right-side-of-chart projection layout
  - Offset layering (Monte Carlo second, JMA forecast furthest)
- ⬜ Push notes

### Build:
- 🔒 Launch research session to design architecture
- 🔒 Discuss in chat, refine design
- 🔒 Launch coding agent PR
- 🔒 Save to `indicators/builds/v2/reversal_future_v1.pine`
- 🔒 Test alongside all indicators
- 🔒 Iterate and merge

## 2.3 Alert System for Each Indicator
> Each indicator fires its OWN alert — Python bot combines them server-side
> This avoids Pine's 64-plot limit (no hidden export plots needed)

- 🔒 Add `alertcondition()` to WAE Signal for entry/exit
- 🔒 Add `alertcondition()` to Multi-TF for zone grade changes
- 🔒 Add `alertcondition()` to Quintuple for divergence + KDE/Peak signals
- 🔒 Add `alertcondition()` to Composite S/R for level breaks
- 🔒 Add `alertcondition()` to Reversal/Future for regime changes + projections
- 🔒 Each alert sends JSON with indicator-specific data
- 🔒 Test: all alerts fire correctly on 1-min chart

---

# PHASE 3: BACKTESTING & OPTIMIZATION
> Goal: Convert indicators to strategies, backtest, optimize
> Timeline: After Phase 2 stable

## 3.1 Create Strategy Versions
- 🔒 `indicators/builds/strategies/wae_signal_strategy.pine`
- 🔒 `indicators/builds/strategies/multitf_scalper_strategy.pine`
- 🔒 `indicators/builds/strategies/composite_strategy.pine` (all signals combined)
- 🔒 Configure: `initial_capital=25000`, `commission_value=0`

## 3.2 Historical Backtesting
- 🔒 Run backtests on 10+ recent small cap gainers
- 🔒 Collect: win rate, profit factor, max drawdown, avg R-multiple
- 🔒 Save to `analysis/backtest_results.md`

## 3.3 Parameter Optimization
- 🔒 Test parameter variations (JMA lengths, ATR periods, Z-score lookbacks)
- 🔒 Find optimal params for 1-min small cap premarket
- 🔒 Save to `analysis/optimization_results.md`

## 3.4 Walk-Forward Testing
- 🔒 Optimize on 3 months → test on next 1 month (out-of-sample)
- 🔒 Document in `analysis/walk_forward_results.md`

---

# PHASE 4: PYTHON TRADING BOT — FOUNDATION
> Goal: Build core bot that receives TradingView alerts and executes on Webull paper
> Timeline: After Phase 3 proves profitability

## 4.1 Environment Setup
- ⬜ Install Python 3.11+
- ⬜ Create virtual environment: `python -m venv bot/venv`
- ⬜ Install: `pip install fastapi uvicorn httpx pydantic sqlalchemy psycopg2-binary`
- ⬜ Install Webull SDK: `pip install webull-python-sdk-core webull-python-sdk-trade webull-python-sdk-quotes-core`
- ⬜ Create `bot/requirements.txt`
- ⬜ Create `bot/config/.env.example` (never commit real keys)
- ⬜ Add `bot/config/.env` to `.gitignore`

## 4.2 Register for Webull API Access
- ⬜ Go to [developer.webull.com](https://developer.webull.com/)
- ⬜ Apply for API access
- ⬜ Generate app key + app secret
- ⬜ Store in `bot/config/.env`
- ⬜ Test connection
- ⬜ Confirm paper trading enabled

## 4.3 Build Broker Interface
- 🔒 `bot/broker/base.py` — abstract `BrokerInterface` class
- 🔒 `bot/broker/webull_broker.py` — Webull implementation
- 🔒 Unit tests in `bot/tests/test_webull_broker.py`
- 🔒 Test: place paper trade, verify in Webull app

## 4.4 Build Webhook Receiver
- 🔒 `bot/api/webhook_receiver.py` — FastAPI app receives alert JSON
- 🔒 `bot/core/signal_processor.py` — combines multiple indicator alerts within 2-sec window, applies confidence threshold, routes to broker
- 🔒 Test locally with curl/Postman

## 4.5 Build Risk Manager
- 🔒 `bot/core/risk_manager.py` — max position size, daily loss limit, max concurrent positions, session hours enforcement, mandatory stop-loss
- 🔒 All limits in `bot/config/settings.py`
- 🔒 Unit tests for each rule

## 4.6 Build Trade Logger + Database
- 🔒 PostgreSQL database (Supabase free tier or local)
- 🔒 Tables: signals, trades, daily_summary, indicator_scores
- 🔒 `bot/learning/trade_logger.py` — auto-records everything

## 4.7 Configure TradingView Alerts → Webhooks
- 🔒 Set webhook URL to bot endpoint for each indicator's alert
- 🔒 Test: trigger alert → bot receives → logs → places paper trade

## 4.8 Paper Trading Launch
- 🔒 Run 1 full week — observe only
- 🔒 Fix issues found
- 🔒 Run 30 days minimum paper trading

---

# PHASE 5: ADAPTIVE LEARNING ENGINE
> Goal: Track performance and improve over time
> Timeline: After 30 days paper trading data

## 5.1 Level 1 — Rule-Based Learning
- 🔒 `bot/learning/performance_analyzer.py` — win rate by signal type, grade, time of day, regime
- 🔒 `bot/learning/weight_optimizer.py` — weekly: adjust thresholds based on results
- 🔒 `bot/scheduler/postmarket_review.py` — 4pm ET daily summary + anomaly detection

## 5.2 Level 2 — Statistical Learning (100+ trades)
- 🔒 `bot/learning/regime_tracker.py` — P&L per market regime
- 🔒 Feature importance via scikit-learn RandomForest
- 🔒 Monthly walk-forward parameter updates from live data

## 5.3 Level 3 — ML-Based Learning (500+ trades, future)
- 🔒 Classification model: indicator scores → predict win/loss
- 🔒 Regression model: setup → predict R-multiple
- 🔒 Reinforcement learning for position sizing
- 🔒 Requires: pytorch, scikit-learn, cloud GPU

---

# PHASE 6: WEB DASHBOARD (lightweight-charts-python + React)
> Goal: Real-time dashboard with TradingView-quality charts, NO Pine Script limits
> This REPLACES the Pine Script dashboard — built in Python with unlimited plots/compute

## 6.1 Python Charting Setup
- 🔒 `pip install lightweight-charts`
- 🔒 Build prototype: load candle data + 3 indicator overlay lines
- 🔒 Add subchart panes for oscillators (like Quintuple pane)
- 🔒 Add markers for entry/exit signals
- 🔒 Add horizontal lines for S/R levels
- 🔒 Add table for dashboard (indicator scores, regime, grade)
- 🔒 Verify: looks and feels like TradingView

## 6.2 Backend API
- 🔒 Extend `bot/api/routes.py`:
  - `GET /api/positions`, `/api/trades`, `/api/performance`, `/api/signals`, `/api/learning`
  - `POST /api/override` — kill switch, force exit
  - `WebSocket /ws/live` — real-time updates

## 6.3 Frontend (React + lightweight-charts)
- 🔒 Price chart with ALL indicator overlays (unlimited lines)
- 🔒 Subchart panes for oscillators, regime probability, divergences
- 🔒 Gauge meter component — composite confidence score
- 🔒 Trade log table with filters
- 🔒 Equity curve + drawdown chart
- 🔒 Learning insights panel
- 🔒 Manual override controls (kill switch, pause, force exit)

## 6.4 Scheduling & Automation
- 🔒 `bot/scheduler/premarket_scan.py` — 4am ET: pull top gainers
- 🔒 `bot/scheduler/session_manager.py` — 9:15 warm up, 9:30 active, 11:00 stop entries, 4:00 review
- 🔒 Use APScheduler or cron

---

# PHASE 7: PORT INDICATORS TO PYTHON + SCANNER
> Goal: Run indicators natively in Python — no Pine Script limits, full ML integration
> Timeline: After 60 days profitable paper trading

## 7.1 Port Core Indicator Logic to Python
> Use ta-lib, scipy, numpy, hmmlearn — institutional grade, no limits
- 🔒 Port JMA calculation to Python (numpy)
- 🔒 Port WAE signal logic (ta-lib for ATR/MACD, numpy for explosion calc)
- 🔒 Port RSX, ROC, FVE, BFF, SDO oscillators (ta-lib + custom)
- 🔒 Port KDE using `scipy.stats.gaussian_kde` (2 lines vs 10 nested loops)
- 🔒 Port HMM using `hmmlearn.hmm.GaussianHMM` (proper implementation)
- 🔒 Port Monte Carlo using `scipy.stats.norm` + numpy vectorization
- 🔒 Validate: Python signals match Pine Script signals on same data
- 🔒 Benchmark: Python indicator calc time vs Pine load time

## 7.2 Scanner Integration
- 🔒 Choose scanner API (Trade Ideas, Benzinga Pro, or custom)
- 🔒 `bot/data/scanner.py` — pull top gainers: small cap, min volume, gap %, float
- 🔒 Auto-apply Python indicators to scanned tickers (no TradingView needed)

## 7.3 Multi-Ticker Management
- 🔒 Monitor 5-10 tickers simultaneously (Python native — no chart limit)
- 🔒 Risk manager ensures total exposure within limits
- 🔒 Priority: A+ on one ticker overrides B on another

## 7.4 Full Autonomous Paper Trading
- 🔒 Run hands-off for 30 days
- 🔒 Monitor via web dashboard
- 🔒 Document in `analysis/autonomous_paper_results.md`

---

# PHASE 8: GO LIVE + FUTURE GROWTH
> Goal: Real money, Lightspeed migration, custom website
> Timeline: After 90+ days paper trading with proven results

## 8.1 Go Live on Webull
- 🔒 Switch paper → live (one config change)
- 🔒 Week 1: 1 trade/day max, manually review each
- 🔒 Week 2: increase frequency if profitable
- 🔒 Month 1: full automation at small size
- 🔒 Scale based on equity curve

## 8.2 Lightspeed Migration
- 🔒 Apply for Lightspeed REST API access
- 🔒 Build `bot/broker/lightspeed_broker.py` (same BrokerInterface)
- 🔒 Test on demo/paper
- 🔒 Switch: one config line change

## 8.3 Custom Website
- 🔒 Deploy dashboard to your own domain (Vercel, AWS, or VPS)
- 🔒 Add authentication
- 🔒 Mobile-responsive
- 🔒 Everything in one spot

## 8.4 Continuous Improvement
- 🔒 Monthly: review learning engine, update parameters
- 🔒 Quarterly: full backtest with updated params
- 🔒 Annually: evaluate Level 3 ML value
- 🔒 Ongoing: add new indicators as markets evolve

---

# 📊 PROGRESS TRACKER

| Phase | Description | Status | Complete | Total |
|---|---|---|---|---|
| 0 | Project Setup & Documentation | 🟡 In Progress | 5 | 19 |
| 1 | Fix & Enhance Core 3 Indicators | ⬜ Not Started | 0 | 24 |
| 2 | Build New Indicators + Alerts | ⬜ Not Started | 0 | 16 |
| 3 | Backtesting & Optimization | ⬜ Not Started | 0 | 8 |
| 4 | Python Bot Foundation | ⬜ Not Started | 0 | 20 |
| 5 | Adaptive Learning Engine | ⬜ Not Started | 0 | 8 |
| 6 | Web Dashboard | ⬜ Not Started | 0 | 12 |
| 7 | Port to Python + Scanner | ⬜ Not Started | 0 | 8 |
| 8 | Go Live + Future Growth | ⬜ Not Started | 0 | 8 |
| **TOTAL** | | | **5** | **123** |
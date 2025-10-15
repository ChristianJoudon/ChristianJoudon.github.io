---
layout: essay
type: essay
title: "Architecting an AI-Driven Economic Simulator for Policy Testing"
date: 2025-01-09
published: true
labels:
  - AI
  - Simulation
  - Policy Testing
---

# AI-Driven Economic Simulator: High-Level Software Architecture

## 1. Overview
This software system provides a testbed for experimenting with economic theories in a simulated, AI-driven environment. It integrates historical data (to ensure realism), event-driven modules (for external shocks or policy changes), and agent-based modeling (to emulate complex market behaviors).

**Key Features:**
- Ingestion of large-scale historical economic and event data for model training.
- Agent-based simulation environment with autonomous, AI-driven agents.
- Modular design for testing different economic policies, cultural touchpoints, or global events.
- Scalable infrastructure that balances accuracy with computational feasibility.

---

## 2. Core Components

### 2.1. Data Ingestion and Preprocessing
**Purpose:** Collect, clean, and standardize datasets that capture historical economic indicators and relevant event metadata.

1. **Data Sources**
    - Economic Metrics: GDP, inflation rates, trade volumes, equity indices.
    - Sociopolitical Events: Government policy changes, significant legislative acts, war/peace events.
    - Cultural/Environmental Events (Optional): Major media releases (e.g., documentaries), natural disasters, public sentiment data from social media.

2. **Data Pipelines**
    - **Extract**: Scheduled jobs that pull data from APIs, databases, or CSVs.
    - **Transform**: Cleaning, normalization, and indexing (e.g., converting currencies, adjusting for inflation).
    - **Load**: Insertion into a centralized database (SQL/NoSQL) or data warehouse (e.g., AWS Redshift, Google BigQuery).

3. **Preprocessing Steps**
    - Time-series alignment for synchronized event comparisons.
    - Data validation, outlier detection, and missing-value imputation.
    - Metadata tagging to enable selective training and scenario-building.

---

### 2.2. Model Training and Validation
**Purpose:** Learn patterns from historical data to generate predictive or adaptive agent behaviors in the simulation.

1. **Model Selection**
    - **Forecasting Models:** ARIMA, SARIMAX, or neural network–based methods (LSTM, Transformers) for macroeconomic time series.
    - **Agent Behavior Models:** Reinforcement Learning (RL) or Behavior Cloning to capture decision-making patterns from historical data.

2. **Training Workflows**
    - **Batch Training:** Periodic offline training on the most recent validated dataset.
    - **Incremental/Online Training:** Optional for real-time assimilation of newly arriving data.

3. **Model Validation**
    - Compare simulated outcomes to historical “ground truth” (e.g., a shock like the 2008 financial crisis).
    - Evaluate performance metrics: MSE (Mean Squared Error), R^2, or custom domain-specific KPIs (e.g., inflation variance).

---

### 2.3. Simulation Environment
**Purpose:** Provide a controllable, sandboxed “world” in which AI agents interact according to economic rules, policies, and event triggers.

1. **World State**
    - **Global Parameters:** Money supply, interest rates, resource constraints.
    - **Agent Population:** Households, corporations, governments, banks—all with distinct utility functions and initial endowments.
    - **Market Mechanisms:** Exchanges, auction houses, or direct peer-to-peer transactions.

2. **Simulation Engine**
    - **Discrete Timesteps or Continuous Time:** Depending on computational needs.
    - **Event Scheduler:** Triggers policy changes, external shocks (pandemic, natural disaster), or cultural events at specified times.

3. **Dynamics**
    - **Policy Modules:** Monetary and fiscal policy sliders (e.g., interest rates, taxation) that can be tweaked in real time.
    - **Feedback Loops:** Price formation, wage adjustments, market clearing processes, and wealth redistribution.

---

### 2.4. Agent-Based Modeling Layer
**Purpose:** Define how individual agents make decisions and react to the evolving economic environment.

1. **Agent Architecture**
    - **Reinforcement Learning Agents:**
        - State: Observed prices, wages, personal holdings, external events.
        - Action: Buy, sell, invest, produce, consume, or alter policy (if the agent is a government entity).
        - Reward: Profit maximization, utility of consumption, or other domain-specific goals.
    - **Behavioral Economics Agents (Optional):**
        - Incorporate heuristics like loss aversion, bounded rationality, or social contagion.

2. **Interaction Models**
    - **Market Interaction:** Agents submit buy/sell orders to a centralized exchange or negotiated trading system.
    - **Social Networks:** Agents can influence each other’s behavior (e.g., herd behavior, cultural shifts) if modeling “cultural touchpoints.”

3. **Parameterization**
    - **Scalability:** Capable of handling thousands to millions of agents, potentially via clustering or GPU acceleration.
    - **Modularity:** Easily swap out agent logic for different economic theories or policy frameworks.

---

### 2.5. Event and Policy Integration
**Purpose:** Simulate how real-world or hypothetical events might alter agent behavior and market outcomes.

1. **Event Definition**
    - **Static Data (Historical):** Wars, major legislation, significant market crashes.
    - **Dynamic Data (Synthetic or Real-Time):** Social media sentiment spikes, cultural movements (like Al Gore’s “An Inconvenient Truth”).

2. **Policy Mechanisms**
    - Central bank announcements, changes in government spending, environmental regulations.
    - Probability-based triggers for unexpected or random “surprise” events.

3. **Outcome Measurement**
    - Track how quickly agents adapt (e.g., reallocate capital, shift consumption).
    - Compare to historically observed responses for validation or scenario planning.

---

### 2.6. Analysis and Visualization Layer
**Purpose:** Provide real-time and post-simulation insights for researchers, policymakers, and other stakeholders.

1. **Data Reporting**
    - Time-series charts for key economic indicators (inflation, GDP, Gini coefficient).
    - Dashboards for agent distribution data (e.g., wealth distribution, firm sizes).

2. **Policy Impact Metrics**
    - Differential outcomes under various policy regimes (e.g., high tax vs. low tax).
    - Scenario comparison tools for “What If?” analyses.

3. **User Interface (UI/UX)**
    - **Simulation Control Panel:** Start/pause simulation, adjust policy sliders, inject events on the fly.
    - **Customizable Widgets:** Drag-and-drop modules for custom analytics (e.g., top trading industries, unemployment rates).

---

## 3. Technical Considerations

### 3.1. Computing Infrastructure
- **Cloud Deployment:** AWS, Azure, or GCP for scalable computation and storage.
- **Microservices Architecture (Optional):** Separate services for data ingestion, modeling, simulation, and visualization to improve maintainability.
- **GPU/TPU Acceleration:** Beneficial for training large-scale neural networks or reinforcement learning.

### 3.2. Accuracy vs. Complexity Trade-Off
- **Granularity of Events:** Including cultural influences (like a documentary) can improve realism but drastically increases complexity and data requirements.
- **Cost-Benefit Analysis:** Focus on the most impactful data sources. High-fidelity cultural modeling may yield diminishing returns compared to broad economic indicators.

### 3.3. Security and Ethics
- **Data Privacy:** Ensure compliance with regulations when using personal financial or demographic data.
- **Model Bias:** Regularly audit models for unwanted biases that could skew policy outcomes.

---

## 4. Example High-Level Pseudocode (Workflow)

Below is a detailed pseudocode example outlining a potential end-to-end workflow for building, running, and analyzing an AI-driven economic simulator. While this example remains language-agnostic and high-level, it uses Python-like syntax to illustrate concepts in a clear and approachable manner.

```python
1) Proposed architecture (clean separation of concerns)
+---------------------------------------------------------------+
|                    Experiments & Scenarios                    |
|  (YAML/JSON configs, seeds, policy toggles, event calendars)  |
+--------------------+---------------------------+--------------+
                     |                           |
                     v                           v
+-------------------------+       +-----------------------------+
|  Data Layer             |       |  Model Training Layer       |
|  - Sources/ETL          |       |  - Macro forecasters        |
|  - Canonical Tables     |       |  - Agent policies (RL/BC)   |
|  - Validation + units   |       |  - Offline datasets         |
+------------+------------+       +-----------------------------+
             |                                        ^
             v                                        |
+-------------------------+       +-------------------+----------------+
|  Simulation Kernel      |<----->|  Agent/Market/Policy Plugins      |
|  - Discrete-event loop  |       |  - Agents (vectorizable)          |
|  - Event scheduler      |       |  - Markets (clearing rules)       |
|  - RNG + timebase       |       |  - Policy modules (monetary/fiscal|
|  - State recorder       |       |  - Shock models                   |
+------------+------------+       +-------------------+----------------+
             |
             v
+-------------------------+
|  Analysis & Viz         |
|  - KPIs & diagnostics   |
|  - Backtests/benchmarks |
|  - Export artifacts     |
+-------------------------+


Rule of thumb: the simulator consumes trained models; it doesn’t train them live (except for controlled online-learning experiments behind a feature flag).

2) Data contracts (canonical schemas)

Economic time series (wide or long):

table: econ_timeseries
columns:
  - ts: datetime (UTC, no tz-aware conversions inside the sim)
  - region: string (ISO 3166-1 alpha-3)
  - indicator: enum[gdp, cpi, unemployment, interest_rate, ...]
  - value: float64
  - unit: string (e.g., "USD_2015", "pct")
  - source: string
constraints:
  - unique(ts, region, indicator)
  - non_null(value)
  - unit_checked_with_registry


Event schema:

table: event_calendar
columns:
  - ts: datetime
  - event_type: enum[policy_change, macro_shock, disaster, media, sentiment_spike]
  - scope: enum[global, region, sector]
  - target: string (e.g., "US", "Energy")
  - payload: json (typed by event_type)
examples:
  - ts: 2008-09-15T00:00:00Z
    event_type: macro_shock
    scope: global
    target: "*"
    payload: { credit_spread_bps_delta: 250 }


Policy action schema:

table: policy_actions
columns:
  - ts: datetime
  - authority: enum[cbank, treasury, regulator]
  - instrument: enum[policy_rate, qe, tax_rate, gov_spend, carbon_price]
  - value: float64
  - unit: string


Enforce these with runtime validators (e.g., pydantic/dataclasses + custom checks). Track units explicitly; conversions happen once at ingestion.

3) Simulation kernel (deterministic, auditable)

Key responsibilities:

Timebase: discrete ticks (e.g., daily) or discrete‑event jumps.

RNG: centralized PRNG with named streams ("agents", "policy", "market") for reproducibility.

Scheduler: merges event calendar + policy schedule into a min‑heap on ts.

Recorder: append‑only store of state deltas per tick (parquet or columnar in‑memory, then flushed).

Invariants to check each tick

Prices > 0, money/asset conservation (subject to creation/destruction rules), no NaNs/inf.

Market clearing converged within tolerance; otherwise fall back to capped adjustment.

4) Agents, markets, policies (plugin contracts)

Agent interface

class Agent:
    def observe(self, obs: "Observation") -> None: ...
    def act(self, t: int) -> "OrderBatch": ...
    def settle(self, fills: "FillBatch") -> None: ...


Internals: a policy function πθ(obs) (learned or rule‑based).

Store state in struct-of-arrays (SoA) for vectorization: wealth, inventory, propensity, etc.

Market interface

class Market:
    def submit(self, orders: "OrderBatch") -> None: ...
    def clear(self) -> "FillBatch": ...
    def quote(self) -> "Quote": ...


Provide at least one call market (periodic double auction) and one tatonnement-like price adjuster (for toy RBC-style tests). Document limitations.

Policy module

class PolicyModule:
    def apply(self, t: int, state: "GlobalState") -> None: ...


Inputs: scheduled actions + event payloads.

Effects: manipulate global parameters, inject transfers, change constraints.

5) Modeling notes (sharp edges)

Lucas critique / policy invariance: avoid judging real‑world effects from agents trained on pre‑policy regimes without counterfactual retraining or structural modeling.

Offline RL safety: prefer behavior‑cloning→conservative/offline RL pipelines to prevent out‑of‑distribution thrash in simulation.

Endogeneity & identifiability: use instrumental variables–like shocks (or synthetic control) when calibrating causal responses.

Heterogeneity: represent cohorts (income deciles, industries) as coarse but meaningful buckets; vectorize within buckets.

6) Validation & benchmarking

Backtests: fixed windows (e.g., 2005–2011 crisis), holdout periods, and stress scenarios.

Metrics:

Forecast: RMSE/MAE/MAPE for CPI, GDP growth, unemployment.

Structural: Phillips‑like tradeoffs, consumption smoothing, wealth Gini trajectory.

Micro: budget violations ≡ 0, inventory nonnegative rates, default frequencies.

Baselines: naive persistence, simple ARIMA, static representative agent. Always compare to them.

7) Observability & governance

Run manifest: seed, config hash, code commit, data snapshot IDs.

Event log: every applied event/policy with before/after diffs.

Dashboards: (1) macro time series, (2) distributional panels, (3) market microstructure, (4) constraint violations.

Ethics: document policy levers and their caveats; provide “do not interpret as advice” overlays on dashboards.

8) Performance & scaling

Start small: 10–100k agents with vectorized numpy/JAX/PyTorch computations for policy inference.

SoA over AoS: arrays of attributes; avoid Python object loops in hot paths.

Batch everything: observations → policy → orders → matching in blocks.

Checkpoints: periodic snapshots to resume long runs.

Parallelism: scenarios parallel by process; agents batched intra‑process.

9) MVP milestone plan (6–8 weeks)

Week 1–2: Data contracts + loaders + unit registry + seedable RNG + recorder.

Week 2–3: Kernel + scheduler + call‑market clearing + simple policy sliders.

Week 3–4: Cohort agents (rule‑based), macro forecaster (naive + ARIMA).

Week 4–5: Validation harness (crisis backtest) + metrics.

Week 5–6: Replace cohorts’ rules with a BC policy; add dashboards.

Week 7–8: Stress scenarios, profiling, and doc pass.

10) Overhauled, executable‑style skeleton (Pythonic pseudocode)

This is a drop‑in scaffold you can start from. It’s still language‑agnostic in spirit, but it’s executable‑leaning, typed, deterministic, and testable.

# sim/__init__.py
from __future__ import annotations
from dataclasses import dataclass, field, asdict
from typing import Dict, Any, List, Tuple, Iterable, Optional
import numpy as np
import math
import uuid

# ----------------------------
# 0) Config & reproducibility
# ----------------------------

@dataclass(frozen=True)
class SimConfig:
    run_id: str
    seed: int
    ticks: int                       # total steps
    dt_days: int                     # days per tick
    region: str                      # e.g., "USA"
    num_agents: int
    market_type: str                 # "call" | "tatonnement"
    initial_interest: float
    initial_tax_rate: float
    money_supply: float
    record_every: int = 1            # snapshot cadence

def make_rngs(seed: int) -> Dict[str, np.random.Generator]:
    base = np.random.SeedSequence(seed)
    streams = {name: np.random.default_rng(s)
               for name, s in zip(["kernel", "agents", "markets", "policy"],
                                  base.spawn(4))}
    return streams

# ----------------------------
# 1) Data contracts (minimal)
# ----------------------------

@dataclass(frozen=True)
class EconPoint:
    ts: np.datetime64
    indicator: str                   # "cpi", "gdp", "u_rate", "policy_rate"
    value: float
    unit: str                        # "pct", "USD_2015", etc.

@dataclass(frozen=True)
class Event:
    ts: np.datetime64
    event_type: str                  # "policy_change", "macro_shock", ...
    scope: str                       # "global" | "region" | "sector"
    target: str                      # e.g., "USA", "Energy", "*"
    payload: Dict[str, Any]

# ----------------------------
# 2) Global state & recorder
# ----------------------------

@dataclass
class GlobalState:
    t: int
    ts: np.datetime64
    interest_rate: float
    tax_rate: float
    money_supply: float
    price_level: float               # CPI proxy
    output: float                    # GDP proxy

class Recorder:
    def __init__(self) -> None:
        self.rows: List[Dict[str, Any]] = []

    def record(self, state: GlobalState, extras: Dict[str, Any]) -> None:
        row = asdict(state) | extras
        self.rows.append(row)

    def snapshot(self) -> List[Dict[str, Any]]:
        # In production: write to parquet; here we just expose memory buffer.
        return self.rows

# ----------------------------
# 3) Agents (vectorized cohort)
# ----------------------------

@dataclass
class AgentCohort:
    # Struct-of-arrays to vectorize over N agents
    ids: np.ndarray                 # shape [N]
    wealth: np.ndarray              # [N]
    income: np.ndarray              # [N]
    propensity_consume: np.ndarray  # [N] in (0,1)
    inventory: np.ndarray           # [N] units of generic good

    def observe(self, state: GlobalState) -> Dict[str, np.ndarray]:
        # Minimal observation vector (extend as needed)
        return {
            "r": np.full_like(self.wealth, state.interest_rate, dtype=float),
            "p": np.full_like(self.wealth, state.price_level, dtype=float),
            "tax": np.full_like(self.wealth, state.tax_rate, dtype=float),
            "y": self.income
        }

    def act(self, obs: Dict[str, np.ndarray]) -> Dict[str, np.ndarray]:
        # Simple rule or learned policy πθ; here: consumption & labor supply toy policy
        after_tax_income = obs["y"] * (1.0 - obs["tax"])
        desired_cons = self.propensity_consume * (self.wealth + after_tax_income)
        orders = {
            "buy_qty": np.clip(desired_cons - self.inventory, a_min=0.0, a_max=None),
            "sell_qty": np.clip(self.inventory - desired_cons, a_min=0.0, a_max=None),
        }
        return orders

    def settle(self, fills: Dict[str, np.ndarray], price: float) -> None:
        # Update inventory and wealth given fills
        buy = fills.get("buy_fill", np.zeros_like(self.wealth))
        sell = fills.get("sell_fill", np.zeros_like(self.wealth))
        self.inventory += buy - sell
        cash_delta = -price * buy + price * sell
        self.wealth += cash_delta

# ----------------------------
# 4) Market (call auction)
# ----------------------------

class CallMarket:
    def __init__(self, rng: np.random.Generator, tick_size: float = 1e-4) -> None:
        self.rng = rng
        self.tick = tick_size

    def clear(self, buy_qty: np.ndarray, sell_qty: np.ndarray, last_price: float) -> Tuple[float, Dict[str, np.ndarray]]:
        """
        Simple price update: move price toward excess demand
        p_{t+1} = p_t * (1 + k * (D - S) / (|D|+|S|+eps))
        Then pro‑rata allocate fills at p_{t+1}.
        """
        eps = 1e-9
        D = float(np.sum(buy_qty))
        S = float(np.sum(sell_qty))
        imbalance = (D - S) / (abs(D) + abs(S) + eps)
        k = 0.05
        new_price = max(self.tick, last_price * (1.0 + k * imbalance))
        # Pro‑rata fills
        buy_fill = buy_qty * min(1.0, S / (D + eps))
        sell_fill = sell_qty * min(1.0, D / (S + eps))
        return new_price, {"buy_fill": buy_fill, "sell_fill": sell_fill}

# ----------------------------
# 5) Policy module
# ----------------------------

class PolicyModule:
    def __init__(self, schedule: Dict[int, Dict[str, float]]) -> None:
        self.schedule = schedule

    def apply(self, t: int, state: GlobalState) -> None:
        actions = self.schedule.get(t)
        if not actions:
            return
        # Supported instruments: policy_rate, tax_rate
        if "policy_rate" in actions:
            state.interest_rate = float(actions["policy_rate"])
        if "tax_rate" in actions:
            state.tax_rate = float(actions["tax_rate"])

# ----------------------------
# 6) Event scheduler
# ----------------------------

class EventScheduler:
    def __init__(self, events: List[Event]) -> None:
        self.by_tick: Dict[int, List[Event]] = {}
        # In practice convert ts→tick using calendar; here assume aligned ext.
        for e in events:
            t = int(e.payload.get("tick", 0))  # placeholder mapping
            self.by_tick.setdefault(t, []).append(e)

    def get(self, t: int) -> List[Event]:
        return self.by_tick.get(t, [])

# ----------------------------
# 7) Kernel
# ----------------------------

class SimulationKernel:
    def __init__(
        self,
        cfg: SimConfig,
        cohort: AgentCohort,
        market,
        policy: PolicyModule,
        scheduler: EventScheduler,
        macro_forecaster: Optional[Any] = None
    ) -> None:
        self.cfg = cfg
        self.rngs = make_rngs(cfg.seed)
        self.cohort = cohort
        self.market = market
        self.policy = policy
        self.scheduler = scheduler
        self.recorder = Recorder()
        self.state = GlobalState(
            t=0,
            ts=np.datetime64("2000-01-01"),  # or from config
            interest_rate=cfg.initial_interest,
            tax_rate=cfg.initial_tax_rate,
            money_supply=cfg.money_supply,
            price_level=1.0,
            output=1.0,
        )
        self.last_price = 1.0
        self.macro = macro_forecaster

    def step(self) -> None:
        t = self.state.t

        # 1) Apply scheduled events (convert to state deltas)
        for e in self.scheduler.get(t):
            if e.event_type == "macro_shock":
                # Example: shock to price level or output
                self.state.price_level *= (1.0 + float(e.payload.get("cpi_jump", 0.0)))
                self.state.output *= (1.0 + float(e.payload.get("gdp_jump", 0.0)))
            elif e.event_type == "policy_change":
                if "tax_rate_delta" in e.payload:
                    self.state.tax_rate += float(e.payload["tax_rate_delta"])

        # 2) Apply policy schedule (authoritative instruments)
        self.policy.apply(t, self.state)

        # 3) Macro forecast (optional)
        if self.macro:
            macro = self.macro.predict(self.state)  # returns dict with deltas
            self.state.price_level *= (1.0 + macro.get("inflation", 0.0))
            self.state.output *= (1.0 + macro.get("gdp_growth", 0.0))

        # 4) Agents observe & act (vectorized)
        obs = self.cohort.observe(self.state)
        orders = self.cohort.act(obs)

        # 5) Market clearing
        new_price, fills = self.market.clear(
            buy_qty=orders["buy_qty"],
            sell_qty=orders["sell_qty"],
            last_price=self.last_price
        )
        self.cohort.settle(fills, price=new_price)
        self.last_price = new_price

        # 6) Invariants / safety
        if not (new_price > 0.0 and np.all(np.isfinite(self.cohort.wealth))):
            raise RuntimeError("Market or agent state invalid (price<=0 or non-finite wealth).")

        # 7) Advance time & record
        self.state.t += 1
        self.state.ts = self.state.ts + np.timedelta64(self.cfg.dt_days, "D")
        if t % self.cfg.record_every == 0:
            extras = {
                "price": self.last_price,
                "mean_wealth": float(np.mean(self.cohort.wealth)),
                "gini_wealth": gini(self.cohort.wealth),
            }
            self.recorder.record(self.state, extras)

    def run(self) -> List[Dict[str, Any]]:
        for _ in range(self.cfg.ticks):
            self.step()
        return self.recorder.snapshot()

# ----------------------------
# 8) Utilities
# ----------------------------

def gini(x: np.ndarray) -> float:
    x = np.asarray(x, dtype=float)
    if np.any(x < 0):
        x = x - np.min(x)  # shift to nonnegative
    if x.sum() == 0:
        return 0.0
    x = np.sort(x)
    n = x.size
    cumx = np.cumsum(x)
    return (n + 1 - 2 * np.sum(cumx) / cumx[-1]) / n

# ----------------------------
# 9) Example wiring (MVP)
# ----------------------------

def build_mvp(num_agents: int = 10000) -> SimulationKernel:
    cfg = SimConfig(
        run_id=str(uuid.uuid4()),
        seed=42,
        ticks=365,
        dt_days=1,
        region="USA",
        num_agents=num_agents,
        market_type="call",
        initial_interest=0.01,
        initial_tax_rate=0.05,
        money_supply=1_000_000.0,
    )
    rngs = make_rngs(cfg.seed)
    ids = np.arange(num_agents)
    wealth = rngs["agents"].lognormal(mean=7.0, sigma=1.0, size=num_agents)  # skewed
    income = rngs["agents"].normal(loc=100.0, scale=20.0, size=num_agents).clip(min=0.0)
    propensity = rngs["agents"].beta(a=2.0, b=5.0, size=num_agents)
    inventory = rngs["agents"].uniform(low=0.0, high=10.0, size=num_agents)

    cohort = AgentCohort(ids, wealth, income, propensity, inventory)
    market = CallMarket(rng=rngs["markets"])
    policy = PolicyModule(schedule={
        30: {"policy_rate": 0.0125},
        90: {"tax_rate": 0.06}
    })
    events = [
        Event(ts=np.datetime64("2000-02-01"), event_type="macro_shock", scope="global", target="*",
              payload={"tick": 60, "cpi_jump": 0.02}),
    ]
    scheduler = EventScheduler(events)
    kernel = SimulationKernel(cfg, cohort, market, policy, scheduler, macro_forecaster=None)
    return kernel

if __name__ == "__main__":
    kernel = build_mvp()
    results = kernel.run()
    # results is a list of dicts you can export to CSV/Parquet or feed to dashboards.



11) Testing checklist (practical)

Unit:

Price never ≤ 0; no NaNs/inf after step().

With zero orders, price stays at last_price.

Tax increase reduces mean post‑tax income in next tick.

Property:

Money conservation when the economy is closed and policy doesn’t inject/withdraw.

Gini stays within [0,1].

Integration:

Replaying the same config/seed yields the same time series.

Event replay (policy flip at t=30) changes trajectories in expected direction.

12) Validation harness (outline)
def validate_against_reference(results: List[Dict[str, Any]], ref_df) -> Dict[str, float]:
    # Align on ts, compute MAE/RMSE for price_level (CPI proxy) and output (GDP proxy)
    # Return {"cpi_rmse": ..., "gdp_rmse": ..., "wealth_gini_trend_corr": ...}
    ...


Add scenario bundles: crisis_2008.yml, pandemic_2020.yml, energy_shock_1979.yml, each with calibration targets and acceptance thresholds.

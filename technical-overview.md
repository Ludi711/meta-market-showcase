## Technical Overview

**The Meta Market** is a Dota 2 virtual stock market where users trade heroes as market assets. Hero prices are updated using real Dota 2 meta-performance data, allowing users to build portfolios, compete on leaderboards, and test how well they can read the meta.

This repository is a showcase version of the live project, highlighting the data pipeline, SQL backend structure, React frontend, and core product logic.

### Tech Stack

* **Frontend:** React
* **Backend / Database:** SQL via Supabase
* **Data Pipeline:** Python
* **Authentication:** Supabase Auth
* **External Data:** Dota 2 hero performance data

### Core Features

* Virtual hero trading system
* Hero price updates based on meta-performance data
* User portfolios and transaction history
* Leaderboards and user rankings
* Stop-loss and take-profit style mechanics
* Daily and weekly quizzes
* Prediction events for patches, tournaments, and meta shifts
* Meta IQ scoring concept
* Persistent user accounts and trading activity

### Data Pipeline

Hero performance data is pulled using Python and transformed into market price signals.

The pipeline follows this basic flow:

1. Pull Dota 2 hero performance data.
2. Clean and standardise hero statistics.
3. Compare current stats against previous snapshots.
4. Calculate hero price movement.
5. Store updated prices and history in Supabase.
6. Update portfolio values, leaderboards, and market pages.

The pricing logic is designed to reward heroes gaining popularity or improving in performance, while heroes falling out of the meta lose value.

### Backend / SQL Design

The backend is built around SQL tables in Supabase, with a focus on storing auditable user activity and market history.

Core table areas include:

* **Profiles** — user account metadata, balances, and leaderboard fields.
* **Heroes** — hero metadata and current market price.
* **Price History** — historical hero price snapshots.
* **Transactions** — buy/sell activity, quantity, price, and timestamp.
* **Portfolios** — user holdings and unrealised portfolio value.
* **Orders** — stop-loss and take-profit logic.
* **Quizzes / Predictions** — quiz answers, prediction entries, scoring, and Meta IQ inputs.
* **Leaderboards** — ranked user performance based on portfolio value and activity.

The transaction model is designed to avoid simply overwriting balances or holdings, making user activity easier to audit and debug.

### Trading Logic

When a user buys or sells a hero, the app checks their available balance, current holdings, and the latest hero price. Valid trades are written to the transaction table and reflected in the user’s portfolio.

Portfolio value is calculated from:

* Cash balance
* Current hero holdings
* Latest hero prices
* Realised and unrealised gains/losses

Stop-loss and take-profit features add simple trading-style risk controls while keeping the experience accessible for casual Dota players.

### React Frontend

The frontend is built in React and presents the platform as a lightweight trading dashboard for Dota 2 players.

Main interface areas include:

* Market overview
* Hero detail pages
* Portfolio dashboard
* Transaction history
* Leaderboard
* Quiz pages
* Prediction event pages
* Meta IQ / user performance sections

The UI is designed to feel playful and game-like while still presenting useful trading and performance information.

### Engagement Features

The platform includes quizzes and prediction events to encourage repeat visits beyond checking portfolio value.

These features support:

* Daily and weekly quizzes
* Patch-based predictions
* Tournament prediction events
* Hero trend forecasting
* Meta IQ scoring
* Future prize-based competitions

The prediction system is designed to be reusable, so new events can be created for patches, tournaments, or weekly meta changes.

### Skills Demonstrated

This project demonstrates:

* React frontend development
* Python data pipeline development
* SQL database design
* Supabase authentication and data storage
* Transaction-based portfolio modelling
* External API/data ingestion
* Market-style pricing logic
* Leaderboard and scoring systems
* Gamified product design
* Building and deploying a live user-facing analytics product

### Future Improvements

Potential future improvements include:

* Automated weekly meta reports
* Email alerts for watched heroes
* Tournament-based prediction competitions
* Prize-supported leaderboard events
* Improved anti-abuse checks
* Public market data API endpoints
* More advanced Meta IQ scoring

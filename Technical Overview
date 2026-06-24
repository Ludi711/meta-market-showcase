## Technical Overview

**The Meta Market** is a Dota 2 virtual stock market platform where users trade heroes as if they were market assets. Hero prices are driven by real meta-performance data, allowing users to build portfolios, compete on leaderboards, and test their ability to read changes in the Dota 2 meta.

This repository is a showcase version of the project, focused on explaining the product architecture, data model, feature logic, and technical implementation behind the live application.

### Core Concept

The platform turns Dota 2 heroes into tradeable virtual assets. Users can buy and sell heroes, track portfolio performance, compete against other users, and interact with daily/weekly engagement features such as quizzes, predictions, and meta-based challenges.

The goal was to combine gaming, market mechanics, data engineering, and retention-focused product design into one interactive web application.

### Key Features

* Virtual hero trading system
* Hero price movement based on real Dota 2 meta data
* User portfolios and transaction history
* Leaderboards and performance rankings
* Stop-loss and take-profit style trading mechanics
* Daily and weekly quizzes
* Prediction events for patches, tournaments, and meta shifts
* Meta IQ scoring concept to reward users for accurate predictions
* User authentication and persistent account data
* Supabase-backed database for trades, balances, rankings, and user activity

### Data Pipeline

The application uses external Dota 2 hero performance data as the basis for market updates. A scheduled data pull retrieves hero statistics such as win rate, pick rate, and recent changes in performance.

This data is transformed into market indicators and used to update hero prices over time. The pricing model is designed to reward heroes that are gaining popularity or improving in performance, while heroes falling out of the meta lose value.

At a high level, the pipeline follows this structure:

1. Pull hero performance data from a Dota 2 data source.
2. Clean and standardise the incoming hero statistics.
3. Compare current hero performance against recent historical snapshots.
4. Calculate price movement signals.
5. Store updated hero prices and historical records in Supabase.
6. Reflect the updated prices across portfolios, leaderboards, and market pages.

### Database Design

Supabase is used as the backend database and authentication layer. The schema is designed around persistent user activity and auditable market transactions.

Core table areas include:

* **Users / Profiles** — stores user account metadata, balances, and leaderboard-related fields.
* **Heroes / Assets** — stores hero metadata and current market price.
* **Price History** — stores historical hero price snapshots for trend analysis.
* **Transactions** — records buy/sell activity, quantity, price, and timestamp.
* **Portfolios** — tracks user holdings and unrealised portfolio value.
* **Orders / Risk Controls** — supports mechanics such as stop-loss and take-profit logic.
* **Quizzes / Predictions** — stores user answers, prediction events, scoring, and Meta IQ inputs.
* **Leaderboard Tables / Views** — aggregate portfolio values and performance rankings.

The structure was designed to keep financial-style transactions auditable rather than simply overwriting user balances or holdings.

### Trading Logic

When a user buys or sells a hero, the application validates the action against the user’s available balance and current holdings. Valid trades are recorded as transactions, and the user’s portfolio is updated accordingly.

Portfolio value is calculated from:

* Current cash balance
* Current hero holdings
* Latest hero market prices
* Realised and unrealised gains/losses

Additional market mechanics, such as stop-loss and take-profit orders, are designed to make the experience feel closer to a simplified trading platform while remaining lightweight and accessible for casual Dota players.

### Engagement Systems

The platform includes quiz and prediction mechanics to encourage repeat visits beyond simple portfolio checking.

These systems are intended to support:

* Daily or weekly user engagement
* Patch-based predictions
* Tournament prediction events
* Hero trend forecasting
* Meta IQ scoring
* Future prize or tournament-based competitions

The prediction framework is designed to be reusable, allowing new events to be created around weekly meta changes, major patches, or professional tournaments.

### Frontend / Product Design

The frontend is designed as a playful but data-rich gaming dashboard. The UI presents market data in a way that feels familiar to both Dota players and users of trading or fantasy sports platforms.

Key interface areas include:

* Market overview
* Hero detail pages
* Portfolio dashboard
* Transaction history
* Leaderboard
* Quiz and prediction pages
* Meta IQ / user performance sections

The design challenge was to make the platform feel fun and game-like while still giving users enough data to make meaningful decisions.

### Technical Skills Demonstrated

This project demonstrates:

* Full-stack product thinking
* Supabase database design
* Authentication-backed user state
* SQL-based transaction and portfolio modelling
* Data pipeline design
* External API ingestion
* Market-style pricing logic
* Leaderboard and scoring systems
* Gamified product design
* Retention mechanics through quizzes and predictions
* Building a live, user-facing analytics product from concept to deployment

### Future Improvements

Potential future improvements include:

* Automated weekly meta reports
* Email alerts for watched heroes
* Tournament-based prediction competitions
* Prize-supported leaderboard events
* Improved anti-abuse and transaction validation
* Public API endpoints for market data
* More advanced Meta IQ scoring

# BetKei by SKUNKEI

BetKei is a restricted-access sports market analysis and Betfair Exchange interface. It brings upcoming events, current exchange prices, market-derived estimates, available historical form, model results, and connected-account betting activity into one authenticated workspace.

BetKei is an information and account-management tool, not a source of certainty. Predictions can be wrong, prices and event coverage can change, and betting can result in the loss of money. BetKei does not promise returns or provide individualized financial advice.

## Why BetKei

Sports markets can be difficult to review alongside recent results and an individual exchange account. BetKei combines those views so an authorized user can inspect the price and the assumptions behind an estimate, compare model outcomes with resolved results, and review connected-account activity in one place.

The product is intentionally market-aware: it does not invent a forecast when it cannot obtain a complete, usable price set for the market. Historical form may add context when the source data and sample are available, but it does not remove uncertainty.

## What It Does

### Market and Event Views

- Browse upcoming events by sport, search by event or league, and sort by start time or prediction availability.
- View current Betfair Exchange AU market prices where available. Price data is refreshed and may be delayed, unavailable, suspended, or changed before an action is confirmed.
- See a model estimate only when the market has a complete set of usable runner prices. The estimate identifies whether it is based on the margin-adjusted market alone or also includes historical form.
- Review results and resolved model outcomes, including model accuracy, qualifying-pick accuracy, sample counts, coverage, Brier score, calibration gap, and sport breakdowns where the data is available.

### Exchange Account and Bets

For appropriately authorized accounts with an active Betfair connection, BetKei can show account balance and exposure, current orders, and settled bet history. Depending on account privileges and service configuration, the upcoming-market view can also place a real **BACK** bet on Betfair after the user selects a runner, reviews the odds and stake, and confirms the action. Unmatched orders can be cancelled where supported.

Bet placement is a separate user action. A model prediction does not place a bet automatically. Check the account, market, selection, price, stake, and status in Betfair before relying on any result; network or provider delays can affect confirmation and matching.

## How the Estimate Works

The current implementation starts from available exchange prices. For each runner, it converts decimal odds to a raw implied probability using the reciprocal price, then normalizes the probabilities across the market to account for the market overround. Where two-team historical-form data is available with a sufficient sample, a bounded form adjustment may shift probability between those outcomes. If prices are incomplete or invalid, BetKei does not present a model forecast for that market.

The result is a model estimate, not a calibrated promise of an event's true probability. The method depends on market quality, price freshness, event/runner matching, historical data coverage, and the size and quality of the form sample. Model rules can change as the service evolves.

## Understanding Performance Figures

- **Model accuracy** summarizes resolved model predictions in the displayed data; it is not a forecast of future accuracy.
- **Pick accuracy** applies to the smaller set of predictions that meet the model's qualifying-pick criteria. Always consider its sample count and resolution coverage.
- **Brier score and calibration gap** describe aspects of historical probability quality. They do not guarantee future calibration.
- **Model or projected P/L** is a notional calculation from recorded model probabilities and available prices/stake assumptions. It is not the user's actual Betfair return and does not include every real-world cost or execution effect.
- **Settled Betfair P/L** comes from connected-account bet records and is distinct from model-projected P/L.

Historical outcomes can be incomplete, delayed, or dependent on event and runner matching. Compare figures using the sample size, coverage, time period, and available data shown alongside them.

## Data Sources and Integrations

- **Betfair Exchange AU** supplies exchange markets, runner prices, account information, and order actions for an authorized connection.
- **TheSportsDB** supplies supported event schedules, scores, results, and historical sports data used where available for event displays and form context.
- **Google Analytics** is configured for website usage measurement. See the [BetKei Privacy Policy](privacy.md) for information handled by the web app and connected services.
- The website may also load presentation assets from a third-party content-delivery service.

Provider availability, sport/league coverage, market type, and event matching vary. A sport shown in the interface does not mean that every event has a Betfair market, complete prices, historical form, or a forecast.

## Access and Security

The current BetKei application requires an authenticated account with the necessary administrative authorization. Betfair connection and live betting actions require additional privileges; live betting may also be disabled by service configuration.

The service uses account access checks, CSRF protection for state-changing browser requests, server-side validation, and HTTPS for supported production traffic. BetKei forwards the Betfair password to Betfair for authentication and does not store it. The Betfair application key and resulting session token are encrypted at rest by the service. This describes the current implementation, not a guarantee that any account, network, or device is invulnerable.

Protect your SKUNKEI and Betfair accounts and devices. Do not share credentials or session details. Re-check the Betfair account directly if a bet request times out or its final status is unclear.

## Responsible Use

BetKei provides sports statistics, model estimates, and exchange tools for analysis and entertainment. It is not betting advice, financial advice, or a guarantee of results. Bet only where legal and if you meet the applicable minimum age (18+ where required). Set limits, do not chase losses, and stop if betting is causing harm.

## Privacy

BetKei handles account and technical information, market/prediction data, and connected Betfair account and order information as needed to provide its features. The app is configured to use Google Analytics for website usage measurement. See [privacy.md](privacy.md) for the current product-specific privacy notice and choices.

## Repository Scope

This repository contains the public-facing BetKei overview and privacy documentation. The authenticated web application, API, and service implementation are maintained as part of the SKUNKEI platform; this repository is not a standalone deployment package.

## Links

- [BetKei web app](https://betkei.skunkei.com/)
- [Privacy policy](privacy.md)
- [SKUNKEI contact](mailto:service@skunkei.com)
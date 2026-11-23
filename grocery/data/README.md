# Grocery price data sources

This folder stores price records collected from publicly displayed online grocery listings.

## Source registry

- **Agora Superstores** — https://agorasuperstores.com/
  - Public product listings include pack/unit descriptions and displayed prices.
  - Agora's terms state that listed prices may vary and the final charged price is the in-store price when the order is processed.
- **Shwapno** — https://www.shwapno.com/
  - Public product listings include pack sizes and displayed prices.
  - Shwapno's terms state that online prices apply to website purchases and may differ from physical stores.
- **Meena Bazar** — no stable first-party public catalogue endpoint has yet been verified for this project. Third-party delivery listings may be location-specific and should be labelled accordingly.

## Record requirements

Each imported record should include:
- product name and normalized product identity
- store name and exact listing/pack size
- displayed price in BDT
- normalized unit and calculated unit price
- source URL
- observed timestamp in Asia/Dhaka
- delivery area, if the source listing is area-specific
- collection method and verification status

Do not publish a record as a current verified price if its source URL, observed time, pack size, or location scope is missing. Keep demo records separate from verified records.

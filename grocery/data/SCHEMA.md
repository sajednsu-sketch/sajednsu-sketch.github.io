# Verified price feed contract

The static comparison page reads `/grocery/data/prices.json` with `fetch(..., { cache: "no-store" })`.

## Required top-level fields

- `schema_version`: integer, currently 1
- `currency`: `BDT`
- `last_checked_at`: ISO-8601 timestamp with timezone, or null
- `records`: array of price observations

## Required record fields

```json
{
  "product_name": "Farm Eggs",
  "variant": "White",
  "brand": null,
  "aliases": ["সাদা ডিম", "white egg"],
  "store_name": "Agora",
  "quantity": 12,
  "unit": "pcs",
  "price": 168,
  "source_url": "https://example.com/product-listing",
  "observed_at": "2026-11-24T04:30:00+06:00",
  "verification_status": "verified",
  "delivery_area": "Dhaka",
  "collection_method": "official_public_listing"
}
```

The example is a schema illustration, not a real price record. Never copy it into production data.

## Publication rules

- Only records with `verification_status: "verified"` are displayed.
- Preserve exact pack size and unit; compare unit prices only for matching product/variant/brand/pack definitions.
- Store the source product URL and observed timestamp in Asia/Dhaka.
- Do not treat a static GitHub Pages file as a live scraper. A scheduled server-side collector or trusted store API integration must update this JSON.
- Store-specific terms, location restrictions, stock status, and delivery fees must be reviewed before publishing.
- Do not invent prices when a store blocks access or has no public catalogue.

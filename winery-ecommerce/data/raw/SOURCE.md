# Data Source

This dataset originates from real client e-commerce order data (a wine e-commerce business),
fully anonymized before being used in this portfolio.

## What was done before publication

The raw export included customer personal data, real product names, and technical/session
metadata. All of this was processed in a private step, never included in this repository,
before the anonymized dataset (`df_valid_anonymized.csv`) was created.

**Removed entirely (never copied into this repo, not even into `data/raw/`):**
- Customer personal data: name, email, phone, billing/shipping address, IP address
- Real product names
- Session-level tracking data: entry URLs, user agent strings, campaign tracking URLs

**Transformed into anonymized/derived fields before removal of the source column:**
- Real product names were parsed to extract structured attributes (product type, format
  size, wine type, alcohol level, subscription flag, gift flag, customization flag,
  category), then the original product name column was dropped.
- Billing company was used to derive a B2B / B2C order type flag, then dropped.
- Session entry URLs were parsed to extract `utm_source`, `utm_medium`, and `utm_campaign`,
  then the original URL column was dropped.
- **Customer identity resolution.** In the raw WooCommerce export, every guest checkout
  shares the same `customer_id = 0` — it is a placeholder, not a real key, so it cannot be
  used to tell guest customers apart or to count them individually. To get a working,
  anonymous primary key, a surrogate `customer_id` was built with a fallback chain: use the
  registered account ID if the customer was logged in; otherwise fall back to a hash of the
  billing email if one was provided; otherwise assign a unique per-row placeholder. The original
  raw `customer_id` column (with its non-unique `0` placeholder) was then dropped and
  replaced entirely by this surrogate key.
- Missing product references on ~2,000 line items were resolved into two explicit
  placeholders (`unknown_pos_sale`, `unknown_gift_item`) based on whether a product name
  was present, before the name itself was dropped.

**Kept in the anonymized dataset**, since it does not identify any individual:
order/payment metadata, order totals, shipping method, shipping location (postcode, city,
state, country), device type, referral source type, and the derived product/order
attributes listed above.

## What starts here

The notebook picking up from this point lives in `01-data-cleaning/`, and reads the
anonymized dataset from `data/processed/df_valid_anonymized.csv`. From there it covers
date validation, order status filtering, further cleaning, and the construction of a small
star schema (`orders`, `products`, `orders_products`, `customers`).

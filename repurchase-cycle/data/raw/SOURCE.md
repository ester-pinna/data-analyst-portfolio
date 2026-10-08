# Data Source

This dataset originates from real client e-commerce order data (a D2C apparel business, WooCommerce store), with customer personal data removed before being used in this portfolio.

## What was done before publication

The raw export included customer personal data, real product names, payment identifiers and technical/session metadata. All of this was processed in a private step, never included in this repository, before the anonymized dataset (`orders_anonymized.csv`) was created.

**Removed entirely (never copied to this repo, not even into `data/raw/`):**
- Customer personal data: name, email, phone, billing/shipping address, IP address
- Payment and transaction identifiers
- Real product names and order notes
- Session-level tracking data: entry URLs, referrers, user agent strings, device type

**Transformed into anonymized/derived fields before removal of the source column:**
- **Customer identity.** The raw WooCommerce export has no usable customer ID, so customers were identified by their billing email. The email was normalized (lowercase, no extra spaces) and each distinct email was replaced by a random customer ID (for example `C00042`). The IDs are shuffled, so they do not follow the order of the file, and they are not a hash of the email, so they cannot be recomputed from a list of emails. Orders without a billing email could not be linked to a customer and were dropped.

**Filtered:** only orders with status `completed` were kept.

**Kept in the anonymized dataset:** order ID, order date, order total, anonymous customer ID, and the coupon items of the order, as exported.

## What starts here

The notebook in `01-repurchase-cycle/` reads the anonymized dataset from `data/processed/orders_anonymized.csv`. From there it covers date preparation, orders and customers tables, the repurchase intervals, the analysis of customers who return after email broadcasts, and recommendations.

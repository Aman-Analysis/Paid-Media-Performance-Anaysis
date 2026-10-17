# Paid Media Performance Analysis — Supporting Data

## Included files

- `meta_ads_campaign_quarterly.csv` — campaign-level quarterly records extracted from the `Meta` tab of the supplied workbook.
- `google_ads_campaign_quarterly.csv` — campaign-level quarterly records extracted from the `Google` tab. Subtotal/grand-total rows are excluded so they are not double-counted.
- `ga4_sessions_quarterly.csv` — quarterly GA4 sessions already used by the dashboard, plus paid-click totals computed from the platform campaign rows.
- `dashboard_reconciliation.csv` — a quarterly tie-out of paid spend, platform-attributed revenue, paid clicks, GA4 sessions, blended platform ROAS, click-to-session rate, and cost per session.

## Important provenance note

These files are **supporting extracts from the portfolio workbook**, not native exports directly downloaded from Meta Ads Manager, Google Ads, or GA4. The workbook provides quarterly campaign-level aggregates and quarterly GA4 session totals; it does not contain original daily/date-level event data. No daily values have been invented or represented as actual observations.

Campaign IDs such as `META-C01` and `GOOG-C01` are anonymized/example identifiers. The workbook does not specify a currency, so spend and revenue values are left without a currency symbol. Google conversions can be fractional, consistent with attribution-modelled conversion data.

## Data-quality notes

1. The supplied workbook documents repeated identical metric patterns across different Meta campaign IDs in multiple quarters. These rows have been preserved exactly as provided; they have not been deduplicated because the original platform exports are unavailable to confirm whether they are errors.
2. The Q1 Google section contains a row labelled `Demand gen Total` with a campaign-like ID. It is a subtotal, not an individual campaign, and is excluded from `google_ads_campaign_quarterly.csv` to avoid double-counting.
3. Revenue is platform-attributed, not reconciled against Shopify or another source of truth.
4. ROAS of 1.0x means attributed revenue equals ad spend; it is not a profit break-even point unless gross margin is 100%.
5. Use this package to reproduce and explain the supplied dashboard, but replace the supporting extracts with permissioned native platform exports before presenting the results as real client or company data.

## Column definitions

### Meta / Google campaign files

- `Quarter`: Quarter label as supplied in the workbook; the calendar year is not specified.
- `Campaign_ID`: An anonymized/example campaign identifier.
- `Campaign_Type`: Google campaign type; omitted from the Meta file.
- `Spend`: Campaign spend, retained to cents.
- `Impressions`, `Clicks`: Counts from the workbook.
- `Conversions`: Attributed conversions from the workbook; Google may contain fractions.
- `Attributed_Revenue`: Platform-attributed conversion value.
- `CTR`: Clicks divided by impressions.
- `CPC`: Spend divided by clicks.
- `CPM`: Spend divided by impressions, multiplied by 1,000.
- `CPA`: Spend divided by conversions.
- `ROAS`: Attributed revenue divided by spend.

Derived metrics are recalculated from the base measures above for consistency.

## Refresh workflow

1. Replace these quarter-level extracts with authorized source exports when available.
2. Standardize campaign names, dates, currency, attribution settings, and conversion definitions.
3. Check for duplicate campaign rows and verify the quarter-to-date totals.
4. Recalculate the dashboard and document any differences in attribution or reporting windows.

# Apify MCP Reference

Use this guide only when the Apify connector is enabled in the current Claude or Cowork conversation.

## Appropriate Uses

Use Apify for public, structured evidence such as:

- Apple App Store and Google Play listings, ratings, reviews, version history, pricing, and in-app purchase information.
- Product websites, pricing pages, changelogs, help centers, privacy policies, terms, and refund policies.
- Reddit discussions and public user complaints.
- Public TikTok, YouTube, Instagram, X, Product Hunt, and other social or launch signals.
- Search results, public company pages, job listings, and public technical documentation.

Do not use scraped data as a substitute for licensed market-intelligence data when the report requires reliable download, revenue, retention, or traffic estimates.

## Actor Selection

1. Search using the source and desired record type, for example `Google Play reviews`, `App Store reviews`, or `Reddit posts`.
2. Inspect candidate Actors before running them.
3. Prefer, in order:
   - Official Actors published by Apify.
   - Actors published by the relevant service or a clearly identified company.
   - Maintained community Actors with recent runs, clear documentation, predictable pricing, and structured output.
4. Avoid Actors with unclear ownership, obsolete documentation, unexplained login requirements, or ambiguous pricing.
5. Select the narrowest Actor and query scope that can answer the research question.

## Execution Workflow

Use the available MCP tools in this order when applicable:

1. `search-actors`: discover candidates.
2. `fetch-actor-details`: inspect input schema, output schema, developer, pricing, and limitations.
3. `add-actor`: expose a selected Actor as a tool when dynamic discovery is supported.
4. Actor-specific tool or `call-actor`: execute the collection.
5. `get-actor-run` or `get-actor-log`: diagnose failed or delayed runs.
6. `get-actor-output`: retrieve complete results when the response only contains a preview.
7. `get-dataset-items`: paginate or filter large datasets when available.

Never fabricate tool names or results. Adapt to the exact tools exposed by the connector.

## Cost And Scope Controls

- Inspect Actor pricing before the first run.
- Begin with a small sample, typically 20-100 records, unless the task requires more.
- Avoid crawling an entire domain when a small set of known URLs is sufficient.
- Deduplicate URLs and queries before execution.
- Reuse an existing dataset from the same research session when it remains current.
- Ask the user before running an Actor if the projected charge is unclear or the scope is unusually large.
- Do not repeatedly retry a paid Actor without checking its run log.

## Privacy And Safety

- Collect only public information necessary for the report.
- Do not bypass authentication, paywalls, CAPTCHAs, access controls, robots restrictions, or platform safeguards.
- Do not collect sensitive personal data or build personal profiles unrelated to legitimate company/team research.
- Treat social posts and reviews as user-generated claims, not verified facts.
- Follow the source platform's applicable terms and the user's lawful purpose.

## Evidence Record

For each useful dataset, record:

| Field | Required content |
|---|---|
| Source platform | App Store, Google Play, Reddit, website, etc. |
| Source URL | Original public page or query URL |
| Actor | Exact Actor name and publisher |
| Collected at | Date and timezone |
| Scope | Query, country, language, date range, and result count |
| Data type | Official page, user review, social post, search result, etc. |
| Limitations | Sampling, missing regions, deleted posts, estimated fields, or parsing issues |

In the final report, cite the original source pages whenever possible. Mention Apify and the Actor in the methodology or evidence notes, but do not cite the Actor as if it were the original publisher.

## Reliability Rules

- Official product pages support product-owned claims, pricing, policies, and release information.
- App-store records support observable listing data and review counts at collection time.
- User reviews and social posts support sentiment analysis, not universal conclusions.
- Scraped rankings are time-sensitive snapshots.
- Scraped company/team details require cross-checking with official profiles or credible databases.
- Revenue, downloads, traffic, and retention must be labeled as estimates unless sourced from official disclosures.

## Failure Handling

If an Actor fails:

1. Inspect the run status and log.
2. Correct invalid inputs or reduce scope once.
3. Try another reputable Actor if the first one appears obsolete or blocked.
4. Stop repeated paid retries.
5. Continue with other evidence sources and disclose the missing data.

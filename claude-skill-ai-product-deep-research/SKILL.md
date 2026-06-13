---
name: ai-product-deep-research
description: Use this skill to generate Chinese deep research reports on AI products, including company tracing, market analysis, technical architecture inference, UX, monetization, competition, growth, risk, and cited sources. Trigger when the user asks for an AI product analysis, competitor deep dive, app teardown, market research report, or a report similar to an existing AI product research PDF.
---

# AI Product Deep Research

## Purpose

Create evidence-backed Chinese deep research reports for AI products. The output should feel like a strategic product teardown, not a feature list.

## Quick Workflow

1. Identify the product: official name, URLs, platform, developer entity, target users, and product category.
2. Check whether the Apify connector is available. When available, use it for structured collection from public websites, app stores, social platforms, and review pages. Follow `references/apify_mcp.md`.
3. Gather current public evidence: official site, app stores, terms/privacy/refund pages, market data, company databases, credible media, model/API documentation, social platforms, and user reviews.
4. Separate evidence levels:
   - Fact: directly supported by official or reliable sources.
   - Estimate: supported by third-party market data or transparent calculation.
   - Inference: reasoned from product behavior, technical patterns, job posts, release notes, or comparable products.
5. Build the report using the structure in `references/report_structure.md`.
6. Use the evidence checklist in `references/research_checklist.md` before finalizing.

## Apify MCP

When an Apify MCP connector is enabled, use it as a collection tool, not as an authority by itself.

1. Use `search-actors` to find Actors relevant to the target source.
2. Use `fetch-actor-details` before execution to inspect the developer, required inputs, output schema, pricing, limitations, and recent maintenance status.
3. Prefer official Apify Actors or well-maintained Actors with transparent pricing and clear schemas.
4. Ask for user confirmation before a costly, unusually broad, login-dependent, or personal-data-heavy run. For normal low-cost public-data collection, proceed directly.
5. Run the selected Actor through its dedicated tool, `call-actor`, or `add-actor` when dynamic tool discovery is supported.
6. Use `get-actor-output` with the returned dataset ID when the initial result is only a preview.
7. Save the source URL, Actor name, collection date, query scope, and important limitations in the evidence map.

If Apify is unavailable, continue with other available browsing or connector tools and state the resulting evidence gaps. Never claim that Apify was used when the connector or Actor did not run successfully.

## Required Report Qualities

- Write in Chinese by default.
- Use numbered headings: `1.`, `1.1`, `1.1.1`.
- Include an executive summary, company/team tracing, market context, product and technical analysis, UX, monetization, competition, growth, risks, future outlook, and references.
- Include at least two tables when enough information is available:
  - Feature/technology/user-value matrix
  - Competitor comparison matrix
- Clearly label uncertain claims with “可能”, “推测”, “根据公开信息判断”, or “尚未确认”.
- Cite sources for factual claims. Do not invent citations.
- Prefer recent data. State the data date when discussing prices, rankings, revenue, downloads, financing, model capabilities, or regulations.

## Source Priority

Use sources in this order when available:

1. Official product website, app store listing, pricing page, changelog, docs, privacy policy, terms, refund policy.
2. Company registry, LinkedIn, founder profiles, Crunchbase/Tracxn/PitchBook equivalents, press releases.
3. Market intelligence sources such as Sensor Tower, data.ai, Appfigures, Similarweb, Semrush, Apptopia, Product Hunt.
4. Credible media, analyst reports, app review analysis, social media trend evidence.
5. Technical papers, model docs, API docs, engineering blogs, job postings.

## Handling Technical Architecture

Most products do not disclose their full AI stack. Infer conservatively:

- Use official docs or release notes when available.
- Use observable features to infer likely methods, such as image-to-image, ControlNet, LoRA, segmentation, inpainting, video diffusion, speech-to-text, RAG, agents, vector databases, or multimodal LLMs.
- Explain why the inference is plausible.
- Never state a vendor or model as fact unless a source confirms it.

## Output Process

Before writing, prepare a compact evidence map:

- Product identity
- Company/developer identity
- Pricing and monetization
- Core features
- Target users and use cases
- Market/traction evidence
- User sentiment
- Competitors
- Risks and unknowns

Then write the full report. If evidence is thin, include an “信息缺口” note and downgrade confidence.

## References

- Use `references/report_structure.md` for the canonical report outline.
- Use `references/research_checklist.md` for source collection and validation.
- Use `references/apify_mcp.md` when collecting evidence through the Apify MCP connector.

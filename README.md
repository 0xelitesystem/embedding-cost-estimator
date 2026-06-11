# embedding-cost-estimator

Estimate embedding costs across 11 providers before you commit to a RAG strategy.

**Live demo:** https://0xelitesystem.github.io/embedding-cost-estimator/

Browser-only, single HTML file. No API calls, no telemetry, no upload.

## What it does

Plug in:
- Number of documents in your corpus
- Average tokens per document
- Re-embed frequency (one-time, quarterly, monthly, weekly, daily)
- Search query volume per month

Get a sorted cost matrix showing:
- Per-1M-token rate
- Backfill cost (one full pass)
- Total annual cost
- Cheapest vs most expensive multiplier

## Providers covered

| Provider | Models included |
|---|---|
| OpenAI | text-embedding-3-small, text-embedding-3-large |
| Voyage | voyage-3, voyage-3-large |
| Cohere | embed-english-v3, embed-multilingual-v3 |
| Jina | jina-embeddings-v3 |
| Mistral | mistral-embed |
| Google | text-embedding-004 |
| BGE | M3 (self-hosted, $0 token cost) |
| Nomic | Embed v1.5 (self-hosted, $0 token cost) |

Self-hosted entries show $0 token cost. Add your own GPU/inference cost on top to compare apples to apples.

## Why this exists

Picking an embedding provider for RAG is a decision you make once and pay for forever. Pricing is fragmented across docs, dimensions vary, and re-indexing costs can dominate query costs depending on how often your corpus changes. Most cost comparison content online is stale within a quarter.

This estimator is a single static file so it loads instantly, runs locally, and the math is auditable in the source.

## Caveats

- Prices are based on each provider's published documentation as of model launch. Verify current rates before commitment for procurement.
- Self-hosted estimates exclude infrastructure cost. A 7B-param embedding model on a single A10G is roughly $0.50/hour; estimate your throughput separately.
- This compares cost only. Recall quality differences between models matter and aren't captured here. Run your own eval on a representative sample before committing.

## Use cases

- Scoping a RAG project: "is this affordable at our corpus size?"
- Provider switch analysis: "what would we save moving from X to Y?"
- Architecture review: "is daily re-embedding the right cadence?"

## Build

No build. Open `index.html` in a browser, or deploy via GitHub Pages.

## License

MIT.

## Related

- [llm-pricing-data](https://github.com/0xelitesystem/llm-pricing-data): inference cost data
- [prompt-cost-calculator](https://github.com/0xelitesystem/prompt-cost-calculator): per-call cost estimator
- [rag-chunk-visualizer](https://github.com/0xelitesystem/rag-chunk-visualizer): visualize chunking strategies
- [rag-evaluation-rubrics](https://github.com/0xelitesystem/rag-evaluation-rubrics): how to measure RAG quality

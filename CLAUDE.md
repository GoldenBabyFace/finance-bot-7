# finance-bot-7

This project uses the [HyperGrok trading desk](https://github.com/galleonlabs/hypergrok-trading-desk) (MIT, Galleon Labs) Claude Code plugin, pinned to `v1.7.1` in `.claude/settings.json`.

- Start with `/hypergrok:desk-operating-model` before delegating desk work.
- Seven subagents: Desk Lead, Market Analyst, Research Analyst, Strategist, Risk Manager, Execution Trader, Trade Reviewer.
- The desk starts in research mode, reading only Hyperliquid's public `/info` endpoint. No key is needed.
- To trade, use a trade-only **API wallet** key from a secret store, never a seed phrase or main-wallet key. Practise on testnet first.
- Every trade follows the same path: Risk Manager PASS, then user approval by exact ticket id, then one send, reconciliation, and review.
- Never commit keys or secrets to this repository.

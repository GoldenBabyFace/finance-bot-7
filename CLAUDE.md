# finance-bot-7

This project uses the [HyperGrok trading desk](https://github.com/galleonlabs/hypergrok-trading-desk) (MIT, Galleon Labs) Claude Code plugin, pinned to `v1.7.1` in `.claude/settings.json`.

- Start with `/hypergrok:desk-operating-model` before delegating desk work.
- Seven subagents: Desk Lead, Market Analyst, Research Analyst, Strategist, Risk Manager, Execution Trader, Trade Reviewer.
- The desk starts in research mode, reading only Hyperliquid's public `/info` endpoint. No key is needed.
- To trade, use a trade-only **API wallet** key from a secret store, never a seed phrase or main-wallet key. Practise on testnet first.
- Every trade follows the same path: Risk Manager PASS, then user approval by exact ticket id, then one send, reconciliation, and review.
- Never commit keys or secrets to this repository.

## Cloud sessions (plugin not loaded)

The plugin does not install in Claude Code cloud sessions, so the pinned v1.7.1 release is also vendored here:

- `hypergrok/`: the release (stands in for upstream `/workspace/hypergrok`). Verify with `python3 hypergrok/scripts/desk_doctor.py --repo-root hypergrok --desk-root trading-desk`.
- `.claude/skills/` and `.claude/agents/`: copies of the 17 skills and 7 agents, so `/desk-operating-model` and the subagents load as project items.
- `.claude/hooks/exchange_write_gate.py`: asks before any Bash command that looks like an `/exchange` write. It is a pattern match, not a native approval gate.
- `trading-desk/`: the desk's working files (stands in for `/workspace/trading-desk`). `desk.md` records research level.
- Cloud environment `finance-bot-7` allows GitHub and the Hyperliquid API hosts (mainnet and testnet).

# RelAI — x402 Paid API Skill

Call paid APIs on the [RelAI marketplace](https://relai.fi) using x402 micropayments. This skill handles API discovery, pricing, and the x402 payment protocol across multiple chains.

## Supported networks

| Network | Status | Wallet |
|---|---|---|
| Solana | **Active** | [lobster.cash](https://www.lobster.cash) |
| EVM (SKALE, Base, Avalanche...) | Planned | TBD |

## Features

- Browse and search the RelAI API marketplace
- Check endpoint pricing before calling
- Full x402 payment flow with on-chain settlement
- Multi-chain architecture (Solana active, EVM ready)
- Automatic filtering of incompatible APIs (zAuth, unsupported networks)

## Requirements

- [OpenClaw](https://openclaw.ai) with [lobster.cash](https://www.lobster.cash) plugin (for Solana)
- `curl` and `jq` installed
- `RELAI_API_URL` defaults to `https://api.relai.fi` (override via env var)

## Installation

```shell
npx skills add relai-fi/agent-skills --skill relai
```

Or manually copy the `relai/` directory to `~/.openclaw/skills/`.

## Configuration

The skill uses `https://api.relai.fi` by default. To override:

```bash
export RELAI_API_URL="https://your-instance.example.com"
```

## Directory structure

```
relai/
├── SKILL.md                        # Main skill (workflow + guardrails)
├── README.md
├── LICENSE
├── agents/
│   └── openai.yaml                 # OpenAI agent config
└── reference/
    ├── marketplace-api.md          # Marketplace API endpoints
    ├── x402-solana.md              # Solana payment flow (active)
    ├── x402-evm.md                 # EVM payment flow (planned)
    └── examples.md                 # Usage examples
```

## How it works

1. **Discover** — browse the marketplace, filter by supported networks
2. **Route** — identify the payment network (Solana or EVM)
3. **Price check** — show cost and get user confirmation
4. **Pay** — send payment via the appropriate wallet
5. **Call** — attach payment proof (X-PAYMENT header) and get the API response

## Related skills

- [x402 protocol](https://github.com/TheGreatAxios/agent-skills/tree/main/x402) — x402 v2 reference for building servers, clients, and facilitators

## License

MIT

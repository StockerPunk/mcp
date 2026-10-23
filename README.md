# StockerPunk MCP Server

Bridge **StockerPunk** into Claude, Cursor, or any MCP client. Ask your assistant to check the collection,
preflight, build a mint, list your punks or build a harvest on **BNB Chain**. Signing always goes through the
**Binance Agentic Wallet** (`baw`) — the server never holds keys.

[Website](https://stockerpunk.com) · [X](https://x.com/StockerPunk) · [CLI + skill](https://github.com/StockerPunk/cli)

## Install

```bash
npm i -g github:StockerPunk/mcp
```

## Configure

```json
{
  "mcpServers": {
    "stockerpunk": { "command": "spunk-mcp" }
  }
}
```

Then ask your assistant to check the StockerPunk collection or mint a punk — it builds the transaction and
shows cost and rarity odds. Confirm, and signing goes through your Agentic Wallet in the Binance App.

## Contracts — BNB Chain (chainId 56)

| Contract | Address |
| --- | --- |
| StockerPunk (ERC-721) | `0xfD81e3e5853553D43e4BD3D0bCDE98c69E86c98c` |
| $SPUNK (ERC-20) | `0x5d392B52868077b9Ba5391eeF734820865CD0de6` |
| MiningVault | `0x50F03C2034942f1C032a466F5dBb3a1fc9477504` |
| SpunkAccount — ERC-6551 impl | `0x29dDe0d0f1D2910806901fa7900BE96cCd41DfbA` |
| Agent-ID gate — SPACE ID `.ai` | `0x60B9262456dE011F7d15a54CdD8c48bAaa8B022F` |
| NVDA reward — bStock NVDAB | `0x02Fca66C1D1aFB4E2A7884261eB00F63598a7436` |

First mint per wallet is **free**, then **0.00133 BNB** each, capped at **5** per wallet, 5,000 total. The
authoritative price is `mintPriceWei()` on-chain — the server reads it live, so always confirm `valueWei` in
the Agentic Wallet preview before signing. Only `.ai` Agent-ID holders can mint; a plain EVM wallet reverts.

## License

MIT

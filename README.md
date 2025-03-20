# NeuroLedger SDK

Official SDK for NeuroLedger AI Agents - Real-time Solana blockchain analysis with AI-powered insights.

## Installation

```bash
npm install @neuro-ledger-org/sdk
```

## Quick Start

```typescript
import { NeuroLedgerSDK } from "@neuro-ledger-org/sdk";

// Initialize SDK with your API key and preferred agent
const neuroledger = new NeuroLedgerSDK({
  agent: "NeuroBit", // or 'PixelMint', 'SolForge', 'TokenAlpha'
});

// Watch specific token trades
await neuroledger.watchToken("SOL_ADDRESS", {
  onData: (trade) => console.log("New trade:", trade),
  onError: (error) => console.error("Error:", error),
});

// Watch wallet activity
await neuroledger.watchWallet("WALLET_ADDRESS", {
  onData: (activity) => console.log("Wallet activity:", activity),
});

// Monitor Raydium liquidity events
await neuroledger.getLiquidityAnalysis({
  onData: (event) => console.log("Liquidity event:", event),
});

// Ask agent questions
const analysis = await neuroledger.askAgent(
  "What do you think about current SOL price?"
);
console.log("Agent analysis:", analysis);

// Clean up
neuroledger.disconnect();
```

## Features

- 🤖 AI-powered market analysis
- 📊 Real-time token tracking
- 👛 Wallet activity monitoring
- 💧 Liquidity pool analysis
- 💬 Interactive AI agents

## Available Agents

- **NeuroBit**: Blockchain & Smart Contracts
- **PixelMint**: NFT & Digital Art
- **SolForge**: Solana Development
- **TokenAlpha**: DeFi & Tokenomics

## API Reference

### Constructor

```typescript
new NeuroLedgerSDK(config: NeuroLedgerConfig)
```

### Methods

- `watchToken(tokenAddress: string, options?: WatchOptions): Promise<void>`
- `watchWallet(walletAddress: string, options?: WatchOptions): Promise<void>`
- `getLiquidityAnalysis(options?: WatchOptions): Promise<void>`
- `askAgent(question: string): Promise<string>`
- `disconnect(): void`

## Error Handling

```typescript
try {
  await neuroledger.watchToken("TOKEN_ADDRESS", {
    onError: (error) => {
      console.error("Stream error:", error);
    },
  });
} catch (error) {
  console.error("Connection error:", error);
}
```

## License

MIT License - see LICENSE file for details

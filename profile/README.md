<p align="center">
  <img src="https://raw.githubusercontent.com/Auto-Wallet/auto-wallet/main/public/icons/cat-transparent.png" width="120" />
</p>

<h1 align="center">Auto Wallet</h1>

<p align="center">
  <strong>Minimal auto-signing Chrome extension wallet for EVM chains</strong>
</p>

<p align="center">
  <a href="https://github.com/Auto-Wallet/auto-wallet">Repository</a> &middot;
  <a href="https://github.com/Auto-Wallet/auto-wallet#getting-started">Get Started</a> &middot;
  <a href="https://github.com/Auto-Wallet/auto-wallet/issues">Issues</a>
</p>

---

## What is Auto Wallet?

Auto Wallet is a lightweight Chrome extension wallet built for power users who interact with dApps frequently. Its core feature is **whitelist-based auto-signing** — trusted dApp/contract/method combinations skip manual confirmation, enabling seamless high-frequency interactions like airdrop farming, DeFi strategies, and automated workflows.

## Key Features

### Whitelist Auto-Signing
Configure auto-sign rules with three independently toggleable dimensions:

| Dimension | Example | Effect |
|-----------|---------|--------|
| **Domain only** | `app.uniswap.org` | All transactions from this site auto-sign |
| **Domain + Contract** | `app.uniswap.org` + `0x68b3...` | Only transactions to this contract |
| **Domain + Contract + Method** | Above + `0x5ae401dc` | Only specific function calls |

Gas limit and value caps are always enforced as a safety net, regardless of rule configuration.

### Multi-Account Management
- Create or import multiple accounts (private key or mnemonic)
- Shared master password across all accounts
- One-click switching from the header dropdown
- Rename, delete, and export private keys with password verification

### Full Token Support
- Add custom ERC-20 tokens by contract address (auto-fetches symbol & decimals)
- Token icons auto-loaded from Trust Wallet CDN with smart fallback
- Send both native tokens and ERC-20 tokens directly from the wallet
- Per-chain token lists with balance display

### Network Management
- 6 pre-configured chains: Ethereum, Polygon, Arbitrum, Optimism, BNB Chain, Avalanche
- Add unlimited custom EVM networks
- Search & filter networks by name, symbol, or chain ID
- dApp-triggered chain addition with user confirmation and HTTPS validation

### Security
- **AES-256-GCM** encryption with PBKDF2 key derivation (600,000 iterations)
- Configurable auto-lock (5 min to 24 hours, or never)
- Non-whitelisted transactions require manual approval via popup
- Origin verification: immune to `postMessage` origin spoofing
- Strict origin matching: prevents prefix-based domain attacks
- Signer address validation in multi-account scenarios
- `wallet_addEthereumChain` requires explicit user approval

### Smart Provider Injection
- **EIP-6963** provider discovery: coexists peacefully with other wallets
- Auto-detects `window.ethereum`: injects only when no other wallet is present
- Optional force-inject mode for legacy dApp compatibility
- dApp-triggered unlock: prompts password when connecting to a locked wallet

---

## EIP Standards

| EIP | Name | Status |
|-----|------|--------|
| **EIP-1193** | JavaScript Ethereum Provider API | Implemented |
| **EIP-6963** | Multi Injected Provider Discovery | Implemented |
| **EIP-1559** | Fee Market Transactions (Type 2) | Implemented |
| **EIP-712** | Typed Structured Data Signing (`signTypedData_v4`) | Implemented |
| **EIP-191** | Personal Sign (`personal_sign`) | Implemented |
| **EIP-3085** | `wallet_addEthereumChain` | Implemented |
| **EIP-3326** | `wallet_switchEthereumChain` | Implemented |
| **EIP-747** | `wallet_watchAsset` (ERC-20) | Implemented |
| **EIP-2255** | `wallet_requestPermissions` | Planned |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Chrome Extension Manifest V3 (Service Worker) |
| Build | Bun |
| Language | TypeScript |
| UI | React |
| Styling | Custom CSS design system ("Clean Slate" light theme) |
| Signing | viem |
| Encryption | Web Crypto API (AES-256-GCM + PBKDF2) |
| Fonts | Plus Jakarta Sans + JetBrains Mono |
| Icons | Lucide (UI) + AI-generated mascot |

---

## Quick Start

```bash
git clone https://github.com/Auto-Wallet/auto-wallet.git
cd auto-wallet
bun install
bun run build
```

Then load `dist/` as an unpacked extension in `chrome://extensions`.

---

<p align="center">
  <sub>Built with Bun, React, and viem. Designed for speed.</sub>
</p>

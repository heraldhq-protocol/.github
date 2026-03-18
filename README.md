# Herald ⚡️

### Privacy-Preserving Notification Infrastructure for Web3

Herald is a protocol that enables DeFi protocols to send notifications to wallet addresses without ever learning the user's email address. By combining on-chain encrypted identity registries with secure, ephemeral decryption in Trusted Execution Environments (TEEs), Herald provides a private, secure, and immutable notification layer for Solana and beyond.

We believe that communication in web3 should be permissionless for protocols and private for users. Herald is built to be that bridge.

## The Problem We Solve

Today, if a DeFi protocol wants to notify a user of a liquidation, they have to ask for an email address. This creates a few problems:
- **Privacy Leakage:** The protocol (and any attacker) now knows the user's email.
- **Fragmented UX:** Users must share their email with every protocol, leading to spam.
- **No Verifiable Proof:** There's no immutable record that a notification was sent.

## The Herald Solution

Herald solves this with a three-part system:

1.  **Privacy Registry (On-Chain):** Users register their email once, encrypted with their wallet, on the Solana blockchain. This record is owned and controlled solely by the user.
2.  **Notification Gateway (Off-Chain):** Protocols call a simple API with a wallet address and message. The gateway resolves the wallet to the encrypted email, securely decrypts it inside a TEE (AWS Nitro Enclave), and delivers the message via email. The plaintext email is never stored or logged.
3.  **ZK Receipts (On-Chain):** Every delivery is written as a low-cost, ZK-compressed receipt on Solana, providing an immutable audit trail for protocols and a notification history for users.

## Core Principles

- **Privacy by Design:** The system is architected so that plaintext user data is never persisted. Email addresses are encrypted client-side and only decrypted ephemerally within a secure enclave.
- **User-Owned Data:** Users own their identity on-chain. They can update, opt-out, or delete their data at any time, with all changes reflected immediately.
- **Verifiable & Immutable:** Every notification sent through Herald is recorded on-chain, providing a transparent and permanent record.
- **Developer Experience First:** With simple SDKs (TypeScript, Rust) and a clear REST API, integrating Herald takes minutes, not days.

## Getting Started

- **For Users:** Register your wallet and manage your preferences at [notify.herald.xyz](https://notify.herald.xyz).
- **For Protocols:** Check out our [Documentation](link-to-docs) to get your API key and start sending notifications.
- **For Developers:** Explore our repositories below to understand the stack, contribute, or run your own instance.

## Key Repositories

Herald is composed of several key components, each in its own repository:

| Repository | Description | Language/Stack |
| :--- | :--- | :--- |
| **[herald-protocol/privacy-registry](link-to-repo)** | The Solana Anchor program that powers the on-chain identity registry. Stores encrypted email mappings and manages user opt-in preferences. | Rust, Anchor |
| **[herald-protocol/notification-gateway](link-to-repo)** | The core NestJS backend. Handles API authentication, rate limiting, wallet resolution, TEE-based decryption, and email dispatch. | TypeScript, NestJS |
| **[herald-protocol/herald-sdk-ts](link-to-repo)** | The official TypeScript/JavaScript SDK for protocols to interact with the Herald API. Supports Node.js and browser environments. | TypeScript |
| **[herald-protocol/herald-sdk-rust](link-to-repo)** | The official Rust SDK for protocols. Async-first, with support for WebAssembly. | Rust |
| **[herald-protocol/user-portal](link-to-repo)** | The Next.js application where users connect their wallet to register, update, or delete their email and notification preferences. | TypeScript, Next.js |
| **[herald-protocol/dev-dashboard](link-to-repo)** | The Next.js dashboard for protocol developers to manage API keys, view analytics, configure webhooks, and handle billing. | TypeScript, Next.js |

## Contributing

We are not open-sourcing the core infrastructure at this time, as we focus on building a secure and reliable product. However, we are actively hiring engineers! If you're passionate about privacy, cryptography, and web3 infrastructure, check out our [Careers](link-to-careers) page.

For everyone else, we welcome feedback, bug reports, and feature requests via our [Discord](link-to-discord) community.

## Status

Herald is currently in a **private beta** with select design partners. We are targeting a mainnet MVP launch by the end of Month 4 (July 2026).

---
**Herald Protocol** - *Private. Verifiable. Composable.*

# Herald Protocol

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

- **For Users:** Register your wallet and manage your preferences at [notify.herald.xyz](https://notify.herald.xyz)
- **For Protocols:** Sign up at [app.herald.xyz](https://app.herald.xyz) to get your API key and start sending notifications
- **For Developers:** Explore our repositories below to understand the stack and contribute
- **For Herald Team:** Access [admin.herald.xyz](https://admin.herald.xyz) for internal operations

## Key Repositories

Herald is composed of several key components, each in its own repository:

| Repository | Description | Language/Stack |
| :--- | :--- | :--- |
| **[privacy-registry](https://github.com/heraldhq-protocol/privacy-registry)** | Solana Anchor program for on-chain identity storage. Stores encrypted email mappings, user opt-in preferences, and protocol registry accounts. | Rust, Anchor |
| **[notification-gateway](https://github.com/heraldhq-protocol/notification-gateway)** | Core notification delivery API (api.herald.xyz). Handles API key auth, rate limiting, wallet resolution, TEE-based decryption, and email dispatch. | TypeScript, NestJS |
| **[admin-registration-api](https://github.com/heraldhq-protocol/admin-registration-api)** | Orchestration API (admin-api.herald.xyz). Powers frontend applications with protocol registration, API key management, user unsubscribe flows, and admin operations. | TypeScript, NestJS |
| **[developer-dashboard](https://github.com/heraldhq-protocol/developer-dashboard)** | Next.js frontend (app.herald.xyz) for protocol teams. Manage API keys, view analytics, configure webhooks, and handle billing. | TypeScript, Next.js |
| **[user-portal](https://github.com/heraldhq-protocol/user-portal)** | Next.js frontend (notify.herald.xyz) for wallet holders. Register email, manage preferences, and view notification history with client-side encryption. | TypeScript, Next.js |
| **[admin-panel](https://github.com/heraldhq-protocol/admin-panel)** | Internal Next.js dashboard (admin.herald.xyz) for Herald operations team. Protocol approvals, user moderation, and system health monitoring. | TypeScript, Next.js |
| **[herald-sdk-ts](https://github.com/heraldhq-protocol/herald-sdk-ts)** | Official TypeScript/JavaScript SDK for protocols to interact with the Herald API. Supports Node.js and browser environments. | TypeScript |
| **[herald-sdk-rust](https://github.com/heraldhq-protocol/herald-sdk-rust)** | Official Rust SDK for protocols. Async-first, with support for WebAssembly. | Rust |

## Contributing

We are not open-sourcing the core infrastructure at this time, as we focus on building a secure and reliable product. However, we are actively hiring engineers! If you're passionate about privacy, cryptography, and web3 infrastructure, check out our [Careers](link-to-careers) page.

For everyone else, we welcome feedback, bug reports, and feature requests via our [Discord](link-to-discord) community.

## Status

Herald is currently in a **private beta** with select design partners. We are targeting a mainnet MVP launch by the end of Month 4 (July 2026).

---
**Herald Protocol** - *Private. Verifiable. Composable.*

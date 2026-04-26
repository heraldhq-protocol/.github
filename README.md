# Herald Protocol

### Privacy-Preserving Notification Infrastructure for Web3

Herald is a protocol that enables DeFi protocols to send notifications to wallet addresses without ever learning the user's personal contact information. By combining on-chain encrypted identity registries with secure, ephemeral decryption in **AWS Nitro Enclaves (TEEs)** and **ZK-compressed delivery receipts** via **Light Protocol**, Herald provides a private, verifiable, and immutable notification layer for Solana and beyond.

We believe that communication in web3 should be permissionless for protocols and private for users. Herald is built to be that bridge.

## The Problem We Solve

Today, if a DeFi protocol wants to notify a user of a liquidation, they have to ask for an email address. This creates several critical issues:
- **Privacy Leakage:** The protocol (and any potential attacker) now knows the user's email address and its connection to their wallet.
- **Fragmented UX:** Users must share their email with every protocol individually, leading to inbox spam and management fatigue.
- **No Verifiable Proof:** There is no immutable record that a notification was actually sent or delivered.

## The Herald Solution

Herald solves this with a robust, privacy-first architecture:

1.  **Privacy Registry (On-Chain):** Users register their contact info once (Email, Telegram, or SMS) on the Solana blockchain. All data is encrypted client-side using NaCl and remains solely under the user's control.
2.  **Notification Gateway (Off-Chain):** Protocols call a simple REST API with a wallet address and message. The gateway resolves the wallet to the encrypted contact info, securely decrypts it inside an **AWS Nitro Enclave**, and delivers the message. The plaintext data is never stored, logged, or exposed outside the enclave.
3.  **ZK Delivery Receipts (On-Chain):** Every notification generates a low-cost, **ZK-compressed receipt** on Solana using **Light Protocol**, providing an immutable audit trail for protocols and a verifiable history for users.

## Core Principles

- **Privacy by Design:** Plaintext user data is never persisted. Contact information is encrypted before it ever touches a server and is only decrypted ephemerally within a secure hardware enclave.
- **User-Owned Identity:** Users own their identity on-chain. They can update preferences, rotate encryption keys, or opt-out at any time, with changes reflected instantly across all integrated protocols.
- **Verifiable & Immutable:** Every notification is backed by an on-chain receipt, ensuring transparency and accountability without compromising privacy.
- **Developer Experience First:** With high-performance SDKs and a clear REST API, integrating Herald takes minutes, allowing protocols to focus on their core logic.

## Getting Started

- **For Users:** Register your wallet and manage your channels at [notify.useherald.xyz](https://notify.useherald.xyz)
- **For Protocols:** Sign up at [app.useherald.xyz](https://app.useherald.xyz) to get your API key and start sending notifications
- **For Developers:** Explore our repositories below to understand the stack and contribute
- **For Herald Team:** Access [admin.useherald.xyz](https://admin.useherald.xyz) for internal operations

## Key Repositories

Herald is composed of several specialized components:

| Repository | Description | Language/Stack |
| :--- | :--- | :--- |
| **[privacy-registry](https://github.com/heraldhq-protocol/privacy-registry)** | Solana Anchor program for on-chain identity and protocol registry. Manages encrypted mappings and writes ZK delivery receipts via Light Protocol. | Rust, Anchor |
| **[notification-gateway](https://github.com/heraldhq-protocol/notification-gateway)** | Core delivery engine. Handles API auth, rate limiting, wallet resolution, and TEE-based decryption inside AWS Nitro Enclaves. | TypeScript, NestJS 11 |
| **[admin-registration-api](https://github.com/heraldhq-protocol/admin-registration-api)** | Orchestration API powering the protocol dashboard and user portal. Manages API keys, billing, and Telegram bot integration. | TypeScript, NestJS 11 |
| **[dev-dashboard](https://github.com/heraldhq-protocol/dev-dashboard)** | Next.js frontend for protocol teams. Manage API keys, view delivery analytics, and configure webhooks. | TypeScript, Next.js 16 |
| **[user-portal](https://github.com/heraldhq-protocol/user-portal)** | Next.js frontend for wallet holders. Register contacts, manage channel preferences (Email, Telegram, SMS), and rotate encryption keys. | TypeScript, Next.js 16 |
| **[landing-page](https://github.com/heraldhq-protocol/landing-page)** | High-performance public landing page showcasing the Herald Protocol features and benefits. | TypeScript, Next.js 16, GSAP |
| **[admin-panel](https://github.com/heraldhq-protocol/admin-panel)** | Internal dashboard for Herald operations. Protocol approvals, system health monitoring, and incident management. | TypeScript, Next.js 16 |
| **[herald-sdk-ts](https://github.com/heraldhq-protocol/herald-sdk-ts)** | Official TypeScript/JavaScript SDK for easy integration into Node.js and browser environments. | TypeScript |
| **[herald-sdk-rust](https://github.com/heraldhq-protocol/herald-sdk-rust)** | Official Rust SDK for protocols. Async-first, with support for WebAssembly. | Rust |

## Contributing

We are focused on building a secure and reliable foundation. While core infrastructure remains proprietary during beta, we welcome feedback and bug reports via our [Discord](link-to-discord). We are also hiring! If you're passionate about privacy and cryptography, reach out to us.

## Status

Herald is currently in **private beta**. We are targeting a mainnet MVP launch by the end of July 2026.

---
**Herald Protocol** - *Private. Verifiable. Composable.*

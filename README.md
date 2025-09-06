# VaultChain Protocol

> **Enterprise Real-World Asset Tokenization Protocol on Bitcoin L2**

VaultChain is a next-generation institutional-grade protocol for tokenizing and managing real-world assets on Stacks, Bitcoin's most secure Layer 2 network. By leveraging Bitcoin's proven security model, VaultChain enables fractional ownership of high-value assets with enterprise-level compliance and regulatory adherence built into every transaction.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Clarity Version](https://img.shields.io/badge/Clarity-v3-blue)](https://docs.stacks.co/clarity)
[![Stacks Network](https://img.shields.io/badge/Network-Stacks-orange)](https://www.stacks.co/)

## 🚀 Key Value Propositions

- **🔒 Bitcoin-Secured Ownership**: Every asset is anchored to Bitcoin's immutable ledger
- **📋 Institutional Compliance**: Built-in KYC/AML with granular regulatory controls  
- **💧 Fractional Liquidity**: Transform illiquid assets into tradeable digital shares
- **🔍 Transparent Provenance**: Immutable ownership history with block-level verification
- **🛡️ Enterprise Security**: Multi-layered protection leveraging Bitcoin's hash power

## 🎯 Perfect For

- **Real Estate** - Fractional property ownership and investment
- **Fine Art** - Democratize access to high-value artworks
- **Commodities** - Tokenize precious metals, oil, and other commodities
- **Private Equity** - Enable liquid markets for private investments
- **Luxury Assets** - Cars, watches, collectibles, and more

## 🏗️ Architecture Overview

VaultChain implements a sophisticated multi-layered architecture:

### Core Components

1. **Asset Registry** - Central repository for asset metadata and ownership structure
2. **Compliance Engine** - KYC/AML verification and regulatory adherence
3. **Fractional Ownership Manager** - Handle partial ownership transfers
4. **Event Logging System** - Immutable transaction history
5. **NFT Integration** - Primary ownership tokens with Bitcoin security

### Smart Contract Features

- **Non-Fungible Token (NFT)** integration for primary ownership
- **Fractional share management** for partial ownership
- **Compliance verification** system for regulatory adherence
- **Event logging** for complete transaction history
- **Input validation** and security checks

## 📋 Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) v2.0+
- [Node.js](https://nodejs.org/) v16+
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

## 🛠️ Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/godwin-smart/vault-chain.git
   cd vault-chain
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Initialize Clarinet environment**

   ```bash
   clarinet check
   ```

## 🧪 Testing

VaultChain includes comprehensive unit tests using Vitest and Clarinet SDK:

```bash
# Run all tests
npm test

# Run tests with coverage report
npm run test:report

# Watch mode for development
npm run test:watch

# Check contracts syntax
clarinet check
```

## 🚀 Quick Start

### 1. Deploy Contract

```bash
# Check contract syntax
clarinet check

# Deploy to local testnet
clarinet integrate

# Deploy to Stacks testnet (requires setup)
clarinet deploy --testnet
```

### 2. Basic Usage Examples

#### Create a New Asset Token

```clarity
;; Tokenize a real estate property
(contract-call? .vault-chain create-asset 
  u1000000      ;; Total supply (1M shares)
  u100000       ;; Fractional shares available
  "ipfs://QmX..." ;; Metadata URI
)
```

#### Transfer Fractional Ownership

```clarity
;; Transfer 1000 shares to another user
(contract-call? .vault-chain transfer-fractional-ownership
  u1            ;; Asset ID
  'ST1HJKN...   ;; Recipient address  
  u1000         ;; Amount of shares
)
```

#### Set Compliance Status

```clarity
;; Approve user for KYC/AML compliance (admin only)
(contract-call? .vault-chain set-compliance-status
  u1            ;; Asset ID
  'ST1HJKN...   ;; User address
  true          ;; Approved status
)
```

## 📚 API Reference

### Public Functions

#### Asset Management

- `create-asset(total-supply, fractional-shares, metadata-uri)` - Tokenize a new real-world asset
- `transfer-fractional-ownership(asset-id, to-principal, amount)` - Transfer partial ownership
- `set-compliance-status(asset-id, user, is-approved)` - Update KYC/AML status (admin only)

### Read-Only Functions

#### Data Access

- `get-asset-details(asset-id)` - Retrieve complete asset information
- `get-owner-shares(asset-id, owner)` - Get ownership share balance
- `get-compliance-details(asset-id, user)` - Check compliance status
- `get-event(event-id)` - Access transaction history

### Error Codes

| Code | Constant | Description |
|------|----------|-------------|
| u1 | `ERR-UNAUTHORIZED` | Unauthorized access attempt |
| u2 | `ERR-INSUFFICIENT-FUNDS` | Insufficient balance for operation |
| u3 | `ERR-INVALID-ASSET` | Invalid or non-existent asset |
| u4 | `ERR-TRANSFER-FAILED` | Transfer operation failed |
| u5 | `ERR-COMPLIANCE-CHECK-FAILED` | KYC/AML verification failed |
| u6 | `ERR-INVALID-INPUT` | Invalid input parameters |
| u7 | `ERR-INSUFFICIENT-SHARES` | Not enough shares for operation |
| u8 | `ERR-EVENT-LOGGING` | Event logging system error |

## 🛡️ Security Features

### Multi-Layer Security

1. **Bitcoin Finality** - All transactions benefit from Bitcoin's proof-of-work security
2. **Input Validation** - Comprehensive parameter checking and sanitization
3. **Access Control** - Role-based permissions for administrative functions
4. **Compliance Integration** - Built-in KYC/AML verification requirements
5. **Immutable Logging** - Complete audit trail of all operations

### Best Practices

- All user inputs are validated before processing
- Compliance checks are mandatory for transfers
- Event logging provides complete transparency
- Administrative functions require proper authorization
- Share arithmetic prevents underflow/overflow attacks

## 📊 Data Structures

### Asset Registry

```clarity
{
  owner: principal,           ;; Asset creator/primary owner
  total-supply: uint,        ;; Maximum number of shares
  fractional-shares: uint,   ;; Available fractional shares
  metadata-uri: string,      ;; IPFS or external metadata link
  is-transferable: bool,     ;; Transfer permission flag
  created-at: uint,          ;; Block height of creation
}
```

### Share Ownership

```clarity
{
  asset-id: uint,           ;; Reference to asset
  owner: principal,         ;; Share owner address
  shares: uint,            ;; Number of owned shares
}
```

### Compliance Status

```clarity
{
  is-approved: bool,        ;; KYC/AML approval status
  last-updated: uint,       ;; Last verification update
  approved-by: principal,   ;; Authorizing admin
}
```

## 🌐 Network Configuration

The protocol supports multiple Stacks network environments:

- **Devnet** - Local development and testing
- **Testnet** - Public testing environment
- **Mainnet** - Production Bitcoin L2 network

Configuration files are located in the `settings/` directory.

## 🤝 Contributing

We welcome contributions to VaultChain! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Add comprehensive tests
5. Ensure all tests pass (`npm test`)
6. Commit your changes (`git commit -m 'Add amazing feature'`)
7. Push to the branch (`git push origin feature/amazing-feature`)
8. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚡ Built on Stacks

VaultChain leverages the power of Stacks blockchain:

- **Bitcoin Security** - Inherits Bitcoin's hash power and finality
- **Smart Contracts** - Clarity language for safe, predictable execution
- **DeFi Integration** - Compatible with Stacks DeFi ecosystem
- **Scalability** - Layer 2 performance with Layer 1 security

---

**VaultChain Protocol** - *Where Bitcoin Meets Real-World Asset Innovation*

> Transform traditional asset ownership through Bitcoin's proven security model, enabling fractional ownership of high-value assets with enterprise-level compliance.

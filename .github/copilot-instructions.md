# AI Agent Instructions for Flash Crypto Software

## Project Overview

**Flash Crypto Software for USDT and BTC** is a cryptocurrency trading and asset management tool designed for easy trading, asset splitting, and fund transfers across supported wallets (Binance, Bybit, and other CEX platforms).

**Repository Type**: This is a **documentation and release distribution repository**. Source code is not included - the software is distributed as compiled executables via GitHub Releases. This repository serves as the central information hub and download location for users.

## Key Architecture

### Core Features
1. **Trading Module**: Handles USDT/BTC trading operations with user-friendly interface
2. **Asset Splitting**: Enables division of cryptocurrency holdings into smaller units
3. **Transfer Module**: Manages fund transfers to recipient wallet addresses
4. **Wallet Management**: Tracks assets and maintains duration constraints (up to 45 days)

### Supported Platforms
- **Binance**: Primary CEX integration
- **Bybit**: Derivatives trading platform support
- **Generic CEX**: Compatible with various centralized exchanges

## Development Conventions

### Repository Scope & Constraints
- **No source code** is maintained in this repository
- **Documentation-focused**: Changes are limited to README.md, contributing guides, and issue management
- **Release management**: Adding release notes, updating installation instructions, and updating download links
- **User communication**: GitHub Issues and Discussions for feature requests and bug reports

### Repository Structure
- **README.md**: Primary documentation with feature overview, installation, and usage guides
- **LICENSE**: MIT License
- **.github/copilot-instructions.md**: AI agent guidance (this file)
- Image assets: Screenshots/documentation images in root directory
- **No build pipeline**: Executables are built and maintained separately; PRs should not attempt to add build infrastructure

### When Contributing
- Focus on clarity in documentation
- Ensure instructions remain OS-agnostic (Windows, macOS, Linux support)
- Update README.md when features or wallet support changes
- Document wallet compatibility clearly

## Critical Workflows

### Installation & Setup
1. Users download executable from releases page
2. Follow on-screen setup instructions
3. Configure wallet connections (Binance, Bybit, or CEX)

### Feature Implementation
When implementing new features, follow the established pattern:
- **Trading**: User selects crypto (USDT/BTC), enters amount, confirms trade
- **Splitting**: User specifies split amount, confirms operation
- **Transfer**: User inputs recipient address, confirms transaction
- **Wallet Management**: Track asset duration and status

## Important Constraints & Patterns

### Asset Duration
- Assets can be held in wallets for up to 45 days
- Implement duration tracking and warnings as assets approach expiration
- Reference wallet management implementation when working with time-based constraints

### Wallet Integration Points
- Each supported wallet (Binance, Bybit, CEX) requires specific integration
- Follow existing patterns for API authentication and transaction handling
- Document wallet-specific limitations and capabilities

### Cross-Component Communication
- Trading operations depend on wallet connection status
- Transfer operations require verified recipient addresses
- Splitting operations must maintain total asset value consistency

## Security Considerations

### Credential & API Key Management
- **Never store API keys** in configuration files, source code, or logs
- Use environment variables or secure vaults for Binance/Bybit API credentials
- Implement API key rotation policies and document them in wallet integration modules
- Ensure API keys have minimal required permissions (read-only for balance checks, specific methods for trading)

### Transaction Security
- **Validate recipient addresses** before execution (format checks, known wallet patterns)
- Implement transaction confirmation UI to prevent accidental transfers of large amounts
- Log all transaction attempts (successful and failed) for audit trails without exposing sensitive data
- Handle decimal precision correctly for USDT (18 decimals) and BTC (8 decimals) to prevent rounding errors that could lead to loss

### Asset Protection
- Encrypt sensitive wallet data at rest if persisting locally
- Implement rate limiting on trading/transfer operations to detect suspicious activity
- Validate all user inputs for injection attacks or malformed cryptocurrency addresses
- Use HTTPS for all external API calls to Binance, Bybit, and other CEX platforms

### Compliance & Auditability
- Document all wallet operations with timestamps and amounts (without PII)
- Maintain separation between testnet and production credentials
- Test security patterns against sample wallets before deploying to production exchanges

## Contribution Guidelines

### For Code Changes
1. Fork the repository
2. Create feature branch with clear naming
3. Implement changes following established patterns
4. Submit pull request with clear description referencing the feature (Trading/Splitting/Transfer/Wallet Management)
5. Ensure wallet compatibility is documented for any changes

### Testing Considerations
- Test against all supported wallets (Binance, Bybit, sample CEX)
- Verify 45-day duration constraint enforcement
- Test edge cases: zero amounts, unsupported currencies, network failures

## Key Files & References
- **README.md**: Feature descriptions, installation steps, and supported wallets list
- Release artifacts: Downloaded from [GitHub Releases](https://github.com/Hayaat787/Flash-crypto-software-for-USDT-and-BTC-/releases)

## External Dependencies
- Wallet APIs: Binance, Bybit (check current API documentation)
- Cryptocurrency data feeds: Real-time USDT/BTC price feeds
- License: MIT License (permissive, allows commercial use with attribution)

## Anti-Patterns to Avoid
- Don't hardcode wallet addresses or API keys
- Don't bypass the 45-day duration constraint
- Don't assume asset values remain constant during operations (handle decimals carefully in USDT)
- Don't implement wallet integrations without testing against actual exchange APIs

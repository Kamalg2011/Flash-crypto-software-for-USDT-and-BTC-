# Copilot Instructions for Flash Crypto Software for USDT and BTC

## Project Overview
This repository provides software for trading, splitting, and transferring USDT and BTC, with wallet management features and support for major exchanges (Binance, Bybit, CEX). The codebase is primarily focused on user-facing operations and asset management workflows.

## Key Architectural Concepts
- **User Operations**: Trading, splitting, and transferring assets are the core flows. Each operation is initiated via a UI and interacts with wallet/exchange APIs.
- **Wallet Integration**: The software supports multiple wallet types and exchanges. Integration points should be modular to allow easy extension for new wallets.
- **Asset Duration**: Assets can be held in wallets for up to 45 days. Duration tracking is a key feature for wallet management.
- **Supported Assets**: USDT and BTC are the primary assets. All logic should be asset-agnostic where possible, but with clear handling for these two.

## Developer Workflows
- **Installation**: Download the latest release from GitHub and run the executable. No build or test scripts are present in the repo; all distribution is via pre-built binaries.
- **Contribution**: Fork, clone, make changes, and submit pull requests. Follow clear commit message conventions and document changes in the README if they affect user workflows.
- **Debugging**: As source code is not present, debugging is limited to runtime behavior of the distributed executable. Issues should be reported via GitHub Issues with detailed reproduction steps.

## Patterns and Conventions
- **Modular Integration**: When adding new wallet or exchange support, follow the pattern of isolating API logic in dedicated modules/classes.
- **User Guidance**: All user-facing features should be documented in the README, with step-by-step instructions for each major operation.
- **No Automated Tests**: There are currently no test scripts or CI/CD workflows. Manual testing and user feedback are the primary validation methods.
- **Release Management**: Releases are managed via GitHub Releases. Update the README and release notes for any new features or changes.

## External Dependencies
- **Wallet APIs**: Integration with Binance, Bybit, and other CEX platforms is expected. Use official SDKs or REST APIs where possible.
- **No Source Code**: The repository does not contain source code, only documentation and release binaries. All logic is inferred from user documentation.

## Example Workflow
- To add support for a new wallet:
  1. Create a new module for the wallet API integration.
  2. Update the UI to allow selection of the new wallet.
  3. Document the new workflow in the README.
  4. Release a new binary and update GitHub Releases.

## Key Files
- `README.md`: Main source of project documentation and user guidance.
- `.github/copilot-instructions.md`: This file, for AI agent guidance.

---

If any section is unclear or missing, please provide feedback so instructions can be improved for future AI agents.

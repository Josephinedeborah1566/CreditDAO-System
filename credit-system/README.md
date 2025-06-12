# Automated Portfolio Rebalancing System

![Automated Portfolio Rebalancing](https://placeholder.svg?height=200&width=800&text=Automated+Portfolio+Rebalancing+System)

A sophisticated smart contract built on the Stacks blockchain using Clarity that enables automated portfolio rebalancing based on target asset allocations. This system allows users to maintain their desired portfolio composition automatically, reducing manual intervention and optimizing investment strategies.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Function Documentation](#function-documentation)
- [Testing](#testing)
- [Security](#security)
- [Contributing](#contributing)
- [License](#license)

## Overview

The Automated Portfolio Rebalancing System is a decentralized finance (DeFi) protocol that helps investors maintain their desired asset allocation automatically. When market movements cause portfolio allocations to drift beyond specified thresholds, the system can automatically rebalance the portfolio back to target allocations, ensuring optimal risk management and investment strategy adherence.

## Features

### Portfolio Management
- **Multi-Asset Portfolios**: Support for up to 5 different assets per portfolio
- **Customizable Allocations**: Set target percentage allocations for each asset (0-100%)
- **Automatic Rebalancing**: Configurable auto-rebalancing when drift exceeds thresholds
- **Threshold Control**: Set custom drift thresholds (e.g., 5% deviation triggers rebalancing)

### Asset Management
- **Dynamic Asset Addition**: Add new assets to existing portfolios
- **Price Oracle Integration**: Real-time asset price updates from authorized oracles
- **Allocation Tracking**: Monitor current vs. target allocations in real-time
- **Asset Metadata**: Store asset names and descriptions for easy identification

### Rebalancing Engine
- **Drift Detection**: Automatically detect when allocations exceed threshold limits
- **Smart Rebalancing**: Calculate optimal trades to restore target allocations
- **Manual Override**: Option to manually trigger rebalancing when needed
- **Rebalancing History**: Track when and how portfolios were rebalanced

### Security & Control
- **Owner Authorization**: Only contract owner can update asset prices
- **User Isolation**: Each user manages their own independent portfolio
- **Threshold Validation**: Prevent invalid allocation percentages and thresholds
- **Asset Duplication Prevention**: Ensure unique assets per portfolio

## Architecture

### Core Components

#### Data Storage
- **Portfolios Map**: Stores user portfolio configurations and metadata
- **Portfolio Assets Map**: Records individual asset holdings and target allocations
- **Asset Prices Map**: Maintains current market prices for all supported assets

#### Rebalancing Algorithm
\`\`\`
1. Calculate current portfolio value across all assets
2. Determine current allocation percentages
3. Compare against target allocations
4. Calculate drift for each asset
5. If maximum drift exceeds threshold, trigger rebalancing
6. Execute trades to restore target allocations
\`\`\`

#### Price Oracle System
\`\`\`
Contract Owner → Update Asset Prices → Price Storage → Portfolio Valuation
\`\`\`

### Data Structures

#### Portfolio Structure
```clarity
{
  total-value: uint,           ;; Total portfolio value in base currency
  last-rebalance: uint,        ;; Block height of last rebalance
  rebalance-threshold: uint,   ;; Drift threshold (e.g., 500 = 5%)
  auto-rebalance-enabled: bool ;; Whether auto-rebalancing is active
}

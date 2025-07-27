# Compound V2/V3 Wallet Risk Scoring System

A comprehensive risk assessment tool that analyzes wallet transaction patterns on Compound Protocol (V2 and V3) and assigns risk scores from 0-1000 to identify potential default risk, liquidity concerns, and behavioral anomalies.

## 🎯 Overview

This system processes wallet addresses and their Compound protocol transaction history to generate risk scores using machine learning and behavioral analysis. It's designed for risk assessment, portfolio management, and DeFi lending decisions.

### Key Features

- **Multi-Protocol Support**: Analyzes both Compound V2 and V3 transactions
- **Comprehensive Risk Assessment**: 25+ risk indicators including default risk, liquidity risk, and behavioral patterns
- **Machine Learning Scoring**: Uses Random Forest ensemble method for accurate risk prediction
- **Batch Processing**: Handles multiple wallet addresses efficiently
- **Export Ready**: Generates CSV output suitable for integration with other systems

## 📊 Risk Scoring Methodology

### Risk Score Scale (0-1000)
- **800-1000**: Very Low Risk (Excellent credit profile)
- **650-799**: Low Risk (Good risk profile with balanced activity)
- **500-649**: Medium Risk (Moderate risk with some concerns)
- **300-499**: High Risk (Poor repayment patterns or liquidation history)
- **0-299**: Very High Risk (Multiple red flags and concerning behavior)

### Key Risk Indicators

#### Default Risk Factors
- Poor repayment history (borrow vs repay ratio)
- Previous liquidation events
- High-risk borrowing patterns
- Debt-to-supply ratio analysis

#### Liquidity Risk Factors
- Volume concentration in single transactions
- Asset concentration patterns
- Transaction frequency anomalies
- Large transaction ratios

#### Behavioral Risk Factors
- Activity consistency (bot-like vs organic behavior)
- Protocol usage patterns
- Gas efficiency metrics
- Time-based activity analysis

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy requests scikit-learn
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/compound-risk-scoring.git
cd compound-risk-scoring
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

### Usage

#### Basic Usage

```python
from compound_risk_scorer import CompoundRiskScorer

# Initialize the scorer
scorer = CompoundRiskScorer()

# Load wallet addresses from CSV
wallet_addresses = scorer.load_wallet_addresses('wallet_list.csv')

# Analyze and score wallets
results = main()
```

#### Google Colab Usage

```python
# Run the convenience function
run_risk_scoring()
```

The system will prompt you to upload a CSV file with wallet addresses and automatically process them.

## 📁 Input Format

Your CSV file should contain wallet addresses in one of these column formats:
- `wallet_id`
- `wallet_address` 
- `address`
- `wallet`

Example CSV:
```csv
wallet_id
0x742d35cc6634c0532925a3b8d0ab1c7d22b8fe2b
0x28c6c06298d514db089934071355e5743bf21d60
0x3f5ce5fbfe3e9af3971dd833d26ba9b5c936f0be
```

## 📈 Output Format

The system generates a CSV file with risk scores:

```csv
wallet_id,score
0x742d35cc6634c0532925a3b8d0ab1c7d22b8fe2b,785
0x28c6c06298d514db089934071355e5743bf21d60,234
0x3f5ce5fbfe3e9af3971dd833d26ba9b5c936f0be,892
```

## 🏗️ Architecture

### Core Components

1. **Data Collection**: Fetches transaction data from Compound V2/V3 APIs
2. **Feature Engineering**: Calculates 25+ risk-related features
3. **Risk Scoring**: Applies ensemble ML model for final scoring
4. **Report Generation**: Creates detailed risk assessment reports

### Feature Categories

#### Transaction Metrics
- Total transaction count and volume
- Average and median transaction sizes  
- Transaction frequency and timing patterns

#### Action Analysis
- Supply/borrow/repay/redeem ratios
- Liquidation history
- Protocol version usage

#### Portfolio Risk
- Asset diversification
- Volume concentration
- Position sizing patterns

#### Behavioral Indicators
- Activity consistency
- Gas usage efficiency
- Time-based patterns

## 🔧 Configuration

### Mock Data Mode
For development and testing, the system can generate realistic mock transaction data:

```python
USE_MOCK_DATA = True  # Set to False for production API calls
```

### Production API Integration
To use real Compound data, implement the following API endpoints:

- **Compound V2**: `https://api.compound.finance/api/v2/account`
- **Compound V3**: GraphQL endpoints
- **Etherscan API**: For detailed transaction data

## 📊 Sample Output

```
=== COMPOUND WALLET RISK ASSESSMENT RESULTS ===

📊 Risk Distribution:
  Very Low Risk: 15 wallets (15.0%)
  Low Risk: 25 wallets (25.0%)
  Medium Risk: 35 wallets (35.0%)
  High Risk: 20 wallets (20.0%)
  Very High Risk: 5 wallets (5.0%)

🏆 Top Risk Factors:
  default_risk_score: 0.245
  liquidation_ratio: 0.198
  repayment_discipline: 0.167
  volume_concentration: 0.134
```

## 🔬 Technical Details

### Machine Learning Model
- **Algorithm**: Random Forest Regressor
- **Features**: 25+ engineered risk indicators  
- **Scaling**: StandardScaler for feature normalization
- **Output**: MinMaxScaler for 0-1000 score range

### Risk Calculation Formula
```
Base Score = 500 (neutral)
+ Supply-only bonus: +150
+ Good repayment: +100  
+ Long-term user: +100
- Liquidation penalty: -200
- Poor repayment: -150
- High-risk borrower: -150
+ Volume factor: up to +75
+ Consistency bonus: +50
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This tool is for educational and analytical purposes. Risk scores should not be the sole basis for financial decisions. Always conduct additional due diligence and consider multiple factors when assessing DeFi lending risk.

## 🔗 Related Resources

- [Compound Protocol Documentation](https://compound.finance/docs)
- [DeFi Risk Assessment Best Practices](https://defipulse.com)
- [Ethereum Transaction Analysis](https://etherscan.io)

## 📧 Support

For questions or support, please open an issue in the GitHub repository or contact [your-email@domain.com].

---

**Built for the DeFi community** 🚀

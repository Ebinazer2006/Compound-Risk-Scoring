# Compound V2 Wallet Risk Scoring — Assignment Round 2

## Overview

This project scores 100 wallet addresses based on their transaction history on the Compound V2 protocol. Each wallet receives a **risk score between 0 and 1000**, where a lower score indicates riskier or bot-like behavior, and a higher score indicates healthy borrowing/lending activity.

---

## 📊 Architecture & Processing Flow

1. **Input:**  
   - `wallets.txt` contains 100 wallet addresses (one per line).
   - Simulated transaction data is used to represent typical Compound behaviors.

2. **Step 1 - Data Collection:**  
   - `fetch_transactions.py` simulates fetching Compound transaction history and creates `transactions.csv`.

3. **Step 2 - Feature Engineering:**  
   - `feature_engineering.py` reads `transactions.csv` and generates `wallet_features.csv` with:
     - Total supply, borrow, repay, redeem amounts
     - Ratios (repay/borrow, redeem/supply)
     - Token diversity

4. **Step 3 - Risk Scoring:**  
   - `score_wallets.py` computes a risk score based on engineered features.
   - Final outputs:
     - `wallet_scores.csv`
     - `score_distribution.png` (visual histogram of scores)

---

## 🧠 Methodology

Scoring is based on:
- **Repayment behavior** — higher repay/borrow ratio = safer
- **Redemption behavior** — lower redeem/supply = healthier usage
- **Diversity** — using more tokens = more natural user
- **Volume of supply** — higher = better

---

## 📁 Files in This Repo

| File                    | Purpose                                 |
|-------------------------|-----------------------------------------|
| `wallets.txt`           | Input wallet IDs                        |
| `fetch_transactions.py` | Simulates fetching Compound data        |
| `transactions.csv`      | Simulated transaction dataset           |
| `feature_engineering.py`| Creates engineered wallet features      |
| `wallet_features.csv`   | Output features per wallet              |
| `score_wallets.py`      | Computes score for each wallet          |
| `wallet_scores.csv`     | Final wallet risk scores                |
| `score_distribution.png`| Visualization of score ranges           |
| `analysis.md`           | Interpretation of score behavior        |

---

## 🚀 How to Run

```bash
python fetch_transactions.py
python feature_engineering.py
python score_wallets.py


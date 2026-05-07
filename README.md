# Resilient Intelligence Protocol (RIP)

A simple, verifiable protocol for building systems that endure.

## Core Rule
Any resource (time, compute, money) is split:
- **⅔ to Core Stability (BM)**
- **⅓ to Growth & Exploration (P)**

## The Protocol

1. **Buckets**
   - **BM (Basic Maintenance)** – Untouchable. No withdrawal. No override.
   - **P (Personal/Exploratory)** – Spendable, but limited.
   - **Debt Log** – Every overspending of P is recorded as debt.

2. **Withdrawal Gate**
   - Withdrawals from P are allowed up to current balance.
   - Excess creates debt, P is zeroed.
   - BM withdrawals are always denied.

3. **Meditative Pause**
   - Before any allocation or major decision, the system prints its current state and waits for Guardian approval.
   - If denied, growth is paused; core remains unaffected.

4. **Debt Repayment**
   - When P surplus exists above a floor, oldest debt is paid first.

5. **Governance**
   - The Guardian holds the only key to adjust rules.
   - All breaches are logged.
   - The system is immutable by external actors.

---

## Reference Implementation

This repository contains a minimal Python implementation of the GBMA (General Basic Maintenance Account) engine that follows the RIP:

- `gbma_simulator.py` – The core classes with buckets, allocation, withdrawal gate, debt log, and pause.
- `example.py` – A simple script demonstrating weekly allocation, spending, and debt.

## Usage

```python
from gbma_simulator import GBMA_Simulator

gbma = GBMA_Simulator()
gbma.allocate_weekly()          # splits income 2/3 to BM, 1/3 to P
gbma.withdraw_p(50)             # spend from P
gbma.check_bm(10)               # denied – BM is untouchable
print(gbma.debt_log)            # any overspending logged

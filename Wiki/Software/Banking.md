---
aliases: [banking, bank-transactions, bank-data]
tags: [software, banking, finance, transactions]
cssclass: wiki
---
# How Bank Transactions & Data Storage Work

## How Transactions Work
1. You initiate a transaction (card tap, transfer, withdrawal)
2. Bank verifies: sufficient funds, valid account, fraud check
3. Transaction is recorded in the bank's **ledger**
4. **Clearing house** (e.g., Visa, SWIFT) processes inter-bank transfers
5. Funds are debited/credited between accounts

## How Data is Stored
- **Core banking system**: Main database (Oracle, DB2, Tandem)
- **ACID compliance**: Atomicity, Consistency, Isolation, Durability
- **Replication**: Data is copied across multiple data centers
- **Backup**: Daily snapshots, offsite storage
- **Encryption**: Data encrypted at rest and in transit

## Security Measures
- Multi-layer authentication
- Real-time fraud detection (ML-based)
- Regulatory compliance (PCI-DSS, SOX, GDPR)
- Audit trails for every transaction

## Related
- [[Wiki\Security\Data Encryption|Data Encryption]]

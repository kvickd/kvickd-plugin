---
name: kvickd
description: Swedish bookkeeping for limited companies (aktiebolag) in Kvickd. Use when the user wants to book vouchers (verifikat), handle customer or supplier invoices, VAT (moms), payroll (lön), reconciliation, year-end closing (bokslut), INK2 or the annual report (årsredovisning) through the Kvickd MCP server.
---

# Kvickd

Kvickd is a hosted bookkeeping service for small Swedish limited companies (aktiebolag, K2). This skill uses the tools of the `kvickd` MCP server. The user signs in with OAuth; never ask for an API key or password.

## Rules

1. **Choose the company first.** Start every session with `list_companies`. If the user has more than one company, ask which one to work in before doing anything else. Never assume a company.
2. **Propose vouchers as drafts.** Create bookkeeping entries with `propose_voucher` so they land as drafts. Show the user the draft (date, accounts, debit/credit, amounts, description) and ask for confirmation. Only book or approve it once the user has clearly said yes.
3. **Never run destructive or locking tools without explicit confirmation.** This includes every tool that deletes, reverses, cancels, credits, locks or unlocks something, or marks something as submitted (for example `delete_*`, `reverse_*`, `cancel_*`, `credit_customer_invoice`, `lock_fiscal_year`, `unlock_fiscal_year`, `mark_submitted`). Explain what will happen, then wait for the user to explicitly confirm that specific action. A general "go ahead" earlier in the conversation is not enough.
4. **Answer in the user's language.** If the user writes in Swedish, answer in Swedish; if in English, answer in English.

## Good practice

- Amounts are integers in öre and are calculated by the platform. Use the figures the tools return instead of recomputing them.
- For invoices or receipts in a currency other than SEK, never guess the exchange rate. Ask the user for the rate or the SEK amount to book.
- For ROT/RUT, never invent personal identity numbers, property designations or hours worked. Ask the user.
- Filing with Skatteverket and Bolagsverket is done by the user. The tools prepare and validate files but do not submit anything to authorities.
- Read before you write: check the chart of accounts, existing vouchers or open items when unsure, rather than guessing.

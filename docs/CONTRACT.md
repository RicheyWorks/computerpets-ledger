# Ledger contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Ledger**
- Repo: `computerpets-ledger`
- Category: Microservices
- Idea: Economy Ledger
- Port / surface: `8086`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Account(id, asset, owner) · Posting(debit, credit, amount, ref) · Asset(COIN|TREAT|WEI|VOTE)

## Surface

- POST /v1/post — {debit, credit, amount, ref} — atomic
- GET /v1/accounts/{id} — balances by asset
- GET /v1/audit/{ref} — both sides of a business event

## Neighbors

- computerpets-minter
- computerpets-bazaar
- computerpets-quests
- computerpets-console
- computerpets-ballot

## Failure doctrine

Unbalanced post → reject. Partial chain settlement → hold in escrow account, never delete the row. Replay → unique(ref) constraint.

## Stack

Java 21 · Spring Boot 3.3 · double-entry tables · Flyway · PostgreSQL · optional chain settlement

---
name: nova-poshta
description: |
  Use Nova Poshta API 2.0 for reference lookups and authenticated counterparty, address, and contact-person operations.
  Use this skill when you need the correct `modelName`, `calledMethod`, request fields, refresh guidance, and response-shape hints for Nova Poshta API requests.
compatibility: Requires network access and curl or Python HTTP client for making POST requests.
allowed-tools: Bash(curl:*) Python(*)
---

# Nova Poshta API

Use the unified JSON endpoint for every request:

https://api.novaposhta.ua/v2.0/json/

## Request shape

Every request uses:

- `modelName`
- `calledMethod`
- `methodProperties`
- `apiKey` for methods that require authentication

Use `<API_KEY>` as a placeholder in examples. Never hardcode a real key.

## Working rules

- **Use official docs first**
  - https://developers.novaposhta.ua/documentation

- **Use mirror docs only as fallback when the official portal is blocked**
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/

- **Check every response envelope**
  - Inspect `success`, `errors`, `errorCodes`, `warningCodes`, `infoCodes`, and `messageCodes`.

- **Cache only stable directories**
  - Refresh address directories daily.
  - Refresh common directories monthly.
  - Refresh account-specific counterparty data on demand and after mutations.

- **Treat `Ref` values as canonical identifiers**
  - Resolve cities, streets, warehouses, counterparties, addresses, and contacts by `Ref` before creating dependent entities.

## Example request

```json
{
  "apiKey": "<API_KEY>",
  "modelName": "Counterparty",
  "calledMethod": "getCounterparties",
  "methodProperties": {
    "CounterpartyProperty": "Sender",
    "Page": 1
  }
}
```

## Suggested workflow

- **1. Resolve directories first**
  - Use `Address` and `Common` methods to obtain valid `Ref` values.

- **2. Perform authenticated mutations live**
  - Use `Counterparty`, `Address`, and `ContactPerson` mutation methods with `<API_KEY>`.

- **3. Invalidate cached account data after writes**
  - Refresh local lists of counterparties, addresses, and contacts after `save`, `update`, or `delete`.

- **4. Escalate verification when docs disagree**
  - A few legacy mirror pages contain naming or payload inconsistencies. Prefer the live official portal whenever it is reachable.

## Reference files

- **[references/address-directory.md](references/address-directory.md)**
  - Address lookups: cities, streets, warehouses, warehouse types.

- **[references/common-directories.md](references/common-directories.md)**
  - Core `Common` directories: payer types, payment forms, cargo types, service types.

- **[references/extended-common-directories.md](references/extended-common-directories.md)**
  - Additional `Common` directories: ownership forms, redelivery types, pallets, time intervals, trays, document statuses, and more.

- **[references/counterparty-directory.md](references/counterparty-directory.md)**
  - Counterparty, address, and contact-person lookup methods.

- **[references/counterparty-operations.md](references/counterparty-operations.md)**
  - Counterparty creation, update, deletion, and option flags.

- **[references/address-operations.md](references/address-operations.md)**
  - Address creation, update, and deletion.

- **[references/contact-operations.md](references/contact-operations.md)**
  - Contact-person creation, update, and deletion.

- **[references/error-handling.md](references/error-handling.md)**
  - Error fields, code lists, and response-handling guidance.

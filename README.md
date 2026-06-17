# Nova Poshta Skills

This repository contains a Windsurf/Cascade skill for working with the Nova Poshta API 2.0.

## What this skill does

- Helps you choose the correct Nova Poshta `modelName` and `calledMethod`
- Documents required and optional request fields for supported methods
- Explains which methods require an API key
- Recommends caching and refresh strategy for stable directories
- Summarizes common response fields and error-envelope handling
- Links each method group back to the official Nova Poshta documentation, with mirror links only as fallback references

## Repository structure

```text
nova-poshta-skills/
├── SKILL.md
├── README.md
└── references/
    ├── address-directory.md
    ├── address-operations.md
    ├── common-directories.md
    ├── contact-operations.md
    ├── counterparty-directory.md
    ├── counterparty-operations.md
    ├── error-handling.md
    └── extended-common-directories.md
```

## Installation

Local installation example:

```bash
npx skills add ./nova-poshta-skill
```

GitHub installation examples:

```bash
npx skills add https://github.com/<owner>/<repo>
```

```bash
npx skills add git+https://github.com/<owner>/<repo>.git
```

## Nova Poshta API key setup

Many `Common`, `Counterparty`, `Address` mutation, and `ContactPerson` methods require a Nova Poshta API key.

Recommended setup:

```bash
export NOVAPOSHTA_API_KEY="<API_KEY>"
```

Rules:

- Use `<API_KEY>` in examples and templates
- Never hardcode a real key in source code or committed files
- Pass the key as the top-level `apiKey` field only for methods that require authentication

## Example API call

```bash
curl -X POST -H 'Content-Type: application/json' \
     -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"getCounterparties","methodProperties":{"CounterpartyProperty":"Sender","Page":1}}' \
     https://api.novaposhta.ua/v2.0/json/
```

## Supported method groups

- `Address`
  - Directory lookups for cities, streets, warehouses, and warehouse types
  - Address creation, update, and deletion

- `Counterparty`
  - Counterparty listing, address listing, contact-person listing
  - Counterparty creation, update, deletion, and option lookup

- `ContactPerson`
  - Contact-person creation, update, and deletion

- `Common`
  - Payer types, payment forms, cargo types, service types
  - Ownership forms, cargo descriptions, redelivery types, pallets, time intervals, tires/wheels, trays, and document statuses

- Error handling
  - Response envelope checks and Nova Poshta error code references

## Documentation notes

Primary official documentation:

- https://developers.novaposhta.ua/documentation
- https://developers.novaposhta.ua/view/
- https://developers.novaposhta.ua/listerrorscodes?quality=10

Fallback mirror documentation, only when the official portal is blocked:

- https://alexpseha.gitbooks.io/api_test_one_chapter/content/

Notes:

- Official URLs are preferred as the source of truth
- Some legacy mirror pages contain malformed examples or inconsistent naming
- This repository marks partially verified behavior explicitly instead of inventing unsupported API behavior

## Usage guidance

- Use `SKILL.md` for the high-level workflow and operating rules
- Use the files in `references/` for method-by-method details
- Refresh stable directories on a schedule, but refresh account-specific counterparty data after writes
- Always inspect `success`, `errors`, `errorCodes`, `warningCodes`, `infoCodes`, and `messageCodes` in responses

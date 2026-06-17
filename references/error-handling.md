# Error Handling

Official error code documentation:

https://developers.novaposhta.ua/listerrorscodes?quality=10

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Every Nova Poshta API response includes a `success` boolean in the top-level envelope.

When `success` is `false`, inspect:

- `errors`
- `messageCodes`
- `errorCodes`
- `warningCodes`
- `infoCodes`

## Recommended handling

- Surface human-readable `errors` to the user.
- Log `errorCodes` and `messageCodes` for troubleshooting.
- Log the request `modelName`, `calledMethod`, and sanitized `methodProperties` together with the response envelope.
- Treat validation errors as user-fixable input issues.
- Treat authentication errors as configuration/API key issues.
- Treat network or timeout errors as retryable when appropriate.
- Refresh cached directories if the error suggests stale references.

## Generic response check

```typescript
if (!response.success) {
  console.error("Nova Poshta API error", {
    errors: response.errors,
    errorCodes: response.errorCodes,
    messageCodes: response.messageCodes,
    warningCodes: response.warningCodes,
    infoCodes: response.infoCodes
  });

  throw new Error(response.errors?.join("; ") || "Nova Poshta API request failed");
}
```

## Useful links

- API documentation: https://developers.novaposhta.ua/documentation
- Error codes: https://developers.novaposhta.ua/listerrorscodes?quality=10
- API endpoint: https://api.novaposhta.ua/v2.0/json/

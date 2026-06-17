# Counterparty Directory

Use these `Counterparty` methods to read account-specific senders, recipients, addresses, and contact persons.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Treat these as account-scoped records.
  - Refresh on demand and after any create, update, or delete operation.
  - If you keep a local copy, refresh at least daily.

## getCounterparties

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `getCounterparties`

- **Purpose**
  - Load a paginated list of counterparties such as senders, recipients, or third persons.

- **Required parameters**
  - `CounterpartyProperty` — the accessible mirror confirms values such as `Sender` and `Recipient`.

- **Optional parameters**
  - `Page` — page number.
  - `FindByString` — counterparty name fragment.

- **Response field summary**
  - Common fields include `Description`, `Ref`, city-related fields, and counterparty-type metadata.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"getCounterparties","methodProperties":{"CounterpartyProperty":"Sender","Page":1}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://developers.novaposhta.ua/view/model/a28f4b04-8512-11ec-8ced-005056b2dbe1/method/a37a06df-8512-11ec-8ced-005056b2dbe1
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_7_zavantazhiti_spisok_kontragentv_vdpravnikvoderz.html

## getCounterpartyAddresses

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `getCounterpartyAddresses`

- **Purpose**
  - Load saved addresses for a specific counterparty.

- **Required parameters**
  - `Ref` — counterparty reference.

- **Optional parameters**
  - `CounterpartyProperty` — sender or recipient context.

- **Response field summary**
  - Expect address references and human-readable address descriptions associated with the counterparty.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"getCounterpartyAddresses","methodProperties":{"Ref":"<COUNTERPARTY_REF>","CounterpartyProperty":"Sender"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_7_zavantazhiti_spisok_kontragentv_vdpravnikvoderz.html

## getCounterpartyContactPersons

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `getCounterpartyContactPersons`

- **Purpose**
  - Load contact persons linked to a counterparty.

- **Required parameters**
  - `Ref` — counterparty reference.

- **Optional parameters**
  - None directly verified from the accessible mirror during this review.

- **Response field summary**
  - Common fields include `LastName`, `FirstName`, `MiddleName`, `Phone`, `Email`, `Description`, and `Ref`.

- **Verification note**
  - Some legacy prose and wrappers use the singular name `getCounterpartyContactPerson`, but current clients and the actual request name used across integrations are `getCounterpartyContactPersons`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"getCounterpartyContactPersons","methodProperties":{"Ref":"<COUNTERPARTY_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_7_zavantazhiti_spisok_kontragentv_vdpravnikvoderz.html

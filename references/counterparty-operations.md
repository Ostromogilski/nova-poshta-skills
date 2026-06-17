# Counterparty Operations

Use these methods to create, update, delete, and inspect counterparties.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Do not rely on stale cached counterparty data after mutations.
  - Refresh related lists immediately after `save`, `update`, or `delete`.

## save private person

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `save`

- **Purpose**
  - Create a private-person counterparty.

- **Required parameters**
  - `CityRef`
  - `FirstName`
  - `LastName`
  - `MiddleName`
  - `Phone`
  - `CounterpartyType` = `PrivatePerson`
  - `CounterpartyProperty` = `Sender` or `Recipient`

- **Optional parameters**
  - `Email`

- **Response field summary**
  - The legacy example returns a created counterparty `Ref`, full description, person-name fields, and related counters/metadata.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"save","methodProperties":{"CityRef":"<CITY_REF>","FirstName":"Іван","LastName":"Іваненко","MiddleName":"Іванович","Phone":"380XXXXXXXXX","Email":"","CounterpartyType":"PrivatePerson","CounterpartyProperty":"Recipient"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://developers.novaposhta.ua/view/model/a28f4b04-8512-11ec-8ced-005056b2dbe1/method/0ae5dd75-8a5f-11ec-8ced-005056b2dbe1
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_20_zberezhennya_kontragenta_metod_save.html

## save organization

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `save`

- **Purpose**
  - Create an organization counterparty.

- **Required parameters**
  - `CityRef`
  - `FirstName` — used as the organization name in the accessible mirror example.
  - `CounterpartyType` = `Organization`
  - `CounterpartyProperty`
  - `OwnershipForm`

- **Optional parameters**
  - `MiddleName`
  - `LastName`
  - `Phone`
  - `Email`

- **Response field summary**
  - Expect created counterparty identifiers and descriptive fields for the saved organization.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"save","methodProperties":{"CityRef":"<CITY_REF>","FirstName":"Компанія","MiddleName":"","LastName":"","Phone":"","Email":"","CounterpartyType":"Organization","CounterpartyProperty":"Recipient","OwnershipForm":"<OWNERSHIP_FORM_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_21_zberegti_kontragenta_z_tipom_yuridichna_osoba_.html

## save third person

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `save`

- **Purpose**
  - Create a third-person counterparty.

- **Required parameters**
  - `CityRef`
  - `CounterpartyProperty` = `ThirdPerson`
  - `CounterpartyType` = `Organization`
  - `EDRPOU`

- **Optional parameters**
  - `FirstName`
  - `MiddleName`
  - `LastName`
  - `Phone`
  - `Email`
  - `OwnershipForm`

- **Response field summary**
  - Expect created counterparty identifiers and descriptive fields for the saved third-person record.

- **Verification note**
  - The accessible mirror example leaves several fields empty. Treat optional organization-identification fields conservatively and verify against the official portal for your exact business flow.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"save","methodProperties":{"CityRef":"<CITY_REF>","FirstName":"","MiddleName":"","LastName":"","Phone":"","Email":"","CounterpartyType":"Organization","CounterpartyProperty":"ThirdPerson","EDRPOU":"99999999","OwnershipForm":""}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_21_zberegti_kontragenta_z_tipom_yuridichna_osoba_.html

## update

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `update`

- **Purpose**
  - Update an existing counterparty.

- **Required parameters**
  - `Ref`
  - In the accessible example: `CityRef`, `FirstName`, `LastName`, `MiddleName`, `Phone`, `Email`, `CounterpartyType`, `CounterpartyProperty`

- **Optional parameters**
  - Only change the fields your workflow needs, but keep the payload aligned with the official portal for your counterparty type.

- **Response field summary**
  - Expect a success envelope and updated counterparty details.

- **Verification note**
  - The legacy documentation states updates are intended before shipment documents are created for that counterparty.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"update","methodProperties":{"Ref":"<COUNTERPARTY_REF>","CityRef":"<CITY_REF>","FirstName":"Іван","MiddleName":"Іванович","LastName":"Іваненко","Phone":"380XXXXXXXXX","Email":"","CounterpartyType":"PrivatePerson","CounterpartyProperty":"Recipient"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_22_onoviti_dan_kontragenta_metod_update.html

## delete

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `delete`

- **Purpose**
  - Delete an existing counterparty record.

- **Required parameters**
  - `Ref`

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect a success envelope describing the deleted record.

- **Verification note**
  - The legacy documentation says API deletion is available for recipient counterparties. Sender-counterparty deletion may require manual support handling.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"delete","methodProperties":{"Ref":"<COUNTERPARTY_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_22_onoviti_dan_kontragenta_metod_update.html

## getCounterpartyOptions

- **modelName**
  - `Counterparty`

- **calledMethod**
  - `getCounterpartyOptions`

- **Purpose**
  - Read capability flags and options for a counterparty.

- **Required parameters**
  - `Ref`

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common flags documented in older materials include `CanPayTheThirdPerson`, `CanAfterpaymentOnGoodsCost`, `CanNonCashPayment`, `CanCreditDocuments`, `HideDeliveryCost`, `CanSameDayDelivery`, `DeliveryByHand`, `DescentFromFloor`, `BackDeliveryValuablePapers`, `BackwardDeliverySubtypesDocuments`, `AfterpaymentType`, and `HaveMoneyWallets`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Counterparty","calledMethod":"getCounterpartyOptions","methodProperties":{"Ref":"<COUNTERPARTY_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_23_zavantazhiti_parametri_kontragenta_metod_getco.html

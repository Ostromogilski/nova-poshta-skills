# Address Operations

Use these methods to create, update, and delete saved counterparty addresses.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Refresh related counterparty-address lists immediately after every mutation.

## save

- **modelName**
  - `Address`

- **calledMethod**
  - `save`

- **Purpose**
  - Create a saved sender or recipient address.

- **Required parameters**
  - `CounterpartyRef`
  - `StreetRef`
  - `BuildingNumber`

- **Optional parameters**
  - `Flat`
  - `Note`

- **Response field summary**
  - Common fields include `Ref` and `Description` for the created address.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Address","calledMethod":"save","methodProperties":{"CounterpartyRef":"<COUNTERPARTY_REF>","StreetRef":"<STREET_REF>","BuildingNumber":"10","Flat":"5","Note":"Entrance 2"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_24_stvorennya_adresi_vdpravnikaotrimuvacha_metod_.html

## update

- **modelName**
  - `Address`

- **calledMethod**
  - `update`

- **Purpose**
  - Update an existing saved address.

- **Required parameters**
  - `Ref`
  - `CounterpartyRef`
  - In the accessible example: `StreetRef`, `BuildingNumber`, `Flat`, and `Note`

- **Optional parameters**
  - Only the fields you intend to change, subject to the official portal rules for your workflow.

- **Response field summary**
  - Expect a success envelope and the updated address details.

- **Verification note**
  - The legacy documentation says address editing is intended before shipment documents are created with that counterparty/address combination.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Address","calledMethod":"update","methodProperties":{"CounterpartyRef":"<COUNTERPARTY_REF>","Ref":"<ADDRESS_REF>","StreetRef":"<STREET_REF>","BuildingNumber":"45","Flat":"12","Note":"Updated note"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_25_onovlennyavidalennya_adresi_kontragenta_vdprav.html

## delete

- **modelName**
  - `Address`

- **calledMethod**
  - `delete`

- **Purpose**
  - Delete a saved address.

- **Required parameters**
  - `Ref`

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect a success envelope describing the deleted address, commonly including the deleted `Ref` and a human-readable description.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Address","calledMethod":"delete","methodProperties":{"Ref":"<ADDRESS_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_25_onovlennyavidalennya_adresi_kontragenta_vdprav.html

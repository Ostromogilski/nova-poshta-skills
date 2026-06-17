# Contact Person Operations

Use these methods to create, update, and delete counterparty contact persons.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Refresh contact-person lists immediately after every mutation.

## save

- **modelName**
  - `ContactPerson`

- **calledMethod**
  - `save`

- **Purpose**
  - Create a contact person linked to a counterparty.

- **Required parameters**
  - `CounterpartyRef`
  - `FirstName`
  - `LastName`
  - `MiddleName`
  - `Phone`

- **Optional parameters**
  - None verified in the accessible example.

- **Response field summary**
  - Common fields include `Ref`, `Description`, `LastName`, `FirstName`, `MiddleName`, `Phones`, and `Email`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"ContactPerson","calledMethod":"save","methodProperties":{"CounterpartyRef":"<COUNTERPARTY_REF>","FirstName":"Іван","LastName":"Іваненко","MiddleName":"Іванович","Phone":"380XXXXXXXXX"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_26_zberezhennya_danih_kontaktno_osobi_vdpravnikao.html

## update

- **modelName**
  - `ContactPerson`

- **calledMethod**
  - `update`

- **Purpose**
  - Update a counterparty contact person.

- **Required parameters**
  - `Ref`
  - `CounterpartyRef`
  - In the accessible example: `FirstName`, `LastName`, `MiddleName`, `Phone`

- **Optional parameters**
  - Only fields supported by your counterparty type and account rules.

- **Response field summary**
  - Expect a success envelope and the updated contact-person details.

- **Verification note**
  - Legacy notes commonly state broader editability for legal entities and more limited editability for private persons. Confirm the exact restriction in the official portal for your case.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"ContactPerson","calledMethod":"update","methodProperties":{"CounterpartyRef":"<COUNTERPARTY_REF>","Ref":"<CONTACT_REF>","FirstName":"Іван","LastName":"Іваненко","MiddleName":"Іванович","Phone":"380XXXXXXXXX"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_27_onovlennyaredaguvannya_danih_kontaktno_osobi_k.html

## delete

- **modelName**
  - `ContactPerson`

- **calledMethod**
  - `delete`

- **Purpose**
  - Delete a contact person.

- **Required parameters**
  - `Ref`

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect a success envelope describing the deleted contact person, commonly including the deleted `Ref`.

- **Verification note**
  - The accessible legacy note says deletion is available for legal entities. Verify your exact account rules in the official portal if this matters to your integration.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"ContactPerson","calledMethod":"delete","methodProperties":{"Ref":"<CONTACT_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_27_onovlennyaredaguvannya_danih_kontaktno_osobi_k.html

# Common Directories

Use `Common` methods to load stable shipment dictionaries that should usually be cached locally and refreshed monthly.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Cache locally and refresh monthly.

## getTypesOfPayers

- **modelName**
  - `Common`

- **calledMethod**
  - `getTypesOfPayers`

- **Purpose**
  - Load payer roles used in shipment and billing payloads.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect dictionary items with description and identifier fields. Common values include sender, recipient, and third-person payer roles.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Common","calledMethod":"getTypesOfPayers","methodProperties":{}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_7_otrimati_spisok_vidv_ta_form_platnikv.html

## getPaymentForm

- **modelName**
  - `Common`

- **calledMethod**
  - `getPaymentForm`

- **Purpose**
  - Load payment-form options such as cash and non-cash payment.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect dictionary items with description and identifier fields. The accessible legacy documentation describes cash and non-cash forms.

- **Verification note**
  - The accessible mirror uses `getPaymentForm` in request examples. Some third-party SDKs expose `getPaymentForms` as a wrapper method name. Keep the API payload on the documented singular `calledMethod` unless the live official portal for your account version says otherwise.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Common","calledMethod":"getPaymentForm","methodProperties":{}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_7_otrimati_spisok_vidv_ta_form_platnikv.html

## getCargoTypes

- **modelName**
  - `Common`

- **calledMethod**
  - `getCargoTypes`

- **Purpose**
  - Load cargo categories used when creating shipment documents.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect dictionary items with description and identifier fields. Common values in legacy examples include cargo, documents, tires/wheels, and pallets.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Common","calledMethod":"getCargoTypes","methodProperties":{}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_8_otrimati_spisok_tipv_vantazhu.html

## getServiceType

- **modelName**
  - `Common`

- **calledMethod**
  - `getServiceType`

- **Purpose**
  - Load delivery service combinations such as warehouse-to-warehouse and door-to-door.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect dictionary items with description and identifier fields. Common values include `WarehouseWarehouse`, `DoorsDoors`, `WarehouseDoors`, and `DoorsWarehouse`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"apiKey":"<API_KEY>","modelName":"Common","calledMethod":"getServiceType","methodProperties":{}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_9_otrimati_spisok_tehnologi_dostavki.html

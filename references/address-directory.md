# Address Directory

Use `Address` methods to resolve settlement, street, and warehouse references before creating or updating delivery data.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

## getCities

- **modelName**
  - `Address`

- **calledMethod**
  - `getCities`

- **Purpose**
  - Load settlements served by Nova Poshta and obtain city `Ref` values for later requests.

- **API key**
  - Not required in accessible examples.

- **Refresh / caching**
  - Cache locally and refresh daily.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - `FindByString` — settlement name fragment.

- **Response field summary**
  - Common fields include `Description`, `DescriptionRu`, `Ref`, `DeliveryCity`, and area/settlement metadata.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"modelName":"Address","calledMethod":"getCities","methodProperties":{"FindByString":"Київ"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://developers.novaposhta.ua/view/model/a0cf0f5f-8512-11ec-8ced-005056b2dbe1/method/a1e6f0a7-8512-11ec-8ced-005056b2dbe1?_lang=ua
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_3_zavantazhiti_dovdnik_mst_kompan_nova_poshta_met.html

## getStreet

- **modelName**
  - `Address`

- **calledMethod**
  - `getStreet`

- **Purpose**
  - Load streets within a settlement identified by `CityRef`.

- **API key**
  - Not required in accessible examples.

- **Refresh / caching**
  - Cache locally and refresh daily.

- **Required parameters**
  - `CityRef` — settlement reference returned by `getCities`.

- **Optional parameters**
  - `FindByString` — street name fragment.
  - `Page` — page number.

- **Response field summary**
  - Common fields include `Description`, `Ref`, `StreetsTypeRef`, and `StreetsType`.

- **Verification note**
  - The accessible mirror page is malformed and incorrectly shows `getCities` in some snippets, but current SDKs and wrappers consistently use `Address/getStreet` with `CityRef`, optional `FindByString`, and optional `Page`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"modelName":"Address","calledMethod":"getStreet","methodProperties":{"CityRef":"<CITY_REF>","FindByString":"Шевченка","Page":1}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://developers.novaposhta.ua/view/model/a0cf0f5f-8512-11ec-8ced-005056b2dbe1/method/a27c20d7-8512-11ec-8ced-005056b2dbe1
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_4_zavantazhiti_dovdnik_vulits_kompan_nova_poshta_.html

## getWarehouses

- **modelName**
  - `Address`

- **calledMethod**
  - `getWarehouses`

- **Purpose**
  - Load Nova Poshta branches and pickup points for a city.

- **API key**
  - Not required in accessible examples.

- **Refresh / caching**
  - Cache locally and refresh daily.

- **Required parameters**
  - `CityRef` — city reference in the accessible mirror example.

- **Optional parameters**
  - `WarehouseId` — warehouse number filter is used in current clients and integrations.

- **Response field summary**
  - Common fields include `Description`, `DescriptionRu`, `TypeOfWarehouse`, `Ref`, `Number`, `CityRef`, `CityDescription`, schedule fields, and capacity-related fields.

- **Verification note**
  - The accessible mirror page again contains a malformed JSON example that shows `getCities` instead of `getWarehouses`. The XML snippet and widespread client usage confirm `calledMethod: getWarehouses`.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"modelName":"Address","calledMethod":"getWarehouses","methodProperties":{"CityRef":"<CITY_REF>"}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_5_zavantazhiti_dovdnik_vddlen_kompan_nova_poshta_.html

## getWarehouseTypes

- **modelName**
  - `Address`

- **calledMethod**
  - `getWarehouseTypes`

- **Purpose**
  - Load warehouse type metadata used by some warehouse-filtering flows.

- **API key**
  - Not required in community client implementations.

- **Refresh / caching**
  - Cache locally and refresh daily or with other address-directory refreshes.

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified from directly accessible documentation during this review.

- **Response field summary**
  - Expect warehouse type identifiers and descriptions suitable for filtering warehouse records.

- **Verification note**
  - The official portal indexes this method, and multiple API clients call `Address/getWarehouseTypes`, but a directly accessible mirror page was not available during this review.

- **Sample request**
  - ```bash
    curl -X POST -H 'Content-Type: application/json' \
         -d '{"modelName":"Address","calledMethod":"getWarehouseTypes","methodProperties":{}}' \
         https://api.novaposhta.ua/v2.0/json/
    ```

- **Source URLs**
  - https://developers.novaposhta.ua/documentation

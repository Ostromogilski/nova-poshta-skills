# Extended Common Directories

These additional `Common` dictionaries are typically stable and can usually be cached locally with monthly refreshes.

Common endpoint:

https://api.novaposhta.ua/v2.0/json/

Primary documentation root:

https://developers.novaposhta.ua/documentation

Default guidance for this file:

- **API key**
  - Required.

- **Refresh / caching**
  - Cache locally and refresh monthly.

## getCargoDescriptionList

- **modelName**
  - `Common`

- **calledMethod**
  - `getCargoDescriptionList`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - `FindByString`

- **Response field summary**
  - Common fields include `Description` and `Ref`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_10_otrimati_spisok_opisu_vantazhu.html

## getOwnershipFormsList

- **modelName**
  - `Common`

- **calledMethod**
  - `getOwnershipFormsList`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description`, `FullName`, and `Ref`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_10_otrimati_spisok_form_vlasnost_metod_getownersh.html

## getBackwardDeliveryCargoTypes

- **modelName**
  - `Common`

- **calledMethod**
  - `getBackwardDeliveryCargoTypes`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description` and `Ref`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_12_otrimati_spisok_vidv_zvorotno_dostavki_metod_g.html

## getPalletsList

- **modelName**
  - `Common`

- **calledMethod**
  - `getPalletsList`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description`, `DescriptionRu`, `Weight`, and `Ref`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_13_otrimati_spisok_vidv_palet_metod_getpalletslis.html

## getTypesOfCounterparties

- **modelName**
  - `Common`

- **calledMethod**
  - `getTypesOfCounterparties`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description` and `Ref`. Common meanings are private person and organization types.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_14_otrimati_spisok_tipv_kontragentv_vdpravnikv_me.html

## getTypesOfPayersForRedelivery

- **modelName**
  - `Common`

- **calledMethod**
  - `getTypesOfPayersForRedelivery`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description` and `Ref`. Typical values in older materials are sender and recipient.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_15_otrimati_spisok_vidv_platnikv_zvorotno_dostavk.html

## getTimeIntervals

- **modelName**
  - `Common`

- **calledMethod**
  - `getTimeIntervals`

- **Required parameters**
  - `RecipientCityRef`
  - `DateTime` — legacy example uses `dd.MM.yyyy` format.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Number`, `Start`, and `End`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_16_otrimati_spisok_chasovih_ntervalv_metod_gettim.html

## getTiresWheelsList

- **modelName**
  - `Common`

- **calledMethod**
  - `getTiresWheelsList`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Common fields include `Description`, `DescriptionRu`, `Weight`, `DescriptionType`, and `Ref`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_17_otrimati_spisok_shin__diskv_metod_gettireswhee.html

## getTraysList

- **modelName**
  - `Common`

- **calledMethod**
  - `getTraysList`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - None verified.

- **Response field summary**
  - Expect tray-type identifiers and descriptions if the method is enabled for your account version.

- **Verification note**
  - This method is referenced by community clients and SDKs, but the accessible mirror page is missing and could not be validated directly during this review.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation

## getDocumentStatuses

- **modelName**
  - `Common`

- **calledMethod**
  - `getDocumentStatuses`

- **Required parameters**
  - None verified.

- **Optional parameters**
  - `StateId`
  - `StateName`
  - `GroupId`

- **Response field summary**
  - Common fields include `StateId`, `StateName`, and `GroupId`.

- **Source URLs**
  - https://developers.novaposhta.ua/documentation
  - https://alexpseha.gitbooks.io/api_test_one_chapter/content/1_19_otrimati_spisok_statusv_dokumentv_metod_getdoc.html

## Generic sample request

```bash
curl -X POST -H 'Content-Type: application/json' \
     -d '{"apiKey":"<API_KEY>","modelName":"Common","calledMethod":"<METHOD_NAME>","methodProperties":{}}' \
     https://api.novaposhta.ua/v2.0/json/
```

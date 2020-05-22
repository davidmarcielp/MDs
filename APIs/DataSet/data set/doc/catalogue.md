---
title: Sales & Post-Sales REST API v2.0.0
language_tabs:
  - java: Java
  - go: Go
  - javascript: JavaScript
language_clients:
  - java: ""
  - go: ""
  - javascript: ""
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2
version: 3.2.1

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="sales-and-post-sales-rest-api">Sales & Post-Sales REST API v2.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="/">/</a>

<h1 id="sales-and-post-sales-rest-api-catalogue">Catalogue</h1>

## get__catalogue_commercial_profiles

> Code samples

```java
URL obj = new URL("/catalogue/commercial_profiles");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_profiles", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_profiles',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_profiles`

*Get commercial profiles*

<h3 id="get__catalogue_commercial_profiles-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|service_provider_name|query|string|false|none|
|dealer_name|query|string|false|none|
|commercial_profile_type|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|commercial_profile_type|CONVERGENT|
|commercial_profile_type|MOBILE|

> Example responses

> 200 Response

```json
[
  {
    "id": 335,
    "type": "MOBILE",
    "name": "66_RESELLER_19",
    "description": "MM PAP 15/01/2020"
  }
]
```

<h3 id="get__catalogue_commercial_profiles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial profiles|Inline|

<h3 id="get__catalogue_commercial_profiles-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommercialProfile](#schemacommercialprofile)]|false|none|none|
|» id|string|false|none|none|
|» type|string|false|none|none|
|» name|string|false|none|none|
|» description|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products`

*Get commercial products*

<h3 id="get__catalogue_commercial_products-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|service_provider_name|query|string|false|none|
|commercial_profile_name|query|string|false|none|
|customer_segment_name|query|string|false|none|
|customer_type_name|query|string|false|none|
|subscription_type_name|query|string|false|none|
|billing_type_name|query|string|false|none|
|numeration_type_name|query|string|false|none|
|sale_type_name|query|string|false|none|
|channel_name|query|string|false|none|
|center_name|query|string|false|none|
|user_name|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|customer_segment_name|PARTICULAR|
|customer_segment_name|EMPRESA|
|customer_type_name|Nuevo|
|customer_type_name|Existente|
|subscription_type_name|PRE-PAGO|
|subscription_type_name|POST-PAGO|
|subscription_type_name|INTERNET FTTH|
|subscription_type_name|FIJO ANALOGICO|
|subscription_type_name|FIJO DIGITAL|
|subscription_type_name|INTERNET ADSL|
|billing_type_name|POSPAGO|
|billing_type_name|PREPAGO CLASICO|
|billing_type_name|PREPAGO AUTOMATICO|
|numeration_type_name|Nuevo numero|
|numeration_type_name|Numero portado|
|numeration_type_name|Numero entre marcas|
|sale_type_name|Venta|
|sale_type_name|Migración|
|sale_type_name|Añadir Línea|
|sale_type_name|Cartera|
|channel_name|NUEVA|
|channel_name|PORTABILIDAD|
|channel_name|CENTRO DE ATENCION AL CLIENTE|
|channel_name|MIGRACION CONTRATO|
|channel_name|REEMPLAZO|
|channel_name|YOSOYMAS|
|channel_name|PORTAL DE DISTRIBUICION|
|channel_name|CANAL ONLINE (AFILIADO)|
|channel_name|MARCA BLANCA (MAYORISTA)|
|channel_name|PORTABILIDAD MARCAS|
|channel_name|MIGRACION HAPPYMOVIL|

> Example responses

> 200 Response

```json
[
  {
    "id": 109,
    "name": "TARIFA CERO PREPAGO 50MIN+1GB",
    "marketing_name": "TARIFA CERO PREPAGO 50MIN+1GB",
    "commercial_info": [
      {
        "id": "109ES1",
        "commercial_description": "<strong>Tarifa CERO prepago 50 Min + 1 GB</strong>  <ul><li>Tarifa CERO Voz:0 cént/min los primeros 5 minutos de cada llamada, a partir del minuto 6:3,63 cts/min (IGIC:3.21 cts/min) .</li><li>Establecimiento:  18.15 cts (IGIC: 16.05 cts) SMS: 9,68 cts/sms (IGIC:8,56 cts/sms).</li><li>Bono voz incluido: 50 min llamadas nacionales. una vez superado, aplica tarifa cero. </li><li>Internet: 1024 MB incluidos + 100 MB en baja velocidad (16 KB); una vez superados: 3,63 cts/MB (IGIC:3,21 cts/MB).</li><li>Tarifa valida 30 dias desde su activación y autorenovable cada 30 dias si se dispone de saldo suficiente </li><li>Renovable de manera anticipada enviando SMS gratuito con texto MMRENUEVA a 2377</li><li>En caso de no renovación:llamadas nacionales: 12.10 cts/min + 18.15 establecimiento (IGIC:16.05cts) y consumo mínimo de 1,21 € mes (IGIC:1,07 €/mes) </li>  </ul>",
        "language": "ES"
      },
      {
        "id": "109EN1",
        "commercial_description": "<strong>Tarifa CERO prepago 50 Min + 1 GB</strong>  <ul><li> Zero rate: 0 cént/min the first 5 mins of every call, from the 6 min : 3,63 cts/min (IGIC:3.21 cts/min) .</li><li> Call set up fee: 18.15 cts (IGIC: 16.05 cts) SMS: 9,68 cts/sms (IGIC:8,56 cts/sms)</li><li> 60 min voice bundle included, valid for nationall calls. Once consumed Zero rate applies. </li><li> 1 GB (1024 MB) data bundle included. Once consumed 100 MB on speed lowering; and once ended 3,63 cts/MB (IGIC:3,21 cts/MB). </li><li> Plan valid for 30 days from activation and auto-renewable every 30 days if there´s enough balance available</li><li> Auto renewable sending a free sms to 2377 with the text mmrenewal</li><li> In case of no renovation: 12.10 cts/min + call set up:18,15 cts (IGIC: 16,05 cts) y minimum consumption of 1,21 €/month (IGIC:1,07/month) </li>  </ul>",
        "language": "EN"
      }
    ],
    "fee": [
      {
        "id": 1,
        "description": "TARIFA CERO cuotamensual",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval": 28,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "TARIFA CERO cuotamensual value euro",
            "value": 23.5,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "free_units_package": [
      {
        "id": 175,
        "name": "VOZ 50MIN TCPREPAGO",
        "marketing_name": "VOZ 50MIN TCPREPAGO",
        "unit_amount": 3000,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "VOZ",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 177,
        "name": "INTERNET 1GB TCPREPAGO",
        "marketing_name": "INTERNET 1GB TCPREPAGO",
        "unit_amount": 1073741824,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 178,
        "name": "BAJADA VELOCIDAD PREPAGO",
        "marketing_name": "BAJADA VELOCIDAD PREPAGO",
        "unit_amount": 104857600,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      }
    ],
    "promotion": []
  },
  {
    "id": 513,
    "name": "Tarifa Base Prepagament",
    "marketing_name": "Tarifa Base Prepagament",
    "commercial_info": [],
    "fee": [
      {
        "id": 3,
        "description": "Tarifa Base Prepagament conminimo",
        "type": "RecurringCharge",
        "subtype": "MinimumConsumption",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "Tarifa Base Prepagament conminimo value euro",
            "value": 1,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "free_units_package": [],
    "promotion": []
  },
  {
    "id": 341,
    "name": "TARIFA MAS 10GB",
    "marketing_name": "TARIFA MAS 10GB",
    "commercial_info": [
      {
        "id": "341ES1",
        "commercial_description": "<strong>Tarifa 0 y 8</strong><br/>Habla por 0 cts/minuto a clientes MÁSMÓVIL y por solo 8 cts/minuto al resto.<ul class='descrip_products'><li>Voz: 0cts/min durante los primeros 10 minutos de cada llamada a clientes MÁSMÓVIL (15cts/est llamada). 8 cts/min exceso y llamadas al resto de operadores (15cts/est llamada).</li><li>SMS: 8cts/sms.</li><li>Internet: 3cts/MB.</li><li>Consumo mínimo: 1eur/mes.</li><li>Precios con IVA: 18,15cts/est llamada, 9,68cts/min, 9,68cts/sms, 3,63cts/MB, 1,21eur/mes consumo mínimo.</li><li>Tarifas válidas para tráfico nacional, excluidos destinos especiales.</li></ul>",
        "language": "ES"
      },
      {
        "id": "341EN1",
        "commercial_description": "<p><strong>Tarifa 0 y 8 </strong><br/>Talk for 0eur with MÁSMÓVIL clients and  8 cts/min with rest.</br><ul class='descrip_products'><li>Call cost: 0 cts/min first 10 minutes of each call to MÁSMÓVIL clients and 8 cts/min to rest national operator, any hour. (Call set-up fee 15 cts).</li><li>SMS: 8 cts/SMS.</li><li>Internet: 3 cts/MB.</li><li>Available for all different payment methods: direct debit, automatic top-up and pay-as-you-go. </li><li>Minimum monthly consumption: 1 eur.</li><li>Excluding VAT. Rates valid for national traffic excluding special numbers. </li></ul>",
        "language": "EN"
      }
    ],
    "fee": [
      {
        "id": 1,
        "description": "TARIFA MAS 10GB cuotamensual",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "TARIFA MAS 10GB cuotamensual value euro",
            "value": 12.31405,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "free_units_package": [
      {
        "id": 444,
        "name": "BONO BAJADA GRATUITO",
        "marketing_name": "BONO BAJADA GRATUITO",
        "unit_amount": 2684354560,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "BoundToBillCycle",
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 469,
        "name": "INTERNET 10GB_TPILI",
        "marketing_name": "INTERNET 10GB_TPILI",
        "unit_amount": 10737418240,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "BoundToBillCycle",
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      }
    ],
    "promotion": [
      {
        "id": 174,
        "name": "MM_DTO 3EUR DURANTE 12 MESES",
        "marketing_name": "MM_DTO 3EUR DURANTE 12 MESES",
        "need_promotion_code": "false",
        "applicability_model": "FeeGeneration",
        "target_applicability_rule": "FeeSubtype",
        "fee_subtypes": "ServiceFee",
        "calculation_model": "Flat",
        "discount_type": "fixed",
        "value": [
          {
            "id": "MM_DTO 3EUR DURANTE 12 MESES value euro",
            "value": 2.479339,
            "currency": "euro"
          }
        ],
        "duration": 12,
        "keep_on_upgrade": "true",
        "keep_on_downgrade": "true",
        "is_mandatory": "true",
        "terms": [
          {
            "id": 11,
            "name": "12 MESES-29,75E",
            "type": "CommitmentContract",
            "commitment_duration": 12,
            "value": [
              {
                "id": "12 MESES-29,75E value euro",
                "value": 29.75,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false"
          }
        ]
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial products|Inline|

<h3 id="get__catalogue_commercial_products-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommercialProduct](#schemacommercialproduct)]|false|none|none|
|» id|string|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» commercial_info|[[CommercialInfo](#schemacommercialinfo)]|false|none|none|
|»» id|string|false|none|none|
|»» commercial_description|number|false|none|none|
|»» language|string|false|none|none|
|» fee|[[Fee](#schemafee)]|false|none|none|
|»» id|string|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|» free_units_package|[[FreeUnitsPackage](#schemafreeunitspackage)]|false|none|none|
|»» id|integer|false|none|none|
|»» name|string|false|none|none|
|»» marketing_name|string|false|none|none|
|»» unit_amount|integer|false|none|none|
|»» isRecurring_package|boolean|false|none|none|
|»» max_grants|integer|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval_type|string|false|none|none|
|»» recurrence_interval_value|integer|false|none|none|
|»» applicability_rule|string|false|none|none|
|»» applicability_priority|integer|false|none|none|
|»» package_type_name|string|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» is_mandatory_optional|boolean|false|none|none|
|»» is_mandatory_for_sale|boolean|false|none|none|
|»» fee|[[Fee](#schemafee)]|false|none|none|
|»» promotion|[[Promotion](#schemapromotion)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» marketing_name|string|false|none|none|
|»»» need_promotion_code|boolean|false|none|none|
|»»» applicability_model|string|false|none|none|
|»»» target_applicability_rule|string|false|none|none|
|»»» fee_subtypes|string|false|none|none|
|»»» calculation_model|string|false|none|none|
|»»» discount_type|string|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» duration|number|false|none|none|
|»»» keep_on_upgrade|boolean|false|none|none|
|»»» keep_on_downgrade|boolean|false|none|none|
|»»» is_mandatory|boolean|false|none|none|
|»»» terms|[[Terms](#schematerms)]|false|none|none|
|» promotion|[[Promotion](#schemapromotion)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|Daily|
|recurrence_interval_type|Monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}`

*Get basic commercial product definition by ID*

<h3 id="get__catalogue_commercial_products_{id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "id": 341,
  "name": "TARIFA MAS 10GB",
  "marketing_name": "TARIFA MAS 10GB",
  "in_catalog_since": "2019-11-20 00:00:00",
  "in_catalog_until": "2080-12-31 23:59:59",
  "mysim_commercial_product_id": "770",
  "billing_type": {
    "id": 1,
    "name": "POSPAGO",
    "description": "modalidad postpago"
  },
  "fee": [
    {
      "id": 1,
      "description": "TARIFA MAS 10GB cuotamensual",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": "false",
      "value": [
        {
          "id": "TARIFA MAS 10GB cuotamensual value euro",
          "value": 12.31405,
          "currency": "euro"
        }
      ],
      "from": "2019-11-20 00:00:00",
      "terms": []
    }
  ]
}
```

<h3 id="get__catalogue_commercial_products_{id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial product|[CommercialProductBasic](#schemacommercialproductbasic)|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_free_units_packages

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/free_units_packages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/free_units_packages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/free_units_packages',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/free_units_packages`

*Get free units packages related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_free_units_packages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 444,
    "name": "BONO BAJADA GRATUITO",
    "marketing_name": "BONO BAJADA GRATUITO",
    "in_catalog_since": "2019-11-20 00:00:00",
    "unit_amount": 2684354560,
    "is_recurring_package": "true",
    "max_grants": 0,
    "recurrence_scheme": "BoundToBillCycle",
    "applicability_priority": 1,
    "package_type_name": "DATOS",
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "true",
    "is_mandatory_optional": "false",
    "is_mandatory_for_sale": "false",
    "fee": [],
    "promotion": [],
    "base_profile": [
      {
        "id": 4442,
        "name": "BONO BAJADA GRATUITO JSC",
        "in_catalog_since": "2019-11-20 00:00:00",
        "network_id": "1",
        "network_provisioning_id": "BAJADA_VELOCIDAD_GRATUITA_2.5GB"
      },
      {
        "id": 4445,
        "name": "BONO BAJADA GRATUITO YOIGO",
        "in_catalog_since": "2019-11-20 00:00:00",
        "network_id": "2"
      }
    ]
  },
  {
    "id": 469,
    "name": "INTERNET 10GB_TPILI",
    "marketing_name": "INTERNET 10GB_TPILI",
    "in_catalog_since": "2019-11-20 00:00:00",
    "unit_amount": 10737418240,
    "is_recurring_package": "true",
    "max_grants": 0,
    "recurrence_scheme": "BoundToBillCycle",
    "applicability_priority": 1,
    "package_type_name": "DATOS",
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "true",
    "is_mandatory_optional": "false",
    "is_mandatory_for_sale": "false",
    "fee": [],
    "promotion": [],
    "base_profile": [
      {
        "id": 4442,
        "name": "INTERNET 10GB_TPILI JSC",
        "in_catalog_since": "2019-11-20 00:00:00",
        "network_id": "1",
        "network_provisioning_id": "INTERNET_TPILI_10GB"
      },
      {
        "id": 4445,
        "name": "INTERNET 10GB_TPILI YOIGO",
        "in_catalog_since": "2019-11-20 00:00:00",
        "network_id": "2"
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_free_units_packages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Free Units Package|Inline|

<h3 id="get__catalogue_commercial_products_{id}_free_units_packages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[FreeUnitsPackageDetail](#schemafreeunitspackagedetail)]|false|none|none|
|» id|integer|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» mysim_free_units_package_id|string|false|none|none|
|» unit_amount|integer|false|none|none|
|» isRecurring_package|boolean|false|none|none|
|» max_grants|integer|false|none|none|
|» recurrence_scheme|string|false|none|none|
|» recurrence_interval_type|string|false|none|none|
|» recurrence_interval_value|integer|false|none|none|
|» applicability_rule|string|false|none|none|
|» applicability_priority|integer|false|none|none|
|» package_type_name|string|false|none|none|
|» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» is_mandatory_optional|boolean|false|none|none|
|» is_mandatory_for_sale|boolean|false|none|none|
|» fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|»» id|string|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» promotion|[[PromotionDetail](#schemapromotiondetail)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» marketing_name|string|false|none|none|
|»» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» need_promotion_code|boolean|false|none|none|
|»» applicability_model|string|false|none|none|
|»» target_applicability_rule|string|false|none|none|
|»» fee_subtypes|string|false|none|none|
|»» calculation_model|string|false|none|none|
|»» discount_type|string|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»» duration|number|false|none|none|
|»» keep_on_upgrade|boolean|false|none|none|
|»» keep_on_downgrade|boolean|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|» base_profile|[[FreeUnitsPackageDetail_base_profile](#schemafreeunitspackagedetail_base_profile)]|false|none|none|
|»» id|integer|false|none|none|
|»» name|string|false|none|none|
|»» in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» network_id|string|false|none|none|
|»» network_provisioning_id|string|false|none|none|
|»» offer_id|string|false|none|none|
|»» charging_id|string|false|none|none|
|»» expire_with_tariff|boolean|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|daily|
|recurrence_interval_type|monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_promotions

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/promotions");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/promotions", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/promotions',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/promotions`

*Get promotions related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_promotions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 174,
    "name": "MM_DTO 3EUR DURANTE 12 MESES",
    "marketing_name": "MM_DTO 3EUR DURANTE 12 MESES",
    "in_catalog_since": "2019-11-20 00:00:00",
    "need_promotion_code": "false",
    "applicability_model": "FeeGeneration",
    "target_applicability_rule": "FeeSubtype",
    "fee_subtypes": "ServiceFee",
    "calculation_model": "Flat",
    "discount_type": "fixed",
    "value": [
      {
        "id": "MM_DTO 3EUR DURANTE 12 MESES value euro",
        "value": 2.479339,
        "currency": "euro"
      }
    ],
    "duration": 12,
    "keep_on_upgrade": "true",
    "keep_on_downgrade": "true",
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "true",
    "terms": [
      {
        "id": 11,
        "name": "12 MESES-29,75E",
        "type": "CommitmentContract",
        "commitment_duration": 12,
        "value": [
          {
            "id": "12 MESES-29,75E value euro",
            "value": 29.75,
            "currency": "euro"
          }
        ],
        "penalty_prorated": "false",
        "from": "2019-11-20 00:00:00"
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_promotions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Promotion|Inline|

<h3 id="get__catalogue_commercial_products_{id}_promotions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[PromotionDetail](#schemapromotiondetail)]|false|none|none|
|» id|string|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» need_promotion_code|boolean|false|none|none|
|» applicability_model|string|false|none|none|
|» target_applicability_rule|string|false|none|none|
|» fee_subtypes|string|false|none|none|
|» calculation_model|string|false|none|none|
|» discount_type|string|false|none|none|
|» value|[[Value](#schemavalue)]|false|none|none|
|»» id|string|false|none|none|
|»» value|number|false|none|none|
|»» currency|string|false|none|none|
|» duration|number|false|none|none|
|» keep_on_upgrade|boolean|false|none|none|
|» keep_on_downgrade|boolean|false|none|none|
|» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» type|string|false|none|none|
|»» commitment_duration|integer|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»» penalty_prorated|boolean|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_commercial_devices

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/commercial_devices");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/commercial_devices", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/commercial_devices',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/commercial_devices`

*Get commercial devices related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_commercial_devices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 579153,
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "false",
    "device": {
      "id": "P045A1SNC",
      "brand": "ALCATEL",
      "model": "ALCATEL 1S NEGRO",
      "name": "ALCATEL 1S NEGRO",
      "in_catalog_since": "2019-11-20 00:00:00",
      "description": "ALCATEL 1S NEGRO: 5,5”, LTE, ANDROID 9, OCTA-CORE (4X1,5GHZ+4X1,2GHZ), 3GB RAM + 32GB ROM, DUAL SIM, BATERÍA 3060MAH",
      "category": "handset",
      "colour": "NEGRO",
      "from": "2019-11-20 00:00:00"
    },
    "fee": [
      {
        "id": 1,
        "description": "579153 pagoupfront",
        "type": "UpfrontFee",
        "subtype": "UpfrontFee",
        "value": [
          {
            "id": "579153 pagoupfront value euro",
            "value": 0,
            "currency": "euro"
          }
        ],
        "from": "2019-11-20 00:00:00",
        "terms": [
          {
            "id": 55,
            "name": "24 MESES-75E",
            "type": "CommitmentContract",
            "commitment_duration": 24,
            "value": [
              {
                "id": "24 MESES-75E value euro",
                "value": 75,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false",
            "from": "2019-11-20 00:00:00"
          }
        ]
      }
    ]
  },
  {
    "id": 579148,
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "false",
    "device": {
      "id": "P075A39NC",
      "brand": "ZTE",
      "model": "ZTE BLADE A3 2019 NEGRO",
      "name": "ZTE BLADE A3 2019 NEGRO",
      "in_catalog_since": "2019-11-20 00:00:00",
      "description": "ZTE BLADE A3 NEGRO: 5”, LTE, ANDROID 9, QUAD CORE (1,5GHZ), 1GB RAM + 16GB ROM, DUAL SIM, BATERÍA 2000MAH",
      "category": "handset",
      "colour": "NEGRO",
      "from": "2019-11-20 00:00:00"
    },
    "fee": [
      {
        "id": 1,
        "description": "579148 pagoupfront",
        "type": "UpfrontFee",
        "subtype": "UpfrontFee",
        "value": [
          {
            "id": "579148 pagoupfront value euro",
            "value": 0,
            "currency": "euro"
          }
        ],
        "from": "2019-11-20 00:00:00",
        "terms": [
          {
            "id": 54,
            "name": "24 MESES-50E",
            "type": "CommitmentContract",
            "commitment_duration": 24,
            "value": [
              {
                "id": "24 MESES-50E value euro",
                "value": 50,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false",
            "from": "2019-11-20 00:00:00"
          }
        ]
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_commercial_devices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial Device|Inline|

<h3 id="get__catalogue_commercial_products_{id}_commercial_devices-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommercialDeviceDetail](#schemacommercialdevicedetail)]|false|none|none|
|» id|string|false|none|none|
|» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» device|[CommercialDeviceDetail_device](#schemacommercialdevicedetail_device)|false|none|none|
|»» id|string|false|none|none|
|»» brand|string|false|none|none|
|»» model|string|false|none|none|
|»» name|string|false|none|none|
|»» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» description|string|false|none|none|
|»» category|string|false|none|none|
|»» colour|string|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» fee|[[CommercialDeviceDetail_fee](#schemacommercialdevicedetail_fee)]|false|none|none|
|»» id|integer|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» installment_plan|[CommercialDeviceDetail_installment_plan](#schemacommercialdevicedetail_installment_plan)|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» duration|integer|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|»»» id|string|false|none|none|
|»»» description|string|false|none|none|
|»»» type|string|false|none|none|
|»»» subtype|string|false|none|none|
|»»» recurrence_scheme|string|false|none|none|
|»»» recurrence_interval|integer|false|none|none|
|»»» paid_in_advance|boolean|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|»»»» id|string|false|none|none|
|»»»» name|string|false|none|none|
|»»»» type|string|false|none|none|
|»»»» commitment_duration|integer|false|none|none|
|»»»» value|[[Value](#schemavalue)]|false|none|none|
|»»»» penalty_prorated|boolean|false|none|none|
|»»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|category|Handset|
|category|STB|
|category|VoiceBox|
|category|Tablet|
|category|Router|
|category|SmartTV|
|category|GameConsole|
|category|Others|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_rate_plan

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/rate_plan");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/rate_plan", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/rate_plan',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/rate_plan`

*Get rate plan related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_rate_plan-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "id": "TARIFA_MAS_BASE"
}
```

<h3 id="get__catalogue_commercial_products_{id}_rate_plan-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|RatePlan|[RatePlan](#schemarateplan)|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_base_profiles

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/base_profiles");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/base_profiles", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/base_profiles',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/base_profiles`

*Get base profiles related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_base_profiles-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 61,
    "name": "PERFIL MOVIL 4G",
    "in_catalog_since": "2019-11-20 00:00:00",
    "network_id": "1",
    "network_provisioning_id": "TARIFA_MAS_BASE",
    "service": [
      {
        "id": 1,
        "name": "VOZ",
        "description": "VOZ",
        "in_catalog_since": "2019-11-20 00:00:00",
        "from": "2019-11-20 00:00:00",
        "default_initial_status": "INSTALADO",
        "activate_on_network_provisioning": "true"
      },
      {
        "id": 2,
        "name": "BUZON VOZ",
        "description": "BUZON VOZ",
        "in_catalog_since": "2019-11-20 00:00:00",
        "from": "2019-11-20 00:00:00",
        "default_initial_status": "BLOQUEO TEMPORAL",
        "activate_on_network_provisioning": "false"
      }
    ]
  },
  {
    "id": 62,
    "name": "PERFIL MOVIL 4G",
    "in_catalog_since": "2019-11-20 00:00:00",
    "network_id": "2",
    "network_provisioning_id": "MM_INT_VC_10G",
    "service_class": "2900",
    "service": [
      {
        "id": 1,
        "name": "VOZ",
        "description": "VOZ",
        "in_catalog_since": "2019-11-20 00:00:00",
        "from": "2019-11-20 00:00:00",
        "default_initial_status": "INSTALADO",
        "activate_on_network_provisioning": "true"
      },
      {
        "id": 2,
        "name": "BUZON VOZ",
        "description": "BUZON VOZ",
        "in_catalog_since": "2019-11-20 00:00:00",
        "from": "2019-11-20 00:00:00",
        "default_initial_status": "BLOQUEO TEMPORAL",
        "activate_on_network_provisioning": "false"
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_base_profiles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Base Profile|Inline|

<h3 id="get__catalogue_commercial_products_{id}_base_profiles-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[BaseProfile](#schemabaseprofile)]|false|none|none|
|» id|integer|false|none|none|
|» name|string|false|none|none|
|» in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» network_id|string|false|none|none|
|» network_provisioning_id|string|false|none|none|
|» service_class|string|false|none|none|
|» offer_id|string|false|none|none|
|» charging_id|string|false|none|none|
|» manual_renewal|boolean|false|none|none|
|» service|[[BaseProfile_service](#schemabaseprofile_service)]|false|none|none|
|»» id|integer|false|none|none|
|»» name|string|false|none|none|
|»» description|string|false|none|none|
|»» in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» default_initial_status|string|false|none|none|
|»» activate_on_network_provisioning|boolean|false|none|none|
|»» language|string|false|none|none|
|»» speed|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_value_added_services

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/value_added_services");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/value_added_services", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/value_added_services',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/value_added_services`

*Get value added services related to a given commercial product*

<h3 id="get__catalogue_commercial_products_{id}_value_added_services-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 261,
    "marketing_name": "IP FIJA",
    "in_catalog_since": "2019-11-20 00:00:00",
    "from": "2019-11-20 00:00:00",
    "is_mandatory": "false",
    "max_cardinality": "1",
    "service": [
      {
        "id": 26,
        "name": "IP FIJA",
        "description": "IP FIJA",
        "in_catalog_since": "2019-11-20 00:00:00",
        "from": "2019-11-20 00:00:00",
        "default_initial_status": "PRE-ACTIVADO"
      }
    ],
    "fee": [
      {
        "id": 1000,
        "description": "26 cuotaservicio",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "26 cuotaservicio value euro",
            "value": 12,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "commercial_device": [],
    "promotion": []
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_value_added_services-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Value Added Service|Inline|

<h3 id="get__catalogue_commercial_products_{id}_value_added_services-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[ValueAddedServiceDetail](#schemavalueaddedservicedetail)]|false|none|none|
|» id|integer|false|none|none|
|» marketing_name|string|false|none|none|
|» in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» max_cardinality|integer|false|none|none|
|» service|[[ValueAddedServiceDetail_service](#schemavalueaddedservicedetail_service)]|false|none|none|
|»» id|integer|false|none|none|
|»» name|string|false|none|none|
|»» description|string|false|none|none|
|»» in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» default_initial_status|string|false|none|none|
|» fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|»» id|string|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|» promotion|[[PromotionDetail](#schemapromotiondetail)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» marketing_name|string|false|none|none|
|»» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»» need_promotion_code|boolean|false|none|none|
|»» applicability_model|string|false|none|none|
|»» target_applicability_rule|string|false|none|none|
|»» fee_subtypes|string|false|none|none|
|»» calculation_model|string|false|none|none|
|»» discount_type|string|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»» duration|number|false|none|none|
|»» keep_on_upgrade|boolean|false|none|none|
|»» keep_on_downgrade|boolean|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|
|» commercial_device|[[CommercialDeviceDetail](#schemacommercialdevicedetail)]|false|none|none|
|»» id|string|false|none|none|
|»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» device|[CommercialDeviceDetail_device](#schemacommercialdevicedetail_device)|false|none|none|
|»»» id|string|false|none|none|
|»»» brand|string|false|none|none|
|»»» model|string|false|none|none|
|»»» name|string|false|none|none|
|»»» in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|»»» description|string|false|none|none|
|»»» category|string|false|none|none|
|»»» colour|string|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» fee|[[CommercialDeviceDetail_fee](#schemacommercialdevicedetail_fee)]|false|none|none|
|»»» id|integer|false|none|none|
|»»» description|string|false|none|none|
|»»» type|string|false|none|none|
|»»» subtype|string|false|none|none|
|»»» recurrence_scheme|string|false|none|none|
|»»» recurrence_interval|integer|false|none|none|
|»»» paid_in_advance|boolean|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» terms|[[Terms](#schematerms)]|false|none|none|
|»»»» id|string|false|none|none|
|»»»» name|string|false|none|none|
|»»»» type|string|false|none|none|
|»»»» commitment_duration|integer|false|none|none|
|»»»» value|[[Value](#schemavalue)]|false|none|none|
|»»»» penalty_prorated|boolean|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»» installment_plan|[CommercialDeviceDetail_installment_plan](#schemacommercialdevicedetail_installment_plan)|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» duration|integer|false|none|none|
|»»» from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|»»» fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|»»» terms|[[TermsDetail](#schematermsdetail)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|
|category|Handset|
|category|STB|
|category|VoiceBox|
|category|Tablet|
|category|Router|
|category|SmartTV|
|category|GameConsole|
|category|Others|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_free_units_packages

> Code samples

```java
URL obj = new URL("/catalogue/free_units_packages");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/free_units_packages", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/free_units_packages',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/free_units_packages`

*Get free units packages*

<h3 id="get__catalogue_free_units_packages-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|commercial_product_id|query|string|false|none|
|sale_type_name|query|string|false|none|
|channel_name|query|string|false|none|
|center_name|query|string|false|none|
|user_name|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|sale_type_name|Venta|
|sale_type_name|Migración|
|sale_type_name|Añadir Línea|
|sale_type_name|Cartera|
|channel_name|NUEVA|
|channel_name|PORTABILIDAD|
|channel_name|CENTRO DE ATENCION AL CLIENTE|
|channel_name|MIGRACION CONTRATO|
|channel_name|REEMPLAZO|
|channel_name|YOSOYMAS|
|channel_name|PORTAL DE DISTRIBUICION|
|channel_name|CANAL ONLINE (AFILIADO)|
|channel_name|MARCA BLANCA (MAYORISTA)|
|channel_name|PORTABILIDAD MARCAS|
|channel_name|MIGRACION HAPPYMOVIL|

> Example responses

> 200 Response

```json
[
  {
    "id": 663,
    "name": "BONO 350 MINUTOS EXTRA 12 MESES",
    "marketing_name": "BONO 350 MINUTOS EXTRA 12 MESES",
    "unit_amount": 21000,
    "is_recurring_package": "true",
    "max_grants": 11,
    "recurrence_scheme": "BoundToBillCycle",
    "applicability_priority": 1,
    "package_type_name": "VOZ",
    "is_mandatory": "false",
    "is_mandatory_optional": "false",
    "is_mandatory_for_sale": "false",
    "fee": [
      {
        "id": 3,
        "description": "BONO 350 MINUTOS EXTRA 12 MESES cargo",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "BONO 350 MINUTOS EXTRA 12 MESES cargo value euro",
            "value": 10.991735,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "promotion": [
      {
        "id": 247,
        "name": "MM_PROMO_BONO 350 MIN EXTRA 12M",
        "marketing_name": "MM_PROMO_BONO 350 MIN EXTRA 12M",
        "needPromotion_code": "false",
        "applicability_model": "FeeGeneration",
        "targetApplicability_rule": "FeeSubtype",
        "fee_subtypes": "ServiceFee",
        "calculation_model": "Flat",
        "discount_type": "fixed",
        "value": [
          {
            "id": "MM_PROMO_BONO 350 MIN EXTRA 12M value euro",
            "value": 10.991735,
            "currency": "euro"
          }
        ],
        "duration": 11,
        "keep_on_upgrade": "true",
        "keep_on_downgrade": "true",
        "is_mandatory": "true",
        "terms": []
      }
    ]
  },
  {
    "id": 70,
    "name": "BONOPREPAGO5GB_AMPLIACION",
    "marketing_name": "BONOPREPAGO5GB_AMPLIACION",
    "unit_amount": 5368709120,
    "is_recurring_package": "false",
    "max_grants": 0,
    "applicability_priority": 1,
    "package_type_name": "DATOS",
    "is_mandatory": "false",
    "is_mandatory_optional": "false",
    "is_mandatory_for_sale": "false",
    "fee": [
      {
        "id": 3,
        "description": "BONOPREPAGO5GB_AMPLIACION cargo",
        "type": "OneTimeFee",
        "subtype": "ActivationFee",
        "value": [
          {
            "id": "BONOPREPAGO5GB_AMPLIACION cargo value euro",
            "value": 5,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "promotion": []
  },
  {
    "id": 70,
    "name": "VOZ 150MIN TCIPREPAGO",
    "marketing_name": "VOZ 150MIN TCIPREPAGO",
    "unit_amount": 9000,
    "is_recurring_package": "false",
    "max_grants": 0,
    "applicability_priority": 1,
    "package_type_name": "VOZ",
    "is_mandatory": "false",
    "is_mandatory_optional": "false",
    "is_mandatory_for_sale": "false",
    "fee": [
      {
        "id": 3,
        "description": "VOZ 150MIN TCIPREPAGO cargo",
        "type": "OneTimeFee",
        "subtype": "ActivationFee",
        "value": [
          {
            "id": "VOZ 150MIN TCIPREPAGO cargo value euro",
            "value": 5,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "promotion": []
  }
]
```

<h3 id="get__catalogue_free_units_packages-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Free units packages|Inline|

<h3 id="get__catalogue_free_units_packages-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[FreeUnitsPackage](#schemafreeunitspackage)]|false|none|none|
|» id|integer|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» unit_amount|integer|false|none|none|
|» isRecurring_package|boolean|false|none|none|
|» max_grants|integer|false|none|none|
|» recurrence_scheme|string|false|none|none|
|» recurrence_interval_type|string|false|none|none|
|» recurrence_interval_value|integer|false|none|none|
|» applicability_rule|string|false|none|none|
|» applicability_priority|integer|false|none|none|
|» package_type_name|string|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» is_mandatory_optional|boolean|false|none|none|
|» is_mandatory_for_sale|boolean|false|none|none|
|» fee|[[Fee](#schemafee)]|false|none|none|
|»» id|string|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|» promotion|[[Promotion](#schemapromotion)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» marketing_name|string|false|none|none|
|»» need_promotion_code|boolean|false|none|none|
|»» applicability_model|string|false|none|none|
|»» target_applicability_rule|string|false|none|none|
|»» fee_subtypes|string|false|none|none|
|»» calculation_model|string|false|none|none|
|»» discount_type|string|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»» duration|number|false|none|none|
|»» keep_on_upgrade|boolean|false|none|none|
|»» keep_on_downgrade|boolean|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|Daily|
|recurrence_interval_type|Monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_promotions

> Code samples

```java
URL obj = new URL("/catalogue/promotions");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/promotions", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/promotions',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/promotions`

*Get promotinos*

<h3 id="get__catalogue_promotions-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|commercial_product_id|query|string|false|none|
|sale_type_name|query|string|false|none|
|channel_name|query|string|false|none|
|customer_type_name|query|string|false|none|
|numeration_type_name|query|string|false|none|
|center_name|query|string|false|none|
|user_name|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|sale_type_name|Venta|
|sale_type_name|Migración|
|sale_type_name|Añadir Línea|
|sale_type_name|Cartera|
|channel_name|NUEVA|
|channel_name|PORTABILIDAD|
|channel_name|CENTRO DE ATENCION AL CLIENTE|
|channel_name|MIGRACION CONTRATO|
|channel_name|REEMPLAZO|
|channel_name|YOSOYMAS|
|channel_name|PORTAL DE DISTRIBUICION|
|channel_name|CANAL ONLINE (AFILIADO)|
|channel_name|MARCA BLANCA (MAYORISTA)|
|channel_name|PORTABILIDAD MARCAS|
|channel_name|MIGRACION HAPPYMOVIL|
|customer_type_name|Nuevo|
|customer_type_name|Existente|
|numeration_type_name|Nuevo numero|
|numeration_type_name|Numero portado|
|numeration_type_name|Numero entre marcas|

> Example responses

> 200 Response

```json
[
  {
    "id": 266,
    "name": "MM_8% DTO_COLECTIVOS",
    "marketing_name": "Descuento 8% para colectivos",
    "need_promotion_code": "true",
    "applicability_model": "FeeGeneration",
    "targe_applicability_rule": "FeeSubtype",
    "fee_subtypes": "ServiceFee",
    "calculation_model": "Flat",
    "discount_type": "percentage",
    "value": [
      {
        "id": "MM_8% DTO_COLECTIVOS value euro",
        "value": 8,
        "currency": "euro"
      }
    ],
    "duration": 0,
    "keep_on_upgrade": "true",
    "keep_on_downgrade": "true",
    "is_mandatory": "false",
    "terms": []
  },
  {
    "id": 315,
    "name": "MM_20%_DTO_MOVIL_36M",
    "marketing_name": "DTO 20% CUOTA DE MOVIL 36 MESES",
    "need_promotion_code": "false",
    "applicability_model": "FeeGeneration",
    "target_applicability_rule": "FeeSubtype",
    "fee_subtypes": "ServiceFee",
    "calculation_model": "Flat",
    "discount_type": "percentage",
    "value": [
      {
        "id": "MM_20%_DTO_MOVIL_36M value euro",
        "value": 20,
        "currency": "euro"
      }
    ],
    "duration": 0,
    "keep_on_upgrade": "true",
    "keep_on_downgrade": "true",
    "is_mandatory": "false",
    "terms": []
  }
]
```

<h3 id="get__catalogue_promotions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Promotions|Inline|

<h3 id="get__catalogue_promotions-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Promotion](#schemapromotion)]|false|none|none|
|» id|string|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» need_promotion_code|boolean|false|none|none|
|» applicability_model|string|false|none|none|
|» target_applicability_rule|string|false|none|none|
|» fee_subtypes|string|false|none|none|
|» calculation_model|string|false|none|none|
|» discount_type|string|false|none|none|
|» value|[[Value](#schemavalue)]|false|none|none|
|»» id|string|false|none|none|
|»» value|number|false|none|none|
|»» currency|string|false|none|none|
|» duration|number|false|none|none|
|» keep_on_upgrade|boolean|false|none|none|
|» keep_on_downgrade|boolean|false|none|none|
|» is_mandatory|boolean|false|none|none|
|» terms|[[Terms](#schematerms)]|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» type|string|false|none|none|
|»» commitment_duration|integer|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»» penalty_prorated|boolean|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_devices

> Code samples

```java
URL obj = new URL("/catalogue/commercial_devices");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_devices", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_devices',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_devices`

*Get commercial devices*

<h3 id="get__catalogue_commercial_devices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|commercial_product_id|query|string|false|none|
|sale_type_name|query|string|false|none|
|numeration_type_name|query|string|false|none|
|center_name|query|string|false|none|
|user_name|query|string|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|sale_type_name|Venta|
|sale_type_name|Migración|
|sale_type_name|Añadir Línea|
|sale_type_name|Cartera|
|numeration_type_name|Nuevo numero|
|numeration_type_name|Numero portado|
|numeration_type_name|Numero entre marcas|

> Example responses

> 200 Response

```json
[
  {
    "id": 579153,
    "device": {
      "id": "P045A1SNC",
      "brand": "ALCATEL",
      "model": "ALCATEL 1S NEGRO",
      "name": "ALCATEL 1S NEGRO",
      "description": "ALCATEL 1S NEGRO: 5,5”, LTE, ANDROID 9, OCTA-CORE (4X1,5GHZ+4X1,2GHZ), 3GB RAM + 32GB ROM, DUAL SIM, BATERÍA 3060MAH",
      "category": "handset",
      "colour": "NEGRO"
    },
    "fee": [
      {
        "id": 1,
        "description": "579153 pagoupfront",
        "type": "UpfrontFee",
        "subtype": "UpfrontFee",
        "value": [
          {
            "id": "579153 pagoupfront value euro",
            "value": 0,
            "currency": "euro"
          }
        ],
        "terms": [
          {
            "id": 55,
            "name": "24 MESES-75E",
            "type": "CommitmentContract",
            "commitment_duration": 24,
            "value": [
              {
                "id": "24 MESES-75E value euro",
                "value": 75,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false"
          }
        ]
      }
    ],
    "installment_plan": []
  },
  {
    "id": 579148,
    "device": {
      "id": "P075A39NC",
      "brand": "ZTE",
      "model": "ZTE BLADE A3 2019 NEGRO",
      "name": "ZTE BLADE A3 2019 NEGRO",
      "description": "ZTE BLADE A3 NEGRO: 5”, LTE, ANDROID 9, QUAD CORE (1,5GHZ), 1GB RAM + 16GB ROM, DUAL SIM, BATERÍA 2000MAH",
      "category": "handset",
      "colour": "NEGRO"
    },
    "fee": [
      {
        "id": 1,
        "description": "579148 pagoupfront",
        "type": "UpfrontFee",
        "subtype": "UpfrontFee",
        "value": [
          {
            "id": "579148 pagoupfront value euro",
            "value": 0,
            "currency": "euro"
          }
        ],
        "terms": [
          {
            "id": 54,
            "name": "24 MESES-50E",
            "type": "CommitmentContract",
            "commitment_duration": 24,
            "value": [
              {
                "id": "24 MESES-50E value euro",
                "value": 50,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false"
          }
        ]
      }
    ],
    "installment_plan": []
  }
]
```

<h3 id="get__catalogue_commercial_devices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial devices|Inline|

<h3 id="get__catalogue_commercial_devices-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommercialDevice](#schemacommercialdevice)]|false|none|none|
|» id|string|false|none|none|
|» device|[CommercialDevice_device](#schemacommercialdevice_device)|false|none|none|
|»» id|string|false|none|none|
|»» brand|string|false|none|none|
|»» model|string|false|none|none|
|»» name|string|false|none|none|
|»» description|string|false|none|none|
|»» category|string|false|none|none|
|»» colour|string|false|none|none|
|» fee|[[CommercialDevice_fee](#schemacommercialdevice_fee)]|false|none|none|
|»» id|integer|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|» installment_plan|[CommercialDevice_installment_plan](#schemacommercialdevice_installment_plan)|false|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» duration|integer|false|none|none|
|»» fee|[[Fee](#schemafee)]|false|none|none|
|»»» id|string|false|none|none|
|»»» description|string|false|none|none|
|»»» type|string|false|none|none|
|»»» subtype|string|false|none|none|
|»»» recurrence_scheme|string|false|none|none|
|»»» recurrence_interval|integer|false|none|none|
|»»» paid_in_advance|boolean|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» terms|[[Terms](#schematerms)]|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|category|Handset|
|category|STB|
|category|VoiceBox|
|category|Tablet|
|category|Router|
|category|SmartTV|
|category|GameConsole|
|category|Others|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|

<aside class="success">
This operation does not require authentication
</aside>

## get__catalogue_commercial_products_{id}_can-switch

> Code samples

```java
URL obj = new URL("/catalogue/commercial_products/{id}/can-switch");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/catalogue/commercial_products/{id}/can-switch", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/catalogue/commercial_products/{id}/can-switch',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /catalogue/commercial_products/{id}/can-switch`

*Get commercial products to which a given commercial product can be changed*

<h3 id="get__catalogue_commercial_products_{id}_can-switch-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|
|user_profile|query|string|false|none|
|center_name|query|string|false|none|
|user_name|query|string|false|none|

> Example responses

> 200 Response

```json
[
  {
    "id": 123,
    "name": "TARIFA CERO PREPAGO 50MIN+1GB",
    "marketing_name": "TARIFA CERO PREPAGO 50MIN+1GB",
    "fee": [
      {
        "id": 1,
        "description": "TARIFA CERO cuotamensual",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval": 28,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "TARIFA CERO cuotamensual value euro",
            "value": 23.5,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "free_units_package": [
      {
        "id": 175,
        "name": "VOZ 50MIN TCPREPAGO",
        "marketing_name": "VOZ 50MIN TCPREPAGO",
        "unit_amount": 3000,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "VOZ",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 177,
        "name": "INTERNET 1GB TCPREPAGO",
        "marketing_name": "INTERNET 1GB TCPREPAGO",
        "unit_amount": 1073741824,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 178,
        "name": "BAJADA VELOCIDAD PREPAGO",
        "marketing_name": "BAJADA VELOCIDAD PREPAGO",
        "unit_amount": 104857600,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "NonBoundToBillCycle",
        "recurrence_interval_type": "BoundToActivation",
        "recurrence_interval_value": 28,
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      }
    ],
    "promotion": []
  },
  {
    "id": 153,
    "name": "Tarifa Base Prepagament",
    "marketing_name": "Tarifa Base Prepagament",
    "fee": [
      {
        "id": 3,
        "description": "Tarifa Base Prepagament conminimo",
        "type": "RecurringCharge",
        "subtype": "MinimumConsumption",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "Tarifa Base Prepagament conminimo value euro",
            "value": 1,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "freeUnitsPackage": [],
    "promotion": []
  },
  {
    "id": 770,
    "name": "TARIFA MAS 10GB",
    "marketing_name": "TARIFA MAS 10GB",
    "fee": [
      {
        "id": 1,
        "description": "TARIFA MAS 10GB cuotamensual",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": "false",
        "value": [
          {
            "id": "TARIFA MAS 10GB cuotamensual value euro",
            "value": 12.31405,
            "currency": "euro"
          }
        ],
        "terms": []
      }
    ],
    "freeUnitsPackage": [
      {
        "id": 444,
        "name": "BONO BAJADA GRATUITO",
        "marketing_name": "BONO BAJADA GRATUITO",
        "unit_amount": 2684354560,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "BoundToBillCycle",
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      },
      {
        "id": 469,
        "name": "INTERNET 10GB_TPILI",
        "marketing_name": "INTERNET 10GB_TPILI",
        "unit_amount": 10737418240,
        "is_recurring_package": "true",
        "max_grants": 0,
        "recurrence_scheme": "BoundToBillCycle",
        "applicability_priority": 1,
        "package_type_name": "DATOS",
        "is_mandatory": "true",
        "is_mandatory_optional": "false",
        "is_mandatory_for_sale": "false",
        "fee": [],
        "promotion": []
      }
    ],
    "promotion": [
      {
        "id": 174,
        "name": "MM_DTO 3EUR DURANTE 12 MESES",
        "marketing_name": "MM_DTO 3EUR DURANTE 12 MESES",
        "need_promotion_code": "false",
        "applicability_model": "FeeGeneration",
        "target_applicability_rule": "FeeSubtype",
        "fee_subtypes": "ServiceFee",
        "calculation_model": "Flat",
        "discount_type": "fixed",
        "value": [
          {
            "id": "MM_DTO 3EUR DURANTE 12 MESES value euro",
            "value": 2.479339,
            "currency": "euro"
          }
        ],
        "duration": 12,
        "keep_on_upgrade": "true",
        "keep_on_downgrade": "true",
        "is_mandatory": "true",
        "terms": [
          {
            "id": 11,
            "name": "12 MESES-29,75E",
            "type": "CommitmentContract",
            "commitment_duration": 12,
            "value": [
              {
                "id": "12 MESES-29,75E value euro",
                "value": 29.75,
                "currency": "euro"
              }
            ],
            "penalty_prorated": "false"
          }
        ]
      }
    ]
  }
]
```

<h3 id="get__catalogue_commercial_products_{id}_can-switch-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Commercial products|Inline|

<h3 id="get__catalogue_commercial_products_{id}_can-switch-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CommercialProduct](#schemacommercialproduct)]|false|none|none|
|» id|string|false|none|none|
|» name|string|false|none|none|
|» marketing_name|string|false|none|none|
|» commercial_info|[[CommercialInfo](#schemacommercialinfo)]|false|none|none|
|»» id|string|false|none|none|
|»» commercial_description|number|false|none|none|
|»» language|string|false|none|none|
|» fee|[[Fee](#schemafee)]|false|none|none|
|»» id|string|false|none|none|
|»» description|string|false|none|none|
|»» type|string|false|none|none|
|»» subtype|string|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval|integer|false|none|none|
|»» paid_in_advance|boolean|false|none|none|
|»» value|[[Value](#schemavalue)]|false|none|none|
|»»» id|string|false|none|none|
|»»» value|number|false|none|none|
|»»» currency|string|false|none|none|
|»» terms|[[Terms](#schematerms)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» type|string|false|none|none|
|»»» commitment_duration|integer|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» penalty_prorated|boolean|false|none|none|
|» free_units_package|[[FreeUnitsPackage](#schemafreeunitspackage)]|false|none|none|
|»» id|integer|false|none|none|
|»» name|string|false|none|none|
|»» marketing_name|string|false|none|none|
|»» unit_amount|integer|false|none|none|
|»» isRecurring_package|boolean|false|none|none|
|»» max_grants|integer|false|none|none|
|»» recurrence_scheme|string|false|none|none|
|»» recurrence_interval_type|string|false|none|none|
|»» recurrence_interval_value|integer|false|none|none|
|»» applicability_rule|string|false|none|none|
|»» applicability_priority|integer|false|none|none|
|»» package_type_name|string|false|none|none|
|»» is_mandatory|boolean|false|none|none|
|»» is_mandatory_optional|boolean|false|none|none|
|»» is_mandatory_for_sale|boolean|false|none|none|
|»» fee|[[Fee](#schemafee)]|false|none|none|
|»» promotion|[[Promotion](#schemapromotion)]|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»»» marketing_name|string|false|none|none|
|»»» need_promotion_code|boolean|false|none|none|
|»»» applicability_model|string|false|none|none|
|»»» target_applicability_rule|string|false|none|none|
|»»» fee_subtypes|string|false|none|none|
|»»» calculation_model|string|false|none|none|
|»»» discount_type|string|false|none|none|
|»»» value|[[Value](#schemavalue)]|false|none|none|
|»»» duration|number|false|none|none|
|»»» keep_on_upgrade|boolean|false|none|none|
|»»» keep_on_downgrade|boolean|false|none|none|
|»»» is_mandatory|boolean|false|none|none|
|»»» terms|[[Terms](#schematerms)]|false|none|none|
|» promotion|[[Promotion](#schemapromotion)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|Daily|
|recurrence_interval_type|Monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_CommercialProfile">CommercialProfile</h2>
<!-- backwards compatibility -->
<a id="schemacommercialprofile"></a>
<a id="schema_CommercialProfile"></a>
<a id="tocScommercialprofile"></a>
<a id="tocscommercialprofile"></a>

```json
{
  "id": "string",
  "type": "string",
  "name": "string",
  "description": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|type|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|

<h2 id="tocS_CommercialDevice">CommercialDevice</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevice"></a>
<a id="schema_CommercialDevice"></a>
<a id="tocScommercialdevice"></a>
<a id="tocscommercialdevice"></a>

```json
{
  "id": "string",
  "device": {
    "id": "string",
    "brand": "string",
    "model": "string",
    "name": "string",
    "description": "string",
    "category": "Handset",
    "colour": "string"
  },
  "fee": [
    {
      "id": 0,
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ],
  "installment_plan": {
    "id": "string",
    "name": "string",
    "duration": 0,
    "fee": [
      {
        "id": "string",
        "description": "string",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": true,
        "value": [
          {
            "id": "string",
            "value": 0,
            "currency": "string"
          }
        ],
        "terms": [
          {
            "id": "string",
            "name": "string",
            "type": "PermanenceContract",
            "commitment_duration": 0,
            "value": [
              {
                "id": "string",
                "value": 0,
                "currency": "string"
              }
            ],
            "penalty_prorated": true
          }
        ]
      }
    ],
    "terms": [
      {
        "id": "string",
        "name": "string",
        "type": "PermanenceContract",
        "commitment_duration": 0,
        "value": [
          {
            "id": "string",
            "value": 0,
            "currency": "string"
          }
        ],
        "penalty_prorated": true
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|device|[CommercialDevice_device](#schemacommercialdevice_device)|false|none|none|
|fee|[[CommercialDevice_fee](#schemacommercialdevice_fee)]|false|none|none|
|installment_plan|[CommercialDevice_installment_plan](#schemacommercialdevice_installment_plan)|false|none|none|

<h2 id="tocS_Terms">Terms</h2>
<!-- backwards compatibility -->
<a id="schematerms"></a>
<a id="schema_Terms"></a>
<a id="tocSterms"></a>
<a id="tocsterms"></a>

```json
{
  "id": "string",
  "name": "string",
  "type": "PermanenceContract",
  "commitment_duration": 0,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "penalty_prorated": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|type|string|false|none|none|
|commitment_duration|integer|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|penalty_prorated|boolean|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<h2 id="tocS_Fee">Fee</h2>
<!-- backwards compatibility -->
<a id="schemafee"></a>
<a id="schema_Fee"></a>
<a id="tocSfee"></a>
<a id="tocsfee"></a>

```json
{
  "id": "string",
  "description": "string",
  "type": "RecurringCharge",
  "subtype": "ServiceFee",
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval": 0,
  "paid_in_advance": true,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|description|string|false|none|none|
|type|string|false|none|none|
|subtype|string|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval|integer|false|none|none|
|paid_in_advance|boolean|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|terms|[[Terms](#schematerms)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|

<h2 id="tocS_Promotion">Promotion</h2>
<!-- backwards compatibility -->
<a id="schemapromotion"></a>
<a id="schema_Promotion"></a>
<a id="tocSpromotion"></a>
<a id="tocspromotion"></a>

```json
{
  "id": "string",
  "name": "string",
  "marketing_name": "string",
  "need_promotion_code": true,
  "applicability_model": "FeeGeneration",
  "target_applicability_rule": "PreviousInvoiceTotalAmount",
  "fee_subtypes": "string",
  "calculation_model": "Flat",
  "discount_type": "Percentage",
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "duration": 0,
  "keep_on_upgrade": true,
  "keep_on_downgrade": true,
  "is_mandatory": true,
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|need_promotion_code|boolean|false|none|none|
|applicability_model|string|false|none|none|
|target_applicability_rule|string|false|none|none|
|fee_subtypes|string|false|none|none|
|calculation_model|string|false|none|none|
|discount_type|string|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|duration|number|false|none|none|
|keep_on_upgrade|boolean|false|none|none|
|keep_on_downgrade|boolean|false|none|none|
|is_mandatory|boolean|false|none|none|
|terms|[[Terms](#schematerms)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<h2 id="tocS_FreeUnitsPackage">FreeUnitsPackage</h2>
<!-- backwards compatibility -->
<a id="schemafreeunitspackage"></a>
<a id="schema_FreeUnitsPackage"></a>
<a id="tocSfreeunitspackage"></a>
<a id="tocsfreeunitspackage"></a>

```json
{
  "id": 0,
  "name": "string",
  "marketing_name": "string",
  "unit_amount": 0,
  "isRecurring_package": true,
  "max_grants": 0,
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval_type": "Weekly",
  "recurrence_interval_value": 0,
  "applicability_rule": "ByPackageType",
  "applicability_priority": 0,
  "package_type_name": "string",
  "is_mandatory": true,
  "is_mandatory_optional": true,
  "is_mandatory_for_sale": true,
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ],
  "promotion": [
    {
      "id": "string",
      "name": "string",
      "marketing_name": "string",
      "need_promotion_code": true,
      "applicability_model": "FeeGeneration",
      "target_applicability_rule": "PreviousInvoiceTotalAmount",
      "fee_subtypes": "string",
      "calculation_model": "Flat",
      "discount_type": "Percentage",
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "duration": 0,
      "keep_on_upgrade": true,
      "keep_on_downgrade": true,
      "is_mandatory": true,
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|unit_amount|integer|false|none|none|
|isRecurring_package|boolean|false|none|none|
|max_grants|integer|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval_type|string|false|none|none|
|recurrence_interval_value|integer|false|none|none|
|applicability_rule|string|false|none|none|
|applicability_priority|integer|false|none|none|
|package_type_name|string|false|none|none|
|is_mandatory|boolean|false|none|none|
|is_mandatory_optional|boolean|false|none|none|
|is_mandatory_for_sale|boolean|false|none|none|
|fee|[[Fee](#schemafee)]|false|none|none|
|promotion|[[Promotion](#schemapromotion)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|Daily|
|recurrence_interval_type|Monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|

<h2 id="tocS_CommercialProduct">CommercialProduct</h2>
<!-- backwards compatibility -->
<a id="schemacommercialproduct"></a>
<a id="schema_CommercialProduct"></a>
<a id="tocScommercialproduct"></a>
<a id="tocscommercialproduct"></a>

```json
{
  "id": "string",
  "name": "string",
  "marketing_name": "string",
  "commercial_info": [
    {
      "id": "string",
      "commercial_description": 0,
      "language": "string"
    }
  ],
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ],
  "free_units_package": [
    {
      "id": 0,
      "name": "string",
      "marketing_name": "string",
      "unit_amount": 0,
      "isRecurring_package": true,
      "max_grants": 0,
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval_type": "Weekly",
      "recurrence_interval_value": 0,
      "applicability_rule": "ByPackageType",
      "applicability_priority": 0,
      "package_type_name": "string",
      "is_mandatory": true,
      "is_mandatory_optional": true,
      "is_mandatory_for_sale": true,
      "fee": [
        {
          "id": "string",
          "description": "string",
          "type": "RecurringCharge",
          "subtype": "ServiceFee",
          "recurrence_scheme": "BoundToBillCycle",
          "recurrence_interval": 0,
          "paid_in_advance": true,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "terms": [
            {
              "id": "string",
              "name": "string",
              "type": "PermanenceContract",
              "commitment_duration": 0,
              "value": [
                {
                  "id": "string",
                  "value": 0,
                  "currency": "string"
                }
              ],
              "penalty_prorated": true
            }
          ]
        }
      ],
      "promotion": [
        {
          "id": "string",
          "name": "string",
          "marketing_name": "string",
          "need_promotion_code": true,
          "applicability_model": "FeeGeneration",
          "target_applicability_rule": "PreviousInvoiceTotalAmount",
          "fee_subtypes": "string",
          "calculation_model": "Flat",
          "discount_type": "Percentage",
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "duration": 0,
          "keep_on_upgrade": true,
          "keep_on_downgrade": true,
          "is_mandatory": true,
          "terms": [
            {
              "id": "string",
              "name": "string",
              "type": "PermanenceContract",
              "commitment_duration": 0,
              "value": [
                {
                  "id": "string",
                  "value": 0,
                  "currency": "string"
                }
              ],
              "penalty_prorated": true
            }
          ]
        }
      ]
    }
  ],
  "promotion": [
    {
      "id": "string",
      "name": "string",
      "marketing_name": "string",
      "need_promotion_code": true,
      "applicability_model": "FeeGeneration",
      "target_applicability_rule": "PreviousInvoiceTotalAmount",
      "fee_subtypes": "string",
      "calculation_model": "Flat",
      "discount_type": "Percentage",
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "duration": 0,
      "keep_on_upgrade": true,
      "keep_on_downgrade": true,
      "is_mandatory": true,
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|commercial_info|[[CommercialInfo](#schemacommercialinfo)]|false|none|none|
|fee|[[Fee](#schemafee)]|false|none|none|
|free_units_package|[[FreeUnitsPackage](#schemafreeunitspackage)]|false|none|none|
|promotion|[[Promotion](#schemapromotion)]|false|none|none|

<h2 id="tocS_Value">Value</h2>
<!-- backwards compatibility -->
<a id="schemavalue"></a>
<a id="schema_Value"></a>
<a id="tocSvalue"></a>
<a id="tocsvalue"></a>

```json
{
  "id": "string",
  "value": 0,
  "currency": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|value|number|false|none|none|
|currency|string|false|none|none|

<h2 id="tocS_CommercialInfo">CommercialInfo</h2>
<!-- backwards compatibility -->
<a id="schemacommercialinfo"></a>
<a id="schema_CommercialInfo"></a>
<a id="tocScommercialinfo"></a>
<a id="tocscommercialinfo"></a>

```json
{
  "id": "string",
  "commercial_description": 0,
  "language": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|commercial_description|number|false|none|none|
|language|string|false|none|none|

<h2 id="tocS_CommercialProductBasic">CommercialProductBasic</h2>
<!-- backwards compatibility -->
<a id="schemacommercialproductbasic"></a>
<a id="schema_CommercialProductBasic"></a>
<a id="tocScommercialproductbasic"></a>
<a id="tocscommercialproductbasic"></a>

```json
{
  "id": "string",
  "name": "string",
  "marketing_name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "mysim_commercial_product_id": "string",
  "billing_type": {
    "id": "string",
    "name": "string",
    "description": "string"
  },
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "from": "string",
      "to": "string",
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|mysim_commercial_product_id|string|false|none|none|
|billing_type|[CommercialProductBasic_billing_type](#schemacommercialproductbasic_billing_type)|false|none|none|
|fee|[[FeeDetail](#schemafeedetail)]|false|none|none|

<h2 id="tocS_FeeDetail">FeeDetail</h2>
<!-- backwards compatibility -->
<a id="schemafeedetail"></a>
<a id="schema_FeeDetail"></a>
<a id="tocSfeedetail"></a>
<a id="tocsfeedetail"></a>

```json
{
  "id": "string",
  "description": "string",
  "type": "RecurringCharge",
  "subtype": "ServiceFee",
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval": 0,
  "paid_in_advance": true,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "from": "string",
  "to": "string",
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true,
      "from": "string",
      "to": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|description|string|false|none|none|
|type|string|false|none|none|
|subtype|string|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval|integer|false|none|none|
|paid_in_advance|boolean|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|terms|[[TermsDetail](#schematermsdetail)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|

<h2 id="tocS_PromotionDetail">PromotionDetail</h2>
<!-- backwards compatibility -->
<a id="schemapromotiondetail"></a>
<a id="schema_PromotionDetail"></a>
<a id="tocSpromotiondetail"></a>
<a id="tocspromotiondetail"></a>

```json
{
  "id": "string",
  "name": "string",
  "marketing_name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "need_promotion_code": true,
  "applicability_model": "FeeGeneration",
  "target_applicability_rule": "PreviousInvoiceTotalAmount",
  "fee_subtypes": "string",
  "calculation_model": "Flat",
  "discount_type": "Percentage",
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "duration": 0,
  "keep_on_upgrade": true,
  "keep_on_downgrade": true,
  "from": "string",
  "to": "string",
  "is_mandatory": true,
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true,
      "from": "string",
      "to": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|need_promotion_code|boolean|false|none|none|
|applicability_model|string|false|none|none|
|target_applicability_rule|string|false|none|none|
|fee_subtypes|string|false|none|none|
|calculation_model|string|false|none|none|
|discount_type|string|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|duration|number|false|none|none|
|keep_on_upgrade|boolean|false|none|none|
|keep_on_downgrade|boolean|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|is_mandatory|boolean|false|none|none|
|terms|[[TermsDetail](#schematermsdetail)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|applicability_model|FeeGeneration|
|applicability_model|Billing|
|applicability_model|TopUp|
|target_applicability_rule|PreviousInvoiceTotalAmount|
|target_applicability_rule|CurrentInvoiceTotalAmount|
|target_applicability_rule|FeeSubtype|
|calculation_model|Flat|
|calculation_model|Bulk|
|discount_type|Percentage|
|discount_type|Fixed|

<h2 id="tocS_FreeUnitsPackageDetail">FreeUnitsPackageDetail</h2>
<!-- backwards compatibility -->
<a id="schemafreeunitspackagedetail"></a>
<a id="schema_FreeUnitsPackageDetail"></a>
<a id="tocSfreeunitspackagedetail"></a>
<a id="tocsfreeunitspackagedetail"></a>

```json
{
  "id": 0,
  "name": "string",
  "marketing_name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "mysim_free_units_package_id": "string",
  "unit_amount": 0,
  "isRecurring_package": true,
  "max_grants": 0,
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval_type": "Weekly",
  "recurrence_interval_value": 0,
  "applicability_rule": "ByPackageType",
  "applicability_priority": 0,
  "package_type_name": "string",
  "from": "string",
  "to": "string",
  "is_mandatory": true,
  "is_mandatory_optional": true,
  "is_mandatory_for_sale": true,
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "from": "string",
      "to": "string",
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ],
  "promotion": [
    {
      "id": "string",
      "name": "string",
      "marketing_name": "string",
      "in_catalog_since": "string",
      "in_catalog_until": "string",
      "need_promotion_code": true,
      "applicability_model": "FeeGeneration",
      "target_applicability_rule": "PreviousInvoiceTotalAmount",
      "fee_subtypes": "string",
      "calculation_model": "Flat",
      "discount_type": "Percentage",
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "duration": 0,
      "keep_on_upgrade": true,
      "keep_on_downgrade": true,
      "from": "string",
      "to": "string",
      "is_mandatory": true,
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ],
  "base_profile": [
    {
      "id": 0,
      "name": "string",
      "in_catalog_since": "string",
      "in_catalog_until": "string",
      "network_id": "string",
      "network_provisioning_id": "string",
      "offer_id": "string",
      "charging_id": "string",
      "expire_with_tariff": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|marketing_name|string|false|none|none|
|in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|mysim_free_units_package_id|string|false|none|none|
|unit_amount|integer|false|none|none|
|isRecurring_package|boolean|false|none|none|
|max_grants|integer|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval_type|string|false|none|none|
|recurrence_interval_value|integer|false|none|none|
|applicability_rule|string|false|none|none|
|applicability_priority|integer|false|none|none|
|package_type_name|string|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|is_mandatory|boolean|false|none|none|
|is_mandatory_optional|boolean|false|none|none|
|is_mandatory_for_sale|boolean|false|none|none|
|fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|promotion|[[PromotionDetail](#schemapromotiondetail)]|false|none|none|
|base_profile|[[FreeUnitsPackageDetail_base_profile](#schemafreeunitspackagedetail_base_profile)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|
|recurrence_interval_type|Weekly|
|recurrence_interval_type|daily|
|recurrence_interval_type|monthly|
|recurrence_interval_type|BoundToActivation|
|applicability_rule|ByPackageType|

<h2 id="tocS_TermsDetail">TermsDetail</h2>
<!-- backwards compatibility -->
<a id="schematermsdetail"></a>
<a id="schema_TermsDetail"></a>
<a id="tocStermsdetail"></a>
<a id="tocstermsdetail"></a>

```json
{
  "id": "string",
  "name": "string",
  "type": "PermanenceContract",
  "commitment_duration": 0,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "penalty_prorated": true,
  "from": "string",
  "to": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|type|string|false|none|none|
|commitment_duration|integer|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|penalty_prorated|boolean|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|PermanenceContract|
|type|ActivationCommitment|
|type|ReturnCommitment|

<h2 id="tocS_CommercialDeviceDetail">CommercialDeviceDetail</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevicedetail"></a>
<a id="schema_CommercialDeviceDetail"></a>
<a id="tocScommercialdevicedetail"></a>
<a id="tocscommercialdevicedetail"></a>

```json
{
  "id": "string",
  "from": "string",
  "to": "string",
  "is_mandatory": true,
  "device": {
    "id": "string",
    "brand": "string",
    "model": "string",
    "name": "string",
    "in_catalog_since": "string",
    "in_catalog_until": "string",
    "description": "string",
    "category": "Handset",
    "colour": "string",
    "from": "string",
    "to": "string"
  },
  "fee": [
    {
      "id": 0,
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ],
      "from": "string",
      "to": "string"
    }
  ],
  "installment_plan": {
    "id": "string",
    "name": "string",
    "duration": 0,
    "from": "string",
    "to": "string",
    "fee": [
      {
        "id": "string",
        "description": "string",
        "type": "RecurringCharge",
        "subtype": "ServiceFee",
        "recurrence_scheme": "BoundToBillCycle",
        "recurrence_interval": 0,
        "paid_in_advance": true,
        "value": [
          {
            "id": "string",
            "value": 0,
            "currency": "string"
          }
        ],
        "from": "string",
        "to": "string",
        "terms": [
          {
            "id": "string",
            "name": "string",
            "type": "PermanenceContract",
            "commitment_duration": 0,
            "value": [
              {
                "id": "string",
                "value": 0,
                "currency": "string"
              }
            ],
            "penalty_prorated": true,
            "from": "string",
            "to": "string"
          }
        ]
      }
    ],
    "terms": [
      {
        "id": "string",
        "name": "string",
        "type": "PermanenceContract",
        "commitment_duration": 0,
        "value": [
          {
            "id": "string",
            "value": 0,
            "currency": "string"
          }
        ],
        "penalty_prorated": true,
        "from": "string",
        "to": "string"
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|is_mandatory|boolean|false|none|none|
|device|[CommercialDeviceDetail_device](#schemacommercialdevicedetail_device)|false|none|none|
|fee|[[CommercialDeviceDetail_fee](#schemacommercialdevicedetail_fee)]|false|none|none|
|installment_plan|[CommercialDeviceDetail_installment_plan](#schemacommercialdevicedetail_installment_plan)|false|none|none|

<h2 id="tocS_RatePlan">RatePlan</h2>
<!-- backwards compatibility -->
<a id="schemarateplan"></a>
<a id="schema_RatePlan"></a>
<a id="tocSrateplan"></a>
<a id="tocsrateplan"></a>

```json
{
  "id": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|

<h2 id="tocS_BaseProfile">BaseProfile</h2>
<!-- backwards compatibility -->
<a id="schemabaseprofile"></a>
<a id="schema_BaseProfile"></a>
<a id="tocSbaseprofile"></a>
<a id="tocsbaseprofile"></a>

```json
{
  "id": 0,
  "name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "network_id": "string",
  "network_provisioning_id": "string",
  "service_class": "string",
  "offer_id": "string",
  "charging_id": "string",
  "manual_renewal": true,
  "service": [
    {
      "id": 0,
      "name": "string",
      "description": "string",
      "in_catalog_since": "string",
      "in_catalog_until": "string",
      "from": "string",
      "to": "string",
      "default_initial_status": "string",
      "activate_on_network_provisioning": true,
      "language": "string",
      "speed": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|network_id|string|false|none|none|
|network_provisioning_id|string|false|none|none|
|service_class|string|false|none|none|
|offer_id|string|false|none|none|
|charging_id|string|false|none|none|
|manual_renewal|boolean|false|none|none|
|service|[[BaseProfile_service](#schemabaseprofile_service)]|false|none|none|

<h2 id="tocS_ValueAddedServiceDetail">ValueAddedServiceDetail</h2>
<!-- backwards compatibility -->
<a id="schemavalueaddedservicedetail"></a>
<a id="schema_ValueAddedServiceDetail"></a>
<a id="tocSvalueaddedservicedetail"></a>
<a id="tocsvalueaddedservicedetail"></a>

```json
{
  "id": 0,
  "marketing_name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "from": "string",
  "to": "string",
  "is_mandatory": true,
  "max_cardinality": 0,
  "service": [
    {
      "id": 0,
      "name": "string",
      "description": "string",
      "in_catalog_since": "string",
      "in_catalog_until": "string",
      "from": "string",
      "to": "string",
      "default_initial_status": "string"
    }
  ],
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "from": "string",
      "to": "string",
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ],
  "promotion": [
    {
      "id": "string",
      "name": "string",
      "marketing_name": "string",
      "in_catalog_since": "string",
      "in_catalog_until": "string",
      "need_promotion_code": true,
      "applicability_model": "FeeGeneration",
      "target_applicability_rule": "PreviousInvoiceTotalAmount",
      "fee_subtypes": "string",
      "calculation_model": "Flat",
      "discount_type": "Percentage",
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "duration": 0,
      "keep_on_upgrade": true,
      "keep_on_downgrade": true,
      "from": "string",
      "to": "string",
      "is_mandatory": true,
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ],
  "commercial_device": [
    {
      "id": "string",
      "from": "string",
      "to": "string",
      "is_mandatory": true,
      "device": {
        "id": "string",
        "brand": "string",
        "model": "string",
        "name": "string",
        "in_catalog_since": "string",
        "in_catalog_until": "string",
        "description": "string",
        "category": "Handset",
        "colour": "string",
        "from": "string",
        "to": "string"
      },
      "fee": [
        {
          "id": 0,
          "description": "string",
          "type": "RecurringCharge",
          "subtype": "ServiceFee",
          "recurrence_scheme": "BoundToBillCycle",
          "recurrence_interval": 0,
          "paid_in_advance": true,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "terms": [
            {
              "id": "string",
              "name": "string",
              "type": "PermanenceContract",
              "commitment_duration": 0,
              "value": [
                {
                  "id": "string",
                  "value": 0,
                  "currency": "string"
                }
              ],
              "penalty_prorated": true
            }
          ],
          "from": "string",
          "to": "string"
        }
      ],
      "installment_plan": {
        "id": "string",
        "name": "string",
        "duration": 0,
        "from": "string",
        "to": "string",
        "fee": [
          {
            "id": "string",
            "description": "string",
            "type": "RecurringCharge",
            "subtype": "ServiceFee",
            "recurrence_scheme": "BoundToBillCycle",
            "recurrence_interval": 0,
            "paid_in_advance": true,
            "value": [
              {
                "id": "string",
                "value": 0,
                "currency": "string"
              }
            ],
            "from": "string",
            "to": "string",
            "terms": [
              {
                "id": "string",
                "name": "string",
                "type": "PermanenceContract",
                "commitment_duration": 0,
                "value": [
                  {
                    "id": "string",
                    "value": 0,
                    "currency": "string"
                  }
                ],
                "penalty_prorated": true,
                "from": "string",
                "to": "string"
              }
            ]
          }
        ],
        "terms": [
          {
            "id": "string",
            "name": "string",
            "type": "PermanenceContract",
            "commitment_duration": 0,
            "value": [
              {
                "id": "string",
                "value": 0,
                "currency": "string"
              }
            ],
            "penalty_prorated": true,
            "from": "string",
            "to": "string"
          }
        ]
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|marketing_name|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|is_mandatory|boolean|false|none|none|
|max_cardinality|integer|false|none|none|
|service|[[ValueAddedServiceDetail_service](#schemavalueaddedservicedetail_service)]|false|none|none|
|fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|promotion|[[PromotionDetail](#schemapromotiondetail)]|false|none|none|
|commercial_device|[[CommercialDeviceDetail](#schemacommercialdevicedetail)]|false|none|none|

<h2 id="tocS_CommercialDevice_device">CommercialDevice_device</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevice_device"></a>
<a id="schema_CommercialDevice_device"></a>
<a id="tocScommercialdevice_device"></a>
<a id="tocscommercialdevice_device"></a>

```json
{
  "id": "string",
  "brand": "string",
  "model": "string",
  "name": "string",
  "description": "string",
  "category": "Handset",
  "colour": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|brand|string|false|none|none|
|model|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|category|string|false|none|none|
|colour|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|category|Handset|
|category|STB|
|category|VoiceBox|
|category|Tablet|
|category|Router|
|category|SmartTV|
|category|GameConsole|
|category|Others|

<h2 id="tocS_CommercialDevice_fee">CommercialDevice_fee</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevice_fee"></a>
<a id="schema_CommercialDevice_fee"></a>
<a id="tocScommercialdevice_fee"></a>
<a id="tocscommercialdevice_fee"></a>

```json
{
  "id": 0,
  "description": "string",
  "type": "RecurringCharge",
  "subtype": "ServiceFee",
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval": 0,
  "paid_in_advance": true,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|description|string|false|none|none|
|type|string|false|none|none|
|subtype|string|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval|integer|false|none|none|
|paid_in_advance|boolean|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|terms|[[Terms](#schematerms)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|

<h2 id="tocS_CommercialDevice_installment_plan">CommercialDevice_installment_plan</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevice_installment_plan"></a>
<a id="schema_CommercialDevice_installment_plan"></a>
<a id="tocScommercialdevice_installment_plan"></a>
<a id="tocscommercialdevice_installment_plan"></a>

```json
{
  "id": "string",
  "name": "string",
  "duration": 0,
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true
        }
      ]
    }
  ],
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|duration|integer|false|none|none|
|fee|[[Fee](#schemafee)]|false|none|none|
|terms|[[Terms](#schematerms)]|false|none|none|

<h2 id="tocS_CommercialProductBasic_billing_type">CommercialProductBasic_billing_type</h2>
<!-- backwards compatibility -->
<a id="schemacommercialproductbasic_billing_type"></a>
<a id="schema_CommercialProductBasic_billing_type"></a>
<a id="tocScommercialproductbasic_billing_type"></a>
<a id="tocscommercialproductbasic_billing_type"></a>

```json
{
  "id": "string",
  "name": "string",
  "description": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|

<h2 id="tocS_FreeUnitsPackageDetail_base_profile">FreeUnitsPackageDetail_base_profile</h2>
<!-- backwards compatibility -->
<a id="schemafreeunitspackagedetail_base_profile"></a>
<a id="schema_FreeUnitsPackageDetail_base_profile"></a>
<a id="tocSfreeunitspackagedetail_base_profile"></a>
<a id="tocsfreeunitspackagedetail_base_profile"></a>

```json
{
  "id": 0,
  "name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "network_id": "string",
  "network_provisioning_id": "string",
  "offer_id": "string",
  "charging_id": "string",
  "expire_with_tariff": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|network_id|string|false|none|none|
|network_provisioning_id|string|false|none|none|
|offer_id|string|false|none|none|
|charging_id|string|false|none|none|
|expire_with_tariff|boolean|false|none|none|

<h2 id="tocS_CommercialDeviceDetail_device">CommercialDeviceDetail_device</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevicedetail_device"></a>
<a id="schema_CommercialDeviceDetail_device"></a>
<a id="tocScommercialdevicedetail_device"></a>
<a id="tocscommercialdevicedetail_device"></a>

```json
{
  "id": "string",
  "brand": "string",
  "model": "string",
  "name": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "description": "string",
  "category": "Handset",
  "colour": "string",
  "from": "string",
  "to": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|brand|string|false|none|none|
|model|string|false|none|none|
|name|string|false|none|none|
|in_catalog_since|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|description|string|false|none|none|
|category|string|false|none|none|
|colour|string|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|category|Handset|
|category|STB|
|category|VoiceBox|
|category|Tablet|
|category|Router|
|category|SmartTV|
|category|GameConsole|
|category|Others|

<h2 id="tocS_CommercialDeviceDetail_fee">CommercialDeviceDetail_fee</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevicedetail_fee"></a>
<a id="schema_CommercialDeviceDetail_fee"></a>
<a id="tocScommercialdevicedetail_fee"></a>
<a id="tocscommercialdevicedetail_fee"></a>

```json
{
  "id": 0,
  "description": "string",
  "type": "RecurringCharge",
  "subtype": "ServiceFee",
  "recurrence_scheme": "BoundToBillCycle",
  "recurrence_interval": 0,
  "paid_in_advance": true,
  "value": [
    {
      "id": "string",
      "value": 0,
      "currency": "string"
    }
  ],
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true
    }
  ],
  "from": "string",
  "to": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|description|string|false|none|none|
|type|string|false|none|none|
|subtype|string|false|none|none|
|recurrence_scheme|string|false|none|none|
|recurrence_interval|integer|false|none|none|
|paid_in_advance|boolean|false|none|none|
|value|[[Value](#schemavalue)]|false|none|none|
|terms|[[Terms](#schematerms)]|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|RecurringCharge|
|type|OneTimeFee|
|subtype|ServiceFee|
|subtype|MinimumConsumption|
|subtype|ActivationFee|
|subtype|InstallationFee|
|subtype|SuspensionServiceFee|
|subtype|DeliveryFee|
|subtype|UpfrontFee|
|subtype|InstallmentFee|
|recurrence_scheme|BoundToBillCycle|
|recurrence_scheme|NonBoundToBillCycle|

<h2 id="tocS_CommercialDeviceDetail_installment_plan">CommercialDeviceDetail_installment_plan</h2>
<!-- backwards compatibility -->
<a id="schemacommercialdevicedetail_installment_plan"></a>
<a id="schema_CommercialDeviceDetail_installment_plan"></a>
<a id="tocScommercialdevicedetail_installment_plan"></a>
<a id="tocscommercialdevicedetail_installment_plan"></a>

```json
{
  "id": "string",
  "name": "string",
  "duration": 0,
  "from": "string",
  "to": "string",
  "fee": [
    {
      "id": "string",
      "description": "string",
      "type": "RecurringCharge",
      "subtype": "ServiceFee",
      "recurrence_scheme": "BoundToBillCycle",
      "recurrence_interval": 0,
      "paid_in_advance": true,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "from": "string",
      "to": "string",
      "terms": [
        {
          "id": "string",
          "name": "string",
          "type": "PermanenceContract",
          "commitment_duration": 0,
          "value": [
            {
              "id": "string",
              "value": 0,
              "currency": "string"
            }
          ],
          "penalty_prorated": true,
          "from": "string",
          "to": "string"
        }
      ]
    }
  ],
  "terms": [
    {
      "id": "string",
      "name": "string",
      "type": "PermanenceContract",
      "commitment_duration": 0,
      "value": [
        {
          "id": "string",
          "value": 0,
          "currency": "string"
        }
      ],
      "penalty_prorated": true,
      "from": "string",
      "to": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|duration|integer|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|fee|[[FeeDetail](#schemafeedetail)]|false|none|none|
|terms|[[TermsDetail](#schematermsdetail)]|false|none|none|

<h2 id="tocS_BaseProfile_service">BaseProfile_service</h2>
<!-- backwards compatibility -->
<a id="schemabaseprofile_service"></a>
<a id="schema_BaseProfile_service"></a>
<a id="tocSbaseprofile_service"></a>
<a id="tocsbaseprofile_service"></a>

```json
{
  "id": 0,
  "name": "string",
  "description": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "from": "string",
  "to": "string",
  "default_initial_status": "string",
  "activate_on_network_provisioning": true,
  "language": "string",
  "speed": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|default_initial_status|string|false|none|none|
|activate_on_network_provisioning|boolean|false|none|none|
|language|string|false|none|none|
|speed|integer|false|none|none|

<h2 id="tocS_ValueAddedServiceDetail_service">ValueAddedServiceDetail_service</h2>
<!-- backwards compatibility -->
<a id="schemavalueaddedservicedetail_service"></a>
<a id="schema_ValueAddedServiceDetail_service"></a>
<a id="tocSvalueaddedservicedetail_service"></a>
<a id="tocsvalueaddedservicedetail_service"></a>

```json
{
  "id": 0,
  "name": "string",
  "description": "string",
  "in_catalog_since": "string",
  "in_catalog_until": "string",
  "from": "string",
  "to": "string",
  "default_initial_status": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|in_catalog_since|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|in_catalog_until|string(yyyy-MM-dd HH:mm:ss)|false|none|none|
|from|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|to|string(YYYY-MM-dd HH:mm:ss)|false|none|none|
|default_initial_status|string|false|none|none|


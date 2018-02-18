---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - php
  - shell
  - python
  - javascript
  - ruby

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Dokan 2.8+ is fully integrated with the WordPress REST API. This allows to manupulate vendor data using requests in JSON format and using WordPress REST API Authentication methods and standard HTTP verbs which are understood by most HTTP clients.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Products

## Product Properties

Parameter | Type | Description
--------- | ------- | -----------
id |  integer | Unique identifier for the resource. `READ-ONLY`
name |  string |  Product name `Required` - Only Create.
slug |  string |  Product slug.
permalink | string |  Product URL. `READ-ONLY`
date_created |  date |-time The date the product was created, in the site’s timezone. `READ-ONLY`
date_created_gmt |  date |-time The date the product was created, as GMT. `READ-ONLY`
date_modified | date |-time The date the product was last modified, in the site’s timezone. `READ-ONLY`
date_modified_gmt | date |-time The date the product was last modified, as GMT. `READ-ONLY`
type |  string |  Product type. Options: simple, grouped, external and variable. Default is simple.
status |  string |  Product status (post status). Options: draft, pending, publish. It depends on vendor publishing admin settings
featured |  boolean | Featured product. Default is false.
catalog_visibility |  string |  Catalog visibility. Options: visible, catalog, search and hidden. Default is visible.
description | string |  Product description.
short_description | string |  Product short description.
sku | string |  Unique identifier.
price | string |  Current product price. `READ-ONLY`
regular_price | string |  Product regular price.
sale_price |  string |  Product sale price.
date_on_sale_from | date |-time Start date of sale price, in the site’s timezone.
date_on_sale_from_gmt | date |-time Start date of sale price, as GMT.
date_on_sale_to | date |-time End date of sale price, in the site’s timezone.
date_on_sale_to_gmt | date |-time End date of sale price, as GMT.
price_html |  string |  Price formatted in HTML. `READ-ONLY`
on_sale | boolean | Shows if the product is on sale. `READ-ONLY`
purchasable | boolean | Shows if the product can be bought. `READ-ONLY`
total_sales | integer | Amount of sales. `READ-ONLY`
virtual | boolean | If the product is virtual. Default is false.
downloadable |  boolean | If the product is downloadable. Default is false.
downloads | array | List of downloadable files. See Product - Downloads properties
download_limit |  integer | Number of times downloadable files can be downloaded after purchase. Default is -1.
download_expiry | integer | Number of days until access to downloadable files expires. Default is -1.
external_url |  string |  Product external URL. Only for external products.
button_text | string |  Product external button text. Only for external products.
tax_status |  string |  Tax status. Options: taxable, shipping and none. Default is taxable.
tax_class | string |  Tax class.
manage_stock |  boolean | Stock management at product level. Default is false.
stock_quantity |  integer | Stock quantity.
in_stock |  boolean | Controls whether or not the product is listed as “in stock” or “out of stock” on the frontend. Default is true.
backorders |  string |  If managing stock, this controls if backorders are allowed. Options: no, notify and yes. Default is no.
backorders_allowed |  boolean | Shows if backorders are allowed. `READ-ONLY`
backordered | boolean | Shows if the product is on backordered. `READ-ONLY`
sold_individually | boolean | Allow one item to be bought in a single order. Default is false.
weight |  string |  Product weight.
dimensions |  object |  Product dimensions. See Product - Dimensions properties
shipping_required | boolean | Shows if the product need to be shipped. `READ-ONLY`
shipping_taxable |  boolean | Shows whether or not the product shipping is taxable. `READ-ONLY`
shipping_class |  string |  Shipping class slug.
shipping_class_id | string |  Shipping class ID. `READ-ONLY`
reviews_allowed | boolean | Allow reviews. Default is true.
average_rating |  string |  Reviews average rating. `READ-ONLY`
rating_count |  integer | Amount of reviews that the product have. `READ-ONLY`
related_ids | array | List of related products IDs. `READ-ONLY`
upsell_ids |  array | List of up-sell products IDs.
cross_sell_ids |  array | List of cross-sell products IDs.
parent_id | integer | Product parent ID.
purchase_note | string |  Optional note to send the customer after purchase.
categories |  array | List of categories. See Product - Categories properties `Required` - Only create
tags |  array | List of tags. See Product - Tags properties
attributes |  array | List of attributes. See Product - Attributes properties
default_attributes |  array | Defaults variation attributes. See Product - Default attributes properties
variations |  array | List of variations IDs. `READ-ONLY`
grouped_products |  array | List of grouped products ID.
menu_order |  integer | Menu order, used to custom sort products.
meta_data | array | Meta data. See Product - Meta data properties

### Product - Downloads properties
Attribute | Type | Description
--------- | ------- | -----------
id | string | File MD5 hash. `READ-ONLY`
name | string | File name.
file | string | File URL.

### Product - Dimensions properties
Attribute | Type | Description
--------- | ------- | -----------
length | string | Product length.
width | string | Product width.
height | string | Product height.

### Product - Categories properties
Attribute | Type | Description
--------- | ------- | -----------
id | integer | Category ID.
name | string | Category name. `READ-ONLY`
slug | string | Category slug. `READ-ONLY`

### Product - Tags properties
Attribute | Type | Description
--------- | ------- | -----------
id | integer | Tag ID.
name | string | Tag name. `READ-ONLY`
slug | string | Tag slug. `READ-ONLY`

### Product - Images properties
Attribute | Type | Description
--------- | ------- | -----------
id |  integer | Image ID.
date_created |  date-time | The date the image was created, in the site’s timezone. `READ-ONLY`
date_created_gmt |  date-time | The date the image was created, as GMT. `READ-ONLY`
date_modified | date-time | The date the image was last modified, in the site’s timezone. `READ-ONLY`
date_modified_gmt | date-time | The date the image was last modified, as GMT. `READ-ONLY`
src | string | Image URL.
name |  string | Image name.
alt | string | Image alternative text.
position |  integer | Image position. 0 means that the image is featured.

### Product - Attributes properties
Attribute | Type | Description
--------- | ------- | -----------
id |  integer | Attribute ID.
name |  string |  Attribute name.
position |  integer | Attribute position.
visible | boolean | Define if the attribute is visible on the “Additional information” tab in the product’s page. Default is false.
variation | boolean | Define if the attribute can be used as variation. Default is false.
options | array | List of available term names of the attribute.

### Product - Default attributes properties
Attribute | Type | Description
--------- | ------- | -----------
id | integer | Attribute ID.
name | string |  Attribute name.
option | string | Selected attribute term name.

### Product - Meta data properties
Attribute | Type | Description
--------- | ------- | -----------
id |  integer | Meta ID. `READ-ONLY`
key | string |  Meta key.
value | string |  Meta value.

## Get All Products

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "http://dokannew.test/wp-json/dokan/v1/products/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Basic authorization_key",
    "Cache-Control: no-cache",
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

```shell
curl -X GET \
  http://dokannew.test/wp-json/dokan/v1/products/ \
  -H 'Authorization: Basic authorization_key' \
  -H 'Cache-Control: no-cache'
```

```python
import http.client

conn = http.client.HTTPConnection("dokannew,test")

headers = {
    'Authorization': "Basic authorization_key",
    'Cache-Control': "no-cache",
  }

conn.request("GET", "wp-json,dokan,v1,products,", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://dokannew.test/wp-json/dokan/v1/products/",
  "method": "GET",
  "headers": {
    "Authorization": "Basic authorization_key",
    "Cache-Control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

```ruby
require 'uri'
require 'net/http'

url = URI("http://dokannew.test/wp-json/dokan/v1/products/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'Basic authorization_key'
request["Cache-Control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 592,
    "name": "Lenevo G7",
    "slug": "",
    "post_author": "31",
    "permalink": "http://dokannew.test/?post_type=product&p=592",
    "date_created": null,
    "date_created_gmt": null,
    "date_modified": null,
    "date_modified_gmt": null,
    "type": "simple",
    "status": "pending",
    "featured": false,
    "catalog_visibility": "visible",
    "description": "",
    "short_description": "<p>lenevo is splash, water, and dust resistant and was tested under controlled laboratory conditions with a rating of IP67 under IEC standard 60529. Splash, water, and dust resistance are not permanent conditions and resistance might decrease as a result of normal wear.</p>",
    "sku": "",
    "price": "449",
    "regular_price": "449",
    "sale_price": "",
    "date_on_sale_from": null,
    "date_on_sale_from_gmt": null,
    "date_on_sale_to": null,
    "date_on_sale_to_gmt": null,
    "price_html": "<span class=\"woocommerce-Price-amount amount\"><span class=\"woocommerce-Price-currencySymbol\">&#36;</span>449.00</span>",
    "on_sale": false,
    "purchasable": true,
    "total_sales": 0,
    "virtual": false,
    "downloadable": false,
    "downloads": [],
    "download_limit": -1,
    "download_expiry": -1,
    "external_url": "",
    "button_text": "",
    "tax_status": "taxable",
    "tax_class": "",
    "manage_stock": false,
    "stock_quantity": null,
    "in_stock": true,
    "backorders": "",
    "backorders_allowed": false,
    "backordered": false,
    "sold_individually": false,
    "weight": "",
    "dimensions": {
      "length": "",
      "width": "",
      "height": ""
    },
    "shipping_required": true,
    "shipping_taxable": true,
    "shipping_class": "",
    "shipping_class_id": 0,
    "reviews_allowed": true,
    "average_rating": "0.00",
    "rating_count": 0,
    "related_ids": [
      589,
      572
    ],
    "upsell_ids": [],
    "cross_sell_ids": [],
    "parent_id": 0,
    "purchase_note": "",
    "categories": [
      {
        "id": 16,
        "name": "Music",
        "slug": "jw-music"
      }
    ],
    "tags": [],
    "images": [
      {
        "id": 0,
        "date_created": "2018-02-15T10:04:46",
        "date_created_gmt": "2018-02-15T04:04:46",
        "date_modified": "2018-02-15T10:04:46",
        "date_modified_gmt": "2018-02-15T04:04:46",
        "src": "http://dokannew.test/wp-content/plugins/woocommerce/assets/images/placeholder.png",
        "name": "Placeholder",
        "alt": "Placeholder",
        "position": 0
      }
    ],
    "attributes": [],
    "default_attributes": [],
    "variations": [],
    "grouped_products": [],
    "menu_order": 0,
    "meta_data": []
  },
  {
    "id": 591,
    "name": "iPhone x",
    "slug": "",
    "post_author": "31",
    "permalink": "http://dokannew.test/?post_type=product&p=591",
    "date_created": null,
    "date_created_gmt": null,
    "date_modified": null,
    "date_modified_gmt": null,
    "type": "simple",
    "status": "pending",
    "featured": false,
    "catalog_visibility": "visible",
    "description": "",
    "short_description": "<p>iPhone X is splash, water, and dust resistant and was tested under controlled laboratory conditions with a rating of IP67 under IEC standard 60529. Splash, water, and dust resistance are not permanent conditions and resistance might decrease as a result of normal wear. Do not attempt to charge a wet iPhone; refer to the user guide for cleaning and drying instructions. Liquid damage not covered under warranty.</p>\n",
    "sku": "",
    "price": "999",
    "regular_price": "999",
    "sale_price": "",
    "date_on_sale_from": null,
    "date_on_sale_from_gmt": null,
    "date_on_sale_to": null,
    "date_on_sale_to_gmt": null,
    "price_html": "<span class=\"woocommerce-Price-amount amount\"><span class=\"woocommerce-Price-currencySymbol\">&#36;</span>999.00</span>",
    "on_sale": false,
    "purchasable": true,
    "total_sales": 0,
    "virtual": false,
    "downloadable": false,
    "downloads": [],
    "download_limit": -1,
    "download_expiry": -1,
    "external_url": "",
    "button_text": "",
    "tax_status": "taxable",
    "tax_class": "",
    "manage_stock": false,
    "stock_quantity": null,
    "in_stock": true,
    "backorders": "",
    "backorders_allowed": false,
    "backordered": false,
    "sold_individually": false,
    "weight": "",
    "dimensions": {
      "length": "",
      "width": "",
      "height": ""
    },
    "shipping_required": true,
    "shipping_taxable": true,
    "shipping_class": "",
    "shipping_class_id": 0,
    "reviews_allowed": true,
    "average_rating": "0.00",
    "rating_count": 0,
    "related_ids": [],
    "upsell_ids": [],
    "cross_sell_ids": [],
    "parent_id": 0,
    "purchase_note": "",
    "categories": [
      {
        "id": 48,
        "name": "Mobile",
        "slug": "mobile"
      }
    ],
    "tags": [],
    "images": [
      {
        "id": 0,
        "date_created": "2018-02-15T10:04:46",
        "date_created_gmt": "2018-02-15T04:04:46",
        "date_modified": "2018-02-15T10:04:46",
        "date_modified_gmt": "2018-02-15T04:04:46",
        "src": "http://dokannew.test/wp-content/plugins/woocommerce/assets/images/placeholder.png",
        "name": "Placeholder",
        "alt": "Placeholder",
        "position": 0
      }
    ],
    "attributes": [],
    "default_attributes": [],
    "variations": [],
    "grouped_products": [],
    "menu_order": 0,
    "meta_data": []
  }
]
```
This endpoint retrieves all Product for authorized vendor.

### HTTP Request

`GET http://dokan.test/wp-json/dokan/v1/products/`

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
per_page | integer | Maximum number of items to be returned in result set. Default is `10`.
page | integer | Current page of the collection. Default is `1`
search | string | Limit results to those matching a string.
after | string |  Limit response to resources published after a given ISO8601 compliant date.
before |  string |  Limit response to resources published before a given ISO8601 compliant date.
exclude | array | Ensure result set excludes specific IDs.
include | array | Limit result set to specific ids.
offset |  integer | Offset the result set by a specific number of items.
order | string |  Order sort attribute ascending or descending. Options: asc and desc. Default is desc.
orderby | string |  Sort collection by object attribute. Options: date, id, include, title and slug. Default is date.
parent |  array | Limit result set to those of particular parent IDs.
parent_exclude |  array | Limit result set to all items except those of a particular parent ID.
slug |  string |  Limit result set to products with a specific slug.
status |  string |  Limit result set to products assigned a specific status. Options: any, draft, pending, private and publish. Default is any.
type |  string |  Limit result set to products assigned a specific type. Options: simple, grouped, external and variable.
sku | string |  Limit result set to products with a specific SKU.
featured |  boolean | Limit result set to featured products.
category |  string |  Limit result set to products assigned a specific category ID.
tag | string |  Limit result set to products assigned a specific tag ID.
shipping_class |  string |  Limit result set to products assigned a specific shipping class ID.
attribute | string |  Limit result set to products with a specific attribute.
attribute_term |  string |  Limit result set to products with a specific attribute term ID (required an assigned attribute).
tax_class | string |  Limit result set to products with a specific tax class. Default options: standard, reduced-rate and zero-rate.
in_stock |  boolean | Limit result set to products in stock or out of stock.
on_sale | boolean | Limit result set to products on sale.
min_price | string |  Limit result set to products based on a minimum price.
max_price | string |  Limit result set to products based on a maximum price.

## Create a Product


```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "http://dokannew.test/wp-json/dokan/v1/products/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{
    \"name\": \"MI 5S\",
    \"type\": \"simple\",
    \"regular_price\": \"299\",
    \"description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.\",
    \"short_description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.\",
    \"categories\": [
      {
        \"id\": 48
      }
    ],
    \"images\": [
      {
        \"src\": \"http://demo.woothemes.com/woocommerce/wp-content/uploads/sites/56/2013/06/T_2_front.jpg\",
        \"position\": 0
      }
    ]
  }",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Basic authorization_key",
    "Cache-Control: no-cache",
    "Content-Type: application/json",
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}```

```shell
curl --request POST \
  --url http://dokannew.test/wp-json/dokan/v1/products/ \
  --header 'Authorization: Basic dmVuZG9yOnBhc3N3b3Jk' \
  --header 'Cache-Control: no-cache' \
  --header 'Content-Type: application/json' \
  --header 'Postman-Token: 2518adad-8135-9904-9107-e62f39c4126f' \
  --data '{
    "name": "MI 5S",
    "type": "simple",
    "regular_price": "299",
    "description": "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.",
    "short_description": "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.",
    "categories": [
      {
        "id": 48
      }
    ],
    "images": [
      {
        "src": "http://demo.woothemes.com/woocommerce/wp-content/uploads/sites/56/2013/06/T_2_front.jpg",
        "position": 0
      }
    ]
  }'
```

```python
import http.client

conn = http.client.HTTPConnection("dokannew,test")

payload = "{
  \"name\": \"MI 5S\",
  \"type\": \"simple\",
  \"regular_price\": \"299\",
  \"description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.\",
  \"short_description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.\",
  \"categories\": [
    {
      \"id\": 48
    }
  ],
  \"images\": [
    {
      \"src\": \"http://demo.woothemes.com/woocommerce/wp-content/uploads/sites/56/2013/06/T_2_front.jpg\",
      \"position\": 0
    }
  ]
}"

headers = {
  'Content-Type': "application/json",
  'Authorization': "Basic authorization_key",
  'Cache-Control': "no-cache",
}

conn.request("POST", "wp-json,dokan,v1,products,", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://dokannew.test/wp-json/dokan/v1/products/",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Basic dmVuZG9yOnBhc3N3b3Jk",
    "Cache-Control": "no-cache",
    "Postman-Token": "d8205bab-7d25-2415-3892-d30519c934a7"
  },
  "processData": false,
  "data": "{
    \"name\": \"MI 5S\",
    \"type\": \"simple\",
    \"regular_price\": \"299\",
    \"description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.\",
    \"short_description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.\",
    \"categories\": [
      {
        \"id\": 48
      }
    ],
    \"images\": [
      {
        \"src\": \"http://demo.woothemes.com/woocommerce/wp-content/uploads/sites/56/2013/06/T_2_front.jpg\",
        \"position\": 0
      }
    ]
  }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});```

```ruby
require 'uri'
require 'net/http'

url = URI("http://dokannew.test/wp-json/dokan/v1/products/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Basic dmVuZG9yOnBhc3N3b3Jk'
request["Cache-Control"] = 'no-cache'
request["Postman-Token"] = '9a77c957-57e0-5763-9940-5a64d704842a'
request.body = "{
  \"name\": \"MI 5S\",
  \"type\": \"simple\",
  \"regular_price\": \"299\",
  \"description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.\",
  \"short_description\": \"Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.\",
  \"categories\": [
    {
      \"id\": 48
    }
  ],
  \"images\": [
    {
      \"src\": \"http://demo.woothemes.com/woocommerce/wp-content/uploads/sites/56/2013/06/T_2_front.jpg\",
      \"position\": 0
    }
  ]
}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
    "id": 601,
    "name": "MI 5S",
    "slug": "",
    "post_author": "31",
    "permalink": "http://dokannew.test/?post_type=product&p=601",
    "date_created": "2018-02-15T11:13:14",
    "date_created_gmt": "2018-02-15T05:13:14",
    "date_modified": "2018-02-15T11:13:14",
    "date_modified_gmt": "2018-02-15T05:13:14",
    "type": "simple",
    "status": "pending",
    "featured": false,
    "catalog_visibility": "visible",
    "description": "<p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo.</p>\n",
    "short_description": "<p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</p>\n",
    "sku": "",
    "price": "299",
    "regular_price": "299",
    "sale_price": "",
    "date_on_sale_from": null,
    "date_on_sale_from_gmt": null,
    "date_on_sale_to": null,
    "date_on_sale_to_gmt": null,
    "price_html": "<span class=\"woocommerce-Price-amount amount\"><span class=\"woocommerce-Price-currencySymbol\">&#36;</span>299.00</span>",
    "on_sale": false,
    "purchasable": true,
    "total_sales": 0,
    "virtual": false,
    "downloadable": false,
    "downloads": [],
    "download_limit": -1,
    "download_expiry": -1,
    "external_url": "",
    "button_text": "",
    "tax_status": "taxable",
    "tax_class": "",
    "manage_stock": false,
    "stock_quantity": null,
    "in_stock": true,
    "backorders": "no",
    "backorders_allowed": false,
    "backordered": false,
    "sold_individually": false,
    "weight": "",
    "dimensions": {
        "length": "",
        "width": "",
        "height": ""
    },
    "shipping_required": true,
    "shipping_taxable": true,
    "shipping_class": "",
    "shipping_class_id": 0,
    "reviews_allowed": true,
    "average_rating": "0.00",
    "rating_count": 0,
    "related_ids": [],
    "upsell_ids": [],
    "cross_sell_ids": [],
    "parent_id": 0,
    "purchase_note": "",
    "categories": [
        {
            "id": 48,
            "name": "Mobile",
            "slug": "mobile"
        }
    ],
    "tags": [],
    "images": [
        {
            "id": 600,
            "date_created": "2018-02-15T11:13:13",
            "date_created_gmt": "2018-02-15T05:13:13",
            "date_modified": "2018-02-15T11:13:13",
            "date_modified_gmt": "2018-02-15T05:13:13",
            "src": "http://dokannew.test/wp-content/uploads/2018/02/T_2_front.jpg",
            "name": "T_2_front.jpg",
            "alt": "",
            "position": 0
        }
    ],
    "attributes": [],
    "default_attributes": [],
    "variations": [],
    "grouped_products": [],
    "menu_order": 0,
    "meta_data": []
}
```
This endpoint helps you to create a new product.

### HTTP Request

`POST http://dokan.test/wp-json/dokan/v1/products/`

### Query Parameters

Parameter | type | Description
--------- | ------- | -----------
name | string | `required` The name or title of the product []
category | array | `required` Set your product category.

Accept all parameters for a product propertiest see

<aside class="info">
Accept all parameters for a product propertiest see
</aside>


# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


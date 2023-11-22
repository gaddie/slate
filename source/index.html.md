---
title: API Reference


language_tabs:
 - shell
 - java
 - python
 - javascript


toc_footers:
 - <a href='#'>Sign Up for a Developer Key</a>
 - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>


includes:
 - errors


search: true


code_clipboard: true


meta:
 - name: description
   content: Documentation for the Kittn API
---


# Introduction


Welcome to the Product Catalog API!


Embark on a journey with our Product Catalog API, a comprehensive solution designed to facilitate the swift integration of partner products into your existing catalog. Whether you're a service provider aiming to streamline processes or a partner eager to showcase your offerings, our API is here to make it happen.


### What Can You Achieve?


The Product Catalog API provides a standardized and efficient solution for quickly adding partner products to your catalog. It empowers service providers to seamlessly communicate technical details about the products they offer to their partners.


Product Catalog API performs the following operations on the resources :


- Retrieve an entity or a collection of entities depending on filter criteria
- Partial update of an entity (including updating rules)
- Create an entity (including default values and creation rules)
- Delete an entity
- Manage notification of events


### Language Bindings


To enhance your development experience, we offer language bindings for a variety of programming languages. Whether you prefer Shell, java, Python, JavaScript, or another language, our API supports it. Explore the code examples in the dark area to the right, and effortlessly switch between programming languages using the tabs in the top right corner.


Let's embark on the journey of enhancing your product catalog together!






# Catalog


## Get All Catalogs


```java


import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpHeaders;
import java.net.http.HttpHeaders;
import java.io.IOException;


public class FetchCatalog {


   public static void main(String[] args) {
       String url = "http://localhost:8080/catalog";


       try {
           // Create an HttpClient
           HttpClient httpClient = HttpClient.newHttpClient();


           // Create an HttpRequest
           HttpRequest request = HttpRequest.newBuilder()
                   .uri(URI.create(url))
                   .build();


           // Send the request and retrieve the response
           HttpResponse<String> response = httpClient.send(request, HttpResponse.BodyHandlers.ofString());


           // Check if the request was successful (status code 200)
           if (response.statusCode() == 200) {
               // Handle the catalog data here
               System.out.println("Catalog: " + response.body());
           } else {
               System.err.println("HTTP error! Status: " + response.statusCode());
           }


       } catch (IOException | InterruptedException e) {
           System.err.println("Error fetching catalog: " + e.getMessage());
       }
   }
}


```




```python
import requests


url = 'http://localhost:8080/catalog'


try:
   response = requests.get(url)


   # Check if the request was successful (status code 200)
   response.raise_for_status()


   # Handle the catalog data here
   print("Catalog:", response.json())


except requests.HTTPError as http_err:
   print(f"HTTP error occurred: {http_err}")
except Exception as err:
   print(f"Error fetching catalog: {err}")


```








```shell


curl -X GET 'http://localhost:8080/catalog' \
 -H 'accept: application/json;charset=utf-8'


```




```javascript


const axios = require('axios');


axios.get('http://localhost:8080/catalog')
 .then(response => {
   // Handle the catalog data here
   console.log("Catalog:", response.data);
 })
 .catch(error => {
   console.error("Error fetching catalog:", error);
 });




```


> The above command returns JSON structured like this:


```json
[
 {
   "id": "12345",
   "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/Catalog/2027",
   "name": "IoT Product Catalog",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the IoT products.",
   "catalogType": "ProductCatalog",
   "version": "2.0",
   "validFor": {
     "startDateTime": "2020-09-29T00:00:00Z",
     "endDateTime": "2024-09-25T00:00:00Z"
   },
   "lastUpdate": "2020-10-27T00:00:00Z",
   "lifecycleStatus": "Active",
   "relatedParty": [
     {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "@referredType": "Organization",
       "@type": "RelatedParty",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
     },
     {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/individual/2999",
       "id": "2999",
       "name": "Humphrey Bogart",
       "role": "Reviser",
       "@referredType": "Individual",
       "@type": "RelatedParty",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
     }
   ],
   "category": [
     {
       "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/category/2129",
       "id": "2129",
       "name": "iotProducts",
       "version": "1.0",
       "@referredType": "Category",
       "@type": "CategoryRef",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Category.schema.json"
     }
   ],
   "@type": "Catalog",
   "@baseType": "",
   "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
 },
 {
   "id": "3830",
   "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/Catalog/3830",
   "name": "Catalog Wholesale Business",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
   "catalogType": "ProductCatalog",
   "version": "1.0",
   "validFor": {
     "startDateTime": "2020-08-29T00:00:00Z",
     "endDateTime": "2024-03-25T00:00:00Z"
   },
   "lastUpdate": "2020-08-27T00:00:00Z",
   "lifecycleStatus": "Active",
   "relatedParty": [
     {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "@referredType": "Organization",
       "@type": "RelatedParty",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
     },
     {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/individual/115566",
       "id": "115566",
       "name": "Roger Collins",
       "role": "Reviser",
       "@referredType": "Individual",
       "@type": "RelatedParty",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
     }
   ],
   "category": [
     {
       "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/category/7757",
       "id": "7757",
       "name": "business",
       "version": "1.0",
       "@referredType": "Category",
       "@type": "CategoryRef",
       "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Category.schema.json"
     }
   ],
   "@type": "Catalog",
   "@baseType": "",
   "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
 }
]
```


This endpoint retrieves all catalogs.


### HTTP Request


`GET http://localhost:8080/catalog`










## Get a Specific Catalog


```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpHeaders;
import java.net.http.HttpHeaders;
import java.io.IOException;


public class FetchCatalog {


   public static void main(String[] args) {
       String url = "http://localhost:8080/catalog/12345";


       try {
           // Create an HttpClient
           HttpClient httpClient = HttpClient.newHttpClient();


           // Create an HttpRequest
           HttpRequest request = HttpRequest.newBuilder()
                   .uri(URI.create(url))
                   .build();


           // Send the request and retrieve the response
           HttpResponse<String> response = httpClient.send(request, HttpResponse.BodyHandlers.ofString());


           // Check if the request was successful (status code 200)
           if (response.statusCode() == 200) {
               // Handle the catalog data here
               System.out.println("Catalog: " + response.body());
           } else {
               System.err.println("HTTP error! Status: " + response.statusCode());
           }


       } catch (IOException | InterruptedException e) {
           System.err.println("Error fetching catalog: " + e.getMessage());
       }
   }
}
```


```python
import requests


url = 'http://localhost:8080/catalog/12345'


try:
   response = requests.get(url)


   # Check if the request was successful (status code 200)
   response.raise_for_status()


   # Handle the catalog data here
   print("Catalog:", response.json())


except requests.HTTPError as http_err:
   print(f"HTTP error occurred: {http_err}")
except Exception as err:
   print(f"Error fetching catalog: {err}")
```


```shell
curl -X GET 'http://localhost:8080/catalog/12345' \
 -H 'accept: application/json;charset=utf-8'


```


```javascript
const axios = require('axios');


axios.get('http://localhost:8080/catalog/12345')
 .then(response => {
   // Handle the catalog data here
   console.log("Catalog:", response.data);
 })
 .catch(error => {
   console.error("Error fetching catalog:", error);
 });
```
> The above command returns JSON structured like this:


```json
{
 "id": "12345",
 "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/Catalog/3830",
 "name": "Catalog Wholesale Business",
 "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
 "catalogType": "ProductCatalog",
 "validFor": {
   "startDateTime": "2020-08-29T00:00:00Z",
   "endDateTime": "2024-03-25T00:00:00Z"
 },
 "lastUpdate": "2020-08-27T00:00:00Z",
 "lifecycleStatus": "Active",
 "relatedParty": [
   {
   "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
   "id": "3426",
   "name": "Broadly Broad Ltd",
   "role": "vendor",
   "@referredType": "Organization",
   "@type": "RelatedParty",
   "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   {
   "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/individual/115566",
   "id": "115566",
   "name": "Roger Collins",
   "role": "Reviser",
   "@referredType": "Individual",
   "@type": "RelatedParty",
   "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   }
 ],
 "category": [
   {
     "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/category/7757",
     "id": "7757",
     "name": "business",
     "version": "1.0",
     "@referredType": "Category",
     "@type": "CategoryRef",
     "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Category.schema.json"
   }
 ],
 "@type": "Catalog",
 "@baseType": "",
 "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
}
```


This endpoint retrieves a specific catalog.




### HTTP Request


`GET http://localhost:8080/catalog/<ID>`


### URL Parameters


Parameter | Description
--------- | -----------
ID | The ID of the catalog to retrieve










## Post a Catalog


```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;


public class PostCatalogExample {


   public static void main(String[] args) {
       String url = "http://localhost:8080/catalog";


       String requestBody = "{" +
           "\"name\": \"Catalog Wholesale Business\"," +
           "\"description\": \"This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.\"," +
           "\"catalogType\": \"ProductCatalog\"," +
           "\"version\": \"1.0\"," +
           "\"validFor\": {" +
               "\"startDateTime\": \"2020-08-29T00:00:00Z\"," +
               "\"endDateTime\": \"2024-03-25T00:00:00Z\"" +
           "}," +
           "\"lifecycleStatus\": \"Active\"," +
           "\"relatedParty\": {" +
               "\"href\": \"https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426\"," +
               "\"id\": \"3426\"," +
               "\"name\": \"Broadly Broad Ltd\"," +
               "\"role\": \"vendor\"," +
               "\"referredType\": \"Organization\"," +
               "\"type\": \"RelatedParty\"," +
               "\"schemaLocation\": \"https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json\"" +
           "}," +
           "\"type\": \"Catalog\"," +
           "\"schemaLocation\": \"https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json\"" +
       "}";


       try {
           HttpClient client = HttpClient.newHttpClient();


           HttpRequest request = HttpRequest.newBuilder()
                   .uri(URI.create(url))
                   .header("Content-Type", "application/json")
                   .POST(HttpRequest.BodyPublishers.ofString(requestBody))
                   .build();


           HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());


           // Handle the response
           System.out.println("Response Code: " + response.statusCode());
           System.out.println("Response Body: " + response.body());
       } catch (Exception e) {
           e.printStackTrace();
       }
   }
}


```


```python
import requests
import json


url = 'http://localhost:8080/catalog'


catalog_data = {
   "name": "Catalog Wholesale Business",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
   "catalogType": "ProductCatalog",
   "version": "1.0",
   "validFor": {
       "startDateTime": "2020-08-29T00:00:00Z",
       "endDateTime": "2024-03-25T00:00:00Z"
   },
   "lifecycleStatus": "Active",
   "relatedParty": {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "referredType": "Organization",
       "type": "RelatedParty",
       "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   "type": "Catalog",
   "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
}


headers = {
   'Content-Type': 'application/json',
}


try:
   response = requests.post(url, json=catalog_data, headers=headers)
   response.raise_for_status()
  
   # Handle the response here
   print("Response:", response.json())


except requests.HTTPError as http_err:
   print(f"HTTP error occurred: {http_err}")
except Exception as err:
   print(f"Error posting catalog data: {err}")


```


```shell
curl -X POST 'http://localhost:8080/catalog' \
 -H 'Content-Type: application/json' \
 -d '{
   "name": "Catalog Wholesale Business",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
   "catalogType": "ProductCatalog",
   "version": "1.0",
   "validFor": {
       "startDateTime": "2020-08-29T00:00:00Z",
       "endDateTime": "2024-03-25T00:00:00Z"
   },
   "lifecycleStatus": "Active",
   "relatedParty": {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "referredType": "Organization",
       "type": "RelatedParty",
       "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   "type": "Catalog",
   "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
 }'




```


```javascript
const fetch = require('node-fetch');


const url = 'http://localhost:8080/catalog';




const catalogData = {
   "name": "Catalog Wholesale Business",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
   "catalogType": "ProductCatalog",
   "version": "1.0",
   "validFor": {
       "startDateTime": "2020-08-29T00:00:00Z",
       "endDateTime": "2024-03-25T00:00:00Z"
   },
   "lifecycleStatus": "Active",
   "relatedParty": {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "referredType": "Organization",
       "type": "RelatedParty",
       "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   "type": "Catalog",
   "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
};


fetch(url, {
   method: 'POST',
   headers: {
       'Content-Type': 'application/json',
   },
   body: JSON.stringify(catalogData),
})
   .then(response => response.json())
   .then(data => console.log("Response:", data))
   .catch(error => console.error("Error posting catalog data:", error));


```


> Example of request body:


```json
{
   "name": "Catalog Wholesale Business",
   "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
   "catalogType": "ProductCatalog",
   "version": "1.0",
   "validFor": {
       "startDateTime": "2020-08-29T00:00:00Z",
       "endDateTime": "2024-03-25T00:00:00Z"
   },
   "lifecycleStatus": "Active",
   "relatedParty": {
       "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
       "id": "3426",
       "name": "Broadly Broad Ltd",
       "role": "vendor",
       "referredType": "Organization",
       "type": "RelatedParty",
       "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   "type": "Catalog",
   "schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
};


```
> Example of respose body:


```json
{
 "id": "12345",
 "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/Catalog/3830",
 "name": "{{ request.body.name }}",
 "description": "{{ request.body.description }}",
 "catalogType": "request.body.catalogType ",
 "version": "{{ request.body.version }}",
 "validFor": {
   "startDateTime": "{{ request.body.validFor.startDateTime }}",
   "endDateTime": "{{ request.body.validFor.endtDateTime }}"
 },
 "lastUpdate": "2020-08-27T00:00:00Z",
 "lifecycleStatus": "{{ request.body.lifecycleStatus }}",
 "relatedParty": [
   {
     "href": "{{ request.body.relatedParty.href }}",
     "id": "{{ request.body.relatedParty.href }}",
     "name": "{{ request.body.relatedParty.name }}",
     "role": "{{ request.body.relatedParty.role }}",
     "@referredType": "{{ request.body.relatedParty.referredType }}",
     "@type": "{{ request.body.relatedParty.type }}",
     "@schemaLocation": "{{ request.body.relatedParty.schemaLocation }}"
   }
 ],
 "category": [],
 "@type": "{{ request.body.type }}",
 "@baseType": "",
 "@schemaLocation": "{{ request.body.schemaLocation }}"
}
```


This endpoint posts a catalog.




### HTTP Request


`POST http://localhost:8080/catalog`


### URL Parameters


Parameter | Description
--------- | -----------
ID | The ID of the catalog to retrieve










## Patch a Specific Catalog


```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class PatchCatalogExample {

    public static void main(String[] args) {
        String url = "http://localhost:8080/catalog/12345";

        String requestBody = "{" +
            "\"version\": \"2.0\"," +
            "\"validFor\": {" +
                "\"startDateTime\": \"2020-08-29T00:00:00Z\"," +
                "\"endDateTime\": \"2024-03-25T00:00:00Z\"" +
            "}" +
        "}";

        try {
            HttpClient client = HttpClient.newHttpClient();

            HttpRequest request = HttpRequest.newBuilder()
                    .uri(URI.create(url))
                    .header("Content-Type", "application/merge-patch+json")
                    .method("PATCH", HttpRequest.BodyPublishers.ofString(requestBody))
                    .build();

            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

            // Handle the response
            System.out.println("Response Code: " + response.statusCode());
            System.out.println("Response Body: " + response.body());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```


```python
import requests
import json

url = 'http://localhost:8080/catalog/12345'

catalog_data = {
  "version": "2.0",
  "validFor": {
    "startDateTime": "2020-09-23T00:00:00Z",
    "endDateTime": ""
  }
}

headers = {
    'Content-Type': 'application/merge-patch+json',
}

try:
    response = requests.patch(url, json=catalog_data, headers=headers)
    response.raise_for_status()
    
    # Handle the response here
    print("Response:", response.json())

except requests.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except Exception as err:
    print(f"Error posting catalog data: {err}")
```


```shell
curl -X PATCH 'http://localhost:8080/catalog/12345' \
 -H 'Content-Type: application/json' \
 -d '{
  "version": "2.0",
  "validFor": {
    "startDateTime": "2020-09-23T00:00:00Z",
    "endDateTime": ""
  }
}'


```


```javascript
const fetch = require('node-fetch');

const url = 'http://localhost:8080/catalog/12345';

const catalogData = {
  "version": "2.0",
  "validFor": {
    "startDateTime": "2020-09-23T00:00:00Z",
    "endDateTime": ""
  }
}


fetch(url, {
   method: 'PATCH',
   headers: {
       'Content-Type': 'application/json',
   },
   body: JSON.stringify(catalogData),
})
   .then(response => response.json())
   .then(data => console.log("Response:", data))
   .catch(error => console.error("Error posting catalog data:", error));

```


```
> Example of a patch request:


```
```json
{
 "version": "2.0",
 "validFor": {
   "startDateTime": "2020-09-23T00:00:00Z",
   "endDateTime": ""
 }
}
```
> Example of a Patch response:


```json
{
 "id": "12345",
 "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/Catalog/3830",
 "name": "Catalog Wholesale Business",
 "description": "This catalog describes Product Offerings and technical specifications intended to address the wholesale business segment.",
 "catalogType": "ProductCatalog",
 "version": "{{ request.body.version }}",
 "validFor": {
   "startDateTime": "{{ request.body.validFor.startDateTime }}",
   "endDateTime": ""
 },
 "lastUpdate": "2020-09-22T00:00:00Z",
 "lifecycleStatus": "Active",
 "relatedParty": [
   {
     "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/organization/3426",
     "id": "3426",
     "name": "Broadly Broad Ltd",
     "role": "vendor",
     "@referredType": "Organization",
     "@type": "RelatedParty",
     "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   },
   {
     "href": "https://mycsp.com:8080/tmf-api/partyManagement/v4/individual/115566",
     "id": "115566",
     "name": "Roger Collins",
     "role": "Reviser",
     "@referredType": "Individual",
     "@type": "RelatedParty",
     "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/EngagedParty/RelatedParty.schema.json"
   }
 ],
 "category": [
   {
     "href": "https://mycsp.com:8080/tmf-api/productCatalogManagement/v4/category/7757",
     "id": "7757",
     "name": "business",
     "version": "1.0",
     "@referredType": "Category",
     "@type": "CategoryRef",
     "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Category.schema.json"
   }
 ],
 "@type": "Catalog",
 "@baseType": "",
 "@schemaLocation": "https://mycsp.com:8080/tmf-api/schemas/Product/Catalog.schema.json"
}
```


This endpoint retrieves a specific catalog.




### HTTP Request


`GET http://localhost:8080/catalog/<ID>`


### URL Parameters


Parameter | Description
--------- | -----------
ID | The ID of the catalog to retrieve






## Delete a Specific Kitten


```java
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
curl "http://example.com/api/kittens/2" \
 -X DELETE \
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













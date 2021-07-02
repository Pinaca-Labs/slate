---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - python/curl

search: true

code_clipboard: true
---

# Auto detect - Translation API

## Sync request from python

> python code :

```python/curl

import requests

URL = "https://gputwo.pinacalabs.com/translation/autodetect_en/v0.1/sync"

user = "USERNAME"

passwd = "PASSWORD"

DATA =  {"data": ["Для Путина поездка в Женеву - первый зарубежный визит за последние полтора года. Он летал в Иерусалим в январе 2020 года, после чего из-за пандемии перешел на встречи по видеосвязи."]}

result = requests.post(URL, json = DATA, auth = (user, passwd)).json()

if result["success"]: 
  print(result["prediction"])

```

> The above command returns JSON structured like this:

```json

{
  "prediction": ["For Putin, the visit to Geneva is the first foreign visit in a year and a half. He was flying to Jerusalem in January 2020, after which, due to a pandemic, he moved to video meetings."], 
"success": true
}


```

This endpoint retrieves translated result.

### Query Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
user | Username for authentication.
passwd | Password for authentication.

## Sync request from curl

> curl request :

```python/curl

curl -d '{"data": ["Для Путина поездка в Женеву - первый зарубежный визит за последние полтора года. Он летал в Иерусалим в январе 2020 года, после чего из-за пандемии перешел на встречи по видеосвязи."]}' -H "Content-Type: application/json" -X POST https://gputwo.pinacalabs.com/translation/autodetect_en/v0.1/sync -u USERNAME:PASSWORD


```

> The above command returns JSON structured like this:

```json

{
  "prediction": ["For Putin, the visit to Geneva is the first foreign visit in a year and a half. He was flying to Jerusalem in January 2020, after which, due to a pandemic, he moved to video meetings."], 
"success": true
}

```

This endpoint retrieves translated result.

### Query Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
user | Username for authentication.
passwd | Password for authentication.

## Async request from python

>python code :

```python/curl

import requests

URL = "https://gputwo.pinacalabs.com/translation/autodetect_en/v0.1/async"

user = "USERNAME"

passwd = "PASSWORD"

DATA =  {"data": ["Для Путина поездка в Женеву - первый зарубежный визит за последние полтора года. Он летал в Иерусалим в январе 2020 года, после чего из-за пандемии перешел на встречи по видеосвязи."], "webhook": None}

result = requests.post(URL, json = DATA, auth = (user, passwd)).json()

if result["success"]: 
  print(result["unique_id"])


```

> The above command returns JSON structured like this:

```json

{
  "success": true, 
  "unique_id": "9_2021-06-18-13-15-55-240_d68c54ff-73a8-42f6-8b95-509c38a332e1"
}

```

This endpoint deletes a specific kitten.

### Notes

`1. If “webhook” is provided, the result will be posted to the webhook once the request is processed`

### URL Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
user | Username for authentication.
passwd | Password for authentication.

## Async request from curl

> curl request :

```python/curl

curl -d '{"data": ["Для Путина поездка в Женеву - первый зарубежный визит за последние полтора года. Он летал в Иерусалим в январе 2020 года, после чего из-за пандемии перешел на встречи по видеосвязи."], "webhook": None}' -H "Content-Type: application/json" -X POST https://gputwo.pinacalabs.com/translation/autodetect_en/v0.1/async -u USERNAME:PASSWORD


```

> The above command returns JSON structured like this:

```json

{
  "success": true, 
  "unique_id": "9_2021-06-18-13-15-55-240_d68c54ff-73a8-42f6-8b95-509c38a332e1"
}

```

This endpoint deletes a specific kitten.

### Notes

`1. If “webhook” is provided, the result will be posted to the webhook once the request is processed`

### URL Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
user | Username for authentication.
passwd | Password for authentication.

## Fetching/ Checking result for async request

> curl request :

```python/curl

curl -d '{"unique_id": "9_2021-06-03-14-29-40-480_cb77178c-4d84-4759-a34c-b9d56f587714"}' -H "Content-Type: application/json" -X POST https://gputwo.pinacalabs.com/translation/autodetect_en/v0.1/result -u USERNAME:PASSWORD


```

> The above command returns JSON structured like this:

```json

{
  "prediction": ["For Putin, the visit to Geneva is the first foreign visit in a year and a half. He was flying to Jerusalem in January 2020, after which, due to a pandemic, he moved to video meetings."], 
  "success": true
}

```

This endpoint deletes a specific kitten.

### Async request Response

`1. If the request is processed, the response for async request is the same as the response for sync request`

`2. Please DO NOT pol for results continuously. Use a reasonable sleep time (at least 1 second) between each /result request`

`3. If the request is not processed yet, the response indicates the same using “success”: False and “reason”`

### Notes

`1. data” field of input JSON should be a list of texts that are sent for prediction. (Here prediction implies translation)`

`2. “success” in the response indicated the status of the result. (if true, “prediction” will contain your results).`

`3. “prediction” in the response (if success is true) contains a list of predictions whose length is the same as “data” in the input json.`

### URL Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
USERNAME | Username for authentication.
PASSWORD | Password for authentication.

## Entity Relationship API

> curl request :

```python/curl

curl -d '{"data": ["Praneeth Bedapudi works at Pinaca Labs."]}' -H "Content-Type: application/json" -X POST https://gpuone.pinacalabs.com/entity_relation/sync -u USERNAME:PASSWORD


```

> The above command returns JSON structured like this:

```json

{
  "prediction": [[{"line": "Praneeth Bedapudi works at Pinaca Labs.", "entities": [{"span": [0, 17], "class": "PER", "phrase": "Praneeth Bedapudi"}, {"span": [27, 38], "class": "ORG", "phrase": "Pinaca Labs"}], "relations": [{"phrase_1": "Praneeth Bedapudi", "phrase_2": "Pinaca Labs", "span_1": [0, 17], "span_2": [27, 38], "relation": "per:employee_of"}]}]], 
  "success": true
}

```

This endpoint retrieves a entities avialable between sentence.

### Entity Relationship API

`1. The entity relationship API follows the same basic structure as that of the translation API. i.e: /sync, /result and /async follow the exact same specifications`

### Notes

`1. The response for each input in the list “data” contains a list of dictionaries with keys “line”: text, “entities”: list (list of dictionaries with “class” and “phrase” as keys) and “relations”.`

`2. The key “class” can be one of` 

MISC 

PER 

ORG 

LOC 


`3. The key “relation” can be one of`

org:alternate_names
org:city_of_headquarters
org:country_of_headquarters
org:dissolved
org:founded
org:founded_by
org:member_of
org:members
org:number_of_employees/members
org:parents
org:political/religious_affiliation
org:shareholders
org:stateorprovince_of_headquarters
org:subsidiaries
org:top_members/employees
org:website
per:age
per:alternate_names
per:cause_of_death
per:charges
per:children
per:cities_of_residence
per:city_of_birth
per:city_of_death
per:countries_of_residence
per:country_of_birth
per:country_of_death
per:date_of_birth
per:date_of_death
per:employee_of
per:origin
per:other_family
per:parents
per:religion
per:schools_attended
per:siblings
per:spouse
per:stateorprovince_of_birth
per:stateorprovince_of_death
per:stateorprovinces_of_residence
per:title


### URL Parameters

Parameter | Description
--------- | -----------
url | The api request url for translating text.
data | The text to be translated.
USERNAME | Username for authentication.
PASSWORD | Password for authentication.


# Natural Language

Natural Language Processing (NLP) services helps you to process, analyze and get insights from text data.

## Sentiment Analysis

Sentiment analysis is used to classify the polarity of a given text to find out whether the expressed opinion in this text is positive, negative, or neutral. 

### HTTP Request

`POST /v1/nlp/sentiment`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/nlp/sentiment' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "text": "I don'\''t like old cabin cruisers.",
    "provider":"AWS",
    "language": "Auto"
}'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer your-token");
myHeaders.append("Content-Type", "text/plain");

var raw = "{\n    \"text\": \"I don't like old cabin cruisers.\",\n    \"provider\":\"AWS\",\n    \"language\": \"Auto\"\n}";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://api.rapyd.ai/v1/nlp/sentiment", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/nlp/sentiment"

payload = "{\n    \"text\": \"I don't like old cabin cruisers.\",\n    \"provider\":\"AWS\",\n    \"language\": \"Auto\"\n}"
headers = {
  'ACCOUNT-ID': 'your-accountid',
  'Content-Type': 'application/json',
  'Authorization': 'Bearer your-token',
  'Content-Type': 'text/plain'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/nlp/sentiment"


payload <- list(text = "I don't like old cabin cruisers.", 
           provider = "aws")

headers <- c(ACCOUNTID = "your-accountid", 
             Authorization = "Bearer your-token")

response <- POST(url, add_headers(headers), body = payload, encode = "json")
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation. The content depends on the chosen provider.

> Example response when provider is `aws`:

```json
{
    "meta": {
        "provider": "AWS",
        "language": "en"
    },
    "result": {
        "sentiment": "NEGATIVE",
        "sentimentScore": {
            "positive": 0.035679124,
            "negative": 0.6906262,
            "neutral": 0.27357435,
            "mixed": 1.2039347E-4
        }
    }
}
```

> Example response when provider is `gcp`:

```json
{
    "meta": {
        "provider": "GCP",
        "language": "en"
    },
    "result": {
        "score": -0.8
    }
}
```
> Example response when provider is `azure`:

```json
{
    "meta": {
        "provider": "AZURE",
        "language": "English"
    },
    "result": {
        "sentiment": "neutral",
        "confidenceScores": {
            "neutral": 0.52,
            "positive": 0.03,
            "negative": 0.45
        },
        "sentences": [
            {
                "text": "I don't like old cabin cruisers.",
                "confidenceScores": {
                    "neutral": 0.52,
                    "positive": 0.03,
                    "negative": 0.45
                },
                "sentiment": "neutral"
            }
        ],
        "warnings": []
    }
}
```

### Request Parameters

The request body contains data in JSON representation: 

Parameter | Default | Description 
--------- | --------| -----------
Text | None | The text which you want to analyse. Maximum is xxxx characters.
Provider | `auto` | The AI service provider you want to use. The AI Service provider can be any of the following: <ul><li>`aws` (Amazon Comprehend)</li><li>`azure` (Microsoft Azure Cognitive Services)</li><li>`gcp` (Google Cloud NLP API).</li><li>`auto` (let RAPYD.AI choose service provider automatically.)</li></ul>
Language | `auto` | The language of the text in the request body. Can be any of the following: <ul><li>`de` (German) </li><li>`en` (English) </li><li>`es` (Spanish) </li><li>`it` (Italian) </li><li>`pt` (Portuguese) </li><li>`fr` (French) </li><li>`ja` (Japanese) </li><li>`ko` (Korean) </li><li>`hi` (Hindi) </li><li>`ar` (Arabic) </li><li>`zh` (Chinese simplified) </li><li>`zh-TW` (Chinese traditional) </li><li>`auto` (Auto-detect language) </li></ul>

## Detect Entities

Detects entities in a given text. An entity is a reference to a real-world object such as people, places, commercial items, and to measures such as dates and quantities.

Each entity comes with a score that indicates the level of confidence for the detected entity type.

### HTTP Request

`POST /v1/nlp/entities`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/nlp/entities' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "text": "Next summer I want to visit Barcelona and Lion.",
    "provider":"aws"
}'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer your-token");
myHeaders.append("Content-Type", "text/plain");

var raw = "{\n    \"text\": \"Next summer I want to visit Barcelona and Lion.\",\n    \"provider\":\"aws\"\n}";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/nlp/entities", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/nlp/entities"

payload = "{\n    \"text\": \"Next summer I want to visit Barcelona and Lion.\",\n    \"provider\":\"aws\"\n}"
headers = {
  'ACCOUNT-ID': 'your-accountid',
  'Content-Type': 'application/json',
  'Authorization': 'Bearer your-token',
  'Content-Type': 'text/plain'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))


```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/nlp/entities"


payload <- list(text = "Next summer I want to visit Barcelona and Lion.", 
           provider = "aws")

headers <- c(ACCOUNTID = "your-accountid", 
             Authorization = "Bearer your-token")

response <- POST(url, add_headers(headers), body = payload, encode = "json")
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation. The content depends on the chosen provider.

> Example response when provider is `aws`:

```json
{
    "meta": {
        "provider": "aws",
        "language": "en"
    },
    "result": {
        "entities": [
            {
                "score": 0.9543518,
                "type": "DATE",
                "text": "Next summer",
                "beginOffset": 0,
                "endOffset": 11
            },
            {
                "score": 0.99991035,
                "type": "LOCATION",
                "text": "Barcelona",
                "beginOffset": 28,
                "endOffset": 37
            },
            {
                "score": 0.99886346,
                "type": "LOCATION",
                "text": "Lion",
                "beginOffset": 42,
                "endOffset": 46
            }
        ]
    }
}
```

> Example response when provider is `gcp`:

```json
{
    "meta": {
        "provider": "GCP",
        "language": "en"
    },
    "result": [
        {
            "name": "Barcelona",
            "salience": 0.6229014992713928,
            "type": "LOCATION"
        },
        {
            "name": "Lion",
            "salience": 0.3770985007286072,
            "type": "ORGANIZATION"
        }
    ]
}
```
> Example response when provider is `azure`:

```json
{
    "meta": {
        "provider": "AZURE",
        "language": "English"
    },
    "result": [
        {
            "text": "Next summer",
            "category": "DateTime",
            "subcategory": "DateRange",
            "confidenceScore": 0.8
        },
        {
            "text": "Barcelona",
            "category": "Location",
            "subcategory": "GPE",
            "confidenceScore": 0.41
        },
        {
            "text": "Lion",
            "category": "Location",
            "subcategory": "GPE",
            "confidenceScore": 0.36
        }
    ]
}
```

### Request Parameters

The request body contains data in JSON representation. 

Parameter | Default | Description 
--------- | --------| -----------
Text | None | The text which you want to analyse. Maximum is xxxx characters.
Provider | `auto` | The AI service provider you want to use. The AI Service provider can be any of the following: <ul><li>`aws` (Amazon Comprehend)</li><li>`azure` (Microsoft Azure Cognitive Services)</li><li>`gcp` (Google Cloud NLP API).</li><li>`auto` (let RAPYD.AI choose service provider automatically.)</li></ul>
Language | `auto` | The language of the text in the request body. Can be any of the following: <ul><li>`de` (German) </li><li>`en` (English) </li><li>`es` (Spanish) </li><li>`it` (Italian) </li><li>`pt` (Portuguese) </li><li>`fr` (French) </li><li>`ja` (Japanese) </li><li>`ko` (Korean) </li><li>`hi` (Hindi) </li><li>`ar` (Arabic) </li><li>`zh` (Chinese simplified) </li><li>`zh-TW` (Chinese traditional) </li><li>`auto` (Auto-detect language) </li></ul>

## Detect Key Phrases

Detects the key noun phrases used in text.

Each key phrase comes with a score that indicates the level of confidence for the detected noun phrase.

### HTTP Request

`POST /v1/nlp/entities`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/nlp/keyphrase' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer your-token' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "text": "Seems it never rains in Southern California.",
    "provider":"aws",
    "language": "auto"
}'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer your-token");
myHeaders.append("Content-Type", "text/plain");

var raw = "{\n    \"text\": \"Seems it never rains in Southern California.\",\n    \"provider\":\"aws\",\n    \"language\": \"auto\"\n}";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/nlp/keyphrase", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/nlp/keyphrase"

payload = "{\n    \"text\": \"Seems it never rains in Southern California.\",\n    \"provider\":\"aws\",\n    \"language\": \"auto\"\n}"
headers = {
  'ACCOUNT-ID': 'your-accountid',
  'Content-Type': 'application/json',
  'Authorization': 'Bearer your-token',
  'Content-Type': 'text/plain'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/nlp/keyphrase"


payload <- list(text = "Seems it never rains in Southern California.", 
           provider = "aws")

headers <- c(ACCOUNTID = "your-accountid", 
             Authorization = "Bearer your-token")

response <- POST(url, add_headers(headers), body = payload, encode = "json")
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation. The content depends on the chosen provider.

> Example response when provider is `aws`:

```json
{
    "meta": {
        "provider": "aws",
        "language": "en"
    },
    "result": {
        "keyPhrases": [
            {
                "score": 0.9999997,
                "text": "Southern California",
                "beginOffset": 24,
                "endOffset": 43
            }
        ]
    }
}
```

> Example response when provider is `azure`:

```json
{
    "meta": {
        "provider": "azure",
        "language": "English"
    },
    "result": [
        "Southern California"
    ]
}
```

### Request Parameters

The request body contains data in JSON representation. 

Parameter | Default | Description 
--------- | --------| -----------
Text | None | The text which you want to analyse. Maximum is xxxx characters.
Provider | `auto` | The AI service provider you want to use. The AI Service provider can be any of the following: <ul><li>`aws` (Amazon Comprehend)</li><li>`azure` (Microsoft Azure Cognitive Services)</li><li>`auto` (let RAPYD.AI choose service provider automatically.)</li></ul>
Language | `auto` | The language of the text in the request body. Can be any of the following: <ul><li>`de` (German) </li><li>`en` (English) </li><li>`es` (Spanish) </li><li>`it` (Italian) </li><li>`pt` (Portuguese) </li><li>`fr` (French) </li><li>`ja` (Japanese) </li><li>`ko` (Korean) </li><li>`hi` (Hindi) </li><li>`ar` (Arabic) </li><li>`zh` (Chinese simplified) </li><li>`zh-TW` (Chinese traditional) </li><li>`auto` (Auto-detect language) </li></ul>

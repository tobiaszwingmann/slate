---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript: JavaScript
  - python: Python
  - r: R
  - shell: cURL

  

toc_footers:
  - <a href='https://www.rapyd.ai/app/sign-up/'>Sign Up for RAPYD.AI</a>

includes:
  - nlp
  - vision
  - errors

search: true

code_clipboard: true
---

# Introduction

> <strong> GETTING STARTED? </strong><br />
Check out our <a href="https://www.rapyd.ai/help-center/quickstart-guide"> quickstart guide</a>.

> <strong> NOT A DEVELOPER? </strong> <br /> 
Sign in to your <a href="https://www.rapyd.ai/app/start">RAPYD.AI dashboard</a> to get started with apps. 

> Base URL:

```markdown
https://api.rapyd.ai
```

RAPYD.AI is an API for AI services. Some people call it AI-as-a-Service. Some call it AI platform. We don't mind how you call it, but here's what RAPYD.AI does in plain English:

<aside class="notice">
<strong>RAPYD.AI gives you a simple API interface to access state-of-the-art AI services from leading providers.</strong>
</aside>

Let's break this statement down:

<strong>A simple API interface</strong>
The RAPYD.AI API is organized around REST. Our API accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs. You can send texts, images, videos or audio files as inputs. You can even use our API to train and deploy custom models (Pro Plan).

<strong>State-of-the-art AI services</strong>
We ensure that the AI services that we provide belong the best of their class. You should focus on your use-case and your AI application and not whether another AI service might do a better job. It might be that another AI achieves better results, especially in very specific or niche settings. But generally speaking, the AI services that we provide here will give you a good baseline to start with.

<strong>Leading providers</strong>
All AI services on RAPYD.AI are production ready. We don't want you to build your prototype using some AI service that does not scale. When you decide to go into production, you can rely that the service provider in the backend can handle your AI production workloads.

# Authentication

The RAPYD.AI API uses a combination of your unique, permanent account ID and a temporary access token to authenticate requests. 

You will get an Account ID when you <a href="https://www.rapyd.ai/app/sign-up/", target = "_blank"> sign up here</a>. We will find your Account-ID in your welcome e-mail as well as in your <a href="https://www.rapyd.ai/app/start/", target = "_blank"> RAPYD.AI Dashboard.</a>

You can generate a token as often as you like either through your <a href="https://www.rapyd.ai/app/start/", target = "_blank"> RAPYD.AI Dashboard</a> or programmatically using the following API end point:

`POST /v1/user/token`

A token is valid for 60 minutes.

> To get a token, use this code:

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/user/token' \
--header 'Content-Type: application/json' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"email":"your-email",
	"password":"your-password"
}
'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Content-Type", "text/plain");

var raw = "{\n	\"email\":\"your-email\",\n	\"password\":\"your-password\"\n}\n";

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/user/token", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
  
```

```python

import requests

url = "https://api.rapyd.ai/v1/user/token"

payload = "{\n\t\"email\":\"your-email\",\n\t\"password\":\"your-password\"\n}\n"
headers = {
  'Content-Type': 'application/json',
  'Content-Type': 'text/plain'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))

```

```r
library(httr)

url <- "https://api.rapyd.ai/v1/user/token"
payload <- list(email = "your-email", 
           password = "your-password")

# Get results
response <- POST(url, body = payload, encode = "json")
result <- content(response, "parsed")
```

> Make sure to replace `your-email` and `your-password`with your password.

> <strong>Never store your password inside your code! </strong> If you are not sure how to manage your passwords safely, use our dashboard to generate a token.

Authentication to the API is performed via Bearer Token Usage. 

RAPYD.AI expects the Account ID and the Token to be included in all API requests to the server in a header that looks like the following:

`'ACCOUNT-ID: your-accountid'`
`'Authorization: Bearer your-token'`

<aside class="notice">
You must replace <code>your-token</code> and <code>your-accountid</code> with your personal API credentials.
</aside>

Never provide your RAPYD.AI login password via the API except for the endpoint `/v1/user/token` . 

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

##Credits

Every successful API request will deduct 1 credit from your RAPYD.AI credit balance.

A successful API request is defined as every request that yields a successful result object.

Errors, rejects or timeouts will not affect your credits balance. 

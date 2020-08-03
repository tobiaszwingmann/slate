# Computer Vision

Computer Vision enables machines to "see" images and recognize objects, entities and texts or extract meta information from a given image.

Currently, the Computer Vision AI services are only available through the provider Google Cloud Platform (`gcp`). More providers will follow soon.

## Face Detection

Face detection identifies faces on images and analyses various characteristics such as the face expression or facial features like eyes, nose or mouth positions.

Each face detection carries a confidence score for recognizing the face itself as well as the features of the face. 

### HTTP Request

`POST /v1/vision/face`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/vision/face' \
--header 'PROVIDER: gcp' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Authorization: Bearer your-token' \
--form 'file=face_demo.png'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("PROVIDER", "gcp");
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Authorization", "Bearer your-token");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "face_demo.png");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/vision/face", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/vision/face"

payload = {}
files = [
  ('file', open('face_demo.png','rb'))
]
headers = {
  'PROVIDER': 'gcp',
  'ACCOUNT-ID': 'your-accountid',
  'Authorization': 'Bearer your-token'
}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))

```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/vision/face"

headers <- c("ACCOUNT-ID" = "your-accountid", 
             "Authorization" = "Bearer your-token",
             "PROVIDER" = "GCP")

payload <- list(file = upload_file("face_demo.png"))

response <- POST(url, add_headers(headers), body = payload)
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation.

> Example response when provider is `gcp`:

```json
{
    "meta": {
        "provider": "GCP",
        "language": ""
    },
    "result": [
        {
            "rollAngle": -0.4798591,
            "panAngle": 0.12718968,
            "tiltAngle": -1.2569677,
            "detectionConfidence": 0.94939417,
            "landmarkingConfidence": 0.80378807,
            "joyRating": 1.0,
            "sorrowRating": 0.2,
            "angerRating": 0.2,
            "surpriseRating": 0.2,
            "underExposedRating": 0.2,
            "blurredRating": 0.2,
            "headwearRating": 0.2,
            "joy": "VERY_LIKELY",
            "sorrow": "VERY_UNLIKELY",
            "anger": "VERY_UNLIKELY",
            "surprise": "VERY_UNLIKELY",
            "underExposed": "VERY_UNLIKELY",
            "blurred": "VERY_UNLIKELY",
            "headwear": "VERY_UNLIKELY",
            "boundingPoly": [
                {
                    "x": 549,
                    "y": 26
                },
                {
                    "x": 1164,
                    "y": 26
                },
                {
                    "x": 1164,
                    "y": 740
                },
                {
                    "x": 549,
                    "y": 740
                }
            ],
            "fdBoundingPoly": [
                {
                    "x": 587,
                    "y": 153
                },
                {
                    "x": 1124,
                    "y": 153
                },
                {
                    "x": 1124,
                    "y": 686
                },
                {
                    "x": 587,
                    "y": 686
                }
            ],
            "landmarks": [
                {
                    "type": "LEFT_EYE",
                    "x": 768.32544,
                    "y": 373.06293,
                    "z": 0.0013751984
                },
                {
                    "type": "RIGHT_EYE",
                    "x": 951.94446,
                    "y": 369.37823,
                    "z": 0.4714136
                },
                {
                    "type": "LEFT_OF_LEFT_EYEBROW",
                    "x": 701.52814,
                    "y": 339.7583,
                    "z": 14.543475
                },
                {
                    "type": "RIGHT_OF_LEFT_EYEBROW",
                    "x": 814.4408,
                    "y": 331.55685,
                    "z": -34.32722
                },
                {
                    "type": "LEFT_OF_RIGHT_EYEBROW",
                    "x": 903.94037,
                    "y": 327.39395,
                    "z": -33.947388
                },
                {
                    "type": "RIGHT_OF_RIGHT_EYEBROW",
                    "x": 1017.8008,
                    "y": 336.4593,
                    "z": 15.296562
                },
                {
                    "type": "MIDPOINT_BETWEEN_EYES",
                    "x": 859.9506,
                    "y": 364.55762,
                    "z": -36.450184
                },
                {
                    "type": "NOSE_TIP",
                    "x": 856.7595,
                    "y": 477.4241,
                    "z": -88.43703
                },
                {
                    "type": "UPPER_LIP",
                    "x": 858.8607,
                    "y": 536.78925,
                    "z": -47.308403
                },
                {
                    "type": "LOWER_LIP",
                    "x": 860.94543,
                    "y": 612.84033,
                    "z": -34.59475
                },
                {
                    "type": "MOUTH_LEFT",
                    "x": 763.8856,
                    "y": 559.6046,
                    "z": 2.3785026
                },
                {
                    "type": "MOUTH_RIGHT",
                    "x": 955.97986,
                    "y": 554.21515,
                    "z": 3.0310767
                },
                {
                    "type": "MOUTH_CENTER",
                    "x": 862.51575,
                    "y": 575.4721,
                    "z": -34.262444
                },
                {
                    "type": "NOSE_BOTTOM_RIGHT",
                    "x": 920.23486,
                    "y": 484.30716,
                    "z": -22.016401
                },
                {
                    "type": "NOSE_BOTTOM_LEFT",
                    "x": 797.2778,
                    "y": 486.82227,
                    "z": -22.553627
                },
                {
                    "type": "NOSE_BOTTOM_CENTER",
                    "x": 858.078,
                    "y": 504.10403,
                    "z": -48.339252
                },
                {
                    "type": "LEFT_EYE_TOP_BOUNDARY",
                    "x": 766.4023,
                    "y": 358.04807,
                    "z": -10.352289
                },
                {
                    "type": "LEFT_EYE_RIGHT_CORNER",
                    "x": 803.16595,
                    "y": 374.9589,
                    "z": -0.06131935
                },
                {
                    "type": "LEFT_EYE_BOTTOM_BOUNDARY",
                    "x": 766.3668,
                    "y": 387.02142,
                    "z": -1.8237071
                },
                {
                    "type": "LEFT_EYE_LEFT_CORNER",
                    "x": 728.4919,
                    "y": 377.98483,
                    "z": 15.790957
                },
                {
                    "type": "RIGHT_EYE_TOP_BOUNDARY",
                    "x": 953.81085,
                    "y": 352.64587,
                    "z": -9.6653805
                },
                {
                    "type": "RIGHT_EYE_RIGHT_CORNER",
                    "x": 991.34924,
                    "y": 374.1126,
                    "z": 16.405922
                },
                {
                    "type": "RIGHT_EYE_BOTTOM_BOUNDARY",
                    "x": 953.1808,
                    "y": 383.13376,
                    "z": -1.3505049
                },
                {
                    "type": "RIGHT_EYE_LEFT_CORNER",
                    "x": 913.28955,
                    "y": 371.66306,
                    "z": 0.2713766
                },
                {
                    "type": "LEFT_EYEBROW_UPPER_MIDPOINT",
                    "x": 759.5528,
                    "y": 317.5705,
                    "z": -20.760433
                },
                {
                    "type": "RIGHT_EYEBROW_UPPER_MIDPOINT",
                    "x": 961.46344,
                    "y": 313.44608,
                    "z": -19.984333
                },
                {
                    "type": "LEFT_EAR_TRAGION",
                    "x": 643.31226,
                    "y": 435.80838,
                    "z": 221.14575
                },
                {
                    "type": "RIGHT_EAR_TRAGION",
                    "x": 1066.6526,
                    "y": 425.88293,
                    "z": 223.30026
                },
                {
                    "type": "FOREHEAD_GLABELLA",
                    "x": 860.34784,
                    "y": 325.64413,
                    "z": -40.136284
                },
                {
                    "type": "CHIN_GNATHION",
                    "x": 861.9055,
                    "y": 709.1296,
                    "z": -9.581303
                },
                {
                    "type": "CHIN_LEFT_GONION",
                    "x": 688.78577,
                    "y": 595.2242,
                    "z": 148.22136
                },
                {
                    "type": "CHIN_RIGHT_GONION",
                    "x": 1029.5104,
                    "y": 582.9388,
                    "z": 149.34828
                },
                {
                    "type": "UNKNOWN_LANDMARK",
                    "x": 726.73364,
                    "y": 497.08798,
                    "z": 17.647654
                },
                {
                    "type": "UNKNOWN_LANDMARK",
                    "x": 994.6479,
                    "y": 492.37317,
                    "z": 18.335396
                }
            ]
        }
    ]
}
```

### File Properties

The request sends a file over HTTPS. 

File Properties | Description 
--------------- | ----------- 
Image File Size | Maximum file size is 7 MB
File Format | The following image types are supported:<ul><li>JPEG</li><li>PNG8</li><li>PNG24</li><li>GIF</li><li>Animated GIF (first frame only)</li><li>BMP</li><li>WEBP</li><li>RAW</li><li>ICO</li><li>PDF</li><li>TIFF</li></ul>
Image Dimensions | The recommended image size is 1600 x 1200 pixels (ca. 1.9M pixels). The larger the faces on the image the better. The distance between eyes is most important.

The response object contains many information. Please see the following links for more details:

<a href = "https://cloud.google.com/vision/docs/reference/rpc/google.cloud.vision.v1#faceannotation", target = "_blank">Face detection results from GCP</a>

## Landmark Detection

Landmark detection detects public places, tourist attractions or well-known landmarks in an image. It provides the label, the geo-coordinates, the position, and the confidence score of the detected landmark.

Object information is returned in English only.

### HTTP Request

`POST /v1/vision/landmark`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/vision/landmark' \
--header 'PROVIDER: gcp' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Authorization: Bearer your-token' \
--form 'file=landmark_demo.png'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("PROVIDER", "gcp");
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Authorization", "Bearer your-token");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "landmark_demo.png");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/vision/landmark", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/vision/landmark"

payload = {}
files = [
  ('file', open('landmark_demo.png','rb'))
]
headers = {
  'PROVIDER': 'gcp',
  'ACCOUNT-ID': 'your-accountid',
  'Authorization': 'Bearer your-token'
}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))

```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/vision/landmark"

headers <- c("ACCOUNT-ID" = "your-accountid", 
             "Authorization" = "Bearer your-token",
             "PROVIDER" = "GCP")

payload <- list(file = upload_file("landmark_demo.png"))

response <- POST(url, add_headers(headers), body = payload)
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation.

> Example response when provider is `gcp`:

```json
{
    "meta": {
        "provider": "GCP",
        "language": ""
    },
    "result": [
        {
            "description": "Palace of Fine Arts",
            "score": 0.68384635,
            "boundingPoly": [
                {
                    "x": 108,
                    "y": 102
                },
                {
                    "x": 256,
                    "y": 102
                },
                {
                    "x": 256,
                    "y": 398
                },
                {
                    "x": 108,
                    "y": 398
                }
            ],
            "locations": [
                {
                    "lng": -122.447777,
                    "lat": 37.80290085993192
                }
            ]
        }
    ]
}
```

### File Properties

The request sends a file over HTTPS. 

File Properties | Description 
--------------- | ----------- 
Image File Size | Maximum file size is 7 MB
File Format | The following image types are supported:<ul><li>JPEG</li><li>PNG8</li><li>PNG24</li><li>GIF</li><li>Animated GIF (first frame only)</li><li>BMP</li><li>WEBP</li><li>RAW</li><li>ICO</li><li>PDF</li><li>TIFF</li></ul>
Image Dimensions | The recommended image size is 640 x 480 pixels (ca. 300k pixels). Larger image sizes may not gain much in accuracy, while greatly increasing bandwidth usage and processing time.

## Object Localization

Object localization detects multiple objects in an image and provides the label, the position, and the confidence score of the detected object.

Object information is returned in English only.

### HTTP Request

`POST /v1/vision/localize`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/vision/localize' \
--header 'PROVIDER: gcp' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Authorization: Bearer your-token' \
--form 'file=localize_demo.png'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("PROVIDER", "gcp");
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Authorization", "Bearer your-token");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "localize_demo.png");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/vision/localize", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/vision/localize"

payload = {}
files = [
  ('file', open('localize_demo.png','rb'))
]
headers = {
  'PROVIDER': 'gcp',
  'ACCOUNT-ID': 'your-accountid',
  'Authorization': 'Bearer your-token'
}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))


```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/vision/localize"

headers <- c("ACCOUNT-ID" = "your-accountid", 
             "Authorization" = "Bearer your-token",
             "PROVIDER" = "GCP")

payload <- list(file = upload_file("localize_demo.png"))

response <- POST(url, add_headers(headers), body = payload)
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation.

> Example response when provider is `gcp`:

```json

```

### File Properties

The request sends a file over HTTPS. 

File Properties | Description 
--------------- | ----------- 
Image File Size | Maximum file size is 7 MB
File Format | The following image types are supported:<ul><li>JPEG</li><li>PNG8</li><li>PNG24</li><li>GIF</li><li>Animated GIF (first frame only)</li><li>BMP</li><li>WEBP</li><li>RAW</li><li>ICO</li><li>PDF</li><li>TIFF</li></ul>
Image Dimensions | The recommended image size is 640 x 480 pixels (ca. 300k pixels). Larger image sizes may not gain much in accuracy, while greatly increasing bandwidth usage and processing time.

## Text Detection

Text detection extracts text from an image using OCR (optical character recognition). 

Extracted text structures follow a strict hierarchy as follows (bottom to top level):
* Symbol -> Word -> Paragraph -> Block -> Page  

Each of these components have their own properties such as position and confidence score.

### HTTP Request

`POST /v1/vision/text`

```shell

curl --location --request POST 'https://api.rapyd.ai/v1/vision/text' \
--header 'PROVIDER: gcp' \
--header 'ACCOUNT-ID: your-accountid' \
--header 'Authorization: Bearer your-token' \
--form 'file=text_demo.jpeg'

```

```javascript

var myHeaders = new Headers();
myHeaders.append("PROVIDER", "gcp");
myHeaders.append("ACCOUNT-ID", "your-accountid");
myHeaders.append("Authorization", "Bearer your-token");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "text_demo.jpeg");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://api.rapyd.ai/v1/vision/localize", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

```

```python

import requests

url = "https://api.rapyd.ai/v1/vision/text"

payload = {}
files = [
  ('file', open('text_demo.jpeg','rb'))
]
headers = {
  'PROVIDER': 'gcp',
  'ACCOUNT-ID': 'your-accountid',
  'Authorization': 'Bearer your-token'
}

response = requests.request("POST", url, headers=headers, data = payload, files = files)

print(response.text.encode('utf8'))


```

```r

library(httr)

url <- "https://api.rapyd.ai/v1/vision/text"

headers <- c("ACCOUNT-ID" = "your-accountid", 
             "Authorization" = "Bearer your-token",
             "PROVIDER" = "GCP")

payload <- list(file = upload_file("text_demo.jpeg"))

response <- POST(url, add_headers(headers), body = payload)
result <- content(response, "parsed")

```

> Make sure to replace `your-accountid` and `your-token` with your personal credentials.

> The above command returns results in JSON representation.

> Example response when provider is `gcp`:

```json
{
    "meta": {
        "provider": "GCP",
        "language": ""
    },
    "result": [
        {
            "description": "SCHOOL\nSPEED\nLIMIT\n25\nWHEN\nCHILDREN\nARE PRESENT\n",
            "boundingPoly": [
                {
                    "x": 596,
                    "y": 387
                },
                {
                    "x": 904,
                    "y": 387
                },
                {
                    "x": 904,
                    "y": 971
                },
                {
                    "x": 596,
                    "y": 971
                }
            ]
        },
        {
            "description": "SCHOOL",
            "boundingPoly": [
                {
                    "x": 596,
                    "y": 389
                },
                {
                    "x": 904,
                    "y": 387
                },
                {
                    "x": 904,
                    "y": 456
                },
                {
                    "x": 596,
                    "y": 458
                }
            ]
        },
        {
            "description": "SPEED",
            "boundingPoly": [
                {
                    "x": 612,
                    "y": 522
                },
                {
                    "x": 877,
                    "y": 520
                },
                {
                    "x": 877,
                    "y": 575
                },
                {
                    "x": 612,
                    "y": 577
                }
            ]
        },
        {
            "description": "LIMIT",
            "boundingPoly": [
                {
                    "x": 634,
                    "y": 604
                },
                {
                    "x": 849,
                    "y": 604
                },
                {
                    "x": 849,
                    "y": 659
                },
                {
                    "x": 634,
                    "y": 659
                }
            ]
        },
        {
            "description": "25",
            "boundingPoly": [
                {
                    "x": 608,
                    "y": 684
                },
                {
                    "x": 867,
                    "y": 684
                },
                {
                    "x": 867,
                    "y": 827
                },
                {
                    "x": 608,
                    "y": 827
                }
            ]
        },
        {
            "description": "WHEN",
            "boundingPoly": [
                {
                    "x": 685,
                    "y": 870
                },
                {
                    "x": 784,
                    "y": 870
                },
                {
                    "x": 784,
                    "y": 897
                },
                {
                    "x": 685,
                    "y": 897
                }
            ]
        },
        {
            "description": "CHILDREN",
            "boundingPoly": [
                {
                    "x": 642,
                    "y": 904
                },
                {
                    "x": 827,
                    "y": 902
                },
                {
                    "x": 827,
                    "y": 933
                },
                {
                    "x": 642,
                    "y": 935
                }
            ]
        },
        {
            "description": "ARE",
            "boundingPoly": [
                {
                    "x": 596,
                    "y": 940
                },
                {
                    "x": 670,
                    "y": 941
                },
                {
                    "x": 670,
                    "y": 970
                },
                {
                    "x": 596,
                    "y": 969
                }
            ]
        },
        {
            "description": "PRESENT",
            "boundingPoly": [
                {
                    "x": 699,
                    "y": 940
                },
                {
                    "x": 871,
                    "y": 941
                },
                {
                    "x": 871,
                    "y": 971
                },
                {
                    "x": 699,
                    "y": 970
                }
            ]
        }
    ]
}
```

### File Properties

The request sends a file over HTTPS. 

File Properties | Description 
--------------- | ----------- 
Image File Size | Maximum file size is 7 MB
File Format | The following image types are supported:<ul><li>JPEG</li><li>PNG8</li><li>PNG24</li><li>GIF</li><li>Animated GIF (first frame only)</li><li>BMP</li><li>WEBP</li><li>RAW</li><li>ICO</li><li>PDF</li><li>TIFF</li></ul>
Image Dimensions | The recommended image size is 1024 x 768 pixels (ca. 786k pixels). The total image size must not exceed 75M pixels (length x width).


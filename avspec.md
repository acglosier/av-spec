---
title: AV HTTP 1.1
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="av-http-1-1">AV HTTP 1.1 v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

HTTP protocol is supported by all Arecont Vision cameras and is supported by almost all third party software systems or plug-ins that support standard IP video over HTTP. Developers would find it easy and quick to locate technical resources to help integrate Arecont cameras using HTTP protocol. Camera performance in terms of frame rate is somewhat slower via HTTP than via TFTP but is comparable to other multi-megapixel products available on the market.

Base URLs:

* <a href="http://<camera IP address>">http://<camera IP address></a>

Email: <a href="mailto:support@arecontvision.com">AV Support</a> Web: <a href="support.arecontvision.com">AV Support</a> 

<h1 id="av-http-1-1-jpeg-mjpeg">JPEG/MJPEG</h1>

Pull JPEG images individually or full MJPEG streams.

## mjpeg

<a id="opIdmjpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/mjpeg \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/mjpeg HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/mjpeg',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

fetch('http://<camera IP address>/mjpeg',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'multipart/x-mixed-replace; boundary=fbdr'
}

result = RestClient.get 'http://<camera IP address>/mjpeg',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/mjpeg', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/mjpeg");
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
        "Accept": []string{"multipart/x-mixed-replace; boundary=fbdr"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/mjpeg", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /mjpeg`

*Get an MJPEG Stream*

open a continuous mjpeg stream from the camera

<h3 id="mjpeg-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|res|query|string|false|The resolution MJPEGs you want to return|
|x0|query|integer(int32)|false|Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y0|query|integer(int32)|false|Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|x1|query|integer(int32)|false|Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y1|query|integer|false|Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|doublescan|query|integer|false|Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.|
|fps|query|integer|false|Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).|
|quality|query|integer|false|The compression quality of the jpeg image|
|ver|query|string|false|Arecont Vision cameras support both HTTP/1.0 and HTTP/1.1 protocols as defined by RFC-1945 and RFC2068, respectively. While HTTP/1.0 is simple, it closes the transmission after each image, forcing the client to incur a round trip delay; this limits the speed of image transmission when you request individual images rather than an mjpeg stream. However, HTTP/1.0 is reliable and supported by all HTTP implementations, albeit with limited speed. By default, Arecont Vision cameras are use HTTP/1.0 protocol regardless of the HTTP version used by the client.|
|channel|query|string|false|Request down-scaled images. Because you preset downscaled image settings (through the UI or the /set endpoint), this parameter does not require size information.|
|sd|query|string|false|Use to request images/video recorded on the SD card. `playback` plays back video in real time; `download` lets you stream video as fast as possible.         |

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|
|ver|HTTP/1.0|
|ver|HTTP/1.1|
|channel|scaled|
|sd|on|
|sd|off|

> Example responses

> 200 Response

<h3 id="mjpeg-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream|string|

<aside class="success">
This operation does not require authentication
</aside>

## jpeg

<a id="opIdjpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/image \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/image HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/image',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

fetch('http://<camera IP address>/image',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'multipart/x-mixed-replace; boundary=fbdr'
}

result = RestClient.get 'http://<camera IP address>/image',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/image', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/image");
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
        "Accept": []string{"multipart/x-mixed-replace; boundary=fbdr"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/image", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /image`

*Get a JPEG Frame*

Pull JPEG frames individually from the camera.

<h3 id="jpeg-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|res|query|string|false|The resolution MJPEGs you want to return|
|x0|query|integer(int32)|false|Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y0|query|integer(int32)|false|Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|x1|query|integer(int32)|false|Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y1|query|integer|false|Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|doublescan|query|integer|false|Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.|
|quality|query|integer|false|The compression quality of the jpeg image|
|ID|query|integer|false|Ignored by the camera, but you might set random IDs to force browsers to refresh a frame. Some browsers might display a cached image if a previous URL is reused without modifying the ID field|

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|

> Example responses

> 200 Response

<h3 id="jpeg-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an image|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-h-264-streaming">h.264 Streaming</h1>

Pull h.264 quality images individually or full video stream.

## get__h264

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/h264 \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/h264 HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/h264',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

fetch('http://<camera IP address>/h264',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'multipart/x-mixed-replace; boundary=fbdr'
}

result = RestClient.get 'http://<camera IP address>/h264',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/h264', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/h264");
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
        "Accept": []string{"multipart/x-mixed-replace; boundary=fbdr"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/h264", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /h264`

*Pull an H.264 Frame*

Pull H.264 frames from cameras. The first frame or the stream is always an IDR (Intra) frame followed by multiple P (Inter) frames. The default number of P-frames is 50, and can be modified via register 3:21 using one of the following HTTP commands —

http://camera_ip/set?keyframeinterval=(0..100)
http://camera_ip/setreg?page=3&reg=21&val=(number of P-frames)

You can get your current P-frame setting from http://camera_ip/getreg?page=3&reg=21 

<h3 id="get__h264-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|res|query|string|false|The resolution MJPEGs you want to return|
|x0|query|integer(int32)|false|Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y0|query|integer(int32)|false|Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|x1|query|integer(int32)|false|Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y1|query|integer|false|Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|qp|query|string|false|The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. |
|doublescan|query|integer|false|Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.|
|ssn|query|integer|false|Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)|
|iframe|query|integer|false|Effectively a boolean (0 or 1). Set to 1 will force the camera to return an Intra frame (I-frame) with a corresponding SPS and PPS as an IDR slice, so that the stream is decodable from this point. When opening a new stream (as when changing the image size and/or frame rate) the I-frame is sent automatically regardless of the input value of `iframe`. To reduce the stream size, reduce the frequency of `iframe = 1` in requests. You can set the P-frames for any of the streams sent by the camera is set using|
|bitrate|query|integer|false|Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.|
|intra_period|query|integer|false|Valid when requesting a non-zero bitrate and periodically requesting `iframe=1`. Specifies the intra-frame period during which you are sending requests with `iframe=1`. If you do not specify `intra_period`, bitrate control will not function correctly unless the actual period of sending iframe=1 requests is the same as the number of P-frames specified in register 3:21 of the camera via one of the commands described above. If you do not request `iframe=1` at all, then the `intra_period` parameter is not required and bitrate control will rely on the number of P-frames set in register 3:21. |

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|

> Example responses

> 200 Response

<h3 id="get__h264-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream according to the parameters in your request.

Each frame sent by the camera may contain multiple zero bytes at the end. A Unit Delimiter (UD) is not used. Although this does not contradict the ITU-T H.264 standard (ISO/IEC 14496-10), some decoders may delay decoded frames by one due to the absence of the UD. If this presents a problem, replace all zero bytes at the end with the UD, a sequence of the following five bytes — `0x00 0x00 0x01 0x09 0x10`. The number of zero bytes at the end of a frame may be significant (up to a few hundred bytes). Replacing them with the UD will also reduce the stream size|string|

<aside class="success">
This operation does not require authentication
</aside>

## get__h264stream

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/h264stream \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/h264stream HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/h264stream',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

fetch('http://<camera IP address>/h264stream',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'multipart/x-mixed-replace; boundary=fbdr'
}

result = RestClient.get 'http://<camera IP address>/h264stream',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/h264stream', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/h264stream");
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
        "Accept": []string{"multipart/x-mixed-replace; boundary=fbdr"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/h264stream", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /h264stream`

*Pull an H.264 Video Stream*

Pull a continuous H.264 video stream with boundary-separated frames.

<h3 id="get__h264stream-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|res|query|string|false|The resolution MJPEGs you want to return|
|x0|query|integer(int32)|false|Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y0|query|integer(int32)|false|Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|x1|query|integer(int32)|false|Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|y1|query|integer|false|Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.|
|qp|query|string|false|The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. |
|doublescan|query|integer|false|Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.|
|ssn|query|integer|false|Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)|
|bitrate|query|integer|false|Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.|
|fps|query|integer|false|Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).|
|ver|query|string|false|Arecont Vision cameras support both HTTP/1.0 and HTTP/1.1 protocols as defined by RFC-1945 and RFC2068, respectively. While HTTP/1.0 is simple, it closes the transmission after each image, forcing the client to incur a round trip delay; this limits the speed of image transmission when you request individual images rather than an mjpeg stream. However, HTTP/1.0 is reliable and supported by all HTTP implementations, albeit with limited speed. By default, Arecont Vision cameras are use HTTP/1.0 protocol regardless of the HTTP version used by the client.|
|channel|query|string|false|Request down-scaled images. Because you preset downscaled image settings (through the UI or the /set endpoint), this parameter does not require size information.|
|sd|query|string|false|Use to request images/video recorded on the SD card. `playback` plays back video in real time; `download` lets you stream video as fast as possible.         |

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|
|ver|HTTP/1.0|
|ver|HTTP/1.1|
|channel|scaled|
|sd|on|
|sd|off|

> Example responses

> 200 Response

<h3 id="get__h264stream-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream according to the parameters in your request.|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-configuration">Configuration</h1>

Get and set camera configuration

## get__get{channel}

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/get{channel} \
  -H 'Accept: text/plain'

```

```http
GET http://<camera IP address>/get{channel} HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/get{channel}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'text/plain'

};

fetch('http://<camera IP address>/get{channel}',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.get 'http://<camera IP address>/get{channel}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('http://<camera IP address>/get{channel}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/get{channel}");
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
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/get{channel}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /get{channel}`

*Get Multisensor Camera Settings*

Return settings for a single channel in a multi-sensor camera. In general, you should use only one query parameter at a time.

<h3 id="get__get{channel}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|channel|path|integer|false|The ID of the channel you want to return information for.|

> Example responses

> 200 Response

<h3 id="get__get{channel}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters specified in the query.|string|

<aside class="success">
This operation does not require authentication
</aside>

## get__get

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/get \
  -H 'Accept: text/plain'

```

```http
GET http://<camera IP address>/get HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/get',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'text/plain'

};

fetch('http://<camera IP address>/get',
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

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.get 'http://<camera IP address>/get',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('http://<camera IP address>/get', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/get");
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
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://<camera IP address>/get", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /get`

*Get Camera Settings*

Return settings from the camera. In general, you should use only one of the following parameters at a time.

<h3 id="get__get-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|day_binning|query|string|false|Enables or disables day binning mode for supported cameras.|
|night_binning|query|string|false|Enables or disables day binning mode for supported cameras.|
|daynight|query|string|false|Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.|
|upscaling|query|string|false|Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. |
|channelenable|query|string|false|The channels you want to enable.|
|brightness|query|integer|false|Sets brightness for the camera or channel.|
|sharpness|query|integer|false|Sets sharpness for the camera or channel.|
|saturation|query|integer|false|Sets color saturation for the camera or channel.|
|blue|query|integer|false|Sets blue balance for the camera or channel.|
|red|query|integer|false|Sets red balance for the camera or channel.|
|illum|query|string|false|Sets illumination for the camera or channel.|
|freq|query|integer|false|Mains frequency in Hz, used for indoor lighting compensation.|
|lowlight|query|string|false|Exposure (low light) mode.|
|shortexposures|query|integer|false|Shutter time in high-speed exposure mode, set in milliseconds.|
|autoexp|query|string|false|Auto exposure mode|
|exposure|query|string|false|Auto exposure mode|
|expwndleft|query|integer|false|The exposure window for the sensor.|
|expwndtop|query|integer|false|The exposure window for the sensor.|
|expwndwidth|query|integer|false|The exposure window for the sensor.|
|expwndheight|query|integer|false|The exposure window for the sensor.|
|sensorleft|query|integer|false|Sensor cropping, from the left.|
|sensortop|query|integer|false|Sensor cropping from the top.|
|sensorwidth|query|integer|false|Sensor cropping based on width. Both sides are equally cropped by half the value.|
|sensorheight|query|integer|false|Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.|
|imgleft|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgtop|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgwidth|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgheight|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgquality|query|integer|false|Image setting, used as the implcit perameter list in img.jpg image requests.|
|imgres|query|string|false|Image setting, used as the implcit perameter list in img.jpg image requests.|
|mac|query|string|false|Returns the MAC address of the camera.|
|model|query|string|false|Returns the camera's model number. `fullname` returns the camera's base model number and feature leter; `releasename` returns the manufacturer model number and feature letter — the real model number.|
|fwversion|query|boolean|false|Returns the camera's firmware version.|
|procversion|query|boolean|false|Returns the image processor version.|
|netversion|query|boolean|false|Returns the network processor version.|
|revision|query|boolean|false|Returns the PCB version.|
|kneepoint|query|integer|false|Custom mode setting|
|analoggain|query|integer|false|Custom mode setting|
|maxkneegain|query|integer|false|Custom mode setting|
|maxexptime|query|integer|false|Custom mode setting|
|maxdigitalgain|query|integer|false|Custom mode setting|
|webserverport|query|integer|false|The port for the camera's web server.|
|admin|query|any|false|Get or set the admin-level password.|
|viewer|query|any|false|Get or set the viewer-level password.|
|maxsensorwidth|query|integer|false|Get the maximum sensor width.|
|maxsensorheight|query|integer|false|Get the maximum sensor height.|
|mdmode|query|string|false|Get or set motion alarm settings|
|motiondetect|query|string|false|Get or set motion detection settings|
|mdtotalzones|query|integer|false|Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.|
|auxin|query|boolean|false|Get auxin.|
|auxout|query|string|false|Get or set auxiliary audio out.|
|cropping|query|string|false|Get or set flexible cropping.|
|1080p_mode|query|string|false|Get or set 1080p mode — used in 10xx5 models only.|
|pmask|query|string|false|Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.|
|focus|query|any|false|Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.|
|zoom|query|any|false|Set zoom moving steps.|
|focusleft|query|integer|false|none|
|focustop|query|integer|false|none|
|focusright|query|integer|false|none|
|focusbottom|query|integer|false|none|
|focuswindow|query|array[integer]|false|Get or set the four sides of the focus window.|
|af_dn|query|string|false|Get or set autofocus after enabling the day-night switch.|
|af_zoom|query|string|false|Get or set autofocus after zoom.|
|casino_mode|query|string|false|Get or set casino mode (1080p models only)|
|netopt|query|integer|false|Get or set network related settings. Integers correspond to the bits you want to enable or disable.|
|multicast_rec|query|string|false|Get or set the multicast reception setting.|
|en_multicast|query|integer|false|Enable multicast announcement.|
|fps|query|integer|false|Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).|
|qp|query|string|false|The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. |
|qp_max|query|string|false|Get or set the maximum allowed QP value — i.e. the lowest allowable quality.|
|ratelimit_mode|query|boolean|false|Get or set variable bitrate limit mode.|
|ratelimit|query|string|false|Get or set a variable bitrate limit.|
|bitrate|query|integer|false|Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.|
|keyframeinterval|query|integer|false|Get or set the key frame interval.|
|rtspport|query|integer|false|Get or set the RTSP port.|
|spacialfilter|query|integer|false|Get or set the low-light noise filter.|
|name|query|string|false|Get or set the camera name.|
|mtu|query|integer|false|Get or set the MTU size.|
|ip|query|string|false|Get or set the camera's IP address.|
|subnetmask|query|string|false|Get or set the camera's subnet mask.|
|gateway|query|string|false|Get or set the camera's default gateway.|
|eth_negotiation|query|string|false|When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.|
|features|query|integer|false|Returns an integer for enabled features. Integers that are not returned are not enabled.|
|audioinput|query|string|false|The source of audio input.|
|linein_volume|query|integer|false|Volume of line-in audio.|
|mic_boost|query|integer|false|Volume of microphone-in audio.|
|piris|query|string|false|Enable/disable P-iris|
|pirispos|query|integer|false|The position P-iris closes to|
|ir|query|string|false|Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.|
|make|query|string|false|Get the make of the camera.|
|white_balance|query|string|false|White balance control.|
|wbwndctrl|query|string|false|White balance window control.|
|wbwndleft|query|integer|false|White balance window left start value. Maximum values depend on your sensor size.|
|wbwndtop|query|integer|false|White balance window top start value. Maximum values depend on your sensor size.|
|wbwndwidth|query|integer|false|White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.|
|wbwndheight|query|integer|false|White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.|
|ntpserver_ip|query|string|false|NTP server address.|
|enclosure|query|string|false|Returns the camera's model name. Provide `code` to return the model type number.|
|gamma|query|integer|false|Gamma for single sensor and Surroundvideo1 cameras.|
|gamma2|query|integer|false|Gamma for the second sensor in dual sensor cameras.|
|bandwidthsaving|query|string|false|Bandwidth saving mode settings.|
|lowpower|query|string|false|Low power mode settings.|
|motion_compensation|query|string|false|Motion compensation settings.|
|adjustable_ir|query|string|false|Adjustable IR light settings.|
|irwidepos|query|integer|false|The adjustable intensity of wide IR lights.|
|irtelpos|query|integer|false|The adjustable intensity of tele IR lights.|
|irpos_chan1|query|integer|false|Controls IR intensity on LED board 1 of FLEX model cameras.|
|irpos_chan2|query|integer|false|Controls IR intensity on LED board 2 of FLEX model cameras.|
|snapstream|query|string|false|Snapstream on/off setting.|
|sensorcount|query|integer|false|Returns the sensor count. Use the sensor count to determine the channels you want to get or set when |
|scaling|query|string|false|Enable or disable down-scaling.|
|sd_codec|query|string|false|The codec used for video recorded to the camera's SD card.|
|sd_fps|query|integer|false|The framerate for video recorded to the camera's SD card.|
|sd_recording|query|string|false|Enables/disables continuous local recording.|
|sd_networkfail|query|string|false|Enables/disables local recording on network failure events.|
|sd_motionalarm|query|string|false|Enables/disables local recording on motion events.|
|sd_ioalarm|query|string|false|Enables/disables local recording on I/O alarm events.|
|sd_stampspan|query|boolean|false|Returns timestamps for recorded video.|
|sd_imgleft|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgright|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgtop|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgbottom|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgres|query|string|false|Determine whether to record SD images at full or half resolution.|
|qos_enabled|query|integer|false|Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. |
|qos_video|query|integer|false|In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.|
|qos_default|query|integer|false|In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.|
|ipv6enabled|query|boolean|false|Enable/disable IPv6.|
|ipv6address|query|string(ipv6)|false|The IPv6 address for the camera.|
|ipv6prefixlen|query|string|false|The IPv6 prefix.|
|ipv6dhcp|query|string|false|Enable/disable DHCP for IPv6.|
|ipv6addresstype|query|string|false|IPv6 address type. Use `manual` to override a DHCP-set address.|
|ipv6acceptrouters|query|boolean|false|IPv6 accept routers setting.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|day_binning|on|
|day_binning|off|
|night_binning|on|
|night_binning|off|
|daynight|auto|
|daynight|day|
|daynight|night|
|daynight|dual|
|upscaling|on|
|upscaling|off|
|illum|auto|
|illum|indoor|
|illum|outdoor|
|illum|mlx|
|lowlight|highspeed|
|lowlight|speed|
|lowlight|balance|
|lowlight|quality|
|lowlight|moonlight|
|autoexp|on|
|autoexp|off|
|exposure|auto|
|exposure|on|
|exposure|off|
|imgres|full|
|imgres|half|
|model|fullname|
|model|releasename|
|model|lpn|
|model|internal|
|mdmode|on|
|mdmode|off|
|motiondetect|on|
|motiondetect|off|
|auxout|on|
|auxout|off|
|cropping|on|
|cropping|off|
|1080p_mode|on|
|1080p_mode|off|
|pmask|on|
|pmask|off|
|af_dn|on|
|af_dn|off|
|af_zoom|on|
|af_zoom|off|
|casino_mode|on|
|casino_mode|off|
|multicast_rec|on|
|multicast_rec|off|
|eth_negotiation|auto|
|eth_negotiation|fixed|
|audioinput|mic|
|audioinput|linein|
|piris|on|
|piris|off|
|ir|on|
|ir|alwayson|
|ir|off|
|white_balance|on|
|white_balance|off|
|wbwndctrl|on|
|wbwndctrl|off|
|enclosure|code|
|bandwidthsaving|on|
|bandwidthsaving|off|
|lowpower|on|
|lowpower|off|
|motion_compensation|on|
|motion_compensation|off|
|adjustable_ir|adaptive|
|adjustable_ir|preset|
|adjustable_ir|disabled|
|snapstream|on|
|snapstream|off|
|scaling|on|
|scaling|off|
|sd_codec|jpeg|
|sd_codec|h264|
|sd_recording|on|
|sd_recording|off|
|sd_networkfail|on|
|sd_networkfail|off|
|sd_motionalarm|on|
|sd_motionalarm|off|
|sd_ioalarm|on|
|sd_ioalarm|off|
|sd_imgres|full|
|sd_imgres|half|
|ipv6dhcp|on|
|ipv6dhcp|off|
|ipv6addresstype|dhcp|
|ipv6addresstype|manual|

> Example responses

> 200 Response

<h3 id="get__get-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters specified in the query.|Inline|

<h3 id="get__get-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## post__set

> Code samples

```shell
# You can also use wget
curl -X POST http://<camera IP address>/set \
  -H 'Accept: text/plain'

```

```http
POST http://<camera IP address>/set HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/set',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'text/plain'

};

fetch('http://<camera IP address>/set',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.post 'http://<camera IP address>/set',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.post('http://<camera IP address>/set', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/set");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
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
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://<camera IP address>/set", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /set`

*Set Camera Settings*

Set camera settings.

<h3 id="post__set-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|day_binning|query|string|false|Enables or disables day binning mode for supported cameras.|
|night_binning|query|string|false|Enables or disables day binning mode for supported cameras.|
|daynight|query|string|false|Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.|
|upscaling|query|string|false|Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. |
|channelenable|query|string|false|The channels you want to enable.|
|rotate|query|integer|false|Sets the rotation of the image in 90 degree increments. 90 and 270 degree rotations are available in newer models; get features to determine whether or not your camera supports these values.|
|brightness|query|integer|false|Sets brightness for the camera or channel.|
|sharpness|query|integer|false|Sets sharpness for the camera or channel.|
|saturation|query|integer|false|Sets color saturation for the camera or channel.|
|blue|query|integer|false|Sets blue balance for the camera or channel.|
|red|query|integer|false|Sets red balance for the camera or channel.|
|illum|query|string|false|Sets illumination for the camera or channel.|
|freq|query|integer|false|Mains frequency in Hz, used for indoor lighting compensation.|
|lowlight|query|string|false|Exposure (low light) mode.|
|shortexposures|query|integer|false|Shutter time in high-speed exposure mode, set in milliseconds.|
|autoexp|query|string|false|Auto exposure mode|
|exposure|query|string|false|Auto exposure mode|
|expwndleft|query|integer|false|The exposure window for the sensor.|
|expwndtop|query|integer|false|The exposure window for the sensor.|
|expwndwidth|query|integer|false|The exposure window for the sensor.|
|expwndheight|query|integer|false|The exposure window for the sensor.|
|sensorleft|query|integer|false|Sensor cropping, from the left.|
|sensortop|query|integer|false|Sensor cropping from the top.|
|sensorwidth|query|integer|false|Sensor cropping based on width. Both sides are equally cropped by half the value.|
|sensorheight|query|integer|false|Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.|
|imgleft|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgtop|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgwidth|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgheight|query|integer|false|Image setting, used as the implcit perameter in img.jpg image requests.|
|imgquality|query|integer|false|Image setting, used as the implcit perameter list in img.jpg image requests.|
|imgres|query|string|false|Image setting, used as the implcit perameter list in img.jpg image requests.|
|params|query|string|false|Perform basic camera actions|
|kneepoint|query|integer|false|Custom mode setting|
|analoggain|query|integer|false|Custom mode setting|
|maxkneegain|query|integer|false|Custom mode setting|
|maxexptime|query|integer|false|Custom mode setting|
|maxdigitalgain|query|integer|false|Custom mode setting|
|webserverport|query|integer|false|The port for the camera's web server.|
|admin|query|any|false|Get or set the admin-level password.|
|viewer|query|any|false|Get or set the viewer-level password.|
|auxout|query|string|false|Get or set auxiliary audio out.|
|cropping|query|string|false|Get or set flexible cropping.|
|1080p_mode|query|string|false|Get or set 1080p mode — used in 10xx5 models only.|
|pmask|query|string|false|Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.|
|focus|query|any|false|Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.|
|zoom|query|any|false|Set zoom moving steps.|
|focusleft|query|integer|false|none|
|focustop|query|integer|false|none|
|focusright|query|integer|false|none|
|focusbottom|query|integer|false|none|
|focuswindow|query|array[integer]|false|Get or set the four sides of the focus window.|
|af_dn|query|string|false|Get or set autofocus after enabling the day-night switch.|
|af_zoom|query|string|false|Get or set autofocus after zoom.|
|casino_mode|query|string|false|Get or set casino mode (1080p models only)|
|netopt|query|integer|false|Get or set network related settings. Integers correspond to the bits you want to enable or disable.|
|multicast_rec|query|string|false|Get or set the multicast reception setting.|
|en_multicast|query|integer|false|Enable multicast announcement.|
|fps|query|integer|false|Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).|
|qp|query|string|false|The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. |
|qp_max|query|string|false|Get or set the maximum allowed QP value — i.e. the lowest allowable quality.|
|ratelimit_mode|query|boolean|false|Get or set variable bitrate limit mode.|
|ratelimit|query|string|false|Get or set a variable bitrate limit.|
|bitrate|query|integer|false|Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.|
|keyframeinterval|query|integer|false|Get or set the key frame interval.|
|keyframe|query|boolean|false|Get or set key frame setting. Yields an I-frame on the next available frame.|
|rtspport|query|integer|false|Get or set the RTSP port.|
|spacialfilter|query|integer|false|Get or set the low-light noise filter.|
|name|query|string|false|Get or set the camera name.|
|mtu|query|integer|false|Get or set the MTU size.|
|ip|query|string|false|Get or set the camera's IP address.|
|subnetmask|query|string|false|Get or set the camera's subnet mask.|
|gateway|query|string|false|Get or set the camera's default gateway.|
|eth_negotiation|query|string|false|When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.|
|audioinput|query|string|false|The source of audio input.|
|linein_volume|query|integer|false|Volume of line-in audio.|
|mic_boost|query|integer|false|Volume of microphone-in audio.|
|piris|query|string|false|Enable/disable P-iris|
|pirispos|query|integer|false|The position P-iris closes to|
|ir|query|string|false|Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.|
|white_balance|query|string|false|White balance control.|
|wbwndctrl|query|string|false|White balance window control.|
|wbwndleft|query|integer|false|White balance window left start value. Maximum values depend on your sensor size.|
|wbwndtop|query|integer|false|White balance window top start value. Maximum values depend on your sensor size.|
|wbwndwidth|query|integer|false|White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.|
|wbwndheight|query|integer|false|White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.|
|ntpserver_ip|query|string|false|NTP server address.|
|gamma|query|integer|false|Gamma for single sensor and Surroundvideo1 cameras.|
|gamma2|query|integer|false|Gamma for the second sensor in dual sensor cameras.|
|bandwidthsaving|query|string|false|Bandwidth saving mode settings.|
|lowpower|query|string|false|Low power mode settings.|
|motion_compensation|query|string|false|Motion compensation settings.|
|adjustable_ir|query|string|false|Adjustable IR light settings.|
|irwidepos|query|integer|false|The adjustable intensity of wide IR lights.|
|irtelpos|query|integer|false|The adjustable intensity of tele IR lights.|
|irpos_chan1|query|integer|false|Controls IR intensity on LED board 1 of FLEX model cameras.|
|irpos_chan2|query|integer|false|Controls IR intensity on LED board 2 of FLEX model cameras.|
|snapstream|query|string|false|Snapstream on/off setting.|
|scaling|query|string|false|Enable or disable down-scaling.|
|sd_codec|query|string|false|The codec used for video recorded to the camera's SD card.|
|sd_fps|query|integer|false|The framerate for video recorded to the camera's SD card.|
|sd_recording|query|string|false|Enables/disables continuous local recording.|
|sd_networkfail|query|string|false|Enables/disables local recording on network failure events.|
|sd_motionalarm|query|string|false|Enables/disables local recording on motion events.|
|sd_ioalarm|query|string|false|Enables/disables local recording on I/O alarm events.|
|sd_stampspan|query|boolean|false|Returns timestamps for recorded video.|
|sd_playbackstamp|query|string|false|Playback video for the recorded timestamps - `beginningTime, endingTime`. If you don't specify the `endTime` or set `0` for the end time, the camera will play until the end of recorded video.|
|sd_imgleft|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgright|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgtop|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgbottom|query|integer|false|Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.|
|sd_imgres|query|string|false|Determine whether to record SD images at full or half resolution.|
|qos_enabled|query|integer|false|Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. |
|qos_video|query|integer|false|In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.|
|qos_default|query|integer|false|In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.|
|ipv6enabled|query|boolean|false|Enable/disable IPv6.|
|ipv6address|query|string(ipv6)|false|The IPv6 address for the camera.|
|ipv6prefixlen|query|string|false|The IPv6 prefix.|
|ipv6dhcp|query|string|false|Enable/disable DHCP for IPv6.|
|ipv6addresstype|query|string|false|IPv6 address type. Use `manual` to override a DHCP-set address.|
|ipv6acceptrouters|query|boolean|false|IPv6 accept routers setting.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|day_binning|on|
|day_binning|off|
|night_binning|on|
|night_binning|off|
|daynight|auto|
|daynight|day|
|daynight|night|
|daynight|dual|
|upscaling|on|
|upscaling|off|
|illum|auto|
|illum|indoor|
|illum|outdoor|
|illum|mlx|
|lowlight|highspeed|
|lowlight|speed|
|lowlight|balance|
|lowlight|quality|
|lowlight|moonlight|
|autoexp|on|
|autoexp|off|
|exposure|auto|
|exposure|on|
|exposure|off|
|imgres|full|
|imgres|half|
|params|save|
|params|factory|
|params|reboot|
|auxout|on|
|auxout|off|
|cropping|on|
|cropping|off|
|1080p_mode|on|
|1080p_mode|off|
|pmask|on|
|pmask|off|
|af_dn|on|
|af_dn|off|
|af_zoom|on|
|af_zoom|off|
|casino_mode|on|
|casino_mode|off|
|multicast_rec|on|
|multicast_rec|off|
|eth_negotiation|auto|
|eth_negotiation|fixed|
|audioinput|mic|
|audioinput|linein|
|piris|on|
|piris|off|
|ir|on|
|ir|alwayson|
|ir|off|
|white_balance|on|
|white_balance|off|
|wbwndctrl|on|
|wbwndctrl|off|
|bandwidthsaving|on|
|bandwidthsaving|off|
|lowpower|on|
|lowpower|off|
|motion_compensation|on|
|motion_compensation|off|
|adjustable_ir|adaptive|
|adjustable_ir|preset|
|adjustable_ir|disabled|
|snapstream|on|
|snapstream|off|
|scaling|on|
|scaling|off|
|sd_codec|jpeg|
|sd_codec|h264|
|sd_recording|on|
|sd_recording|off|
|sd_networkfail|on|
|sd_networkfail|off|
|sd_motionalarm|on|
|sd_motionalarm|off|
|sd_ioalarm|on|
|sd_ioalarm|off|
|sd_playbackstamp|on|
|sd_playbackstamp|off|
|sd_imgres|full|
|sd_imgres|half|
|ipv6dhcp|on|
|ipv6dhcp|off|
|ipv6addresstype|dhcp|
|ipv6addresstype|manual|

> Example responses

> 200 Response

<h3 id="post__set-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters set in the request.|Inline|

<h3 id="post__set-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-audio">Audio</h1>

Get and set audio configuration

## post__g711

> Code samples

```shell
# You can also use wget
curl -X POST http://<camera IP address>/g711 \
  -H 'Accept: text/plain'

```

```http
POST http://<camera IP address>/g711 HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/g711',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'text/plain'

};

fetch('http://<camera IP address>/g711',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.post 'http://<camera IP address>/g711',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.post('http://<camera IP address>/g711', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/g711");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
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
        "Accept": []string{"text/plain"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://<camera IP address>/g711", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /g711`

*Transmit Audio to Line Out*

Transmits continuous G.711 Audio to Arecont Vision cameras.

> Example responses

> 200 Response

<h3 id="post__g711-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an audio stream.|string|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocSipv6dhcp">ipv6dhcp</h2>

<a id="schemaipv6dhcp"></a>

```json
null

```

*Enable/disable DHCP for IPv6.
*

### Properties

*None*

<h2 id="tocSipv6addresstype">ipv6addresstype</h2>

<a id="schemaipv6addresstype"></a>

```json
null

```

*IPv6 address type. Use `manual` to override a DHCP-set address.
*

### Properties

*None*

<h2 id="tocSipv6acceptrouters">ipv6acceptrouters</h2>

<a id="schemaipv6acceptrouters"></a>

```json
null

```

*IPv6 accept routers setting.
*

### Properties

*None*

<h2 id="tocSipv6enabled">ipv6enabled</h2>

<a id="schemaipv6enabled"></a>

```json
null

```

*Enable/disable IPv6.
*

### Properties

*None*

<h2 id="tocSipv6address">ipv6address</h2>

<a id="schemaipv6address"></a>

```json
null

```

*The IPv6 address for the camera.
*

### Properties

*None*

<h2 id="tocSipv6prefixlen">ipv6prefixlen</h2>

<a id="schemaipv6prefixlen"></a>

```json
null

```

*The IPv6 prefix.
*

### Properties

*None*

<h2 id="tocSscaling">scaling</h2>

<a id="schemascaling"></a>

```json
null

```

*Enable or disable down-scaling.*

### Properties

*None*

<h2 id="tocSscaling_size">scaling_size</h2>

<a id="schemascaling_size"></a>

```json
null

```

*Set scaling size as `width, height`. Width ranges from 128 to 1280; height ranges from 96 to 720.*

### Properties

*None*

<h2 id="tocSqos_enabled">qos_enabled</h2>

<a id="schemaqos_enabled"></a>

```json
null

```

*Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. 

Enable or disable quality of service (QOS).
*

### Properties

*None*

<h2 id="tocSqos_video">qos_video</h2>

<a id="schemaqos_video"></a>

```json
null

```

*In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.
*

### Properties

*None*

<h2 id="tocSqos_default">qos_default</h2>

<a id="schemaqos_default"></a>

```json
null

```

*In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.
*

### Properties

*None*

<h2 id="tocSsd_codec">sd_codec</h2>

<a id="schemasd_codec"></a>

```json
null

```

*The codec used for video recorded to the camera's SD card.*

### Properties

*None*

<h2 id="tocSsd_fps">sd_fps</h2>

<a id="schemasd_fps"></a>

```json
null

```

*The framerate for video recorded to the camera's SD card.*

### Properties

*None*

<h2 id="tocSsd_playback_fps">sd_playback_fps</h2>

<a id="schemasd_playback_fps"></a>

```json
null

```

*Used to playback video from SD cards in 4k models. For 4K models, you do not “download” video from the SD card. Instead, you dynamically controll the playback framerate.*

### Properties

*None*

<h2 id="tocSsd_recording">sd_recording</h2>

<a id="schemasd_recording"></a>

```json
null

```

*Enables/disables continuous local recording.*

### Properties

*None*

<h2 id="tocSsd_networkfail">sd_networkfail</h2>

<a id="schemasd_networkfail"></a>

```json
null

```

*Enables/disables local recording on network failure events.*

### Properties

*None*

<h2 id="tocSsd_motionalarm">sd_motionalarm</h2>

<a id="schemasd_motionalarm"></a>

```json
null

```

*Enables/disables local recording on motion events.*

### Properties

*None*

<h2 id="tocSsd_ioalarm">sd_ioalarm</h2>

<a id="schemasd_ioalarm"></a>

```json
null

```

*Enables/disables local recording on I/O alarm events.*

### Properties

*None*

<h2 id="tocSsd_stampspan">sd_stampspan</h2>

<a id="schemasd_stampspan"></a>

```json
null

```

*Returns timestamps for recorded video.*

### Properties

*None*

<h2 id="tocSsd_playbackstamp">sd_playbackstamp</h2>

<a id="schemasd_playbackstamp"></a>

```json
null

```

*Playback video for the recorded timestamps - `beginningTime, endingTime`. If you don't specify the `endTime` or set `0` for the end time, the camera will play until the end of recorded video.*

### Properties

*None*

<h2 id="tocSsd">sd</h2>

<a id="schemasd"></a>

```json
null

```

*Request images/video recorded on the SD card (local recording). `playback` plays back video in real time; `download` lets you stream video as fast as possible. Do not provide other parameters when reqeusting video recorded locally. 
*

### Properties

*None*

<h2 id="tocSsd_imgleft">sd_imgleft</h2>

<a id="schemasd_imgleft"></a>

```json
null

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

*None*

<h2 id="tocSsd_imgright">sd_imgright</h2>

<a id="schemasd_imgright"></a>

```json
null

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

*None*

<h2 id="tocSsd_imgtop">sd_imgtop</h2>

<a id="schemasd_imgtop"></a>

```json
null

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

*None*

<h2 id="tocSsd_imgbottom">sd_imgbottom</h2>

<a id="schemasd_imgbottom"></a>

```json
null

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

*None*

<h2 id="tocSsd_imgres">sd_imgres</h2>

<a id="schemasd_imgres"></a>

```json
null

```

*Determine whether to record SD images at full or half resolution.*

### Properties

*None*

<h2 id="tocSirpos_chan1">irpos_chan1</h2>

<a id="schemairpos_chan1"></a>

```json
null

```

*Controls IR intensity on LED board 1 of FLEX model cameras.
*

### Properties

*None*

<h2 id="tocSirpos_chan2">irpos_chan2</h2>

<a id="schemairpos_chan2"></a>

```json
null

```

*Controls IR intensity on LED board 2 of FLEX model cameras.
*

### Properties

*None*

<h2 id="tocSkneepoint">kneepoint</h2>

<a id="schemakneepoint"></a>

```json
null

```

*Custom mode setting
*

### Properties

*None*

<h2 id="tocSanaloggain">analoggain</h2>

<a id="schemaanaloggain"></a>

```json
null

```

*Custom mode setting
*

### Properties

*None*

<h2 id="tocSmaxkneegain">maxkneegain</h2>

<a id="schemamaxkneegain"></a>

```json
null

```

*Custom mode setting
*

### Properties

*None*

<h2 id="tocSmaxexptime">maxexptime</h2>

<a id="schemamaxexptime"></a>

```json
null

```

*Custom mode setting
*

### Properties

*None*

<h2 id="tocSmaxdigitalgain">maxdigitalgain</h2>

<a id="schemamaxdigitalgain"></a>

```json
null

```

*Custom mode setting
*

### Properties

*None*

<h2 id="tocSday_binning">day_binning</h2>

<a id="schemaday_binning"></a>

```json
null

```

*Enables or disables day binning mode for supported cameras.
*

### Properties

*None*

<h2 id="tocSnight_binning">night_binning</h2>

<a id="schemanight_binning"></a>

```json
null

```

*Enables or disables day binning mode for supported cameras.
*

### Properties

*None*

<h2 id="tocSdaynight">daynight</h2>

<a id="schemadaynight"></a>

```json
null

```

*Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.*

### Properties

*None*

<h2 id="tocSupscaling">upscaling</h2>

<a id="schemaupscaling"></a>

```json
null

```

*Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. 
*

### Properties

*None*

<h2 id="tocSchannelenable">channelenable</h2>

<a id="schemachannelenable"></a>

```json
null

```

*The channels you want to enable.*

### Properties

*None*

<h2 id="tocSrotate">rotate</h2>

<a id="schemarotate"></a>

```json
null

```

*Sets the rotation of the image in 90 degree increments. 90 and 270 degree rotations are available in newer models; get features to determine whether or not your camera supports these values.
*

### Properties

*None*

<h2 id="tocSbrightness">brightness</h2>

<a id="schemabrightness"></a>

```json
null

```

*Sets brightness for the camera or channel.*

### Properties

*None*

<h2 id="tocSsharpness">sharpness</h2>

<a id="schemasharpness"></a>

```json
null

```

*Sets sharpness for the camera or channel.*

### Properties

*None*

<h2 id="tocSsaturation">saturation</h2>

<a id="schemasaturation"></a>

```json
null

```

*Sets color saturation for the camera or channel.*

### Properties

*None*

<h2 id="tocSblue">blue</h2>

<a id="schemablue"></a>

```json
null

```

*Sets blue balance for the camera or channel.*

### Properties

*None*

<h2 id="tocSred">red</h2>

<a id="schemared"></a>

```json
null

```

*Sets red balance for the camera or channel.*

### Properties

*None*

<h2 id="tocSillum">illum</h2>

<a id="schemaillum"></a>

```json
null

```

*Sets illumination for the camera or channel.*

### Properties

*None*

<h2 id="tocSfreq">freq</h2>

<a id="schemafreq"></a>

```json
null

```

*Mains frequency in Hz, used for indoor lighting compensation.*

### Properties

*None*

<h2 id="tocSlowlight">lowlight</h2>

<a id="schemalowlight"></a>

```json
null

```

*Exposure (low light) mode.*

### Properties

*None*

<h2 id="tocSshortexposures">shortexposures</h2>

<a id="schemashortexposures"></a>

```json
null

```

*Shutter time in high-speed exposure mode, set in milliseconds.*

### Properties

*None*

<h2 id="tocSexposure">exposure</h2>

<a id="schemaexposure"></a>

```json
null

```

*Auto exposure mode*

### Properties

*None*

<h2 id="tocSautoexp">autoexp</h2>

<a id="schemaautoexp"></a>

```json
null

```

*Auto exposure mode*

### Properties

*None*

<h2 id="tocSexpwndleft">expwndleft</h2>

<a id="schemaexpwndleft"></a>

```json
null

```

*The exposure window for the sensor.*

### Properties

*None*

<h2 id="tocSexpwndtop">expwndtop</h2>

<a id="schemaexpwndtop"></a>

```json
null

```

*The exposure window for the sensor.*

### Properties

*None*

<h2 id="tocSexpwndwidth">expwndwidth</h2>

<a id="schemaexpwndwidth"></a>

```json
null

```

*The exposure window for the sensor.*

### Properties

*None*

<h2 id="tocSexpwndheight">expwndheight</h2>

<a id="schemaexpwndheight"></a>

```json
null

```

*The exposure window for the sensor.*

### Properties

*None*

<h2 id="tocSsensorleft">sensorleft</h2>

<a id="schemasensorleft"></a>

```json
null

```

*Sensor cropping, from the left.*

### Properties

*None*

<h2 id="tocSsensortop">sensortop</h2>

<a id="schemasensortop"></a>

```json
null

```

*Sensor cropping from the top.*

### Properties

*None*

<h2 id="tocSsensorwidth">sensorwidth</h2>

<a id="schemasensorwidth"></a>

```json
null

```

*Sensor cropping based on width. Both sides are equally cropped by half the value.*

### Properties

*None*

<h2 id="tocSsensorheight">sensorheight</h2>

<a id="schemasensorheight"></a>

```json
null

```

*Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.*

### Properties

*None*

<h2 id="tocSimgleft">imgleft</h2>

<a id="schemaimgleft"></a>

```json
null

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSimgtop">imgtop</h2>

<a id="schemaimgtop"></a>

```json
null

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSimgwidth">imgwidth</h2>

<a id="schemaimgwidth"></a>

```json
null

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSimgheight">imgheight</h2>

<a id="schemaimgheight"></a>

```json
null

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSimgquality">imgquality</h2>

<a id="schemaimgquality"></a>

```json
null

```

*Image setting, used as the implcit perameter list in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSimgres">imgres</h2>

<a id="schemaimgres"></a>

```json
null

```

*Image setting, used as the implcit perameter list in img.jpg image requests.*

### Properties

*None*

<h2 id="tocSmac">mac</h2>

<a id="schemamac"></a>

```json
null

```

*Returns the MAC address of the camera.*

### Properties

*None*

<h2 id="tocSmodel">model</h2>

<a id="schemamodel"></a>

```json
null

```

*Returns the camera's model number. `fullname` returns the camera's base model number and feature leter; `releasename` returns the manufacturer model number and feature letter — the real model number.*

### Properties

*None*

<h2 id="tocSfwversion">fwversion</h2>

<a id="schemafwversion"></a>

```json
null

```

*Returns the camera's firmware version.*

### Properties

*None*

<h2 id="tocSprocversion">procversion</h2>

<a id="schemaprocversion"></a>

```json
null

```

*Returns the image processor version.*

### Properties

*None*

<h2 id="tocSnetversion">netversion</h2>

<a id="schemanetversion"></a>

```json
null

```

*Returns the network processor version.*

### Properties

*None*

<h2 id="tocSrevision">revision</h2>

<a id="schemarevision"></a>

```json
null

```

*Returns the PCB version.*

### Properties

*None*

<h2 id="tocSparams">params</h2>

<a id="schemaparams"></a>

```json
null

```

*Perform basic camera actions

* save - commits current settings to flash memory
* factory - restore factory default settings
* reboot - restarts the camera
*

### Properties

*None*

<h2 id="tocSwebserverport">webserverport</h2>

<a id="schemawebserverport"></a>

```json
null

```

*The port for the camera's web server.*

### Properties

*None*

<h2 id="tocSadmin">admin</h2>

<a id="schemaadmin"></a>

```json
null

```

*Get or set the admin-level password.*

### Properties

*None*

<h2 id="tocSviewer">viewer</h2>

<a id="schemaviewer"></a>

```json
null

```

*Get or set the viewer-level password.*

### Properties

*None*

<h2 id="tocSmaxsensorwidth">maxsensorwidth</h2>

<a id="schemamaxsensorwidth"></a>

```json
null

```

*Get the maximum sensor width.*

### Properties

*None*

<h2 id="tocSmaxsensorheight">maxsensorheight</h2>

<a id="schemamaxsensorheight"></a>

```json
null

```

*Get the maximum sensor height.*

### Properties

*None*

<h2 id="tocSmdmode">mdmode</h2>

<a id="schemamdmode"></a>

```json
null

```

*Get or set motion alarm settings*

### Properties

*None*

<h2 id="tocSmotiondetect">motiondetect</h2>

<a id="schemamotiondetect"></a>

```json
null

```

*Get or set motion detection settings*

### Properties

*None*

<h2 id="tocSmdtotalzones">mdtotalzones</h2>

<a id="schemamdtotalzones"></a>

```json
null

```

*Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.*

### Properties

*None*

<h2 id="tocSauxin">auxin</h2>

<a id="schemaauxin"></a>

```json
null

```

*Get auxin.*

### Properties

*None*

<h2 id="tocSauxout">auxout</h2>

<a id="schemaauxout"></a>

```json
null

```

*Get or set auxiliary audio out.*

### Properties

*None*

<h2 id="tocScropping">cropping</h2>

<a id="schemacropping"></a>

```json
null

```

*Get or set flexible cropping.
*

### Properties

*None*

<h2 id="tocS1080p_mode">1080p_mode</h2>

<a id="schema1080p_mode"></a>

```json
null

```

*Get or set 1080p mode — used in 10xx5 models only.
*

### Properties

*None*

<h2 id="tocSpmask">pmask</h2>

<a id="schemapmask"></a>

```json
null

```

*Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.
*

### Properties

*None*

<h2 id="tocSpmaskblock">pmaskblock</h2>

<a id="schemapmaskblock"></a>

```json
null

```

*Set the privacy mask block.
*

### Properties

*None*

<h2 id="tocSfocus">focus</h2>

<a id="schemafocus"></a>

```json
null

```

*Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.
*

### Properties

*None*

<h2 id="tocSfocusleft">focusleft</h2>

<a id="schemafocusleft"></a>

```json
null

```

### Properties

*None*

<h2 id="tocSfocustop">focustop</h2>

<a id="schemafocustop"></a>

```json
null

```

### Properties

*None*

<h2 id="tocSfocusright">focusright</h2>

<a id="schemafocusright"></a>

```json
null

```

### Properties

*None*

<h2 id="tocSfocusbottom">focusbottom</h2>

<a id="schemafocusbottom"></a>

```json
null

```

### Properties

*None*

<h2 id="tocSzoom">zoom</h2>

<a id="schemazoom"></a>

```json
null

```

*Set zoom moving steps.
*

### Properties

*None*

<h2 id="tocSfocuswindow">focuswindow</h2>

<a id="schemafocuswindow"></a>

```json
null

```

*Get or set the four sides of the focus window.*

### Properties

*None*

<h2 id="tocSaf_dn">af_dn</h2>

<a id="schemaaf_dn"></a>

```json
null

```

*Get or set autofocus after enabling the day-night switch.
*

### Properties

*None*

<h2 id="tocSaf_zoom">af_zoom</h2>

<a id="schemaaf_zoom"></a>

```json
null

```

*Get or set autofocus after zoom.*

### Properties

*None*

<h2 id="tocScasino_mode">casino_mode</h2>

<a id="schemacasino_mode"></a>

```json
null

```

*Get or set casino mode (1080p models only)*

### Properties

*None*

<h2 id="tocSnetopt">netopt</h2>

<a id="schemanetopt"></a>

```json
null

```

*Get or set network related settings. Integers correspond to the bits you want to enable or disable.

bit 0 = DHCP IP assignment; bit 1 = BOOTP IP assignment; bit 2 = RARP IP assignment; bit 3 = IP lock; bit 4 = NTP time requester; bit 5 = PSIA discovery multicast server; bit 6 = RTP multicast server; bit 7 = MTU enable/disable; bit 8 = PSIA discovery zeroconfig server; bit 9 = IPv6 stack enable; bit 10 = DHCPv6 enable
*

### Properties

*None*

<h2 id="tocSstreamip">streamip</h2>

<a id="schemastreamip"></a>

```json
null

```

*Get or set the multicast IP address.*

### Properties

*None*

<h2 id="tocSrtpport">rtpport</h2>

<a id="schemartpport"></a>

```json
null

```

*Get or set the multicast port.*

### Properties

*None*

<h2 id="tocSsapip">sapip</h2>

<a id="schemasapip"></a>

```json
null

```

*Get or set the multicast SAP IP address.*

### Properties

*None*

<h2 id="tocSmulticast_rec">multicast_rec</h2>

<a id="schemamulticast_rec"></a>

```json
null

```

*Get or set the multicast reception setting.*

### Properties

*None*

<h2 id="tocSen_multicast">en_multicast</h2>

<a id="schemaen_multicast"></a>

```json
null

```

*Enable multicast announcement.

1. To pass ONVIF conformance test, firmware does not announce ONVIF multicast by default. You need to use this HTTP command to enable multicast announcement manually, or your VMS may fail to establish multicast streaming.
2. This setting enables or disables support for incoming multicast traffic. Disabling this feature will not affect the camera's ability to provide multicast video. 
3. For multi-sensor cameras, HTTP commands streamip, sapip and rtpport are channel specific and not global. Currently SurroundVideo series is the only multi-sensor camera that supports these multicast HTTP commands, starting from firmware 65192.14.
*

### Properties

*None*

<h2 id="tocSres">res</h2>

<a id="schemares"></a>

```json
{}

```

*The resolution MJPEGs you want to return*

### Properties

*None*

<h2 id="tocSx0">x0</h2>

<a id="schemax0"></a>

```json
{}

```

*Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

*None*

<h2 id="tocSy0">y0</h2>

<a id="schemay0"></a>

```json
null

```

*Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

*None*

<h2 id="tocSx1">x1</h2>

<a id="schemax1"></a>

```json
{}

```

*Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

*None*

<h2 id="tocSy1">y1</h2>

<a id="schemay1"></a>

```json
null

```

*Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

*None*

<h2 id="tocSqp">qp</h2>

<a id="schemaqp"></a>

```json
null

```

*The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 
*

### Properties

*None*

<h2 id="tocSqp_max">qp_max</h2>

<a id="schemaqp_max"></a>

```json
null

```

*Get or set the maximum allowed QP value — i.e. the lowest allowable quality.
*

### Properties

*None*

<h2 id="tocSratelimit_mode">ratelimit_mode</h2>

<a id="schemaratelimit_mode"></a>

```json
null

```

*Get or set variable bitrate limit mode.
*

### Properties

*None*

<h2 id="tocSratelimit">ratelimit</h2>

<a id="schemaratelimit"></a>

```json
null

```

*Get or set a variable bitrate limit.
*

### Properties

*None*

<h2 id="tocSquality">quality</h2>

<a id="schemaquality"></a>

```json
null

```

*The compression quality of the image*

### Properties

*None*

<h2 id="tocSdoublescan">doublescan</h2>

<a id="schemadoublescan"></a>

```json
null

```

*Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.*

### Properties

*None*

<h2 id="tocSssn">ssn</h2>

<a id="schemassn"></a>

```json
null

```

*Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)
*

### Properties

*None*

<h2 id="tocSiframe">iframe</h2>

<a id="schemaiframe"></a>

```json
null

```

*Effectively a boolean (0 or 1). Set to 1 will force the camera to return an Intra frame (I-frame) with a corresponding SPS and PPS as an IDR slice, so that the stream is decodable from this point. When opening a new stream (as when changing the image size and/or frame rate) the I-frame is sent automatically regardless of the input value of `iframe`. To reduce the stream size, reduce the frequency of `iframe = 1` in requests. You can set the P-frames for any of the streams sent by the camera is set using
one of the following HTTP commands :
http://camera_ip/setreg?page=3&reg=21&val=(0..100)

http://camera_ip/set?keyframeinterval=(0..100)
When the on-camera counter of P-frames fills up, the camera will return an I-frame even if iframe in the request is set to 0. To find out whether an I-frame was received, check the HTTP Content Type.
*

### Properties

*None*

<h2 id="tocSbitrate">bitrate</h2>

<a id="schemabitrate"></a>

```json
null

```

*Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.
*

### Properties

*None*

<h2 id="tocSintra_period">intra_period</h2>

<a id="schemaintra_period"></a>

```json
null

```

*Valid when requesting a non-zero bitrate and periodically requesting `iframe=1`. Specifies the intra-frame period during which you are sending requests with `iframe=1`. If you do not specify `intra_period`, bitrate control will not function correctly unless the actual period of sending iframe=1 requests is the same as the number of P-frames specified in register 3:21 of the camera via one of the commands described above. If you do not request `iframe=1` at all, then the `intra_period` parameter is not required and bitrate control will rely on the number of P-frames set in register 3:21. 
*

### Properties

*None*

<h2 id="tocSfps">fps</h2>

<a id="schemafps"></a>

```json
null

```

*Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).*

### Properties

*None*

<h2 id="tocSchannel">channel</h2>

<a id="schemachannel"></a>

```json
null

```

*If `upscaling=on`, use the channel parameter to retrieve color or monochrome images from the camera.
*

### Properties

*None*

<h2 id="tocSkeyframe">keyframe</h2>

<a id="schemakeyframe"></a>

```json
null

```

*Get or set key frame setting. Yields an I-frame on the next available frame.
*

### Properties

*None*

<h2 id="tocSkeyframeinterval">keyframeinterval</h2>

<a id="schemakeyframeinterval"></a>

```json
null

```

*Get or set the key frame interval.

* For non-4K models the maximum limit is 100
* The numerical value in “set?keyframeinterval=(0…65535)” represents the P-frame count between two consecutive key frames (I-frames)
*

### Properties

*None*

<h2 id="tocSrtspport">rtspport</h2>

<a id="schemartspport"></a>

```json
null

```

*Get or set the RTSP port.
*

### Properties

*None*

<h2 id="tocSspacialfilter">spacialfilter</h2>

<a id="schemaspacialfilter"></a>

```json
null

```

*Get or set the low-light noise filter.
*

### Properties

*None*

<h2 id="tocSname">name</h2>

<a id="schemaname"></a>

```json
null

```

*Get or set the camera name.
*

### Properties

*None*

<h2 id="tocSmtu">mtu</h2>

<a id="schemamtu"></a>

```json
null

```

*Get or set the MTU size.
*

### Properties

*None*

<h2 id="tocSip">ip</h2>

<a id="schemaip"></a>

```json
null

```

*Get or set the camera's IP address.
*

### Properties

*None*

<h2 id="tocSsubnetmask">subnetmask</h2>

<a id="schemasubnetmask"></a>

```json
null

```

*Get or set the camera's subnet mask.
*

### Properties

*None*

<h2 id="tocSgateway">gateway</h2>

<a id="schemagateway"></a>

```json
null

```

*Get or set the camera's default gateway.
*

### Properties

*None*

<h2 id="tocSeth_negotiation">eth_negotiation</h2>

<a id="schemaeth_negotiation"></a>

```json
null

```

*When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.

When set to fixed, the camera uses a transmission speed of 100Mb and full duplex mode.
*

### Properties

*None*

<h2 id="tocSfeatures">features</h2>

<a id="schemafeatures"></a>

```json
null

```

*Returns an integer for enabled features. Integers that are not returned are not enabled.
*

### Properties

*None*

<h2 id="tocSaudioinput">audioinput</h2>

<a id="schemaaudioinput"></a>

```json
null

```

*The source of audio input.
*

### Properties

*None*

<h2 id="tocSlinein_volume">linein_volume</h2>

<a id="schemalinein_volume"></a>

```json
null

```

*Volume of line-in audio.
*

### Properties

*None*

<h2 id="tocSmic_boost">mic_boost</h2>

<a id="schemamic_boost"></a>

```json
null

```

*Volume of microphone-in audio.
*

### Properties

*None*

<h2 id="tocSpiris">piris</h2>

<a id="schemapiris"></a>

```json
null

```

*Enable/disable P-iris
*

### Properties

*None*

<h2 id="tocSpirispos">pirispos</h2>

<a id="schemapirispos"></a>

```json
null

```

*The position P-iris closes to
*

### Properties

*None*

<h2 id="tocSir">ir</h2>

<a id="schemair"></a>

```json
null

```

*Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.
*

### Properties

*None*

<h2 id="tocSmake">make</h2>

<a id="schemamake"></a>

```json
null

```

*Get the make of the camera.
*

### Properties

*None*

<h2 id="tocSwhite_balance">white_balance</h2>

<a id="schemawhite_balance"></a>

```json
null

```

*White balance control.
*

### Properties

*None*

<h2 id="tocSwbwndctrl">wbwndctrl</h2>

<a id="schemawbwndctrl"></a>

```json
null

```

*White balance window control.
*

### Properties

*None*

<h2 id="tocSwbwndleft">wbwndleft</h2>

<a id="schemawbwndleft"></a>

```json
null

```

*White balance window left start value. Maximum values depend on your sensor size.
*

### Properties

*None*

<h2 id="tocSwbwndtop">wbwndtop</h2>

<a id="schemawbwndtop"></a>

```json
null

```

*White balance window top start value. Maximum values depend on your sensor size.
*

### Properties

*None*

<h2 id="tocSwbwndwidth">wbwndwidth</h2>

<a id="schemawbwndwidth"></a>

```json
null

```

*White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.
*

### Properties

*None*

<h2 id="tocSwbwndheight">wbwndheight</h2>

<a id="schemawbwndheight"></a>

```json
null

```

*White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.
*

### Properties

*None*

<h2 id="tocSntpserver_ip">ntpserver_ip</h2>

<a id="schemantpserver_ip"></a>

```json
null

```

*NTP server address.
*

### Properties

*None*

<h2 id="tocSenclosure">enclosure</h2>

<a id="schemaenclosure"></a>

```json
null

```

*Returns the camera's model name. Provide `code` to return the model type number.
*

### Properties

*None*

<h2 id="tocSgamma">gamma</h2>

<a id="schemagamma"></a>

```json
null

```

*Gamma for single sensor and Surroundvideo1 cameras.
*

### Properties

*None*

<h2 id="tocSgamma2">gamma2</h2>

<a id="schemagamma2"></a>

```json
null

```

*Gamma for the second sensor in dual sensor cameras.
*

### Properties

*None*

<h2 id="tocSbandwidthsaving">bandwidthsaving</h2>

<a id="schemabandwidthsaving"></a>

```json
null

```

*Bandwidth saving mode settings.
*

### Properties

*None*

<h2 id="tocSlowpower">lowpower</h2>

<a id="schemalowpower"></a>

```json
null

```

*Low power mode settings.
*

### Properties

*None*

<h2 id="tocSmotion_compensation">motion_compensation</h2>

<a id="schemamotion_compensation"></a>

```json
null

```

*Motion compensation settings.
*

### Properties

*None*

<h2 id="tocSadjustable_ir">adjustable_ir</h2>

<a id="schemaadjustable_ir"></a>

```json
null

```

*Adjustable IR light settings.
*

### Properties

*None*

<h2 id="tocSirwidepos">irwidepos</h2>

<a id="schemairwidepos"></a>

```json
null

```

*The adjustable intensity of wide IR lights.
*

### Properties

*None*

<h2 id="tocSirtelepos">irtelepos</h2>

<a id="schemairtelepos"></a>

```json
null

```

*The adjustable intensity of tele IR lights.
*

### Properties

*None*

<h2 id="tocSsnapstream">snapstream</h2>

<a id="schemasnapstream"></a>

```json
null

```

*Snapstream on/off setting.
*

### Properties

*None*

<h2 id="tocSsensorcount">sensorcount</h2>

<a id="schemasensorcount"></a>

```json
null

```

*Returns the sensor count. Use the sensor count to determine the channels you want to get or set when 
*

### Properties

*None*


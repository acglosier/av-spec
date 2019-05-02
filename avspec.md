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

## Get an MJPEG Stream

<a id="opIdmjpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/mjpeg?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=scaled&sd=on \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/mjpeg?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=scaled&sd=on HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/mjpeg',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=scaled&sd=on',
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

fetch('http://<camera IP address>/mjpeg?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=scaled&sd=on',
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
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'doublescan' => 'integer',
'fps' => 'integer',
'quality' => 'integer',
'ver' => 'string',
'channel' => 'string',
'sd' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/mjpeg', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'doublescan': '0',  'fps': '0',  'quality': '1',  'ver': 'HTTP/1.0',  'channel': 'scaled',  'sd': 'on'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/mjpeg?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=scaled&sd=on");
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

open a continuous mjpeg stream from the camera

<h3 id="get-an-mjpeg-stream-parameters">Parameters</h3>

|res|in query|string|optional|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|optional|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|optional|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|optional|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|optional|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|doublescan|in query|integer|optional|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|fps|in query|integer|optional|
|---|---|---|---|

Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).

|quality|in query|integer|optional|
|---|---|---|---|

The compression quality of the jpeg image

|ver|in query|string|optional|
|---|---|---|---|

Arecont Vision cameras support both HTTP/1.0 and HTTP/1.1 protocols as defined by RFC-1945 and RFC2068, respectively. While HTTP/1.0 is simple, it closes the transmission after each image, forcing the client to incur a round trip delay; this limits the speed of image transmission when you request individual images rather than an mjpeg stream. However, HTTP/1.0 is reliable and supported by all HTTP implementations, albeit with limited speed. By default, Arecont Vision cameras are use HTTP/1.0 protocol regardless of the HTTP version used by the client.

|channel|in query|string|optional|
|---|---|---|---|

Request down-scaled images. Because you preset downscaled image settings (through the UI or the /set endpoint), this parameter does not require size information.

|sd|in query|string|optional|
|---|---|---|---|

Use to request images/video recorded on the SD card. `playback` plays back video in real time; `download` lets you stream video as fast as possible.         

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

<h3 id="get-an-mjpeg-stream-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream|string|

<aside class="success">
This operation does not require authentication
</aside>

## Get a JPEG Frame

<a id="opIdjpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/image?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1 \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/image?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1 HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/image',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1',
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

fetch('http://<camera IP address>/image?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1',
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
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'doublescan' => 'integer',
'quality' => 'integer',
'ID' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/image', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'doublescan': '0',  'quality': '1',  'ID': '1'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/image?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1");
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

Pull JPEG frames individually from the camera.

<h3 id="get-a-jpeg-frame-parameters">Parameters</h3>

|res|in query|string|required|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|required|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|required|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|required|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|required|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|doublescan|in query|integer|required|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|quality|in query|integer|optional|
|---|---|---|---|

The compression quality of the jpeg image

|ID|in query|integer|optional|
|---|---|---|---|

Ignored by the camera, but you might set random IDs to force browsers to refresh a frame. Some browsers might display a cached image if a previous URL is reused without modifying the ID field

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|

> Example responses

> 200 Response

<h3 id="get-a-jpeg-frame-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an image|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-h-264-streaming">h.264 Streaming</h1>

Pull h.264 quality images individually or full video stream.

## Pull an H.264 Frame

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/h264?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&iframe=0&bitrate=1&intra_period=0 \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/h264?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&iframe=0&bitrate=1&intra_period=0 HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/h264',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&iframe=0&bitrate=1&intra_period=0',
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

fetch('http://<camera IP address>/h264?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&iframe=0&bitrate=1&intra_period=0',
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
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'qp' => 'string',
'doublescan' => 'integer',
'ssn' => 'integer',
'iframe' => 'integer',
'bitrate' => 'integer',
'intra_period' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/h264', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'qp': 'string',  'doublescan': '0',  'ssn': '1',  'iframe': '0',  'bitrate': '1',  'intra_period': '0'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/h264?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&iframe=0&bitrate=1&intra_period=0");
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

Pull H.264 frames from cameras. The first frame or the stream is always an IDR (Intra) frame followed by multiple P (Inter) frames. The default number of P-frames is 50, and can be modified via register 3:21 using one of the following HTTP commands —

http://camera_ip/set?keyframeinterval=(0..100)
http://camera_ip/setreg?page=3&reg=21&val=(number of P-frames)

You can get your current P-frame setting from http://camera_ip/getreg?page=3&reg=21 

<h3 id="pull-an-h.264-frame-parameters">Parameters</h3>

|res|in query|string|required|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|required|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|required|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|required|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|required|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|qp|in query|string|optional|
|---|---|---|---|

The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 

|doublescan|in query|integer|required|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|ssn|in query|integer|optional|
|---|---|---|---|

Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)

|iframe|in query|integer|optional|
|---|---|---|---|

Effectively a boolean (0 or 1). Set to 1 will force the camera to return an Intra frame (I-frame) with a corresponding SPS and PPS as an IDR slice, so that the stream is decodable from this point. When opening a new stream (as when changing the image size and/or frame rate) the I-frame is sent automatically regardless of the input value of `iframe`. To reduce the stream size, reduce the frequency of `iframe = 1` in requests. You can set the P-frames for any of the streams sent by the camera is set using

|bitrate|in query|integer|optional|
|---|---|---|---|

Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.

|intra_period|in query|integer|optional|
|---|---|---|---|

Valid when requesting a non-zero bitrate and periodically requesting `iframe=1`. Specifies the intra-frame period during which you are sending requests with `iframe=1`. If you do not specify `intra_period`, bitrate control will not function correctly unless the actual period of sending iframe=1 requests is the same as the number of P-frames specified in register 3:21 of the camera via one of the commands described above. If you do not request `iframe=1` at all, then the `intra_period` parameter is not required and bitrate control will rely on the number of P-frames set in register 3:21. 

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|

> Example responses

> 200 Response

<h3 id="pull-an-h.264-frame-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream according to the parameters in your request.

Each frame sent by the camera may contain multiple zero bytes at the end. A Unit Delimiter (UD) is not used. Although this does not contradict the ITU-T H.264 standard (ISO/IEC 14496-10), some decoders may delay decoded frames by one due to the absence of the UD. If this presents a problem, replace all zero bytes at the end with the UD, a sequence of the following five bytes — `0x00 0x00 0x01 0x09 0x10`. The number of zero bytes at the end of a frame may be significant (up to a few hundred bytes). Replacing them with the UD will also reduce the stream size|string|

<aside class="success">
This operation does not require authentication
</aside>

## Pull an H.264 Video Stream

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/h264stream?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&bitrate=1&fps=0&ver=HTTP%2F1.0&channel=scaled&sd=on \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/h264stream?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&bitrate=1&fps=0&ver=HTTP%2F1.0&channel=scaled&sd=on HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/h264stream',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&bitrate=1&fps=0&ver=HTTP%2F1.0&channel=scaled&sd=on',
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

fetch('http://<camera IP address>/h264stream?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&bitrate=1&fps=0&ver=HTTP%2F1.0&channel=scaled&sd=on',
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
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'qp' => 'string',
'doublescan' => 'integer',
'ssn' => 'integer',
'bitrate' => 'integer',
'fps' => 'integer',
'ver' => 'string',
'channel' => 'string',
'sd' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/h264stream', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'qp': 'string',  'doublescan': '0',  'ssn': '1',  'bitrate': '1',  'fps': '0',  'ver': 'HTTP/1.0',  'channel': 'scaled',  'sd': 'on'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/h264stream?res=full&x0=0&y0=0&x1=0&y1=0&qp=string&doublescan=0&ssn=1&bitrate=1&fps=0&ver=HTTP%2F1.0&channel=scaled&sd=on");
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

Pull a continuous H.264 video stream with boundary-separated frames.

<h3 id="pull-an-h.264-video-stream-parameters">Parameters</h3>

|res|in query|string|required|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|required|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|required|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|required|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|required|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|qp|in query|string|required|
|---|---|---|---|

The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 

|doublescan|in query|integer|required|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|ssn|in query|integer|required|
|---|---|---|---|

Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)

|bitrate|in query|integer|required|
|---|---|---|---|

Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.

|fps|in query|integer|required|
|---|---|---|---|

Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).

|ver|in query|string|required|
|---|---|---|---|

Arecont Vision cameras support both HTTP/1.0 and HTTP/1.1 protocols as defined by RFC-1945 and RFC2068, respectively. While HTTP/1.0 is simple, it closes the transmission after each image, forcing the client to incur a round trip delay; this limits the speed of image transmission when you request individual images rather than an mjpeg stream. However, HTTP/1.0 is reliable and supported by all HTTP implementations, albeit with limited speed. By default, Arecont Vision cameras are use HTTP/1.0 protocol regardless of the HTTP version used by the client.

|channel|in query|string|optional|
|---|---|---|---|

Request down-scaled images. Because you preset downscaled image settings (through the UI or the /set endpoint), this parameter does not require size information.

|sd|in query|string|required|
|---|---|---|---|

Use to request images/video recorded on the SD card. `playback` plays back video in real time; `download` lets you stream video as fast as possible.         

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

<h3 id="pull-an-h.264-video-stream-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream according to the parameters in your request.|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-multisensor-camera-streaming">Multisensor Camera Streaming</h1>

Get images or video from a sensor belonging to a multisensor camera.

## Get an MJPEG Stream

<a id="opIdmultimjpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/mjpeg{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=1&ssn=1&ID=1&sd=on \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/mjpeg{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=1&ssn=1&ID=1&sd=on HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/mjpeg{channel}',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=1&ssn=1&ID=1&sd=on',
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

fetch('http://<camera IP address>/mjpeg{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=1&ssn=1&ID=1&sd=on',
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

result = RestClient.get 'http://<camera IP address>/mjpeg{channel}',
  params: {
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'doublescan' => 'integer',
'fps' => 'integer',
'quality' => 'integer',
'ver' => 'string',
'channel' => 'string',
'ssn' => 'integer',
'ID' => 'integer',
'sd' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/mjpeg{channel}', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'doublescan': '0',  'fps': '0',  'quality': '1',  'ver': 'HTTP/1.0',  'channel': 'scaled',  'ssn': '1',  'ID': '1',  'sd': 'on'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/mjpeg{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&fps=0&quality=1&ver=HTTP%2F1.0&channel=1&ssn=1&ID=1&sd=on");
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
    req, err := http.NewRequest("GET", "http://<camera IP address>/mjpeg{channel}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /mjpeg{channel}`

open a continuous mjpeg stream from a sensor belonging to a multisensor camera.

<h3 id="get-an-mjpeg-stream-parameters">Parameters</h3>

|res|in query|string|required|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|required|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|required|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|required|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|required|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|doublescan|in query|integer|required|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|fps|in query|integer|required|
|---|---|---|---|

Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).

|quality|in query|integer|optional|
|---|---|---|---|

The compression quality of the jpeg image

|ver|in query|string|required|
|---|---|---|---|

Arecont Vision cameras support both HTTP/1.0 and HTTP/1.1 protocols as defined by RFC-1945 and RFC2068, respectively. While HTTP/1.0 is simple, it closes the transmission after each image, forcing the client to incur a round trip delay; this limits the speed of image transmission when you request individual images rather than an mjpeg stream. However, HTTP/1.0 is reliable and supported by all HTTP implementations, albeit with limited speed. By default, Arecont Vision cameras are use HTTP/1.0 protocol regardless of the HTTP version used by the client.

|channel|in query|string|optional|
|---|---|---|---|

Request down-scaled images. Because you preset downscaled image settings (through the UI or the /set endpoint), this parameter does not require size information.

|ssn|in query|integer|required|
|---|---|---|---|

Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)

|ID|in query|integer|optional|
|---|---|---|---|

Ignored by the camera, but you might set random IDs to force browsers to refresh a frame. Some browsers might display a cached image if a previous URL is reused without modifying the ID field

|sd|in query|string|required|
|---|---|---|---|

Use to request images/video recorded on the SD card. `playback` plays back video in real time; `download` lets you stream video as fast as possible.         

|channel|in path|integer|required|
|---|---|---|---|

The ID of the channel you want to return information for. If you do not specify the channel, the camera will transmit the next available image from any of the enabled channels.

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

<h3 id="get-an-mjpeg-stream-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a stream|string|

<aside class="success">
This operation does not require authentication
</aside>

## Get a JPEG Frame

<a id="opIdmultijpeg"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/image{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1&ssn=1 \
  -H 'Accept: multipart/x-mixed-replace; boundary=fbdr'

```

```http
GET http://<camera IP address>/image{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1&ssn=1 HTTP/1.1

Accept: multipart/x-mixed-replace; boundary=fbdr

```

```javascript
var headers = {
  'Accept':'multipart/x-mixed-replace; boundary=fbdr'

};

$.ajax({
  url: 'http://<camera IP address>/image{channel}',
  method: 'get',
  data: '?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1&ssn=1',
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

fetch('http://<camera IP address>/image{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1&ssn=1',
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

result = RestClient.get 'http://<camera IP address>/image{channel}',
  params: {
  'res' => 'string',
'x0' => 'integer(int32)',
'y0' => 'integer(int32)',
'x1' => 'integer(int32)',
'y1' => 'integer',
'doublescan' => 'integer',
'quality' => 'integer',
'ID' => 'integer',
'ssn' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'multipart/x-mixed-replace; boundary=fbdr'
}

r = requests.get('http://<camera IP address>/image{channel}', params={
  'res': 'full',  'x0': '0',  'y0': '0',  'x1': '0',  'y1': '0',  'doublescan': '0',  'quality': '1',  'ID': '1',  'ssn': '1'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/image{channel}?res=full&x0=0&y0=0&x1=0&y1=0&doublescan=0&quality=1&ID=1&ssn=1");
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
    req, err := http.NewRequest("GET", "http://<camera IP address>/image{channel}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /image{channel}`

Pull JPEG frames individually from the camera.

<h3 id="get-a-jpeg-frame-parameters">Parameters</h3>

|res|in query|string|required|
|---|---|---|---|

The resolution MJPEGs you want to return

|x0|in query|integer(int32)|required|
|---|---|---|---|

Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y0|in query|integer(int32)|required|
|---|---|---|---|

Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|x1|in query|integer(int32)|required|
|---|---|---|---|

Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|y1|in query|integer|required|
|---|---|---|---|

Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.

|doublescan|in query|integer|required|
|---|---|---|---|

Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.

|quality|in query|integer|optional|
|---|---|---|---|

The compression quality of the jpeg image

|ID|in query|integer|optional|
|---|---|---|---|

Ignored by the camera, but you might set random IDs to force browsers to refresh a frame. Some browsers might display a cached image if a previous URL is reused without modifying the ID field

|ssn|in query|integer|required|
|---|---|---|---|

Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)

|channel|in path|integer|required|
|---|---|---|---|

The ID of the channel you want to return information for. If you do not specify the channel, the camera will transmit the next available image from any of the enabled channels.

#### Enumerated Values

|Parameter|Value|
|---|---|
|res|full|
|res|half|

> Example responses

> 200 Response

<h3 id="get-a-jpeg-frame-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an image|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-configuration">Configuration</h1>

Get and set camera configuration

## Get Multisensor Camera Settings

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0 \
  -H 'Accept: text/plain'

```

```http
GET http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0 HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/get{channel}',
  method: 'get',
  data: '?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0',
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

fetch('http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0',
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
  'brightness' => 'integer',
'sharpness' => 'integer',
'saturation' => 'integer',
'blue' => 'integer',
'red' => 'integer',
'illum' => 'string',
'freq' => 'integer',
'lowlight' => 'string',
'shortexposures' => 'integer',
'autoexp' => 'string',
'exposure' => 'string',
'kneepoint' => 'integer',
'analoggain' => 'integer',
'maxkneegain' => 'integer',
'maxexptime' => 'integer',
'maxdigitalgain' => 'integer',
'mdmode' => 'string',
'motiondetect' => 'string',
'mdtotalzones' => 'integer',
'mdlevelthreshold' => 'integer',
'mdprivacymask' => 'integer',
'pmask' => 'string',
'pmaskleft' => 'integer',
'pmasktop' => 'integer',
'pmaskright' => 'integer',
'pmaskbottom' => 'integer',
'streamip' => 'string(ipv4)',
'rtpport' => 'integer',
'sapip' => 'string(ipv4)',
'vertical_shift' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('http://<camera IP address>/get{channel}', params={
  'brightness': '-50',  'sharpness': '0',  'saturation': '0',  'blue': '-10',  'red': '-10',  'illum': 'auto',  'freq': '50',  'lowlight': 'highspeed',  'shortexposures': '1',  'autoexp': 'on',  'exposure': 'auto',  'kneepoint': '1',  'analoggain': '1',  'maxkneegain': '1',  'maxexptime': '1',  'maxdigitalgain': '1',  'mdmode': 'on',  'motiondetect': 'on',  'mdtotalzones': '0',  'mdlevelthreshold': '2',  'mdprivacymask': '0',  'pmask': 'on',  'pmaskleft': '0',  'pmasktop': '0',  'pmaskright': '0',  'pmaskbottom': '0',  'streamip': '192.168.0.1',  'rtpport': '0',  'sapip': '192.168.0.1',  'vertical_shift': '0'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0");
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

Return settings for a single channel in a multi-sensor camera. In general, you should use only one query parameter at a time.

<h3 id="get-multisensor-camera-settings-parameters">Parameters</h3>

|brightness|in query|integer|optional|
|---|---|---|---|

Sets brightness for the camera or channel.

|sharpness|in query|integer|optional|
|---|---|---|---|

Sets sharpness for the camera or channel.

|saturation|in query|integer|optional|
|---|---|---|---|

Sets color saturation for the camera or channel.

|blue|in query|integer|optional|
|---|---|---|---|

Sets blue balance for the camera or channel.

|red|in query|integer|optional|
|---|---|---|---|

Sets red balance for the camera or channel.

|illum|in query|string|optional|
|---|---|---|---|

Sets illumination for the camera or channel.

|freq|in query|integer|optional|
|---|---|---|---|

Mains frequency in Hz, used for indoor lighting compensation.

|lowlight|in query|string|optional|
|---|---|---|---|

Exposure (low light) mode.

|shortexposures|in query|integer|optional|
|---|---|---|---|

Shutter time in high-speed exposure mode, set in milliseconds.

|autoexp|in query|string|optional|
|---|---|---|---|

Auto exposure mode

|exposure|in query|string|optional|
|---|---|---|---|

Auto exposure mode

|kneepoint|in query|integer|optional|
|---|---|---|---|

Custom mode setting

|analoggain|in query|integer|optional|
|---|---|---|---|

Custom mode setting

|maxkneegain|in query|integer|optional|
|---|---|---|---|

Custom mode setting

|maxexptime|in query|integer|optional|
|---|---|---|---|

Custom mode setting

|maxdigitalgain|in query|integer|optional|
|---|---|---|---|

Custom mode setting

|mdmode|in query|string|optional|
|---|---|---|---|

Get or set motion alarm settings

|motiondetect|in query|string|optional|
|---|---|---|---|

Get or set motion detection settings

|mdtotalzones|in query|integer|optional|
|---|---|---|---|

Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.

|mdlevelthreshold|in query|integer|optional|
|---|---|---|---|

Motion detection zone threshold

|mdprivacymask|in query|integer|optional|
|---|---|---|---|

Motion detection privacy mask

|pmask|in query|string|optional|
|---|---|---|---|

Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.

|pmaskleft|in query|integer|optional|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmasktop|in query|integer|optional|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmaskright|in query|integer|optional|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmaskbottom|in query|integer|optional|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|streamip|in query|string(ipv4)|optional|
|---|---|---|---|

Get or set the multicast IP address.

|rtpport|in query|integer|optional|
|---|---|---|---|

Get or set the multicast port.

|sapip|in query|string(ipv4)|optional|
|---|---|---|---|

Get or set the multicast SAP IP address.

|vertical_shift|in query|integer|optional|
|---|---|---|---|

Shift sensors vertically.

|channel|in path|integer|required|
|---|---|---|---|

The ID of the channel you want to return information for. If you do not specify the channel, the camera will transmit the next available image from any of the enabled channels.

#### Enumerated Values

|Parameter|Value|
|---|---|
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
|mdmode|on|
|mdmode|off|
|motiondetect|on|
|motiondetect|off|
|pmask|on|
|pmask|off|

> Example responses

> 200 Response

<h3 id="get-multisensor-camera-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters specified in the query.|Inline|

<h3 id="get-multisensor-camera-settings-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## Set Multisensor Camera Settings

> Code samples

```shell
# You can also use wget
curl -X POST http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0 \
  -H 'Accept: text/plain'

```

```http
POST http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0 HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/get{channel}',
  method: 'post',
  data: '?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0',
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

fetch('http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0',
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

result = RestClient.post 'http://<camera IP address>/get{channel}',
  params: {
  'brightness' => 'integer',
'sharpness' => 'integer',
'saturation' => 'integer',
'blue' => 'integer',
'red' => 'integer',
'illum' => 'string',
'freq' => 'integer',
'lowlight' => 'string',
'shortexposures' => 'integer',
'autoexp' => 'string',
'exposure' => 'string',
'kneepoint' => 'integer',
'analoggain' => 'integer',
'maxkneegain' => 'integer',
'maxexptime' => 'integer',
'maxdigitalgain' => 'integer',
'mdmode' => 'string',
'motiondetect' => 'string',
'mdtotalzones' => 'integer',
'mdlevelthreshold' => 'integer',
'mdprivacymask' => 'integer',
'pmask' => 'string',
'pmaskleft' => 'integer',
'pmasktop' => 'integer',
'pmaskright' => 'integer',
'pmaskbottom' => 'integer',
'streamip' => 'string(ipv4)',
'rtpport' => 'integer',
'sapip' => 'string(ipv4)',
'vertical_shift' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.post('http://<camera IP address>/get{channel}', params={
  'brightness': '-50',  'sharpness': '0',  'saturation': '0',  'blue': '-10',  'red': '-10',  'illum': 'auto',  'freq': '50',  'lowlight': 'highspeed',  'shortexposures': '1',  'autoexp': 'on',  'exposure': 'auto',  'kneepoint': '1',  'analoggain': '1',  'maxkneegain': '1',  'maxexptime': '1',  'maxdigitalgain': '1',  'mdmode': 'on',  'motiondetect': 'on',  'mdtotalzones': '0',  'mdlevelthreshold': '2',  'mdprivacymask': '0',  'pmask': 'on',  'pmaskleft': '0',  'pmasktop': '0',  'pmaskright': '0',  'pmaskbottom': '0',  'streamip': '192.168.0.1',  'rtpport': '0',  'sapip': '192.168.0.1',  'vertical_shift': '0'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/get{channel}?brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&mdmode=on&motiondetect=on&mdtotalzones=0&mdlevelthreshold=2&mdprivacymask=0&pmask=on&pmaskleft=0&pmasktop=0&pmaskright=0&pmaskbottom=0&streamip=192.168.0.1&rtpport=0&sapip=192.168.0.1&vertical_shift=0");
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
    req, err := http.NewRequest("POST", "http://<camera IP address>/get{channel}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /get{channel}`

Set parameters for a single channel in a multi-sensor camera. In general, you should use only one query parameter at a time.

<h3 id="set-multisensor-camera-settings-parameters">Parameters</h3>

|brightness|in query|integer|required|
|---|---|---|---|

Sets brightness for the camera or channel.

|sharpness|in query|integer|required|
|---|---|---|---|

Sets sharpness for the camera or channel.

|saturation|in query|integer|required|
|---|---|---|---|

Sets color saturation for the camera or channel.

|blue|in query|integer|required|
|---|---|---|---|

Sets blue balance for the camera or channel.

|red|in query|integer|required|
|---|---|---|---|

Sets red balance for the camera or channel.

|illum|in query|string|required|
|---|---|---|---|

Sets illumination for the camera or channel.

|freq|in query|integer|required|
|---|---|---|---|

Mains frequency in Hz, used for indoor lighting compensation.

|lowlight|in query|string|required|
|---|---|---|---|

Exposure (low light) mode.

|shortexposures|in query|integer|required|
|---|---|---|---|

Shutter time in high-speed exposure mode, set in milliseconds.

|autoexp|in query|string|required|
|---|---|---|---|

Auto exposure mode

|exposure|in query|string|required|
|---|---|---|---|

Auto exposure mode

|kneepoint|in query|integer|required|
|---|---|---|---|

Custom mode setting

|analoggain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxkneegain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxexptime|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxdigitalgain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|mdmode|in query|string|required|
|---|---|---|---|

Get or set motion alarm settings

|motiondetect|in query|string|required|
|---|---|---|---|

Get or set motion detection settings

|mdtotalzones|in query|integer|required|
|---|---|---|---|

Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.

|mdlevelthreshold|in query|integer|required|
|---|---|---|---|

Motion detection zone threshold

|mdprivacymask|in query|integer|required|
|---|---|---|---|

Motion detection privacy mask

|pmask|in query|string|required|
|---|---|---|---|

Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.

|pmaskleft|in query|integer|required|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmasktop|in query|integer|required|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmaskright|in query|integer|required|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|pmaskbottom|in query|integer|required|
|---|---|---|---|

Get, set, or erace a privacy mask block (32 x 32 pixels per block).

|streamip|in query|string(ipv4)|required|
|---|---|---|---|

Get or set the multicast IP address.

|rtpport|in query|integer|required|
|---|---|---|---|

Get or set the multicast port.

|sapip|in query|string(ipv4)|required|
|---|---|---|---|

Get or set the multicast SAP IP address.

|vertical_shift|in query|integer|required|
|---|---|---|---|

Shift sensors vertically.

|channel|in path|integer|required|
|---|---|---|---|

The ID of the channel you want to return information for. If you do not specify the channel, the camera will transmit the next available image from any of the enabled channels.

#### Enumerated Values

|Parameter|Value|
|---|---|
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
|mdmode|on|
|mdmode|off|
|motiondetect|on|
|motiondetect|off|
|pmask|on|
|pmask|off|

> Example responses

> 200 Response

<h3 id="set-multisensor-camera-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters specified in the query.|Inline|

<h3 id="set-multisensor-camera-settings-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## Get Camera Settings

> Code samples

```shell
# You can also use wget
curl -X GET http://<camera IP address>/get?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&mac=string&model=fullname&fwversion=true&procversion=true&netversion=true&revision=true&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&make=string&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&enclosure=code&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0 \
  -H 'Accept: text/plain'

```

```http
GET http://<camera IP address>/get?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&mac=string&model=fullname&fwversion=true&procversion=true&netversion=true&revision=true&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&make=string&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&enclosure=code&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0 HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/get',
  method: 'get',
  data: '?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&mac=string&model=fullname&fwversion=true&procversion=true&netversion=true&revision=true&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&make=string&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&enclosure=code&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0',
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

fetch('http://<camera IP address>/get?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&mac=string&model=fullname&fwversion=true&procversion=true&netversion=true&revision=true&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&make=string&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&enclosure=code&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0',
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
  'day_binning' => 'string',
'night_binning' => 'string',
'daynight' => 'string',
'upscaling' => 'string',
'channelenable' => 'string',
'brightness' => 'integer',
'sharpness' => 'integer',
'saturation' => 'integer',
'blue' => 'integer',
'red' => 'integer',
'illum' => 'string',
'freq' => 'integer',
'lowlight' => 'string',
'shortexposures' => 'integer',
'autoexp' => 'string',
'exposure' => 'string',
'expwndleft' => 'integer',
'expwndtop' => 'integer',
'expwndwidth' => 'integer',
'expwndheight' => 'integer',
'sensorleft' => 'integer',
'sensortop' => 'integer',
'sensorwidth' => 'integer',
'sensorheight' => 'integer',
'imgleft' => 'integer',
'imgtop' => 'integer',
'imgwidth' => 'integer',
'imgheight' => 'integer',
'imgquality' => 'integer',
'imgres' => 'string',
'mac' => 'string',
'model' => 'string',
'fwversion' => 'boolean',
'procversion' => 'boolean',
'netversion' => 'boolean',
'revision' => 'boolean',
'kneepoint' => 'integer',
'analoggain' => 'integer',
'maxkneegain' => 'integer',
'maxexptime' => 'integer',
'maxdigitalgain' => 'integer',
'webserverport' => 'integer',
'admin' => 'any',
'viewer' => 'any',
'maxsensorwidth' => 'integer',
'maxsensorheight' => 'integer',
'mdmode' => 'string',
'motiondetect' => 'string',
'mdtotalzones' => 'integer',
'auxin' => 'boolean',
'auxout' => 'string',
'cropping' => 'string',
'1080p_mode' => 'string',
'pmask' => 'string',
'focus' => 'any',
'zoom' => 'any',
'focusleft' => 'integer',
'focustop' => 'integer',
'focusright' => 'integer',
'focusbottom' => 'integer',
'focuswindow' => 'array[integer]',
'af_dn' => 'string',
'af_zoom' => 'string',
'casino_mode' => 'string',
'netopt' => 'integer',
'multicast_rec' => 'string',
'en_multicast' => 'integer',
'fps' => 'integer',
'qp' => 'string',
'qp_max' => 'string',
'ratelimit_mode' => 'boolean',
'ratelimit' => 'string',
'bitrate' => 'integer',
'keyframeinterval' => 'integer',
'rtspport' => 'integer',
'spacialfilter' => 'integer',
'name' => 'string',
'mtu' => 'integer',
'ip' => 'string',
'subnetmask' => 'string',
'gateway' => 'string',
'eth_negotiation' => 'string',
'features' => 'integer',
'audioinput' => 'string',
'linein_volume' => 'integer',
'mic_boost' => 'integer',
'piris' => 'string',
'pirispos' => 'integer',
'ir' => 'string',
'make' => 'string',
'white_balance' => 'string',
'wbwndctrl' => 'string',
'wbwndleft' => 'integer',
'wbwndtop' => 'integer',
'wbwndwidth' => 'integer',
'wbwndheight' => 'integer',
'ntpserver_ip' => 'string',
'enclosure' => 'string',
'gamma' => 'integer',
'gamma2' => 'integer',
'bandwidthsaving' => 'string',
'lowpower' => 'string',
'motion_compensation' => 'string',
'adjustable_ir' => 'string',
'irwidepos' => 'integer',
'irtelpos' => 'integer',
'irpos_chan1' => 'integer',
'irpos_chan2' => 'integer',
'snapstream' => 'string',
'sensorcount' => 'integer',
'scaling' => 'string',
'sd_codec' => 'string',
'sd_fps' => 'integer',
'sd_recording' => 'string',
'sd_networkfail' => 'string',
'sd_motionalarm' => 'string',
'sd_ioalarm' => 'string',
'sd_stampspan' => 'boolean',
'sd_imgleft' => 'integer',
'sd_imgright' => 'integer',
'sd_imgtop' => 'integer',
'sd_imgbottom' => 'integer',
'sd_imgres' => 'string',
'qos_enabled' => 'integer',
'qos_video' => 'integer',
'qos_default' => 'integer',
'ipv6enabled' => 'boolean',
'ipv6address' => 'string(ipv6)',
'ipv6prefixlen' => 'string',
'ipv6dhcp' => 'string',
'ipv6addresstype' => 'string',
'ipv6acceptrouters' => 'boolean',
'equalbright' => 'string',
'equalcolor' => 'string',
'vertical_alignment' => 'string',
'piris_ref_channel' => 'integer',
'exp_ref_channel' => 'any'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('http://<camera IP address>/get', params={
  'day_binning': 'on',  'night_binning': 'on',  'daynight': 'auto',  'upscaling': 'on',  'channelenable': 'string',  'brightness': '-50',  'sharpness': '0',  'saturation': '0',  'blue': '-10',  'red': '-10',  'illum': 'auto',  'freq': '50',  'lowlight': 'highspeed',  'shortexposures': '1',  'autoexp': 'on',  'exposure': 'auto',  'expwndleft': '0',  'expwndtop': '0',  'expwndwidth': '0',  'expwndheight': '0',  'sensorleft': '0',  'sensortop': '0',  'sensorwidth': '0',  'sensorheight': '0',  'imgleft': '0',  'imgtop': '0',  'imgwidth': '0',  'imgheight': '0',  'imgquality': '1',  'imgres': 'full',  'mac': 'string',  'model': 'fullname',  'fwversion': 'true',  'procversion': 'true',  'netversion': 'true',  'revision': 'true',  'kneepoint': '1',  'analoggain': '1',  'maxkneegain': '1',  'maxexptime': '1',  'maxdigitalgain': '1',  'webserverport': '0',  'admin': 'pa$$word',  'viewer': 'pa$$word',  'maxsensorwidth': '0',  'maxsensorheight': '0',  'mdmode': 'on',  'motiondetect': 'on',  'mdtotalzones': '0',  'auxin': 'true',  'auxout': 'on',  'cropping': 'on',  '1080p_mode': 'on',  'pmask': 'on',  'focus': 'fullrange',  'zoom': 'reset',  'focusleft': '0',  'focustop': '0',  'focusright': '0',  'focusbottom': '0',  'focuswindow': [
  0,
  0,
  0,
  0
],  'af_dn': 'on',  'af_zoom': 'on',  'casino_mode': 'on',  'netopt': '0',  'multicast_rec': 'on',  'en_multicast': '0',  'fps': '0',  'qp': 'string',  'qp_max': 'string',  'ratelimit_mode': 'true',  'ratelimit': 'string',  'bitrate': '1',  'keyframeinterval': '50',  'rtspport': '554',  'spacialfilter': '0',  'name': 'string',  'mtu': '512',  'ip': 'string',  'subnetmask': 'string',  'gateway': 'string',  'eth_negotiation': 'auto',  'features': '0',  'audioinput': 'mic',  'linein_volume': '0',  'mic_boost': '0',  'piris': 'on',  'pirispos': '0',  'ir': 'on',  'make': 'string',  'white_balance': 'on',  'wbwndctrl': 'on',  'wbwndleft': '0',  'wbwndtop': '0',  'wbwndwidth': '0',  'wbwndheight': '0',  'ntpserver_ip': 'string',  'enclosure': 'code',  'gamma': '0',  'gamma2': '0',  'bandwidthsaving': 'on',  'lowpower': 'on',  'motion_compensation': 'on',  'adjustable_ir': 'adaptive',  'irwidepos': '0',  'irtelpos': '0',  'irpos_chan1': '0',  'irpos_chan2': '0',  'snapstream': 'on',  'sensorcount': '0',  'scaling': 'on',  'sd_codec': 'jpeg',  'sd_fps': '0',  'sd_recording': 'on',  'sd_networkfail': 'on',  'sd_motionalarm': 'on',  'sd_ioalarm': 'on',  'sd_stampspan': 'true',  'sd_imgleft': '0',  'sd_imgright': '0',  'sd_imgtop': '0',  'sd_imgbottom': '0',  'sd_imgres': 'full',  'qos_enabled': '0',  'qos_video': '0',  'qos_default': '0',  'ipv6enabled': 'true',  'ipv6address': '2001:0db8:85a3:0000:0000:8a2e:0370:7334',  'ipv6prefixlen': 'string',  'ipv6dhcp': 'on',  'ipv6addresstype': 'dhcp',  'ipv6acceptrouters': 'true',  'equalbright': 'on',  'equalcolor': 'on',  'vertical_alignment': 'on',  'piris_ref_channel': '0',  'exp_ref_channel': '0'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/get?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&mac=string&model=fullname&fwversion=true&procversion=true&netversion=true&revision=true&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&make=string&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&enclosure=code&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0");
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

Return settings from the camera. In general, you should use only one of the following parameters at a time.

<h3 id="get-camera-settings-parameters">Parameters</h3>

|day_binning|in query|string|optional|
|---|---|---|---|

Enables or disables day binning mode for supported cameras.

|night_binning|in query|string|optional|
|---|---|---|---|

Enables or disables day binning mode for supported cameras.

|daynight|in query|string|optional|
|---|---|---|---|

Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.

|upscaling|in query|string|optional|
|---|---|---|---|

Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. 

|channelenable|in query|string|optional|
|---|---|---|---|

The channels you want to enable.

|brightness|in query|integer|required|
|---|---|---|---|

Sets brightness for the camera or channel.

|sharpness|in query|integer|required|
|---|---|---|---|

Sets sharpness for the camera or channel.

|saturation|in query|integer|required|
|---|---|---|---|

Sets color saturation for the camera or channel.

|blue|in query|integer|required|
|---|---|---|---|

Sets blue balance for the camera or channel.

|red|in query|integer|required|
|---|---|---|---|

Sets red balance for the camera or channel.

|illum|in query|string|required|
|---|---|---|---|

Sets illumination for the camera or channel.

|freq|in query|integer|required|
|---|---|---|---|

Mains frequency in Hz, used for indoor lighting compensation.

|lowlight|in query|string|required|
|---|---|---|---|

Exposure (low light) mode.

|shortexposures|in query|integer|required|
|---|---|---|---|

Shutter time in high-speed exposure mode, set in milliseconds.

|autoexp|in query|string|required|
|---|---|---|---|

Auto exposure mode

|exposure|in query|string|required|
|---|---|---|---|

Auto exposure mode

|expwndleft|in query|integer|optional|
|---|---|---|---|

The exposure window for the sensor.

|expwndtop|in query|integer|optional|
|---|---|---|---|

The exposure window for the sensor.

|expwndwidth|in query|integer|optional|
|---|---|---|---|

The exposure window for the sensor.

|expwndheight|in query|integer|optional|
|---|---|---|---|

The exposure window for the sensor.

|sensorleft|in query|integer|optional|
|---|---|---|---|

Sensor cropping, from the left.

|sensortop|in query|integer|optional|
|---|---|---|---|

Sensor cropping from the top.

|sensorwidth|in query|integer|optional|
|---|---|---|---|

Sensor cropping based on width. Both sides are equally cropped by half the value.

|sensorheight|in query|integer|optional|
|---|---|---|---|

Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.

|imgleft|in query|integer|optional|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgtop|in query|integer|optional|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgwidth|in query|integer|optional|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgheight|in query|integer|optional|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgquality|in query|integer|optional|
|---|---|---|---|

Image setting, used as the implcit perameter list in img.jpg image requests.

|imgres|in query|string|optional|
|---|---|---|---|

Image setting, used as the implcit perameter list in img.jpg image requests.

|mac|in query|string|optional|
|---|---|---|---|

Returns the MAC address of the camera.

|model|in query|string|optional|
|---|---|---|---|

Returns the camera's model number. `fullname` returns the camera's base model number and feature leter; `releasename` returns the manufacturer model number and feature letter — the real model number.

|fwversion|in query|boolean|optional|
|---|---|---|---|

Returns the camera's firmware version.

|procversion|in query|boolean|optional|
|---|---|---|---|

Returns the image processor version.

|netversion|in query|boolean|optional|
|---|---|---|---|

Returns the network processor version.

|revision|in query|boolean|optional|
|---|---|---|---|

Returns the PCB version.

|kneepoint|in query|integer|required|
|---|---|---|---|

Custom mode setting

|analoggain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxkneegain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxexptime|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxdigitalgain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|webserverport|in query|integer|optional|
|---|---|---|---|

The port for the camera's web server.

|admin|in query|any|optional|
|---|---|---|---|

Get or set the admin-level password.

|viewer|in query|any|optional|
|---|---|---|---|

Get or set the viewer-level password.

|maxsensorwidth|in query|integer|optional|
|---|---|---|---|

Get the maximum sensor width.

|maxsensorheight|in query|integer|optional|
|---|---|---|---|

Get the maximum sensor height.

|mdmode|in query|string|required|
|---|---|---|---|

Get or set motion alarm settings

|motiondetect|in query|string|required|
|---|---|---|---|

Get or set motion detection settings

|mdtotalzones|in query|integer|required|
|---|---|---|---|

Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.

|auxin|in query|boolean|optional|
|---|---|---|---|

Get auxin.

|auxout|in query|string|optional|
|---|---|---|---|

Get or set auxiliary audio out.

|cropping|in query|string|optional|
|---|---|---|---|

Get or set flexible cropping.

|1080p_mode|in query|string|optional|
|---|---|---|---|

Get or set 1080p mode — used in 10xx5 models only.

|pmask|in query|string|required|
|---|---|---|---|

Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.

|focus|in query|any|optional|
|---|---|---|---|

Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.

|zoom|in query|any|optional|
|---|---|---|---|

Set zoom moving steps.

|focusleft|in query|integer|optional|
|---|---|---|---|

none

|focustop|in query|integer|optional|
|---|---|---|---|

none

|focusright|in query|integer|optional|
|---|---|---|---|

none

|focusbottom|in query|integer|optional|
|---|---|---|---|

none

|focuswindow|in query|array[integer]|optional|
|---|---|---|---|

Get or set the four sides of the focus window.

|af_dn|in query|string|optional|
|---|---|---|---|

Get or set autofocus after enabling the day-night switch.

|af_zoom|in query|string|optional|
|---|---|---|---|

Get or set autofocus after zoom.

|casino_mode|in query|string|optional|
|---|---|---|---|

Get or set casino mode (1080p models only)

|netopt|in query|integer|optional|
|---|---|---|---|

Get or set network related settings. Integers correspond to the bits you want to enable or disable.

|multicast_rec|in query|string|optional|
|---|---|---|---|

Get or set the multicast reception setting.

|en_multicast|in query|integer|optional|
|---|---|---|---|

Enable multicast announcement.

|fps|in query|integer|required|
|---|---|---|---|

Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).

|qp|in query|string|required|
|---|---|---|---|

The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 

|qp_max|in query|string|optional|
|---|---|---|---|

Get or set the maximum allowed QP value — i.e. the lowest allowable quality.

|ratelimit_mode|in query|boolean|optional|
|---|---|---|---|

Get or set variable bitrate limit mode.

|ratelimit|in query|string|optional|
|---|---|---|---|

Get or set a variable bitrate limit.

|bitrate|in query|integer|required|
|---|---|---|---|

Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.

|keyframeinterval|in query|integer|optional|
|---|---|---|---|

Get or set the key frame interval.

|rtspport|in query|integer|optional|
|---|---|---|---|

Get or set the RTSP port.

|spacialfilter|in query|integer|optional|
|---|---|---|---|

Get or set the low-light noise filter.

|name|in query|string|optional|
|---|---|---|---|

Get or set the camera name.

|mtu|in query|integer|optional|
|---|---|---|---|

Get or set the MTU size.

|ip|in query|string|optional|
|---|---|---|---|

Get or set the camera's IP address.

|subnetmask|in query|string|optional|
|---|---|---|---|

Get or set the camera's subnet mask.

|gateway|in query|string|optional|
|---|---|---|---|

Get or set the camera's default gateway.

|eth_negotiation|in query|string|optional|
|---|---|---|---|

When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.

|features|in query|integer|optional|
|---|---|---|---|

Returns an integer for enabled features. Integers that are not returned are not enabled.

|audioinput|in query|string|optional|
|---|---|---|---|

The source of audio input.

|linein_volume|in query|integer|optional|
|---|---|---|---|

Volume of line-in audio.

|mic_boost|in query|integer|optional|
|---|---|---|---|

Volume of microphone-in audio.

|piris|in query|string|optional|
|---|---|---|---|

Enable/disable P-iris

|pirispos|in query|integer|optional|
|---|---|---|---|

The position P-iris closes to

|ir|in query|string|optional|
|---|---|---|---|

Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.

|make|in query|string|optional|
|---|---|---|---|

Get the make of the camera.

|white_balance|in query|string|optional|
|---|---|---|---|

White balance control.

|wbwndctrl|in query|string|optional|
|---|---|---|---|

White balance window control.

|wbwndleft|in query|integer|optional|
|---|---|---|---|

White balance window left start value. Maximum values depend on your sensor size.

|wbwndtop|in query|integer|optional|
|---|---|---|---|

White balance window top start value. Maximum values depend on your sensor size.

|wbwndwidth|in query|integer|optional|
|---|---|---|---|

White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.

|wbwndheight|in query|integer|optional|
|---|---|---|---|

White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.

|ntpserver_ip|in query|string|optional|
|---|---|---|---|

NTP server address.

|enclosure|in query|string|optional|
|---|---|---|---|

Returns the camera's model name. Provide `code` to return the model type number.

|gamma|in query|integer|optional|
|---|---|---|---|

Gamma for single sensor and Surroundvideo1 cameras.

|gamma2|in query|integer|optional|
|---|---|---|---|

Gamma for the second sensor in dual sensor cameras.

|bandwidthsaving|in query|string|optional|
|---|---|---|---|

Bandwidth saving mode settings.

|lowpower|in query|string|optional|
|---|---|---|---|

Low power mode settings.

|motion_compensation|in query|string|optional|
|---|---|---|---|

Motion compensation settings.

|adjustable_ir|in query|string|optional|
|---|---|---|---|

Adjustable IR light settings.

|irwidepos|in query|integer|optional|
|---|---|---|---|

The adjustable intensity of wide IR lights.

|irtelpos|in query|integer|optional|
|---|---|---|---|

The adjustable intensity of tele IR lights.

|irpos_chan1|in query|integer|optional|
|---|---|---|---|

Controls IR intensity on LED board 1 of FLEX model cameras.

|irpos_chan2|in query|integer|optional|
|---|---|---|---|

Controls IR intensity on LED board 2 of FLEX model cameras.

|snapstream|in query|string|optional|
|---|---|---|---|

Snapstream on/off setting.

|sensorcount|in query|integer|optional|
|---|---|---|---|

Returns the sensor count. Use the sensor count to determine the channels you want to get or set when 

|scaling|in query|string|optional|
|---|---|---|---|

Enable or disable down-scaling.

|sd_codec|in query|string|optional|
|---|---|---|---|

The codec used for video recorded to the camera's SD card.

|sd_fps|in query|integer|optional|
|---|---|---|---|

The framerate for video recorded to the camera's SD card.

|sd_recording|in query|string|optional|
|---|---|---|---|

Enables/disables continuous local recording.

|sd_networkfail|in query|string|optional|
|---|---|---|---|

Enables/disables local recording on network failure events.

|sd_motionalarm|in query|string|optional|
|---|---|---|---|

Enables/disables local recording on motion events.

|sd_ioalarm|in query|string|optional|
|---|---|---|---|

Enables/disables local recording on I/O alarm events.

|sd_stampspan|in query|boolean|optional|
|---|---|---|---|

Returns timestamps for recorded video.

|sd_imgleft|in query|integer|optional|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgright|in query|integer|optional|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgtop|in query|integer|optional|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgbottom|in query|integer|optional|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgres|in query|string|optional|
|---|---|---|---|

Determine whether to record SD images at full or half resolution.

|qos_enabled|in query|integer|optional|
|---|---|---|---|

Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. 

|qos_video|in query|integer|optional|
|---|---|---|---|

In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.

|qos_default|in query|integer|optional|
|---|---|---|---|

In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.

|ipv6enabled|in query|boolean|optional|
|---|---|---|---|

Enable/disable IPv6.

|ipv6address|in query|string(ipv6)|optional|
|---|---|---|---|

The IPv6 address for the camera.

|ipv6prefixlen|in query|string|optional|
|---|---|---|---|

The IPv6 prefix.

|ipv6dhcp|in query|string|optional|
|---|---|---|---|

Enable/disable DHCP for IPv6.

|ipv6addresstype|in query|string|optional|
|---|---|---|---|

IPv6 address type. Use `manual` to override a DHCP-set address.

|ipv6acceptrouters|in query|boolean|optional|
|---|---|---|---|

IPv6 accept routers setting.

|equalbright|in query|string|optional|
|---|---|---|---|

Equalize brightness across sensors in a multisensor camera.

|equalcolor|in query|string|optional|
|---|---|---|---|

Equalize color across sensors in a multisensor camera.

|vertical_alignment|in query|string|optional|
|---|---|---|---|

Align sensors in a multisensor camera.

|piris_ref_channel|in query|integer|optional|
|---|---|---|---|

Set the P-iris reference channel for a multi-channel camera.

|exp_ref_channel|in query|any|optional|
|---|---|---|---|

Set the exposure reference for a multi-channel camera.

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
|equalbright|on|
|equalbright|off|
|equalcolor|on|
|equalcolor|off|
|vertical_alignment|on|
|vertical_alignment|off|

> Example responses

> 200 Response

<h3 id="get-camera-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters specified in the query.|Inline|

<h3 id="get-camera-settings-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## Set Camera Settings

> Code samples

```shell
# You can also use wget
curl -X POST http://<camera IP address>/set?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0 \
  -H 'Accept: text/plain'

```

```http
POST http://<camera IP address>/set?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0 HTTP/1.1

Accept: text/plain

```

```javascript
var headers = {
  'Accept':'text/plain'

};

$.ajax({
  url: 'http://<camera IP address>/set',
  method: 'post',
  data: '?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0',
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

fetch('http://<camera IP address>/set?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0',
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
  'day_binning' => 'string',
'night_binning' => 'string',
'daynight' => 'string',
'upscaling' => 'string',
'channelenable' => 'string',
'brightness' => 'integer',
'sharpness' => 'integer',
'saturation' => 'integer',
'blue' => 'integer',
'red' => 'integer',
'illum' => 'string',
'freq' => 'integer',
'lowlight' => 'string',
'shortexposures' => 'integer',
'autoexp' => 'string',
'exposure' => 'string',
'expwndleft' => 'integer',
'expwndtop' => 'integer',
'expwndwidth' => 'integer',
'expwndheight' => 'integer',
'sensorleft' => 'integer',
'sensortop' => 'integer',
'sensorwidth' => 'integer',
'sensorheight' => 'integer',
'imgleft' => 'integer',
'imgtop' => 'integer',
'imgwidth' => 'integer',
'imgheight' => 'integer',
'imgquality' => 'integer',
'imgres' => 'string',
'kneepoint' => 'integer',
'analoggain' => 'integer',
'maxkneegain' => 'integer',
'maxexptime' => 'integer',
'maxdigitalgain' => 'integer',
'webserverport' => 'integer',
'admin' => 'any',
'viewer' => 'any',
'maxsensorwidth' => 'integer',
'maxsensorheight' => 'integer',
'mdmode' => 'string',
'motiondetect' => 'string',
'mdtotalzones' => 'integer',
'auxin' => 'boolean',
'auxout' => 'string',
'cropping' => 'string',
'1080p_mode' => 'string',
'pmask' => 'string',
'focus' => 'any',
'zoom' => 'any',
'focusleft' => 'integer',
'focustop' => 'integer',
'focusright' => 'integer',
'focusbottom' => 'integer',
'focuswindow' => 'array[integer]',
'af_dn' => 'string',
'af_zoom' => 'string',
'casino_mode' => 'string',
'netopt' => 'integer',
'multicast_rec' => 'string',
'en_multicast' => 'integer',
'fps' => 'integer',
'qp' => 'string',
'qp_max' => 'string',
'ratelimit_mode' => 'boolean',
'ratelimit' => 'string',
'bitrate' => 'integer',
'keyframeinterval' => 'integer',
'rtspport' => 'integer',
'spacialfilter' => 'integer',
'name' => 'string',
'mtu' => 'integer',
'ip' => 'string',
'subnetmask' => 'string',
'gateway' => 'string',
'eth_negotiation' => 'string',
'features' => 'integer',
'audioinput' => 'string',
'linein_volume' => 'integer',
'mic_boost' => 'integer',
'piris' => 'string',
'pirispos' => 'integer',
'ir' => 'string',
'white_balance' => 'string',
'wbwndctrl' => 'string',
'wbwndleft' => 'integer',
'wbwndtop' => 'integer',
'wbwndwidth' => 'integer',
'wbwndheight' => 'integer',
'ntpserver_ip' => 'string',
'gamma' => 'integer',
'gamma2' => 'integer',
'bandwidthsaving' => 'string',
'lowpower' => 'string',
'motion_compensation' => 'string',
'adjustable_ir' => 'string',
'irwidepos' => 'integer',
'irtelpos' => 'integer',
'irpos_chan1' => 'integer',
'irpos_chan2' => 'integer',
'snapstream' => 'string',
'sensorcount' => 'integer',
'scaling' => 'string',
'sd_codec' => 'string',
'sd_fps' => 'integer',
'sd_recording' => 'string',
'sd_networkfail' => 'string',
'sd_motionalarm' => 'string',
'sd_ioalarm' => 'string',
'sd_stampspan' => 'boolean',
'sd_imgleft' => 'integer',
'sd_imgright' => 'integer',
'sd_imgtop' => 'integer',
'sd_imgbottom' => 'integer',
'sd_imgres' => 'string',
'qos_enabled' => 'integer',
'qos_video' => 'integer',
'qos_default' => 'integer',
'ipv6enabled' => 'boolean',
'ipv6address' => 'string(ipv6)',
'ipv6prefixlen' => 'string',
'ipv6dhcp' => 'string',
'ipv6addresstype' => 'string',
'ipv6acceptrouters' => 'boolean',
'equalbright' => 'string',
'equalcolor' => 'string',
'vertical_alignment' => 'string',
'piris_ref_channel' => 'integer',
'exp_ref_channel' => 'any'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.post('http://<camera IP address>/set', params={
  'day_binning': 'on',  'night_binning': 'on',  'daynight': 'auto',  'upscaling': 'on',  'channelenable': 'string',  'brightness': '-50',  'sharpness': '0',  'saturation': '0',  'blue': '-10',  'red': '-10',  'illum': 'auto',  'freq': '50',  'lowlight': 'highspeed',  'shortexposures': '1',  'autoexp': 'on',  'exposure': 'auto',  'expwndleft': '0',  'expwndtop': '0',  'expwndwidth': '0',  'expwndheight': '0',  'sensorleft': '0',  'sensortop': '0',  'sensorwidth': '0',  'sensorheight': '0',  'imgleft': '0',  'imgtop': '0',  'imgwidth': '0',  'imgheight': '0',  'imgquality': '1',  'imgres': 'full',  'kneepoint': '1',  'analoggain': '1',  'maxkneegain': '1',  'maxexptime': '1',  'maxdigitalgain': '1',  'webserverport': '0',  'admin': 'pa$$word',  'viewer': 'pa$$word',  'maxsensorwidth': '0',  'maxsensorheight': '0',  'mdmode': 'on',  'motiondetect': 'on',  'mdtotalzones': '0',  'auxin': 'true',  'auxout': 'on',  'cropping': 'on',  '1080p_mode': 'on',  'pmask': 'on',  'focus': 'fullrange',  'zoom': 'reset',  'focusleft': '0',  'focustop': '0',  'focusright': '0',  'focusbottom': '0',  'focuswindow': [
  0,
  0,
  0,
  0
],  'af_dn': 'on',  'af_zoom': 'on',  'casino_mode': 'on',  'netopt': '0',  'multicast_rec': 'on',  'en_multicast': '0',  'fps': '0',  'qp': 'string',  'qp_max': 'string',  'ratelimit_mode': 'true',  'ratelimit': 'string',  'bitrate': '1',  'keyframeinterval': '50',  'rtspport': '554',  'spacialfilter': '0',  'name': 'string',  'mtu': '512',  'ip': 'string',  'subnetmask': 'string',  'gateway': 'string',  'eth_negotiation': 'auto',  'features': '0',  'audioinput': 'mic',  'linein_volume': '0',  'mic_boost': '0',  'piris': 'on',  'pirispos': '0',  'ir': 'on',  'white_balance': 'on',  'wbwndctrl': 'on',  'wbwndleft': '0',  'wbwndtop': '0',  'wbwndwidth': '0',  'wbwndheight': '0',  'ntpserver_ip': 'string',  'gamma': '0',  'gamma2': '0',  'bandwidthsaving': 'on',  'lowpower': 'on',  'motion_compensation': 'on',  'adjustable_ir': 'adaptive',  'irwidepos': '0',  'irtelpos': '0',  'irpos_chan1': '0',  'irpos_chan2': '0',  'snapstream': 'on',  'sensorcount': '0',  'scaling': 'on',  'sd_codec': 'jpeg',  'sd_fps': '0',  'sd_recording': 'on',  'sd_networkfail': 'on',  'sd_motionalarm': 'on',  'sd_ioalarm': 'on',  'sd_stampspan': 'true',  'sd_imgleft': '0',  'sd_imgright': '0',  'sd_imgtop': '0',  'sd_imgbottom': '0',  'sd_imgres': 'full',  'qos_enabled': '0',  'qos_video': '0',  'qos_default': '0',  'ipv6enabled': 'true',  'ipv6address': '2001:0db8:85a3:0000:0000:8a2e:0370:7334',  'ipv6prefixlen': 'string',  'ipv6dhcp': 'on',  'ipv6addresstype': 'dhcp',  'ipv6acceptrouters': 'true',  'equalbright': 'on',  'equalcolor': 'on',  'vertical_alignment': 'on',  'piris_ref_channel': '0',  'exp_ref_channel': '0'
}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://<camera IP address>/set?day_binning=on&night_binning=on&daynight=auto&upscaling=on&channelenable=string&brightness=-50&sharpness=0&saturation=0&blue=-10&red=-10&illum=auto&freq=50&lowlight=highspeed&shortexposures=1&autoexp=on&exposure=auto&expwndleft=0&expwndtop=0&expwndwidth=0&expwndheight=0&sensorleft=0&sensortop=0&sensorwidth=0&sensorheight=0&imgleft=0&imgtop=0&imgwidth=0&imgheight=0&imgquality=1&imgres=full&kneepoint=1&analoggain=1&maxkneegain=1&maxexptime=1&maxdigitalgain=1&webserverport=0&admin=pa%24%24word&viewer=pa%24%24word&maxsensorwidth=0&maxsensorheight=0&mdmode=on&motiondetect=on&mdtotalzones=0&auxin=true&auxout=on&cropping=on&1080p_mode=on&pmask=on&focus=fullrange&zoom=reset&focusleft=0&focustop=0&focusright=0&focusbottom=0&focuswindow=0,0,0,0&af_dn=on&af_zoom=on&casino_mode=on&netopt=0&multicast_rec=on&en_multicast=0&fps=0&qp=string&qp_max=string&ratelimit_mode=true&ratelimit=string&bitrate=1&keyframeinterval=50&rtspport=554&spacialfilter=0&name=string&mtu=512&ip=string&subnetmask=string&gateway=string&eth_negotiation=auto&features=0&audioinput=mic&linein_volume=0&mic_boost=0&piris=on&pirispos=0&ir=on&white_balance=on&wbwndctrl=on&wbwndleft=0&wbwndtop=0&wbwndwidth=0&wbwndheight=0&ntpserver_ip=string&gamma=0&gamma2=0&bandwidthsaving=on&lowpower=on&motion_compensation=on&adjustable_ir=adaptive&irwidepos=0&irtelpos=0&irpos_chan1=0&irpos_chan2=0&snapstream=on&sensorcount=0&scaling=on&sd_codec=jpeg&sd_fps=0&sd_recording=on&sd_networkfail=on&sd_motionalarm=on&sd_ioalarm=on&sd_stampspan=true&sd_imgleft=0&sd_imgright=0&sd_imgtop=0&sd_imgbottom=0&sd_imgres=full&qos_enabled=0&qos_video=0&qos_default=0&ipv6enabled=true&ipv6address=2001%3A0db8%3A85a3%3A0000%3A0000%3A8a2e%3A0370%3A7334&ipv6prefixlen=string&ipv6dhcp=on&ipv6addresstype=dhcp&ipv6acceptrouters=true&equalbright=on&equalcolor=on&vertical_alignment=on&piris_ref_channel=0&exp_ref_channel=0");
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

Set camera settings.

<h3 id="set-camera-settings-parameters">Parameters</h3>

|day_binning|in query|string|required|
|---|---|---|---|

Enables or disables day binning mode for supported cameras.

|night_binning|in query|string|required|
|---|---|---|---|

Enables or disables day binning mode for supported cameras.

|daynight|in query|string|required|
|---|---|---|---|

Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.

|upscaling|in query|string|required|
|---|---|---|---|

Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. 

|channelenable|in query|string|required|
|---|---|---|---|

The channels you want to enable.

|brightness|in query|integer|required|
|---|---|---|---|

Sets brightness for the camera or channel.

|sharpness|in query|integer|required|
|---|---|---|---|

Sets sharpness for the camera or channel.

|saturation|in query|integer|required|
|---|---|---|---|

Sets color saturation for the camera or channel.

|blue|in query|integer|required|
|---|---|---|---|

Sets blue balance for the camera or channel.

|red|in query|integer|required|
|---|---|---|---|

Sets red balance for the camera or channel.

|illum|in query|string|required|
|---|---|---|---|

Sets illumination for the camera or channel.

|freq|in query|integer|required|
|---|---|---|---|

Mains frequency in Hz, used for indoor lighting compensation.

|lowlight|in query|string|required|
|---|---|---|---|

Exposure (low light) mode.

|shortexposures|in query|integer|required|
|---|---|---|---|

Shutter time in high-speed exposure mode, set in milliseconds.

|autoexp|in query|string|required|
|---|---|---|---|

Auto exposure mode

|exposure|in query|string|required|
|---|---|---|---|

Auto exposure mode

|expwndleft|in query|integer|required|
|---|---|---|---|

The exposure window for the sensor.

|expwndtop|in query|integer|required|
|---|---|---|---|

The exposure window for the sensor.

|expwndwidth|in query|integer|required|
|---|---|---|---|

The exposure window for the sensor.

|expwndheight|in query|integer|required|
|---|---|---|---|

The exposure window for the sensor.

|sensorleft|in query|integer|required|
|---|---|---|---|

Sensor cropping, from the left.

|sensortop|in query|integer|required|
|---|---|---|---|

Sensor cropping from the top.

|sensorwidth|in query|integer|required|
|---|---|---|---|

Sensor cropping based on width. Both sides are equally cropped by half the value.

|sensorheight|in query|integer|required|
|---|---|---|---|

Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.

|imgleft|in query|integer|required|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgtop|in query|integer|required|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgwidth|in query|integer|required|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgheight|in query|integer|required|
|---|---|---|---|

Image setting, used as the implcit perameter in img.jpg image requests.

|imgquality|in query|integer|required|
|---|---|---|---|

Image setting, used as the implcit perameter list in img.jpg image requests.

|imgres|in query|string|required|
|---|---|---|---|

Image setting, used as the implcit perameter list in img.jpg image requests.

|kneepoint|in query|integer|required|
|---|---|---|---|

Custom mode setting

|analoggain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxkneegain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxexptime|in query|integer|required|
|---|---|---|---|

Custom mode setting

|maxdigitalgain|in query|integer|required|
|---|---|---|---|

Custom mode setting

|webserverport|in query|integer|required|
|---|---|---|---|

The port for the camera's web server.

|admin|in query|any|required|
|---|---|---|---|

Get or set the admin-level password.

|viewer|in query|any|required|
|---|---|---|---|

Get or set the viewer-level password.

|maxsensorwidth|in query|integer|required|
|---|---|---|---|

Get the maximum sensor width.

|maxsensorheight|in query|integer|required|
|---|---|---|---|

Get the maximum sensor height.

|mdmode|in query|string|required|
|---|---|---|---|

Get or set motion alarm settings

|motiondetect|in query|string|required|
|---|---|---|---|

Get or set motion detection settings

|mdtotalzones|in query|integer|required|
|---|---|---|---|

Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.

|auxin|in query|boolean|required|
|---|---|---|---|

Get auxin.

|auxout|in query|string|required|
|---|---|---|---|

Get or set auxiliary audio out.

|cropping|in query|string|required|
|---|---|---|---|

Get or set flexible cropping.

|1080p_mode|in query|string|required|
|---|---|---|---|

Get or set 1080p mode — used in 10xx5 models only.

|pmask|in query|string|required|
|---|---|---|---|

Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.

|focus|in query|any|required|
|---|---|---|---|

Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.

|zoom|in query|any|required|
|---|---|---|---|

Set zoom moving steps.

|focusleft|in query|integer|required|
|---|---|---|---|

none

|focustop|in query|integer|required|
|---|---|---|---|

none

|focusright|in query|integer|required|
|---|---|---|---|

none

|focusbottom|in query|integer|required|
|---|---|---|---|

none

|focuswindow|in query|array[integer]|required|
|---|---|---|---|

Get or set the four sides of the focus window.

|af_dn|in query|string|required|
|---|---|---|---|

Get or set autofocus after enabling the day-night switch.

|af_zoom|in query|string|required|
|---|---|---|---|

Get or set autofocus after zoom.

|casino_mode|in query|string|required|
|---|---|---|---|

Get or set casino mode (1080p models only)

|netopt|in query|integer|required|
|---|---|---|---|

Get or set network related settings. Integers correspond to the bits you want to enable or disable.

|multicast_rec|in query|string|required|
|---|---|---|---|

Get or set the multicast reception setting.

|en_multicast|in query|integer|required|
|---|---|---|---|

Enable multicast announcement.

|fps|in query|integer|required|
|---|---|---|---|

Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).

|qp|in query|string|required|
|---|---|---|---|

The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 

|qp_max|in query|string|required|
|---|---|---|---|

Get or set the maximum allowed QP value — i.e. the lowest allowable quality.

|ratelimit_mode|in query|boolean|required|
|---|---|---|---|

Get or set variable bitrate limit mode.

|ratelimit|in query|string|required|
|---|---|---|---|

Get or set a variable bitrate limit.

|bitrate|in query|integer|required|
|---|---|---|---|

Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.

|keyframeinterval|in query|integer|required|
|---|---|---|---|

Get or set the key frame interval.

|rtspport|in query|integer|required|
|---|---|---|---|

Get or set the RTSP port.

|spacialfilter|in query|integer|required|
|---|---|---|---|

Get or set the low-light noise filter.

|name|in query|string|required|
|---|---|---|---|

Get or set the camera name.

|mtu|in query|integer|required|
|---|---|---|---|

Get or set the MTU size.

|ip|in query|string|required|
|---|---|---|---|

Get or set the camera's IP address.

|subnetmask|in query|string|required|
|---|---|---|---|

Get or set the camera's subnet mask.

|gateway|in query|string|required|
|---|---|---|---|

Get or set the camera's default gateway.

|eth_negotiation|in query|string|required|
|---|---|---|---|

When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.

|features|in query|integer|required|
|---|---|---|---|

Returns an integer for enabled features. Integers that are not returned are not enabled.

|audioinput|in query|string|required|
|---|---|---|---|

The source of audio input.

|linein_volume|in query|integer|required|
|---|---|---|---|

Volume of line-in audio.

|mic_boost|in query|integer|required|
|---|---|---|---|

Volume of microphone-in audio.

|piris|in query|string|required|
|---|---|---|---|

Enable/disable P-iris

|pirispos|in query|integer|required|
|---|---|---|---|

The position P-iris closes to

|ir|in query|string|required|
|---|---|---|---|

Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.

|white_balance|in query|string|required|
|---|---|---|---|

White balance control.

|wbwndctrl|in query|string|required|
|---|---|---|---|

White balance window control.

|wbwndleft|in query|integer|required|
|---|---|---|---|

White balance window left start value. Maximum values depend on your sensor size.

|wbwndtop|in query|integer|required|
|---|---|---|---|

White balance window top start value. Maximum values depend on your sensor size.

|wbwndwidth|in query|integer|required|
|---|---|---|---|

White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.

|wbwndheight|in query|integer|required|
|---|---|---|---|

White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.

|ntpserver_ip|in query|string|required|
|---|---|---|---|

NTP server address.

|gamma|in query|integer|required|
|---|---|---|---|

Gamma for single sensor and Surroundvideo1 cameras.

|gamma2|in query|integer|required|
|---|---|---|---|

Gamma for the second sensor in dual sensor cameras.

|bandwidthsaving|in query|string|required|
|---|---|---|---|

Bandwidth saving mode settings.

|lowpower|in query|string|required|
|---|---|---|---|

Low power mode settings.

|motion_compensation|in query|string|required|
|---|---|---|---|

Motion compensation settings.

|adjustable_ir|in query|string|required|
|---|---|---|---|

Adjustable IR light settings.

|irwidepos|in query|integer|required|
|---|---|---|---|

The adjustable intensity of wide IR lights.

|irtelpos|in query|integer|required|
|---|---|---|---|

The adjustable intensity of tele IR lights.

|irpos_chan1|in query|integer|required|
|---|---|---|---|

Controls IR intensity on LED board 1 of FLEX model cameras.

|irpos_chan2|in query|integer|required|
|---|---|---|---|

Controls IR intensity on LED board 2 of FLEX model cameras.

|snapstream|in query|string|required|
|---|---|---|---|

Snapstream on/off setting.

|sensorcount|in query|integer|required|
|---|---|---|---|

Returns the sensor count. Use the sensor count to determine the channels you want to get or set when 

|scaling|in query|string|required|
|---|---|---|---|

Enable or disable down-scaling.

|sd_codec|in query|string|required|
|---|---|---|---|

The codec used for video recorded to the camera's SD card.

|sd_fps|in query|integer|required|
|---|---|---|---|

The framerate for video recorded to the camera's SD card.

|sd_recording|in query|string|required|
|---|---|---|---|

Enables/disables continuous local recording.

|sd_networkfail|in query|string|required|
|---|---|---|---|

Enables/disables local recording on network failure events.

|sd_motionalarm|in query|string|required|
|---|---|---|---|

Enables/disables local recording on motion events.

|sd_ioalarm|in query|string|required|
|---|---|---|---|

Enables/disables local recording on I/O alarm events.

|sd_stampspan|in query|boolean|required|
|---|---|---|---|

Returns timestamps for recorded video.

|sd_imgleft|in query|integer|required|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgright|in query|integer|required|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgtop|in query|integer|required|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgbottom|in query|integer|required|
|---|---|---|---|

Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.

|sd_imgres|in query|string|required|
|---|---|---|---|

Determine whether to record SD images at full or half resolution.

|qos_enabled|in query|integer|required|
|---|---|---|---|

Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. 

|qos_video|in query|integer|required|
|---|---|---|---|

In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.

|qos_default|in query|integer|required|
|---|---|---|---|

In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.

|ipv6enabled|in query|boolean|required|
|---|---|---|---|

Enable/disable IPv6.

|ipv6address|in query|string(ipv6)|required|
|---|---|---|---|

The IPv6 address for the camera.

|ipv6prefixlen|in query|string|required|
|---|---|---|---|

The IPv6 prefix.

|ipv6dhcp|in query|string|required|
|---|---|---|---|

Enable/disable DHCP for IPv6.

|ipv6addresstype|in query|string|required|
|---|---|---|---|

IPv6 address type. Use `manual` to override a DHCP-set address.

|ipv6acceptrouters|in query|boolean|required|
|---|---|---|---|

IPv6 accept routers setting.

|equalbright|in query|string|required|
|---|---|---|---|

Equalize brightness across sensors in a multisensor camera.

|equalcolor|in query|string|required|
|---|---|---|---|

Equalize color across sensors in a multisensor camera.

|vertical_alignment|in query|string|required|
|---|---|---|---|

Align sensors in a multisensor camera.

|piris_ref_channel|in query|integer|required|
|---|---|---|---|

Set the P-iris reference channel for a multi-channel camera.

|exp_ref_channel|in query|any|required|
|---|---|---|---|

Set the exposure reference for a multi-channel camera.

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
|equalbright|on|
|equalbright|off|
|equalcolor|on|
|equalcolor|off|
|vertical_alignment|on|
|vertical_alignment|off|

> Example responses

> 200 Response

<h3 id="set-camera-settings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the parameters set in the request.|Inline|

<h3 id="set-camera-settings-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="av-http-1-1-audio">Audio</h1>

Get and set audio configuration

## Transmit Audio to Line Out

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

Transmits continuous G.711 Audio to Arecont Vision cameras.

> Example responses

> 200 Response

<h3 id="transmit-audio-to-line-out-responses">Responses</h3>

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
"on"

```

*Enable/disable DHCP for IPv6.
*

### Properties

|---|---|---|
|ipv6dhcp|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSipv6addresstype">ipv6addresstype</h2>

<a id="schemaipv6addresstype"></a>

```json
"dhcp"

```

*IPv6 address type. Use `manual` to override a DHCP-set address.
*

### Properties

|---|---|---|
|ipv6addresstype|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|dhcp|
|*anonymous*|manual|

<h2 id="tocSipv6acceptrouters">ipv6acceptrouters</h2>

<a id="schemaipv6acceptrouters"></a>

```json
true

```

*IPv6 accept routers setting.
*

### Properties

|---|---|---|
|ipv6acceptrouters|boolean|false|

<h2 id="tocSipv6enabled">ipv6enabled</h2>

<a id="schemaipv6enabled"></a>

```json
true

```

*Enable/disable IPv6.
*

### Properties

|---|---|---|
|ipv6enabled|boolean|false|

<h2 id="tocSipv6address">ipv6address</h2>

<a id="schemaipv6address"></a>

```json
"2001:0db8:85a3:0000:0000:8a2e:0370:7334"

```

*The IPv6 address for the camera.
*

### Properties

|---|---|---|
|ipv6address|string(ipv6)|false|

<h2 id="tocSipv6prefixlen">ipv6prefixlen</h2>

<a id="schemaipv6prefixlen"></a>

```json
"string"

```

*The IPv6 prefix.
*

### Properties

|---|---|---|
|ipv6prefixlen|string|false|

<h2 id="tocSscaling">scaling</h2>

<a id="schemascaling"></a>

```json
"on"

```

*Enable or disable down-scaling.*

### Properties

|---|---|---|
|scaling|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSscaling_size">scaling_size</h2>

<a id="schemascaling_size"></a>

```json
"string"

```

*Set scaling size as `width, height`. Width ranges from 128 to 1280; height ranges from 96 to 720.*

### Properties

|---|---|---|
|scaling_size|string|false|

<h2 id="tocSqos_enabled">qos_enabled</h2>

<a id="schemaqos_enabled"></a>

```json
0

```

*Arecont Vision cameras support RFC 2474 “Definition of the Differentiated services field (DS field) in the IPv4 and IPv6 headers”, which is widely adopted by router manufacturers to implement quality of service (QoS) mechanism. 

Enable or disable quality of service (QOS).
*

### Properties

|---|---|---|
|qos_enabled|integer|false|

<h2 id="tocSqos_video">qos_video</h2>

<a id="schemaqos_video"></a>

```json
0

```

*In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop.
*

### Properties

|---|---|---|
|qos_video|integer|false|

<h2 id="tocSqos_default">qos_default</h2>

<a id="schemaqos_default"></a>

```json
0

```

*In Arecont Vision cameras, Per-Hop Behavior (PHB) type Assured Forwarding (AF) is the default PHB for video streaming over RTP. The recommended default Differentiated Services Code Point (DSCP) of AF is 34, which means low drop. All other traffic uses default PHB with DSCP value 0.
*

### Properties

|---|---|---|
|qos_default|integer|false|

<h2 id="tocSsd_codec">sd_codec</h2>

<a id="schemasd_codec"></a>

```json
"jpeg"

```

*The codec used for video recorded to the camera's SD card.*

### Properties

|---|---|---|
|sd_codec|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|jpeg|
|*anonymous*|h264|

<h2 id="tocSsd_fps">sd_fps</h2>

<a id="schemasd_fps"></a>

```json
0

```

*The framerate for video recorded to the camera's SD card.*

### Properties

|---|---|---|
|sd_fps|integer|false|

<h2 id="tocSsd_playback_fps">sd_playback_fps</h2>

<a id="schemasd_playback_fps"></a>

```json
0

```

*Used to playback video from SD cards in 4k models. For 4K models, you do not “download” video from the SD card. Instead, you dynamically controll the playback framerate.*

### Properties

|---|---|---|
|sd_playback_fps|integer|false|

<h2 id="tocSsd_recording">sd_recording</h2>

<a id="schemasd_recording"></a>

```json
"on"

```

*Enables/disables continuous local recording.*

### Properties

|---|---|---|
|sd_recording|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd_networkfail">sd_networkfail</h2>

<a id="schemasd_networkfail"></a>

```json
"on"

```

*Enables/disables local recording on network failure events.*

### Properties

|---|---|---|
|sd_networkfail|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd_motionalarm">sd_motionalarm</h2>

<a id="schemasd_motionalarm"></a>

```json
"on"

```

*Enables/disables local recording on motion events.*

### Properties

|---|---|---|
|sd_motionalarm|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd_ioalarm">sd_ioalarm</h2>

<a id="schemasd_ioalarm"></a>

```json
"on"

```

*Enables/disables local recording on I/O alarm events.*

### Properties

|---|---|---|
|sd_ioalarm|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd_stampspan">sd_stampspan</h2>

<a id="schemasd_stampspan"></a>

```json
true

```

*Returns timestamps for recorded video.*

### Properties

|---|---|---|
|sd_stampspan|boolean|false|

<h2 id="tocSsd_playbackstamp">sd_playbackstamp</h2>

<a id="schemasd_playbackstamp"></a>

```json
"on"

```

*Playback video for the recorded timestamps - `beginningTime, endingTime`. If you don't specify the `endTime` or set `0` for the end time, the camera will play until the end of recorded video.*

### Properties

|---|---|---|
|sd_playbackstamp|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd">sd</h2>

<a id="schemasd"></a>

```json
"on"

```

*Request images/video recorded on the SD card (local recording). `playback` plays back video in real time; `download` lets you stream video as fast as possible. Do not provide other parameters when reqeusting video recorded locally. 
*

### Properties

|---|---|---|
|sd|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsd_imgleft">sd_imgleft</h2>

<a id="schemasd_imgleft"></a>

```json
0

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

|---|---|---|
|sd_imgleft|integer|false|

<h2 id="tocSsd_imgright">sd_imgright</h2>

<a id="schemasd_imgright"></a>

```json
0

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

|---|---|---|
|sd_imgright|integer|false|

<h2 id="tocSsd_imgtop">sd_imgtop</h2>

<a id="schemasd_imgtop"></a>

```json
0

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

|---|---|---|
|sd_imgtop|integer|false|

<h2 id="tocSsd_imgbottom">sd_imgbottom</h2>

<a id="schemasd_imgbottom"></a>

```json
0

```

*Select a region of video that you want ot record to the SD card. You should set this parameter before you turn on local recording.*

### Properties

|---|---|---|
|sd_imgbottom|integer|false|

<h2 id="tocSsd_imgres">sd_imgres</h2>

<a id="schemasd_imgres"></a>

```json
"full"

```

*Determine whether to record SD images at full or half resolution.*

### Properties

|---|---|---|
|sd_imgres|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|full|
|*anonymous*|half|

<h2 id="tocSirpos_chan1">irpos_chan1</h2>

<a id="schemairpos_chan1"></a>

```json
0

```

*Controls IR intensity on LED board 1 of FLEX model cameras.
*

### Properties

|---|---|---|
|irpos_chan1|integer|false|

<h2 id="tocSirpos_chan2">irpos_chan2</h2>

<a id="schemairpos_chan2"></a>

```json
0

```

*Controls IR intensity on LED board 2 of FLEX model cameras.
*

### Properties

|---|---|---|
|irpos_chan2|integer|false|

<h2 id="tocSkneepoint">kneepoint</h2>

<a id="schemakneepoint"></a>

```json
1

```

*Custom mode setting
*

### Properties

|---|---|---|
|kneepoint|integer|false|

<h2 id="tocSanaloggain">analoggain</h2>

<a id="schemaanaloggain"></a>

```json
1

```

*Custom mode setting
*

### Properties

|---|---|---|
|analoggain|integer|false|

<h2 id="tocSmaxkneegain">maxkneegain</h2>

<a id="schemamaxkneegain"></a>

```json
1

```

*Custom mode setting
*

### Properties

|---|---|---|
|maxkneegain|integer|false|

<h2 id="tocSmaxexptime">maxexptime</h2>

<a id="schemamaxexptime"></a>

```json
1

```

*Custom mode setting
*

### Properties

|---|---|---|
|maxexptime|integer|false|

<h2 id="tocSmaxdigitalgain">maxdigitalgain</h2>

<a id="schemamaxdigitalgain"></a>

```json
1

```

*Custom mode setting
*

### Properties

|---|---|---|
|maxdigitalgain|integer|false|

<h2 id="tocSday_binning">day_binning</h2>

<a id="schemaday_binning"></a>

```json
"on"

```

*Enables or disables day binning mode for supported cameras.
*

### Properties

|---|---|---|
|day_binning|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSnight_binning">night_binning</h2>

<a id="schemanight_binning"></a>

```json
"on"

```

*Enables or disables day binning mode for supported cameras.
*

### Properties

|---|---|---|
|night_binning|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSdaynight">daynight</h2>

<a id="schemadaynight"></a>

```json
"auto"

```

*Sets day/night mode. Cameras default to `auto`, which sets day and night modes automatically. `dual` allows the client to pull both color and grayscale images simultaneously.*

### Properties

|---|---|---|
|daynight|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|auto|
|*anonymous*|day|
|*anonymous*|night|
|*anonymous*|dual|

<h2 id="tocSupscaling">upscaling</h2>

<a id="schemaupscaling"></a>

```json
"on"

```

*Scales monocrome images to the same size as color images. If upscaling is disabled, the ratio is 1.6 between color images and monochrome images. 
*

### Properties

|---|---|---|
|upscaling|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSchannelenable">channelenable</h2>

<a id="schemachannelenable"></a>

```json
"string"

```

*The channels you want to enable.*

### Properties

|---|---|---|
|channelenable|string|false|

<h2 id="tocSrotate">rotate</h2>

<a id="schemarotate"></a>

```json
0

```

*Sets the rotation of the image in 90 degree increments. 90 and 270 degree rotations are available in newer models; get features to determine whether or not your camera supports these values.
*

### Properties

|---|---|---|
|rotate|integer|false|

<h2 id="tocSbrightness">brightness</h2>

<a id="schemabrightness"></a>

```json
-50

```

*Sets brightness for the camera or channel.*

### Properties

|---|---|---|
|brightness|integer|false|

<h2 id="tocSsharpness">sharpness</h2>

<a id="schemasharpness"></a>

```json
0

```

*Sets sharpness for the camera or channel.*

### Properties

|---|---|---|
|sharpness|integer|false|

<h2 id="tocSsaturation">saturation</h2>

<a id="schemasaturation"></a>

```json
0

```

*Sets color saturation for the camera or channel.*

### Properties

|---|---|---|
|saturation|integer|false|

<h2 id="tocSblue">blue</h2>

<a id="schemablue"></a>

```json
-10

```

*Sets blue balance for the camera or channel.*

### Properties

|---|---|---|
|blue|integer|false|

<h2 id="tocSred">red</h2>

<a id="schemared"></a>

```json
-10

```

*Sets red balance for the camera or channel.*

### Properties

|---|---|---|
|red|integer|false|

<h2 id="tocSillum">illum</h2>

<a id="schemaillum"></a>

```json
"auto"

```

*Sets illumination for the camera or channel.*

### Properties

|---|---|---|
|illum|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|auto|
|*anonymous*|indoor|
|*anonymous*|outdoor|
|*anonymous*|mlx|

<h2 id="tocSfreq">freq</h2>

<a id="schemafreq"></a>

```json
50

```

*Mains frequency in Hz, used for indoor lighting compensation.*

### Properties

|---|---|---|
|freq|integer|false|

<h2 id="tocSlowlight">lowlight</h2>

<a id="schemalowlight"></a>

```json
"highspeed"

```

*Exposure (low light) mode.*

### Properties

|---|---|---|
|lowlight|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|highspeed|
|*anonymous*|speed|
|*anonymous*|balance|
|*anonymous*|quality|
|*anonymous*|moonlight|

<h2 id="tocSshortexposures">shortexposures</h2>

<a id="schemashortexposures"></a>

```json
1

```

*Shutter time in high-speed exposure mode, set in milliseconds.*

### Properties

|---|---|---|
|shortexposures|integer|false|

<h2 id="tocSexposure">exposure</h2>

<a id="schemaexposure"></a>

```json
"auto"

```

*Auto exposure mode*

### Properties

|---|---|---|
|exposure|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|auto|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSautoexp">autoexp</h2>

<a id="schemaautoexp"></a>

```json
"on"

```

*Auto exposure mode*

### Properties

|---|---|---|
|autoexp|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSexpwndleft">expwndleft</h2>

<a id="schemaexpwndleft"></a>

```json
0

```

*The exposure window for the sensor.*

### Properties

|---|---|---|
|expwndleft|integer|false|

<h2 id="tocSexpwndtop">expwndtop</h2>

<a id="schemaexpwndtop"></a>

```json
0

```

*The exposure window for the sensor.*

### Properties

|---|---|---|
|expwndtop|integer|false|

<h2 id="tocSexpwndwidth">expwndwidth</h2>

<a id="schemaexpwndwidth"></a>

```json
0

```

*The exposure window for the sensor.*

### Properties

|---|---|---|
|expwndwidth|integer|false|

<h2 id="tocSexpwndheight">expwndheight</h2>

<a id="schemaexpwndheight"></a>

```json
0

```

*The exposure window for the sensor.*

### Properties

|---|---|---|
|expwndheight|integer|false|

<h2 id="tocSsensorleft">sensorleft</h2>

<a id="schemasensorleft"></a>

```json
0

```

*Sensor cropping, from the left.*

### Properties

|---|---|---|
|sensorleft|integer|false|

<h2 id="tocSsensortop">sensortop</h2>

<a id="schemasensortop"></a>

```json
0

```

*Sensor cropping from the top.*

### Properties

|---|---|---|
|sensortop|integer|false|

<h2 id="tocSsensorwidth">sensorwidth</h2>

<a id="schemasensorwidth"></a>

```json
0

```

*Sensor cropping based on width. Both sides are equally cropped by half the value.*

### Properties

|---|---|---|
|sensorwidth|integer|false|

<h2 id="tocSsensorheight">sensorheight</h2>

<a id="schemasensorheight"></a>

```json
0

```

*Sensor cropping based on height. The top and bottom are equally cropped by half the value, centering the image.*

### Properties

|---|---|---|
|sensorheight|integer|false|

<h2 id="tocSimgleft">imgleft</h2>

<a id="schemaimgleft"></a>

```json
0

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

|---|---|---|
|imgleft|integer|false|

<h2 id="tocSimgtop">imgtop</h2>

<a id="schemaimgtop"></a>

```json
0

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

|---|---|---|
|imgtop|integer|false|

<h2 id="tocSimgwidth">imgwidth</h2>

<a id="schemaimgwidth"></a>

```json
0

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

|---|---|---|
|imgwidth|integer|false|

<h2 id="tocSimgheight">imgheight</h2>

<a id="schemaimgheight"></a>

```json
0

```

*Image setting, used as the implcit perameter in img.jpg image requests.*

### Properties

|---|---|---|
|imgheight|integer|false|

<h2 id="tocSimgquality">imgquality</h2>

<a id="schemaimgquality"></a>

```json
1

```

*Image setting, used as the implcit perameter list in img.jpg image requests.*

### Properties

|---|---|---|
|imgquality|integer|false|

<h2 id="tocSimgres">imgres</h2>

<a id="schemaimgres"></a>

```json
"full"

```

*Image setting, used as the implcit perameter list in img.jpg image requests.*

### Properties

|---|---|---|
|imgres|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|full|
|*anonymous*|half|

<h2 id="tocSmac">mac</h2>

<a id="schemamac"></a>

```json
"string"

```

*Returns the MAC address of the camera.*

### Properties

|---|---|---|
|mac|string|false|

<h2 id="tocSmodel">model</h2>

<a id="schemamodel"></a>

```json
"fullname"

```

*Returns the camera's model number. `fullname` returns the camera's base model number and feature leter; `releasename` returns the manufacturer model number and feature letter — the real model number.*

### Properties

|---|---|---|
|model|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|fullname|
|*anonymous*|releasename|
|*anonymous*|lpn|
|*anonymous*|internal|

<h2 id="tocSfwversion">fwversion</h2>

<a id="schemafwversion"></a>

```json
true

```

*Returns the camera's firmware version.*

### Properties

|---|---|---|
|fwversion|boolean|false|

<h2 id="tocSprocversion">procversion</h2>

<a id="schemaprocversion"></a>

```json
true

```

*Returns the image processor version.*

### Properties

|---|---|---|
|procversion|boolean|false|

<h2 id="tocSnetversion">netversion</h2>

<a id="schemanetversion"></a>

```json
true

```

*Returns the network processor version.*

### Properties

|---|---|---|
|netversion|boolean|false|

<h2 id="tocSrevision">revision</h2>

<a id="schemarevision"></a>

```json
true

```

*Returns the PCB version.*

### Properties

|---|---|---|
|revision|boolean|false|

<h2 id="tocSparams">params</h2>

<a id="schemaparams"></a>

```json
"save"

```

*Perform basic camera actions

* save - commits current settings to flash memory
* factory - restore factory default settings
* reboot - restarts the camera
*

### Properties

|---|---|---|
|params|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|save|
|*anonymous*|factory|
|*anonymous*|reboot|

<h2 id="tocSwebserverport">webserverport</h2>

<a id="schemawebserverport"></a>

```json
0

```

*The port for the camera's web server.*

### Properties

|---|---|---|
|webserverport|integer|false|

<h2 id="tocSadmin">admin</h2>

<a id="schemaadmin"></a>

```json
"pa$$word"

```

*Get or set the admin-level password. Use the word 'empty' to reset the password.*

### Properties

|---|---|---|
|admin|string(password)|false|

<h2 id="tocSviewer">viewer</h2>

<a id="schemaviewer"></a>

```json
"pa$$word"

```

*Get or set the viewer-level password. Use the word 'empty' to reset the password.*

### Properties

|---|---|---|
|viewer|string(password)|false|

<h2 id="tocSmaxsensorwidth">maxsensorwidth</h2>

<a id="schemamaxsensorwidth"></a>

```json
0

```

*Get the maximum sensor width.*

### Properties

|---|---|---|
|maxsensorwidth|integer|false|

<h2 id="tocSmaxsensorheight">maxsensorheight</h2>

<a id="schemamaxsensorheight"></a>

```json
0

```

*Get the maximum sensor height.*

### Properties

|---|---|---|
|maxsensorheight|integer|false|

<h2 id="tocSmdmode">mdmode</h2>

<a id="schemamdmode"></a>

```json
"on"

```

*Get or set motion alarm settings*

### Properties

|---|---|---|
|mdmode|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSmotiondetect">motiondetect</h2>

<a id="schemamotiondetect"></a>

```json
"on"

```

*Get or set motion detection settings*

### Properties

|---|---|---|
|motiondetect|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSmdtotalzones">mdtotalzones</h2>

<a id="schemamdtotalzones"></a>

```json
0

```

*Set regular (64) or extended motion detection mode (1024). 4k cameras support motion detection in extended mode either.*

### Properties

|---|---|---|
|mdtotalzones|integer|false|

<h2 id="tocSmdzonesize">mdzonesize</h2>

<a id="schemamdzonesize"></a>

```json
1

```

*Set motion detection zone size.*

### Properties

|---|---|---|
|mdzonesize|integer|false|

<h2 id="tocSmdlevelthreshold">mdlevelthreshold</h2>

<a id="schemamdlevelthreshold"></a>

```json
2

```

*Motion detection zone threshold*

### Properties

|---|---|---|
|mdlevelthreshold|integer|false|

<h2 id="tocSmddetail">mddetail</h2>

<a id="schemamddetail"></a>

```json
1

```

*Motion detection zone detail*

### Properties

|---|---|---|
|mddetail|integer|false|

<h2 id="tocSmdprivacymask">mdprivacymask</h2>

<a id="schemamdprivacymask"></a>

```json
0

```

*Motion detection privacy mask*

### Properties

|---|---|---|
|mdprivacymask|integer|false|

<h2 id="tocSmdresult">mdresult</h2>

<a id="schemamdresult"></a>

```json
"string"

```

*Motion detection zone result*

### Properties

|---|---|---|
|mdresult|string|false|

<h2 id="tocSauxin">auxin</h2>

<a id="schemaauxin"></a>

```json
true

```

*Get auxin.*

### Properties

|---|---|---|
|auxin|boolean|false|

<h2 id="tocSauxout">auxout</h2>

<a id="schemaauxout"></a>

```json
"on"

```

*Get or set auxiliary audio out.*

### Properties

|---|---|---|
|auxout|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocScropping">cropping</h2>

<a id="schemacropping"></a>

```json
"on"

```

*Get or set flexible cropping.
*

### Properties

|---|---|---|
|cropping|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocS1080p_mode">1080p_mode</h2>

<a id="schema1080p_mode"></a>

```json
"on"

```

*Get or set 1080p mode — used in 10xx5 models only.
*

### Properties

|---|---|---|
|1080p_mode|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSpmask">pmask</h2>

<a id="schemapmask"></a>

```json
"on"

```

*Get or set the privacy mask. Use `pmask<direction>` to set the privacy mask block.
*

### Properties

|---|---|---|
|pmask|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSpmaskleft">pmaskleft</h2>

<a id="schemapmaskleft"></a>

```json
0

```

*Get, set, or erace a privacy mask block (32 x 32 pixels per block).
*

### Properties

|---|---|---|
|pmaskleft|integer|false|

<h2 id="tocSpmaskright">pmaskright</h2>

<a id="schemapmaskright"></a>

```json
0

```

*Get, set, or erace a privacy mask block (32 x 32 pixels per block).
*

### Properties

|---|---|---|
|pmaskright|integer|false|

<h2 id="tocSpmasktop">pmasktop</h2>

<a id="schemapmasktop"></a>

```json
0

```

*Get, set, or erace a privacy mask block (32 x 32 pixels per block).
*

### Properties

|---|---|---|
|pmasktop|integer|false|

<h2 id="tocSpmaskbottom">pmaskbottom</h2>

<a id="schemapmaskbottom"></a>

```json
0

```

*Get, set, or erace a privacy mask block (32 x 32 pixels per block).
*

### Properties

|---|---|---|
|pmaskbottom|integer|false|

<h2 id="tocSpmaskblock">pmaskblock</h2>

<a id="schemapmaskblock"></a>

```json
"on"

```

*Set the privacy mask block.
*

### Properties

|---|---|---|
|pmaskblock|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSfocus">focus</h2>

<a id="schemafocus"></a>

```json
"fullrange"

```

*Get or set focus moving steps. After setting focus/zoom, the new focus becomes valid after the next frame.
*

### Properties

*oneOf*

|---|---|---|
|focus|string|false|

*xor*

|---|---|---|
|focus|integer|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|fullrange|
|*anonymous*|shortrange|
|*anonymous*|status|

<h2 id="tocSfocusleft">focusleft</h2>

<a id="schemafocusleft"></a>

```json
0

```

### Properties

|---|---|---|
|focusleft|integer|false|

<h2 id="tocSfocustop">focustop</h2>

<a id="schemafocustop"></a>

```json
0

```

### Properties

|---|---|---|
|focustop|integer|false|

<h2 id="tocSfocusright">focusright</h2>

<a id="schemafocusright"></a>

```json
0

```

### Properties

|---|---|---|
|focusright|integer|false|

<h2 id="tocSfocusbottom">focusbottom</h2>

<a id="schemafocusbottom"></a>

```json
0

```

### Properties

|---|---|---|
|focusbottom|integer|false|

<h2 id="tocSzoom">zoom</h2>

<a id="schemazoom"></a>

```json
"reset"

```

*Set zoom moving steps.
*

### Properties

*oneOf*

|---|---|---|
|zoom|string|false|

*xor*

|---|---|---|
|zoom|integer|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|reset|

<h2 id="tocSfocuswindow">focuswindow</h2>

<a id="schemafocuswindow"></a>

```json
[
  0,
  0,
  0,
  0
]

```

*Get or set the four sides of the focus window.

When setting the focus window, provide the four values of the focus window as comma-separated integers from 0 to the maximum sensor value — width, height, width, height.
*

### Properties

*None*

<h2 id="tocSaf_dn">af_dn</h2>

<a id="schemaaf_dn"></a>

```json
"on"

```

*Get or set autofocus after enabling the day-night switch.
*

### Properties

|---|---|---|
|af_dn|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSaf_zoom">af_zoom</h2>

<a id="schemaaf_zoom"></a>

```json
"on"

```

*Get or set autofocus after zoom.*

### Properties

|---|---|---|
|af_zoom|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocScasino_mode">casino_mode</h2>

<a id="schemacasino_mode"></a>

```json
"on"

```

*Get or set casino mode (1080p models only)*

### Properties

|---|---|---|
|casino_mode|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSnetopt">netopt</h2>

<a id="schemanetopt"></a>

```json
0

```

*Get or set network related settings. Integers correspond to the bits you want to enable or disable.

bit 0 = DHCP IP assignment; bit 1 = BOOTP IP assignment; bit 2 = RARP IP assignment; bit 3 = IP lock; bit 4 = NTP time requester; bit 5 = PSIA discovery multicast server; bit 6 = RTP multicast server; bit 7 = MTU enable/disable; bit 8 = PSIA discovery zeroconfig server; bit 9 = IPv6 stack enable; bit 10 = DHCPv6 enable
*

### Properties

|---|---|---|
|netopt|integer|false|

<h2 id="tocSstreamip">streamip</h2>

<a id="schemastreamip"></a>

```json
"192.168.0.1"

```

*Get or set the multicast IP address.*

### Properties

|---|---|---|
|streamip|string(ipv4)|false|

<h2 id="tocSrtpport">rtpport</h2>

<a id="schemartpport"></a>

```json
0

```

*Get or set the multicast port.*

### Properties

|---|---|---|
|rtpport|integer|false|

<h2 id="tocSsapip">sapip</h2>

<a id="schemasapip"></a>

```json
"192.168.0.1"

```

*Get or set the multicast SAP IP address.*

### Properties

|---|---|---|
|sapip|string(ipv4)|false|

<h2 id="tocSmulticast_rec">multicast_rec</h2>

<a id="schemamulticast_rec"></a>

```json
"on"

```

*Get or set the multicast reception setting.*

### Properties

|---|---|---|
|multicast_rec|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSen_multicast">en_multicast</h2>

<a id="schemaen_multicast"></a>

```json
0

```

*Enable multicast announcement.

1. To pass ONVIF conformance test, firmware does not announce ONVIF multicast by default. You need to use this HTTP command to enable multicast announcement manually, or your VMS may fail to establish multicast streaming.
2. This setting enables or disables support for incoming multicast traffic. Disabling this feature will not affect the camera's ability to provide multicast video. 
3. For multi-sensor cameras, HTTP commands streamip, sapip and rtpport are channel specific and not global. Currently SurroundVideo series is the only multi-sensor camera that supports these multicast HTTP commands, starting from firmware 65192.14.
*

### Properties

|---|---|---|
|en_multicast|integer|false|

<h2 id="tocSres">res</h2>

<a id="schemares"></a>

```json
"full"

```

*The resolution MJPEGs you want to return*

### Properties

|---|---|---|
|res|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|full|
|*anonymous*|half|

<h2 id="tocSx0">x0</h2>

<a id="schemax0"></a>

```json
0

```

*Left coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

|---|---|---|
|x0|integer(int32)|false|

<h2 id="tocSy0">y0</h2>

<a id="schemay0"></a>

```json
0

```

*Top coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

|---|---|---|
|y0|integer(int32)|false|

<h2 id="tocSx1">x1</h2>

<a id="schemax1"></a>

```json
0

```

*Right coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

|---|---|---|
|x1|integer(int32)|false|

<h2 id="tocSy1">y1</h2>

<a id="schemay1"></a>

```json
0

```

*Bottom coordinate, used to offset the image. This value should be divisible by 32 if `res=full` or 64 if `res=half`.
*

### Properties

|---|---|---|
|y1|integer|false|

<h2 id="tocSqp">qp</h2>

<a id="schemaqp"></a>

```json
"string"

```

*The quantization parameter for the H.264 encoder. Sets the target qp. Lower qp indicates a higher quality image. This paramaeter is ignored if your request includes the bitrate parameter. 
*

### Properties

|---|---|---|
|qp|string|false|

<h2 id="tocSqp_max">qp_max</h2>

<a id="schemaqp_max"></a>

```json
"string"

```

*Get or set the maximum allowed QP value — i.e. the lowest allowable quality.
*

### Properties

|---|---|---|
|qp_max|string|false|

<h2 id="tocSratelimit_mode">ratelimit_mode</h2>

<a id="schemaratelimit_mode"></a>

```json
true

```

*Get or set variable bitrate limit mode.
*

### Properties

|---|---|---|
|ratelimit_mode|boolean|false|

<h2 id="tocSratelimit">ratelimit</h2>

<a id="schemaratelimit"></a>

```json
"string"

```

*Get or set a variable bitrate limit.
*

### Properties

|---|---|---|
|ratelimit|string|false|

<h2 id="tocSquality">quality</h2>

<a id="schemaquality"></a>

```json
1

```

*The compression quality of the image*

### Properties

|---|---|---|
|quality|integer|false|

<h2 id="tocSdoublescan">doublescan</h2>

<a id="schemadoublescan"></a>

```json
0

```

*Effectively a boolean that determines whether or not the camera should delay image output until a new image is available.*

### Properties

|---|---|---|
|doublescan|integer|false|

<h2 id="tocSssn">ssn</h2>

<a id="schemassn"></a>

```json
1

```

*Stream identifier — distinguishes multiple streams from one another. Use a unique ssn for each stream with a unique image size, quality and/or frame rate. Each camera supports up to eight simultaneous non-identical streams. Each client must have a unique (ip:ssn)
*

### Properties

|---|---|---|
|ssn|integer|false|

<h2 id="tocSiframe">iframe</h2>

<a id="schemaiframe"></a>

```json
0

```

*Effectively a boolean (0 or 1). Set to 1 will force the camera to return an Intra frame (I-frame) with a corresponding SPS and PPS as an IDR slice, so that the stream is decodable from this point. When opening a new stream (as when changing the image size and/or frame rate) the I-frame is sent automatically regardless of the input value of `iframe`. To reduce the stream size, reduce the frequency of `iframe = 1` in requests. You can set the P-frames for any of the streams sent by the camera is set using
one of the following HTTP commands :
http://camera_ip/setreg?page=3&reg=21&val=(0..100)

http://camera_ip/set?keyframeinterval=(0..100)
When the on-camera counter of P-frames fills up, the camera will return an I-frame even if iframe in the request is set to 0. To find out whether an I-frame was received, check the HTTP Content Type.
*

### Properties

|---|---|---|
|iframe|integer|false|

<h2 id="tocSbitrate">bitrate</h2>

<a id="schemabitrate"></a>

```json
1

```

*Sets a constant bitrate in kilobits per second. If this parameter is present in the request, the QP parameter is ignored, and the camera adjusts quantization parameters automatically to maintain the specified bitrate.
*

### Properties

|---|---|---|
|bitrate|integer|false|

<h2 id="tocSintra_period">intra_period</h2>

<a id="schemaintra_period"></a>

```json
0

```

*Valid when requesting a non-zero bitrate and periodically requesting `iframe=1`. Specifies the intra-frame period during which you are sending requests with `iframe=1`. If you do not specify `intra_period`, bitrate control will not function correctly unless the actual period of sending iframe=1 requests is the same as the number of P-frames specified in register 3:21 of the camera via one of the commands described above. If you do not request `iframe=1` at all, then the `intra_period` parameter is not required and bitrate control will rely on the number of P-frames set in register 3:21. 
*

### Properties

|---|---|---|
|intra_period|integer|false|

<h2 id="tocSfps">fps</h2>

<a id="schemafps"></a>

```json
0

```

*Get or set the camera framerate. values over the camera's famerate will return the camera's maximum framerate (model dependent).*

### Properties

|---|---|---|
|fps|integer|false|

<h2 id="tocSchannel">channel</h2>

<a id="schemachannel"></a>

```json
"color"

```

*If `upscaling=on`, use the channel parameter to retrieve color or monochrome images from the camera.
*

### Properties

|---|---|---|
|channel|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|color|
|*anonymous*|mono|

<h2 id="tocSkeyframe">keyframe</h2>

<a id="schemakeyframe"></a>

```json
true

```

*Get or set key frame setting. Yields an I-frame on the next available frame.
*

### Properties

|---|---|---|
|keyframe|boolean|false|

<h2 id="tocSkeyframeinterval">keyframeinterval</h2>

<a id="schemakeyframeinterval"></a>

```json
50

```

*Get or set the key frame interval.

* For non-4K models the maximum limit is 100
* The numerical value in “set?keyframeinterval=(0…65535)” represents the P-frame count between two consecutive key frames (I-frames)
*

### Properties

|---|---|---|
|keyframeinterval|integer|false|

<h2 id="tocSrtspport">rtspport</h2>

<a id="schemartspport"></a>

```json
554

```

*Get or set the RTSP port.
*

### Properties

|---|---|---|
|rtspport|integer|false|

<h2 id="tocSspacialfilter">spacialfilter</h2>

<a id="schemaspacialfilter"></a>

```json
0

```

*Get or set the low-light noise filter.
*

### Properties

|---|---|---|
|spacialfilter|integer|false|

<h2 id="tocSname">name</h2>

<a id="schemaname"></a>

```json
"string"

```

*Get or set the camera name.
*

### Properties

|---|---|---|
|name|string|false|

<h2 id="tocSmtu">mtu</h2>

<a id="schemamtu"></a>

```json
512

```

*Get or set the MTU size.
*

### Properties

|---|---|---|
|mtu|integer|false|

<h2 id="tocSip">ip</h2>

<a id="schemaip"></a>

```json
"string"

```

*Get or set the camera's IP address.
*

### Properties

|---|---|---|
|ip|string|false|

<h2 id="tocSsubnetmask">subnetmask</h2>

<a id="schemasubnetmask"></a>

```json
"string"

```

*Get or set the camera's subnet mask.
*

### Properties

|---|---|---|
|subnetmask|string|false|

<h2 id="tocSgateway">gateway</h2>

<a id="schemagateway"></a>

```json
"string"

```

*Get or set the camera's default gateway.
*

### Properties

|---|---|---|
|gateway|string|false|

<h2 id="tocSeth_negotiation">eth_negotiation</h2>

<a id="schemaeth_negotiation"></a>

```json
"auto"

```

*When set to auto, auto negotiation is enabled. Connected devices will first share their transmission capabilities, such as speed and duplex mode, and then choose the highest performance transmission mode they both support.

When set to fixed, the camera uses a transmission speed of 100Mb and full duplex mode.
*

### Properties

|---|---|---|
|eth_negotiation|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|auto|
|*anonymous*|fixed|

<h2 id="tocSfeatures">features</h2>

<a id="schemafeatures"></a>

```json
0

```

*Returns an integer for enabled features. Integers that are not returned are not enabled.
*

### Properties

|---|---|---|
|features|integer|false|

<h2 id="tocSaudioinput">audioinput</h2>

<a id="schemaaudioinput"></a>

```json
"mic"

```

*The source of audio input.
*

### Properties

|---|---|---|
|audioinput|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|mic|
|*anonymous*|linein|

<h2 id="tocSlinein_volume">linein_volume</h2>

<a id="schemalinein_volume"></a>

```json
0

```

*Volume of line-in audio.
*

### Properties

|---|---|---|
|linein_volume|integer|false|

<h2 id="tocSmic_boost">mic_boost</h2>

<a id="schemamic_boost"></a>

```json
0

```

*Volume of microphone-in audio.
*

### Properties

|---|---|---|
|mic_boost|integer|false|

<h2 id="tocSpiris">piris</h2>

<a id="schemapiris"></a>

```json
"on"

```

*Enable/disable P-iris
*

### Properties

|---|---|---|
|piris|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSpirispos">pirispos</h2>

<a id="schemapirispos"></a>

```json
0

```

*The position P-iris closes to
*

### Properties

|---|---|---|
|pirispos|integer|false|

<h2 id="tocSequalbright">equalbright</h2>

<a id="schemaequalbright"></a>

```json
"on"

```

*Equalize brightness across sensors in a multisensor camera.
*

### Properties

|---|---|---|
|equalbright|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSequalcolor">equalcolor</h2>

<a id="schemaequalcolor"></a>

```json
"on"

```

*Equalize color across sensors in a multisensor camera.
*

### Properties

|---|---|---|
|equalcolor|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSvertical_alignment">vertical_alignment</h2>

<a id="schemavertical_alignment"></a>

```json
"on"

```

*Align sensors in a multisensor camera.
*

### Properties

|---|---|---|
|vertical_alignment|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSvertical_shift">vertical_shift</h2>

<a id="schemavertical_shift"></a>

```json
0

```

*Shift sensors vertically.
*

### Properties

|---|---|---|
|vertical_shift|integer|false|

<h2 id="tocSpiris_ref_channel">piris_ref_channel</h2>

<a id="schemapiris_ref_channel"></a>

```json
0

```

*Set the P-iris reference channel for a multi-channel camera.
*

### Properties

|---|---|---|
|piris_ref_channel|integer|false|

<h2 id="tocSexp_ref_channel">exp_ref_channel</h2>

<a id="schemaexp_ref_channel"></a>

```json
0

```

*Set the WDR reference channel for a multi-channel camera.
*

### Properties

*oneOf*

|---|---|---|
|exp_ref_channel|integer|false|

*xor*

|---|---|---|
|exp_ref_channel|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|off|

<h2 id="tocSir">ir</h2>

<a id="schemair"></a>

```json
"on"

```

*Infrafred light control. `on` enables IR in night mode; `alwayson` enables IR always.
*

### Properties

|---|---|---|
|ir|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|alwayson|
|*anonymous*|off|

<h2 id="tocSmake">make</h2>

<a id="schemamake"></a>

```json
"string"

```

*Get the make of the camera.
*

### Properties

|---|---|---|
|make|string|false|

<h2 id="tocSwhite_balance">white_balance</h2>

<a id="schemawhite_balance"></a>

```json
"on"

```

*White balance control.
*

### Properties

|---|---|---|
|white_balance|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSwbwndctrl">wbwndctrl</h2>

<a id="schemawbwndctrl"></a>

```json
"on"

```

*White balance window control.
*

### Properties

|---|---|---|
|wbwndctrl|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSwbwndleft">wbwndleft</h2>

<a id="schemawbwndleft"></a>

```json
0

```

*White balance window left start value. Maximum values depend on your sensor size.
*

### Properties

|---|---|---|
|wbwndleft|integer|false|

<h2 id="tocSwbwndtop">wbwndtop</h2>

<a id="schemawbwndtop"></a>

```json
0

```

*White balance window top start value. Maximum values depend on your sensor size.
*

### Properties

|---|---|---|
|wbwndtop|integer|false|

<h2 id="tocSwbwndwidth">wbwndwidth</h2>

<a id="schemawbwndwidth"></a>

```json
0

```

*White balance window width, beginning from the `wbwndleft` value. Maximum values depend on your sensor size.
*

### Properties

|---|---|---|
|wbwndwidth|integer|false|

<h2 id="tocSwbwndheight">wbwndheight</h2>

<a id="schemawbwndheight"></a>

```json
0

```

*White balance window height, beginning from the `wbwndtop` value. Maximum values depend on your sensor size.
*

### Properties

|---|---|---|
|wbwndheight|integer|false|

<h2 id="tocSntpserver_ip">ntpserver_ip</h2>

<a id="schemantpserver_ip"></a>

```json
"string"

```

*NTP server address.
*

### Properties

|---|---|---|
|ntpserver_ip|string|false|

<h2 id="tocSenclosure">enclosure</h2>

<a id="schemaenclosure"></a>

```json
"code"

```

*Returns the camera's model name. Provide `code` to return the model type number.
*

### Properties

|---|---|---|
|enclosure|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|code|

<h2 id="tocSgamma">gamma</h2>

<a id="schemagamma"></a>

```json
0

```

*Gamma for single sensor and Surroundvideo1 cameras.
*

### Properties

|---|---|---|
|gamma|integer|false|

<h2 id="tocSgamma2">gamma2</h2>

<a id="schemagamma2"></a>

```json
0

```

*Gamma for the second sensor in dual sensor cameras.
*

### Properties

|---|---|---|
|gamma2|integer|false|

<h2 id="tocSbandwidthsaving">bandwidthsaving</h2>

<a id="schemabandwidthsaving"></a>

```json
"on"

```

*Bandwidth saving mode settings.
*

### Properties

|---|---|---|
|bandwidthsaving|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSlowpower">lowpower</h2>

<a id="schemalowpower"></a>

```json
"on"

```

*Low power mode settings.
*

### Properties

|---|---|---|
|lowpower|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSmotion_compensation">motion_compensation</h2>

<a id="schemamotion_compensation"></a>

```json
"on"

```

*Motion compensation settings.
*

### Properties

|---|---|---|
|motion_compensation|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSadjustable_ir">adjustable_ir</h2>

<a id="schemaadjustable_ir"></a>

```json
"adaptive"

```

*Adjustable IR light settings.
*

### Properties

|---|---|---|
|adjustable_ir|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|adaptive|
|*anonymous*|preset|
|*anonymous*|disabled|

<h2 id="tocSirwidepos">irwidepos</h2>

<a id="schemairwidepos"></a>

```json
0

```

*The adjustable intensity of wide IR lights.
*

### Properties

|---|---|---|
|irwidepos|integer|false|

<h2 id="tocSirtelepos">irtelepos</h2>

<a id="schemairtelepos"></a>

```json
0

```

*The adjustable intensity of tele IR lights.
*

### Properties

|---|---|---|
|irtelepos|integer|false|

<h2 id="tocSsnapstream">snapstream</h2>

<a id="schemasnapstream"></a>

```json
"on"

```

*Snapstream on/off setting.
*

### Properties

|---|---|---|
|snapstream|string|false|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|on|
|*anonymous*|off|

<h2 id="tocSsensorcount">sensorcount</h2>

<a id="schemasensorcount"></a>

```json
0

```

*Returns the sensor count. Use the sensor count to determine the channels you want to get or set when 
*

### Properties

|---|---|---|
|sensorcount|integer|false|


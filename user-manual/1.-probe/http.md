# HTTP

**HTTP**. Checking the HTTP status code, Support mTLS, HTTP Basic Auth, and can set the Request Header/Body. ( HTTP Probe Configuration )

### HTTP Probe Configuration

```
# HTTP Probe Configuration

http:
  # A Website
  - name: MegaEase Website (Global)
    url: https://megaease.com

  # Some of the Software support the HTTP Query
  - name: ElasticSearch
    url: http://elasticsearch.server:9200
  - name: Eureka
    url: http://eureka.server:8761
  - name: Prometheus
    url: http://prometheus:9090/graph

  # Spring Boot Application with Actuator Heath API
  - name: EaseService-Governance
    url: http://easeservice-mgmt-governance:38012/actuator/health
  - name: EaseService-Control
    url: http://easeservice-mgmt-control:38013/actuator/health
  - name: EaseService-Mesh
    url: http://easeservice-mgmt-mesh:38013/actuator/health
```

#### Complete HTTP Configuration

```yaml
http:
  # A completed HTTP Probe configuration
  - name: Special Website
    url: https://megaease.cn
    # Proxy setting, support sock5, http, https, for example:
    #   proxy: http://proxy.server:8080
    #   proxy: socks5://localhost:1085
    #   proxy: https://user:password@proxy.example.com:443
    # Also support `HTTP_PROXY` & `HTTPS_PROXY` environment variables
    proxy: http://proxy.server:8080
    # Request Method
    method: GET
    # Request Header
    headers:
      User-Agent: Customized User-Agent # default: "MegaEase EaseProbe / v1.6.0"
      X-head-one: xxxxxx
      X-head-two: yyyyyy
      X-head-THREE: zzzzzzX-
    content_encoding: text/json
    # Request Body
    body: '{ "FirstName": "Mega", "LastName" : "Ease", "UserName" : "megaease", "Email" : "user@example.com"}'
    # HTTP Basic Auth
    username: username
    password: password
    # mTLS
    ca: /path/to/file.ca
    cert: /path/to/file.crt
    key: /path/to/file.key
    # TLS
    insecure: true # skip any security checks, useful for self-signed and expired certs. default: false
    # HTTP successful response code range, default is [0, 499].
    success_code:
      - [200,206] # the code >=200 and <= 206
      - [300,308] # the code >=300 and <= 308
    # Response Checking
    contain: "success" # response body must contain this string, if not the probe is considered failed.
    not_contain: "failure" # response body must NOT contain this string, if it does the probe is considered failed.
    regex: false # if true, the contain and not_contain will be treated as regular expression. default: false
    eval: # eval is a expression evaluation for HTTP response message
      doc: XML # support  XML, JSON, HTML, TEXT.
      expression: "x_time('//feed/updated') > '2022-07-01'" # the expression to evaluate.
    # configuration
    timeout: 10s # default is 30 seconds
```

> **Note**:
>
> The Regular Expression supported refer to https://github.com/google/re2/wiki/Syntax The XPath only supported 1.0/2.0) syntax. refer to https://www.w3.org/TR/xpath/, and the library is https://github.com/antchfx/xpath

#### Expression Evaluation

HTTP Probe supports two type of expression evaluation.

* `XML`, `JSON`, `HTML` : using the **XPath(1.0/2.0)** to extract the value
* `TEXT` : using the **Regression Expression** to extract the value

And the configuration can be two types as below:

**1) Variable Definition**

```yaml
  eval:
    doc: XML # support  XML, JSON, HTML, TEXT
    expression: "updated > '2022-07-01'"
    variables: # variables definition
        - name: updated # variable name
            type: time # variable type, support `int`, `float`, `bool`, `time` and `duration`.
            query: "//feed/updated" # the XPath query to get the variable value.
```

**2) Build-in XPath function Expression Evaluation**

you can just use the XPath build-in function in expression so simplify the configuration.

```yaml
  eval:
    doc: XML # support  XML, JSON, HTML, TEXT.
    expression: "x_time('//feed/updated') > '2022-07-01'" # the expression to evaluate.
```

Currently, EaseProbe supports the following XPath functions:

* `x_str` - get the string value from the XPath/RegExp query result.
* `x_int` - get the integer value from the XPath/RegExp query result.
* `x_float` - get the float value from the XPath/RegExp query result.
* `x_time` - get the time value from the XPath/RegExp query result.
* `x_duration` - get the duration value from the XPath/RegExp query result.

**3) Build-in Functions**

Currently, EaseProbe supports the following build-in functions:

* `strlen` - get the string length.
* `now` - get the current time.
* `duration` - get the duration value.

For examples:

check the `time` from response is 5 seconds later than the current time.

```yaml
eval:
   doc: HTML
   expression: "now() - x_time('//div[@id=\\'time\\']') > 5"
```

Check the duration from response is less than 1 second.

```yaml
eval:
    doc: HTML
    expression: "duration(rt) < duration('1s')"
    variables:
        - name: rt # variable name `rt` will be used in expression.
            type: duration # variable type is `duration`
            query: "//div[@id=\\'time\\']" # the XPath query the value.
```

Or

```yaml
eval:
    doc: HTML
    expression: "x_duration('//div[@id=\\'resp_time\\']') < duration('1s')"
```

**4) XPath Syntax Example**

Considering we have the following response:

```json
{
    "company": {
        "name": "MegaEase",
        "person": [{
                "name": "Bob",
                "email": "bob@example.com",
                "age": 35,
                "salary": 35000.12,
                "birth": "1984-10-12",
                "work": "40h",
                "fulltime": true
            },
            {
                "name": "Alice",
                "email": "alice@example.com",
                "age": 25,
                "salary": 25000.12,
                "birth": "1985-10-12",
                "work": "30h",
                "fulltime": false
            }
        ]
    }
}
```

Then, the extraction syntax as below:

```
"//name"                                        ==>  "MegaEase"
"//company/name"                                ==>  "MegaEase"
"//email"                                       ==>  "bob@example.com"
"//company/person/*[1]/name"                    ==>  "Bob"
"//company/person/*[2]/emai                     ==>  "alice@example.com"
"//company/person/*[last()]/name"               ==>  "Alice"
"//company/person/*[last()]/age"                ==>  "25"
"//company/person/*[salary=25000.12]/salary"    ==>  "25000.12"
"//company/person/*[name='Bob']/birth"          ==>  "1984-10-12"
"//company/person/*[name='Alice']/work"         ==>  "30h"
"//*/email[contains(.,'bob')]"                  ==>  "bob@example.com"
"//work",                                       ==>  "40h"
"//person/*[2]/fulltime"                        ==>  "false"
```

**5) Regression Expression Syntax Examples**

Considering we have the following response:

`name: Bob, email: bob@example.com, age: 35, salary: 35000.12, birth: 1984-10-12, work: 40h, fulltime: true`

Then, the extraction syntax as below:

```
"name: (?P<name>[a-zA-Z0-9 ]*)"           ==>  "Bob"
"email: (?P<email>[a-zA-Z0-9@.]*)"        ==>  "bob@example.com"
"age: (?P<age>[0-9]*)"                    ==>  "35"
"age: (?P<age>\\d+)"                      ==>  "35"
"salary: (?P<salary>[0-9.]*)"             ==>  "35000.12"
"salary: (?P<salary>\\d+\\.\\d+)"         ==>  "35000.12"
"birth: (?P<birth>[0-9-]*)"               ==>  "1984-10-12"
"birth: (?P<birth>\\d{4}-\\d{2}-\\d{2})"  ==>  "1984-10-12"
"work: (?P<work>\\d+[hms])"               ==>  "40h"
"fulltime: (?P<fulltime>true|false)"      ==>  "true"
```

> Notes
>
> Checking the unit test case in `eval` package you can find more examples.

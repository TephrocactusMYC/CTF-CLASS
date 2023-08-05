# knoeledge

重点是http 请求报文，这部分不太涉及响应报文
一个 http 请求报文由四个部分组成：

1. 请求行（Request-Line）
2. 请求头部（Request Header Fields）
3. 回车换行（CRLF）
4. 消息体（Message Body）

### 请求行（Request-Line）

我们来看一开始给的示例的请求行
```
POST / HTTP/1.1
```
请求行分为了三个部分：

1. 请求方法（Method）
2. 请求 URI
3. HTTP 协议版本
三者之间用空格分隔。

#### 请求方法

- GET：获取资源
- POST：传输实体主体
- PUT：传输文件
- HEAD：获得报文首部（相当于GET方法获得的资源去掉正文）
- DELETE：删除文件
- OPTIONS：询问支持的方法（客户端问服务器）
- TRACE：追踪路径
- OCONNECT：要求用隧道协议连接代理
- LINK：建立与资源之间的联系
- UNLINE：断开连接关系

### 请求头部（Request Header Fields）

这部分由成对的请求头部组成，用来告知服务端请求的更多信息。

**这是未来的重中之重！务必掌握！**
- Host ：请求的资源在哪个主机的端口上
- Connection：该请求支持长连接（heep_alive）
- Content-Length：正文内容长度
- Content-Type：数据类型
- User-Agent：声明用户的操作系统和浏览器版本信息
- Accent：发起了请求
- Referer：当前页面是从哪个页面跳转过来的
- Accept-Encoding：接受的编码
- Accept-Language：接受的语言类型
- Cookie：用于在客户端存储少量信息，通常用于实现会话（session）功能

### 消息体（Message Body）

这部分携带了本次请求需要发往服务端的信息，有的 Method 有这部分，而有的 Method 不需要这部分。

比如 get 方法就没有消息体，get 方法一般都是通过 query 来传递参数。

而 post 方法一般就有消息体。

## 请求头部具体信息

## ref

- [https://zhuanlan.zhihu.com/p/112060856](https://zhuanlan.zhihu.com/p/112060856)
- [https://blog.csdn.net/qq_40933663/article/details/90045869](https://blog.csdn.net/qq_40933663/article/details/90045869)

# Useful cmd

```
/challenge/run
```
Output:
```
hacker@talking-web-level-12:~$ /challenge/run
 * Serving Flask app 'run'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:80
Press CTRL+C to quit
```
行吧，这一大堆挑战，倒是让我把curl nc这俩玩意儿玩儿熟了。。。


# level1

Send an HTTP request using curl
```
curl http://127.0.0.1:80
```


# level2

Send an HTTP request using nc
```
printf "GET / HTTP/1.1\r\n\r\n" | nc 127.0.0.1 80
```

## ref

[a blog](https://osric.com/chris/accidental-developer/2018/01/using-nc-netcat-to-make-an-http-request/)


# level3

Send an HTTP request using python
```
import requests

response = requests.get('http://127.0.0.1:80')
print(response.content)
```


# level4

Set the host header in an HTTP request using curl
```
curl -H 'Host: f04e757423e4172f7391a2c52dd6d52b' http://127.0.0.1:80
```


# level5

Set the host header in an HTTP request using nc
```
echo -e "GET / HTTP/1.1\r\nHost: e87665191d938ed557e6d75bed2a59e7\r\n\r\n" | nc 127.0.0.1 80
```


# level6

Set the host header in an HTTP request using python
```
import requests

url = 'http://127.0.0.1:80'
headers = {'Host': '37ae8c34ce6b69de03c0514664f1de72'}
response = requests.get(url, headers=headers)

print(response.text)

```

# level7

Set the path in an HTTP request using curl
```
curl http://127.0.0.1:80/32edfeba32e2616897b6a4907182e609
```

# level8

Set the path in an HTTP request using nc
```
printf "GET /a2ef4bee2f651380996e3e91ec9ae47b HTTP/1.1\r\n\r\n" | nc 127.0.0.1 80
```

# level9

Set the path in an HTTP request using python
```
import requests

url = 'http://127.0.0.1:80/563d4434a61e9b4f8aad9f89476f9d56'
headers = {'Host': '37ae8c34ce6b69de03c0514664f1de72'}
response = requests.get(url, headers=headers)

print(response.text)

```

# level10

URL encode a path in an HTTP request using curl
```
curl --request GET --url 'http://127.0.0.1/5db90f90%20c57f0931/898c7a05%207a6a6c70'
```

# level11

URL encode a path in an HTTP request using nc
```
echo -ne "GET /c84632a0%203d7cd667/cc68c4e5%205289cce4 HTTP/1.1\r\nHost: 127.0.0.1\r\n\r\n" | nc 127.0.0.1 80
```

# level12

URL encode a path in an HTTP request using python
```
import http.client

conn = http.client.HTTPConnection("127.0.0.1", 80)
path = '/24f18995%2035ce2423/0dc75e53%20a62355c0'
conn.request("GET", path)
response = conn.getresponse()

print(response.read().decode())

```

# level13

Specify an argument in an HTTP request using curl
```
curl -X GET "http://127.0.0.1?a=d12e875e302a313b93e311080177c69e"

```

# level14

Specify an argument in an HTTP request using nc
```
echo -ne "GET /?a=2469a7322bdff77e7cf50f7a397ecf1e HTTP/1.1\r\nHost: 127.0.0.1\r\n\r\n" | nc 127.0.0.1 80

```

# level15

Specify an argument in an HTTP request using python
```
import http.client

conn = http.client.HTTPConnection("127.0.0.1", 80)
params = 'a=70206814776ee99485d36f75416cc53e'
conn.request("GET", "/?" + params)
response = conn.getresponse()

print(response.read().decode())
```
or
```
import requests

url = 'http://127.0.0.1/?a=2469a7322bdff77e7cf50f7a397ecf1e'
response = requests.get(url)

print(response.text)

```

# level16

Specify multiple arguments in an HTTP request using curl
```
curl -X GET "http://127.0.0.1?a=ecd147484bddde7d37b1911de43a8879&b=40d9af5c%20d0b5b669%266fea1792%23e808fb58"
```

# level17

Specify multiple arguments in an HTTP request using nc
```
echo -ne "GET /?a=5d723fd68383a9c49eb60b0633069601&b=164073f7%207871c6b5%26b94dd88d%23977ae717 HTTP/1.1\r\nHost: 127.0.0.1\r\n\r\n" | nc 127.0.0.1 80
```

# level18

Specify multiple arguments in an HTTP request using python
```
import requests

url = 'http://127.0.0.1/?a=4ce9272291b7199073124105d91e05b8&b=56eb0b42%204ae6359b%26f16e873e%2313ac55ab'
response = requests.get(url)

print(response.text)

```

# level19

Include form data in an HTTP request using curl
```
curl -X POST -d "a=aa62a14fe954e109fd0afd6a6b81ae87&b=123" "http://127.0.0.1/"

```

# level20

Include form data in an HTTP request using nc
```
echo -ne "POST / HTTP/1.1\r\nHost: 127.0.0.1\r\nContent-Type: application/x-www-form-urlencoded\r\nContent-Length: 64\r\n\r\na=0f4e8daf3fc9d8aa6a59af8b111cd9b6" | nc 127.0.0.1 80

```

# level21

Include form data in an HTTP request using python
```
import requests

url = 'http://127.0.0.1/'
data = {'a': '728301dd59f5157a45b164530cd4bd9a'}
response = requests.post(url, data=data)

print(response.text)

```

# level22

Include form data with multiple fields in an HTTP request using curl
```
curl -X POST -d "a=6d2e619d8691e29c605eacecff1d17f5&b=40f3c192%204a42b9c8%26042940eb%23ce8b5cc9" "http://127.0.0.1/"
```

# level23

Include form data with multiple fields in an HTTP request using nc
```
echo -ne "POST / HTTP/1.1\r\nHost: 127.0.0.1\r\nContent-Type: application/x-www-form-urlencoded\r\nContent-Length: 78\r\n\r\na=7bd29b83c57c2e3a0c9f0387fabea724&b=20c245cf%2075d26cf5%26100f8c42%23d1702767" | nc 127.0.0.1 80
```

# level24

Include form data with multiple fields in an HTTP request using python
```
import requests

url = 'http://127.0.0.1/'
data = {'a': 'db865b3bfd0d2e5ffa0c112dc700ddb9','b':'d7d3ad1a edee631b&eba293d5#d6e4cf79'}
response = requests.post(url, data=data)

print(response.text)

```

# level25

Include json data in an HTTP request using curl
```
curl -X POST -H "Content-Type: application/json" -d '{"a": "e1d94af35f929e364d037ca78f5dbfa0"}' http://127.0.0.1/

```

# level26

Include json data in an HTTP request using nc
```
data='{"a": "95a77ed287428e0fbc550158d061c07c"}'
length=$(echo -n "$data" | wc -c)
printf 'POST / HTTP/1.1\r\nHost: 127.0.0.1\r\nContent-Type: application/json\r\nContent-Length: %s\r\n\r\n%s' "$length" "$data" | nc 127.0.0.1 80

```

# level27

Include json data in an HTTP request using python
```
import requests
import json

url = "http://127.0.0.1"
data = {'a': "98f37a6b119aec9d10b6a7de1934c9ca"}
json_data = json.dumps(data)

headers = {'Content-Type': 'application/json'}

response = requests.post(url, data=json_data, headers=headers)

print(response.text)

```

# level28

Include complex json data in an HTTP request using curl
```
curl -X POST -H "Content-Type: application/json" -d '{"a": "39a0e409bba714d0ffe73ce038cb7b3a", "b": {"c": "930862ea", "d": ["c6a605f0", "c7ad7398 3fbbb9dc&458f3441#25f76ea0"]}}' http://127.0.0.1/

```

# level29

Include complex json data in an HTTP request using nc
```
data='{"a": "b7ae4afbfd6f78ad7ab06f1203ece1be","b":{"c": "0ce40827", "d": ["fb1739d2", "5cde3361 bfdb9003&a42c27d5#f291d8c2"]}}'
length=$(echo -n "$data" | wc -c)
printf 'POST / HTTP/1.1\r\nHost: 127.0.0.1\r\nContent-Type: application/json\r\nContent-Length: %s\r\n\r\n%s' "$length" "$data" | nc -q 0 127.0.0.1 80
```

# level30

Include complex json data in an HTTP request using python
```
import requests
import json

url = "http://127.0.0.1"
data = {'a': "04c2b7fc38f2a2057ab89b310a7d8311",
    "b":{
        'c': '5ff12d56',
        'd': ['93ca0c53', '9b346607 fa6d6f12&c772efa3#fddc4350']
        }
    }
json_data = json.dumps(data)

headers = {'Content-Type': 'application/json'}

response = requests.post(url, data=json_data, headers=headers)

print(response.text)
```

# level31

Follow an HTTP redirect from HTTP response using curl
```
curl -L http://127.0.0.1
```

# level32

Follow an HTTP redirect from HTTP response using nc
```
printf 'GET /fd33eca3350f203a7cc09fa116eaa060 HTTP/1.1\r\nHost: 127.0.0.1\r\nConnection: close\r\n\r\n' | nc -w 10 -q 0 127.0.0.1 80
```

# level33

Follow an HTTP redirect from HTTP response using python
```
import requests

url = 'http://127.0.0.1'
response = requests.get(url, allow_redirects=True)
new_response = requests.get(response.url)
print(new_response.text)
```

# level34

Include a cookie from HTTP response using curl
```
curl -b "cookie=d2b2eb6ac86abb563027659450780a51" -L -v http://127.0.0.1

```

# level35

Include a cookie from HTTP response using nc
```
printf 'GET / HTTP/1.1\r\nHost: 127.0.0.1\r\nCookie: cookie=c1c5e422a53c2b73d080674d417d06fd\r\nConnection: close\r\n\r\n' | nc 127.0.0.1 80

```

# level36

Include a cookie from HTTP response using python
貌似题有点儿毛病啊。。。
```
import requests

url = 'http://127.0.0.1'
cookies = {'cookie_name': 'cookie_value'}
response = requests.get(url, cookies=cookies)

print(response.text)
```

# level37

Include a cookie from HTTP response using curl
```
curl -c cookies.txt http://127.0.0.1
curl -b cookies.txt -L -v http://127.0.0.1
```

# level38

Include a cookie from HTTP response using nc

好吧这个玩意儿，就是重复运行几遍，就行了，应该写个脚本。。。
我TM手动输了好几遍，我日。。。
```
printf 'GET / HTTP/1.1\r\nHost: 127.0.0.1\r\nCookie: session=eyJzdGF0ZSI6MX0.ZLMdXw.VU5O3fTNhAgzX_0GG5B3kRNVZ0M\r\nConnection: close\r\n\r\n' | nc 127.0.0.1 80
printf 'GET / HTTP/1.1\r\nHost: 127.0.0.1\r\nCookie: session=eyJzdGF0ZSI6Mn0.ZLMdcQ.Ip32pWs2LPaq23ckcO5TQSjN5Us\r\nConnection: close\r\n\r\n' | nc 127.0.0.1 80
printf 'GET / HTTP/1.1\r\nHost: 127.0.0.1\r\nCookie: session=eyJzdGF0ZSI6M30.ZLMdjQ.3QXprUl27h0da-RC0xjx1ZwrLZ0\r\nConnection: close\r\n\r\n' | nc 127.0.0.1 80

```

# level39

Include a cookie from HTTP response using python

貌似确实有毛病了
```
import requests

url = 'http://127.0.0.1'
cookies = {'cookie_name': 'cookie_value'}
response = requests.get(url, cookies=cookies)

print(response.text)
```

**碎碎念，这个nc是真的难用，还是python好用**
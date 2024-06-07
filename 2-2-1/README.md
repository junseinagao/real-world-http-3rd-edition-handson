# Setup

```bash
cd 2-2-1
go run main.go
```

# Commands

## 2-2

```bash
curl --http1.0 http://localhost:18888/greeting
# --- Go Server のログ ---
# GET /greeting HTTP/1.0
# Host: localhost:18888
# Accept: */*
# User-Agent: curl/7.88.1
```

```bash
curl --http1.0 --get --data-urlencode "search word" http://localhost:18888

```

## 2-4

```bash
curl -v --http1.0 http://localhost:18888/greeting
# *   Trying 127.0.0.1:18888...
# * Connected to localhost (127.0.0.1) port 18888 (#0)
# > GET /greeting HTTP/1.0
# > Host: localhost:18888
# > User-Agent: curl/7.88.1
# > Accept: */*
# > 
# * HTTP 1.0, assume close after body
# < HTTP/1.0 200 OK
# < Date: Fri, 07 Jun 2024 00:51:49 GMT
# < Content-Length: 32
# < Content-Type: text/html; charset=utf-8
# < 
# <html><body>hello</body></html>
# * Closing connection 0
```

## 2-4-1

```bash
curl --http1.0 -H "X-Test: Hello" http://localhost:18888
# --- Go Server のログ ---
# GET / HTTP/1.0
# Host: localhost:18888
# Accept: */*
# User-Agent: curl/7.88.1
# X-Test: Hello
```

```bash
curl -v --http1.0 -A "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)" http://localhost:18888
# *   Trying 127.0.0.1:18888...
# * Connected to localhost (127.0.0.1) port 18888 (#0)
# > GET / HTTP/1.0
# > Host: localhost:18888
# > User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)
# > Accept: */*
# > 
# * HTTP 1.0, assume close after body
# < HTTP/1.0 200 OK
# < Date: Fri, 07 Jun 2024 04:19:23 GMT
# < Content-Length: 32
# < Content-Type: text/html; charset=utf-8
# < 
# <html><body>hello</body></html>
# * Closing connection 0

# --- Go Server のログ ---
# GET / HTTP/1.0
# Host: localhost:18888
# Accept: */*
# User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)
```

```bash
curl -v --http1.0 -H "User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)" http://localhost:18888
```

## 2-5-1

```bash
curl --http1.0 -X POST http://localhost:18888/greeting
# --- Go Server のログ ---
# POST /greeting HTTP/1.0
# Host: localhost:18888
# Accept: */*
# User-Agent: curl/7.88.1
```
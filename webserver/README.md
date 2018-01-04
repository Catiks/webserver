# 一个golang实现的简单的web服务器，并进行了测试

[GitHub 项目地址](https://github.com/Catiks/webserver)

## 程序运行

> 找到main可执行文件，命令行中输入./main 即可启动服务器

## 依赖说明
>本程序可能对一下包有依赖
>	"github.com/codegangsta/negroni"
	"github.com/gorilla/mux"
	"github.com/unrolled/render"
解决协议来问题，输入go get "——————"
其中"——————"替换为以上任意一个地址

##结果
>curl访问
>命令：curl -v http://localhost:8080/
>>结果：
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET / HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 404 Not Found
< Content-Type: text/plain; charset=utf-8
< X-Content-Type-Options: nosniff
< Date: Thu, 04 Jan 2018 18:29:09 GMT
< Content-Length: 19
< 
404 page not found
* Connection #0 to host localhost left intact

>压力测试
>命令：ab -n 1000 -c 100 http://localhost:8080/hello/your
>>解释:-n在测试会话中所执行的请求个数 这里为1000个
	-c一次产生的请求个数，这里为100个
>>结果：
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking localhost (be patient)
Completed 100 requests
Completed 200 requests
Completed 300 requests
Completed 400 requests
Completed 500 requests
Completed 600 requests
Completed 700 requests
Completed 800 requests
Completed 900 requests
Completed 1000 requests
Finished 1000 requests


Server Software:        
Server Hostname:        localhost
Server Port:            8080

Document Path:          /hello/your
Document Length:        27 bytes

Concurrency Level:      100
Time taken for tests:   0.125 seconds
Complete requests:      1000
Failed requests:        0
Total transferred:      150000 bytes
HTML transferred:       27000 bytes
Requests per second:    7972.64 [#/sec] (mean)
Time per request:       12.543 [ms] (mean)
Time per request:       0.125 [ms] (mean, across all concurrent requests)
Transfer rate:          1167.87 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    3   1.2      3       7
Processing:     2    9   7.6      6      37
Waiting:        1    8   7.2      5      37
Total:          4   12   7.4      9      41

Percentage of the requests served within a certain time (ms)
  50%      9
  66%     11
  75%     13
  80%     15
  90%     27
  95%     32
  98%     35
  99%     36
 100%     41 (longest request)
>

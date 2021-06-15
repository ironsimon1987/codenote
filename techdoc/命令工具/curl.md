# curl

## refer
- [curl command in Linux with Examples](https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/)
- [curl 的用法指南](https://www.ruanyifeng.com/blog/2019/09/curl-reference.html)


## 常见用例

Post 请求(使用`-d`携带参数)
``` 
> curl domain.www -X POST -d "`params1:`value1`"
```

HEAD 请求
```
> curl -I https://www.baidu.com
> curl --head https://www.baidu.com
```


使用 socks 代理
```
curl --socks5 127.0.0.1:1080 http://httpbin.org/get
```

下载文件
-O : This option downloads the file and saves it with the same name as in the URL.
-o : saves the downloaded file on the local machine with the name provided in the parameters.
```
curl -O ftp://speedtest.tele2.net/1MB.zip
curl -o hello.zip ftp://speedtest.tele2.net/1MB.zip
```


带请求头字段设置，进行分段请求
Note: 可以使用`-H` 替换 `--header`
```sh
> curl https://www.baidu.com --header "Range: bytes=0-8"
> curl https://www.baidu.com -r 0-8
```


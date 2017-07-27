## shadowsocksr-kcptun

Shadowsocksr and kcptun docker image.

* **shadowsocksr version: 3.3.3 2017-06-03**
* **kcptun version: 20170525**

### Usage:

``` sh
docker run -d -p 27327:27327/tcp -p 27372:27372/udp --name ssr_kcp cumulus4721/shadowsocksr-kcptun:latest
```

### Kcptun Client Usage:

- Download from:  [https://github.com/xtaci/kcptun](https://github.com/xtaci/kcptun)

``` sh
./client_linux_amd64 -r "Server IP:27372" -l ":27327" -mode fast2
```

### Shadowsocksr Client Usage:

&emsp;&emsp;**Details :** [https://github.com/breakwa11/shadowsocks-rss/wiki](https://github.com/breakwa11/shadowsocks-rss/wiki)

- `Server Address(use kcptun):` Your kcptun client IP
- `Server Address(ssr only):` Server IP
- `Server Port:` 27327
- `Password:` misaki
- `Encrypt Method:` aes-256-ctr
- `Protocol:` auth_chain_a
- `Obfs:` tls1.2_ticket_auth

***

### 关于启动参数

&emsp;&emsp;这个镜像是实现功能的第一版，为了省事启动脚本直接把默认参数复制进去了，很快会增加启动参数设置的功能。<br>
&emsp;&emsp;要自定义参数。若在VPS上使用，启动可以用`/bin/bash`覆盖默认的启动命令。然后修改脚本`/usr/bin/ssr_kcp.sh`中的参数再自行运行脚本即可。<br>
&emsp;&emsp;若使用樱花docker，可以通过定义`ENV`的方式自定义参数。

### 关于樱花docker
选择开放端口：
- **27327/tcp**
- **27372/udp**

&emsp;若要自定义参数，请参照`dockerfile`定义`ENV`覆盖默认值即可。<br>
&emsp;不要定义启动`CMD`。


### 最后
&emsp;&emsp;暑假在家折腾搭梯子，自用需要又没有搜到于是现学现卖搞了这个镜像。刚入门，哪里有问题各位大佬多指出。


&emsp;&emsp;**大部分内容参考了`breakwa11`和`mritd`两位大佬的镜像**
- [https://hub.docker.com/r/breakwa11/shadowsocksr/](https://hub.docker.com/r/breakwa11/shadowsocksr/)
- [https://hub.docker.com/r/mritd/shadowsocks/](https://hub.docker.com/r/mritd/shadowsocks/)

# OS proxy settings:
## Ubuntu (>version 18) file: /etc/environment
```bash
http_proxy=
https_proxy=
ftp_proxy=
no_proxy=127.0.0.*;localhost
```

## CentOS file: /etc/profile.d/proxy.sh
```bash
export http_proxy=http://child-prc.intel.com:913
export https_proxy=http://child-prc.intel.com:913
export no_proxy="192.168.*.*"
```


# Wget
## file: /etc/wgetrc. the file includes sample
```text
https_proxy = http://child-prc.intel.com:913/
http_proxy = http://child-prc.intel.com:913/
ftp_proxy = http://child-prc.intel.com:913/
use_proxy = on
```


# apt
## file: /etc/apt/apt.conf.d/proxy [optional]
Acquire::http::Proxy "http://proxy-server:port/";
Acquire::https::Proxy "https://proxy-server:port/";
Acquire::ftp::Proxy "https://proxy-server:port/";
## socks needs confirm
#Acquire::socks::Proxy "socks5://proxy-server:port/"; 


# Git
Shell command
```bash
git config --global http.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
git config --global https.proxy https://proxyUsername:proxyPassword@proxy.server.com:port
or
git config --global http.https://domain.com.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
git config --global http.https://domain.com.sslVerify false
```

Or in file /etc/gitconfig
```text
[http]
[http "https://domain.com"]    # only this domain.com affected with sslverify=false.
	proxy = http://proxyUsername:proxyPassword@proxy.server.com:port
	sslVerify = false
```

Or in file ~/.gitconfig
```text
tbd
```


# docker
In file /etc/systemd/system/docker.service.d/http-proxy.conf
```text
[Service]
Environment="HTTP_PROXY=http://user01:password@10.10.10.10:8080/"
Environment="HTTPS_PROXY=https://user01:password@10.10.10.10:8080/"
Environment="NO_PROXY= hostname.example.com,172.10.10.10"
```
Enable configuration.
```bash
systemctl daemon-reload
systemctl restart docker
systemctl show docker --property Environment
```

# npm
NPM is what? I forgot.
```bash
$ npm config set proxy http://<username>:<password>@<proxy-server-url>:<port>
$ npm config set https-proxy http://<username>:<password>@<proxy-server-url>:<port>
```


# apm (atom config)
Atom plugin installation needs proxy.
```bash
apm config set proxy "http://localhost:8888"
apm config set https_proxy proxy "http://localhost:8888"
apm config set strict-ssl false
```

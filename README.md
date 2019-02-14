### Apache服务器安装SSL证书
1. yun install -y  mod_ssl
2. 1. 在Apache的安装目录下创建cert目录，并且将下载的全部文件拷贝到cert目录中。(阿里云 默认位置 /etc/httpd
2. 2. 如果申请证书时是自己创建的CSR文件，请将对应的私钥文件放到cert目录下并且命名为a.key；
3. 打开 apache 安装目录下 conf/extra/httpd-ssl.conf 文件 (也可能是conf.d/ssl.conf，与操作系统及安装方式有关)， 在配置文件中查找以下配置语句:
```# 添加 SSL 协议支持协议，去掉不安全的协议
SSLProtocol all -SSLv2 -SSLv3
# 修改加密套件如下
SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM
SSLHonorCipherOrder on
# 证书公钥配置
SSLCertificateFile cert/public.pem
# 证书私钥配置
SSLCertificateKeyFile cert/214221995500121.key
# 证书链配置，如果该属性开头有 '#'字符，请删除掉
SSLCertificateChainFile cert/chain.pem
```
### windows 上传到 阿里云 centos
1. scp -r 18.key root@0.0.0.0:/home 普通远程拷贝 -r 递归拷贝 包含文件夹内所有内容
2. scp -i ali.pem -r 1819107_top.xuiux.top.key root@149.129.73.23:/home^C 以加密sshkey 上传。


##使用cf scale提高应用的可伸缩性

考虑的因素诸如用户负载，应用执行任务的数量等，可以改变应用所使用磁盘空间和内存大小。对于大多数应用来说，增加磁盘空间或者内存可以提高性能。类似的，增加额外的服务器可以让应用承载更多的用户负载和并发请求。这些做法就可以称为提高应用的伸缩性。

使用```cf scale```可以按需调整应用的伸缩性。

###横向扩展

通过创建或者销毁应用的服务器达到横向扩展。

所有请求都通过负载均衡服务器自动的分发到不同的应用服务器上，应用服务器之间并行处理所有任务。添加更多的应用服务器可以按需处理更多的站点流量。

使用```cf scale APP -i INSTANCES```命令可以横向扩张应用。Cloud Foundry会根据```INSTANCES```的数量来决定添加还是删除应用的服务器数量。

```
$ cf scale myApp -i 5
```

###纵向扩张

所谓纵向扩张，就是通过改变所有应用服务器的磁盘或内存空间大小。

使用```cf scale APP -k DISK```改变所有应用服务器的磁盘空间大小。```DISK```参数必须是正整数，单位可以用**M**百万字节，或者**G**千兆字节。

```
$ cf scale myApp -k 512M
```

使用```cf scale APP -m MEMORY```改变所有应用服务器的内存大小。```MEMORY ```参数必须是正整数，单位可以用**M**百万字节，或者**G**千兆字节。

```
$ cf scale myApp -m 1G
```
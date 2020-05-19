描述
====
目前社区有很多 PHP 的 RPC 实现，但是在专业性上与其他编程语言存在差距。Swoole 底层内置一个 RPC 服务器/客户端，由 Swoole 团队支持维护，提高 PHP 在服务治理方面的通用性。


设计
=====
与 GRPC、BRPC、Tars 的差异
-----
Protobuf、Thrift、Tars 使用了 `IDL` 描述数据结构，配合代码生成工具，对静态语言更友好。而动态语言可以直接将对象、数组进行序列化传输，更简单、易用、灵活。

同时底层也会尽可能地兼容 Protobuf、Thrift、Tars、JSON、MsgPack 等编码格式。

在通信协议方面，底层会兼容各种常见的 GRPC、BRPC、Tars 的通信协议。

分层设计
----
我们将整个 RPC 分为：

- 通信层，如：Http2、Swoole RPC、B-RPC、GRPC、Tars
- 编码层，如：PHP-Serialize、JSON、Protobuf、Thrift、Tars、MsgPack
- 治理层，如：服务发现、故障转移、超时控制、智能重试、熔断、降级、限流、日志、监控、报警、链路追踪、性能分析、调试

支持范围
----
* 客户端：支持 FPM、Swoole 协程两种环境
* 服务端：支持同步阻塞模式、协程模式

协程模式下提供更高级特性，FPM 同步客户端与同步阻塞服务端，仅支持基本的功能。

实现方法
----
使用纯 PHP 代码实现，在 `swoole/library` 中实现，打包到 `Swoole` 内核。

伪代码
-----
### 客户端
```php
<?php
$client = new Swoole\RPC\Client("service.domain.name", 9501);

//串行调用
$response1 = $client->call('/hello/world/test1', ['hello' => 'world1', 'name' => 'rango']);
$response2 = $client->call('/hello/world/test2', ['hello' => 'world2', 'name' => 'rango']);
$response3 = $client->call('/hello/world/test3', ['hello' => 'world3', 'name' => 'rango']);

//并行调用
$requeset1 = $client->send('/hello/world/test1', ['hello' => 'world1', 'name' => 'rango']);
$requeset2 = $client->send('/hello/world/test2', ['hello' => 'world2', 'name' => 'rango']);
$requeset3 = $client->send('/hello/world/test3', ['hello' => 'world3', 'name' => 'rango']);

//通过 $request 和 $response 的 ID 来匹配
$response3 = $client->recv();
$response1 = $client->recv();
$response2 = $client->recv();


```
### 服务端

```php
<?php
$server = new Swoole\RPC\Server("service.domain.name", 9501);

$server->on('Request', function ($request, $response) {
     var_dump($request->header);
     //根据 path 路由到不同的 controller
     var_dump($request->path);
     $response->end(['code' => 0, 'data' => 'hello world']);
});

$server->start();
```

服务注册/发现
=====

DNS [默认方式]
----
默认使用 `DNS` 方式实现服务发现，但由于`DNS`仅支持发现，不支持注册，因此在`Server`端不做任何处理，直接监听端口。

在客户端，通过`DNS`获取`IP`地址进行`TCP`连接。可以搭建`HaProxy + LVS`作为网关，分发请求到不同的`Server`节点。

ZooKeeper
----

ETCD
----

Consul
-----

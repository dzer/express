# 快递查询

## 安装

环境要求：PHP >= 5.3.0

1. 使用 [composer](https://getcomposer.org/)

  ```shell
  composer require "overtrue/wechat:~3.0" -vvv
  ```

## 使用

基本使用（以服务端为例）:

```php
<?php

use EasyWeChat\Foundation\Application;

$options = [
    'debug'     => true,
    'app_id'    => 'wx3cf0f39249eb0e60',
    'secret'    => 'f1c242f4f28f735d4687abb469072a29',
    'token'     => 'easywechat',
    'log' => [
        'level' => 'debug',
        'file'  => '/tmp/easywechat.log',
    ],
    // ...
];

$app = new Application($options);

$server = $app->server;
$user = $app->user;

$server->setMessageHandler(function($message) use ($user) {
    $fromUser = $user->get($message->FromUserName);

    return "{$fromUser->nickname} 您好！欢迎关注 overtrue!";
});

$server->serve()->send();
```

更多请参考[http://easywechat.org/](http://easywechat.org/)。

## 文档

[http://easywechat.org/](http://easywechat.org/)

> 强烈建议看懂微信文档后再来使用本 SDK。

## 框架集成

[Laravel 5 拓展包: overtrue/laravel-wechat](https://github.com/overtrue/laravel-wechat)

## 贡献代码

[贡献指南](CONTRIBUTING.md)

## License

MIT

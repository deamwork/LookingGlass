# LookingGlass

## Overview 总览

LookingGlass is a user-friendly PHP based looking glass that allows the public (via a web interface) to execute network
commands on behalf of your server.

其实大家都懂，不然你也不会来看这个repo的，简述我就不翻译了。

当前版本: v1.3.1(基于原版1.3.0修改)


## Features 特性

* Automated install via bash script
* IPv4 & IPv6 support
* Live output via long polling
* Multiple themes
* Rate limiting of network commands

* 通过bash脚本自动安装
* 支持 IPv4 & IPv6
* 实时输出测试结果
* 多主题
* 支持限制

## Implemented commands 支持的测试命令

* host
* mtr
* mtr6 (IPv6)
* ping
* ping6 (IPv6)
* traceroute
* traceroute6 (IPv6)

__IPv6 commands will only work if your server has external IPv6 setup (or tunneled)__

__IPv6命令仅在服务器开启并支持IPv6设置的情况下才会有效__

## Requirements 安装需求

* PHP >= 5.3
* PHP PDO with SQLite driver (required for rate-limit)
* SSH/Terminal access (able to install commands/functions if non-existent)

* PHP版本高于5.3
* PHP 支持SQLite驱动的PDO层 (需要支持rate-limit)
* SSH/终端访问 (able to install commands/functions if non-existent)

## Install 安装

1. Download [LookingGlass](https://github.com/telephone/LookingGlass/archive/v1.3.0.tar.gz) to the intended
folder within your web directory
2. Extract archive:
    - Option #1 - Extract archive to the current directory:
        - `tar -zxvf LookingGlass-1.3.0.tar.gz --strip-components 1`
    - Option #2 - Extract archive to a directory named `LookingGlass`:
        - `tar -zxvf LookingGlass-1.3.0.tar.gz --transform 's!^[^/]\+\($\|/\)!LookingGlass\1!'`
3. Navigate to the `LookingGlass` subdirectory in terminal
4. Run `bash configure.sh`
5. Follow the instructions and `configure.sh` will take care of the rest

_Forgot a setting? Simply run the `configure.sh` script again_

1. 下载[LookingGlass](https://github.com/deamwork/LookingGlass/archive/v1.3.1.tar.gz)并放置于网站根目录。
2. 解压此文件
    - 解压到当前目录:
        - `tar -zxvf LookingGlass-1.3.1.tar.gz --strip-components 1`
    - 解压到`LookingGlass`目录:
        - `tar -zxvf LookingGlass-1.3.1.tar.gz --transform 's!^[^/]\+\($\|/\)!LookingGlass\1!'`
3. 在ssh下切换到`LookingGlass`目录：`cd LookingGlass`
4. 执行 `bash configure.sh`
5. 根据屏幕提示完成安装过程

如果需要重置配置，再次执行第四、五步即可

## Updating 更新

1. Download [LookingGlass](https://github.com/deamwork/LookingGlass/archive/v1.3.1.tar.gz) to the folder containing
your existing install
2. Extract archive: `tar -zxvf LookingGlass-1.3.0.tar.gz --overwrite --strip-components 1`
    - This will overwrite/update existing files
3. Navigate to the `LookingGlass` subdirectory in terminal
4. Run `bash configure.sh`
5. Follow the instructions and `configure.sh` will take care of the rest
    - Note: Re-enter test files to create random test files from `GNU shred`

_Forgot a setting? Simply run the `configure.sh` script again_

1. 下载[LookingGlass](https://github.com/deamwork/LookingGlass/archive/v1.3.1.tar.gz)并放置于先前版本的网站根目录。
2. 执行解压 `tar -zxvf LookingGlass-1.3.1.tar.gz --overwrite --strip-components 1`
    - 注意 此操作会覆盖并更新现有文件
3. 在ssh下切换到`LookingGlass`目录：`cd LookingGlass`
4. 执行 `bash configure.sh`
5. 根据屏幕提示完成安装过程

如果需要重置配置，再次执行第四、五步即可

## Apache

An .htaccess is included which protects the rate-limit database, disables indexes, and disables gzip on test files.
Ensure `AllowOverride` is on for .htaccess to take effect.

Output buffering __should__ work by default.

For an HTTPS setup, please visit:
- [Mozilla SSL Configuration Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/)

## Nginx

如果使用php5.x，请参照以下配置文件:
[Nginx(http2) with php5.x](LookingGlass/lookingglass-http.nginx.conf)

如果使用php7，请参照以下配置文件：
[Nginx(http2) with php7](LookingGlass/lookingglass-php7-http.nginx.conf)

若要设置ssl相关，请取消注释上述配置文件中的`SSL configuration`字段，并参照:
- [Best nginx configuration for security](http://tautt.com/best-nginx-configuration-for-security/)
- [Mozilla SSL Configuration Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/)

## PHP

此程序支持 php5.x 及 php7 ，根据不同需要，依照LookingGlass目录下的对应文件修改您的Nginx配置即可。
请注意 使用LookingGlass需要启用两个非安全函数，分别为`proc_open`, `proc_get_status`。
如果您是Oneinstack或者LinuxEye的一键包用户，请修改`/usr/local/php/etc/php.ini`，对应内容位于300行。

## Hop 默认的跳数限制


## License 协议

此程序依照MIT协议开源并遵守。
Code is licensed under MIT Public License.

支持原作者，请保留页面底端的版权链接。
* If you wish to support my efforts, keep the "Powered by LookingGlass" link intact.

## Thanks 鸣谢
感谢 akw28888 对本 repo 的贡献
感谢 telephone 创建了这个项目
# NeverIdle

*我喜欢你，但别删我机，好么？*

本程序随手写的，下面介绍也是随心写的，不喜勿碰。

## 一键脚本 One click to go

```shell
bash <(curl -s -L https://gist.githubusercontent.com/Ansen/e45320205faf5786d3282ac880f20bab/raw/onekey-NeverIdle.sh)
```

MJJ 们估计会喜欢这个。感谢脚本作者 @Ansen

默认执行下面的命令，当然肯定没法覆盖所有的需求。  
比如 AMD 没有 2G 内存，也没有浪费内存的要求。  
所以依然建议各位自己安装，也是非常便捷迅速的。

## Usage

从 Release 下载可执行文件。注意区分 amd64 和 arm64。

在服务器上启动一个 screen，然后执行本程序，用法自己搜。

命令参数：

```shell
./NeverIdle -c 2h -m 2 -n 4h
```

其中：

-c 指启用 CPU 定期浪费，后面跟随每次浪费的间隔时间。  
如每 12 小时 23 分钟 34 秒浪费一次，则为 12h23m34s。按照格式填。

-m 指启用浪费的内存量，后面是一个数字，单位为 GiB。  
启动后会占用对应量的内存，并且保持不会释放，直到手动杀死进程。

-n 指启用网络定期浪费，后面跟随每次浪费的间隔时间。  
格式同 CPU。会定期执行一次 Ookla Speed Test（还会输出结果哦！）

-t 指设置网络定期浪费的并发连接数。 
默认为10个，值越大消耗的资源越多，一般情况不需要更改。

*启动该程序后即立刻执行一次你配置的所有功能，可以观察效果。*

## Docker

```shell
docker run ghcr.io/m3chd09/neveridle /app/NeverIdle -c 2h -m 2 -n 4h
```

docker-compose.yml

```yaml
version: '3.9'
services:
  app:
    image: ghcr.io/m3chd09/neveridle
    command: /app/NeverIdle -c 2h -m 2 -n 4h
    restart: always
    volumes:
      - /etc/ssl/certs/ca-certificates.crt:/etc/ssl/certs/ca-certificates.crt:ro
```

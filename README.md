# FinalSpeed
FinalSpeed 是高速双边加速软件，可加速所有基于 TCP 协议的网络服务，在高丢包和高延迟环境下，仍可达到 90% 的物理带宽利用率，即使高峰时段也能轻松跑满带宽。

## Build
Java 1.7 or higher is required.
- Windows: `winpcap`
- Linux: `libpcap`, `iptables`

### Windows
- Build client: `gradlew releaseClient`
- Build server: `gradlew releaseServer`
- Build client & server: `gradlew release`

### Linux
- Build client: `./gradlew releaseClient`
- Build server: `./gradlew releaseServer`
- Build client&server: `./gradlew release`

### Binary
- Client: `output/FinalSpeedClient-version.jar`
- Server: `output/FinalSpeedServer-version.jar`

`/output/libs/*.jar` is required.

## Usage

### 客户端配置
```sh
# 运行CLI版
java -jar finalspeed.jar -b
# 运行GUI版
java -jar finalspeed.jar
```

配置文件与 FinalSpeed 必须在同一目录下。

`client_config.json`
```
{
    // 服务器地址
    "server_address": "1.2.3.4",
    // 服务器端口
    "server_port": 150,
    // 协议
    "protocal": "udp",
    // 上传速度 (byte/s)
    "upload_speed": 3574690,
    // 下载速度 (byte/s)
    "download_speed": 17873454
}
```

`port_map.json`
```
{
    "map_list": [
        {
            // 备注名
            "name": "shadowsocks",
            // 目标端口
            "dst_port": 1234,
            // 本地端口
            "listen_port": 1234
        },
        {
            "name": "ssh",
            "dst_port": 22,
            "listen_port": 2222
        }
    ]
}
```

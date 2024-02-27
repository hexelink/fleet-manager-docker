# Fleet Manager Docker 部署

## 服务器防火墙设置

使用默认配置服务器端需要开放以下端口：

- TCP:8090
- UDP:51820
- UDP:40000-...

## 服务器安装软件

服务器端需安装 WireGuard 和 Docker-Compose，已 Ubuntu 为例，安装方法如下：

```bash
sudo apt update
sudo apt install wireguard docker-compose
```

## 下载 docker-compose.yml

下载 docker-compose.yml 文件到服务器上的任意目录，例如/opt/fleet-manager

运行以下命令启动 fleet-manager

```bash
cd /opt/fleet-manager
docker-compose up -d
```

## 通过 Web 访问

通过浏览器访问`http://服务器IP:8090`

## 环境变量设置

### Fleet Commander

- CAPTAIN_GRPC: 设置 fleet-captain gRPC 地址
- LIAISON_GRPC: 设置 fleet-liaison gRPC 地址
- PUBLIC_ADDRESS: 设置服务器公网地址
- ADMIN_EMAIL: 设置系统管理员邮箱
- ADMIN_PASSWORD: 设置系统管理员初始密码
- APP_COMPANY_NAME: 设置公司名称
- APP_HEADER_TITLE: 设置页面顶部标题
- APP_LOGIN_TITLE: 设置登录页面标题

### Fleet Captain

- WG_NAME: WireGuard 网络名称
- WG_ADDRESS: WireGuard 服务器的网络地址，CIDR 格式，未指定则生成一个 10.x.0.1/16 的地址，其中 x 为随机数
- WG_PORT: WireGuard 网络端口，未指定则从 51820 开始查找一个未被占用的端口
- GRPC_PORT: gRPC 端口，未指定则使用 8051

### Fleet Liaison

- WG_PORT_START: WireGuard 端口起始值，未指定则使用 40000，每个远程连接使用一个单独的端口
- GRPC_PORT: gRPC 端口，未指定则使用 9051

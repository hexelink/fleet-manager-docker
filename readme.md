# Fleet Manager Docker 部署

## 服务器防火墙设置

使用默认配置服务器端需要开放以下端口：
- TCP:8090
- UDP:51820

## 服务器安装软件
服务器端需安装WireGuard和Docker-Compose，已Ubuntu为例，安装方法如下：
```bash
sudo apt update
sudo apt install wireguard docker-compose
```
## 下载docker-compose.yml
下载docker-compose.yml文件到服务器上的任意目录，例如/opt/fleet-manager

运行以下命令启动fleet-manager
```bash
cd /opt/fleet-manager
docker-compose up -d
```

## 通过Web访问
通过浏览器访问`http://服务器IP:8090`

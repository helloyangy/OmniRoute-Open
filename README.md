# OmniRoute

免费额度的路由网关，自动容灾切换，并用压缩引擎省下 15–95% 的 Token。

项目地址：https://github.com/diegosouzapw/OmniRoute/blob/main/docs/i18n/zh-CN/README.md

![a02746712006c101895c9ab78655d246.png](./_resources/a02746712006c101895c9ab78655d246.png)

可以反代很多软件，例如反代 OpenCode 等都可以。

![d9b71ff64a248b6abe07e59933ade368.png](./_resources/d9b71ff64a248b6abe07e59933ade368.png)

---

## 服务器推荐

腾讯云新加坡、硅谷、东京地区 **199 元/年**，可同价续费

| 配置 | 详情 |
|------|------|
| CPU | 2 核 |
| 内存 | 4 GB |
| 带宽 | 30 Mbps |
| 硬盘 | 60 GB SSD |
| 月流量 | 1.5 TB |

推荐首尔线路，系统选 Ubuntu 24

购买地址：https://curl.qcloud.com/oyWDLkRJ

![72d493eab65af6588b3ed9cb7585b177.png](./_resources/72d493eab65af6588b3ed9cb7585b177.png)

---

## 部署教程

### 1. 安装 Docker

```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

![1583ad3273b3909a8328305ebce9d6d7.png](./_resources/1583ad3273b3909a8328305ebce9d6d7.png)

### 2. Docker 部署项目

```bash
docker run -d --name omniroute --restart unless-stopped --stop-timeout 40 \
  -p 20128:20128 -v omniroute-data:/app/data diegosouzapw/omniroute:latest
```

![01bfc1658a9d96e63c53226144da4646.png](./_resources/01bfc1658a9d96e63c53226144da4646.png)

### 3. 访问服务

记得在服务器厂商控制台面板放通防火墙端口 20128

```
http://你的服务器IP:20128
```

![9d9cfb1ff73320de646bba6f6dbfbbbb.png](./_resources/9d9cfb1ff73320de646bba6f6dbfbbbb.png)

### 4. 选择提供商

例如选择 OpenCode

![8ddfbe355b75c9dea416b1c2187b70af.png](./_resources/8ddfbe355b75c9dea416b1c2187b70af.png)

### 5. 测试

![41a6ee5c773bae6758b56bed9064a713.png](./_resources/41a6ee5c773bae6758b56bed9064a713.png)

| 参数 | 值 |
|------|----|
| 接口 | `http://你的服务器IP:20128/v1` |
| 模型 | `oc/big-pickle` |

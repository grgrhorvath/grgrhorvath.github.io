本教程参考了多个在线资源，使用开源项目 [Chatgpt-web](https://github.com/Chanzhaoyu/chatgpt-web)，经过测试可用。通过 DigitalOcean 的服务器进行搭建，无需翻墙。

## 所需费用

- **DigitalOcean 服务器**：4 美金/月，注册有 200 美金，2 个月有效。
- **野卡 开卡费用**：15 美金。
- **OpenAI Token 费用**：每 100,000 个 token 4 美分，大约 5 万个汉字。

## 先决条件

1. **DigitalOcean 账号**
2. **OpenAI 账号**

推荐使用 [野卡](https://bit.ly/bewildcard) ，OpenAI 仅支持信用卡支付，但不接受中国信用卡。创建 API Key 时需要验证手机号，使用 野卡 可以轻松完成注册、验证和开卡。

## 开始搭建

### 一. 创建 DigitalOcean 服务器

选择新加坡数据中心，使用 CentOS 8。

- **CPU 选项**：个人使用选择 4 美金/月的最低配置即可。
- **认证方法**：选择 SSH Key，DigitalOcean 提供创建 SSH Key 的教程。

点击 **Create Droplet**，等待服务器创建成功后，记录服务器 IP。

### 二. 服务器安装 Docker

通过 **Access Console** 打开服务器终端。

1. **更新 yum**

   bash
   yum update
   

2. **下载 Docker-ce 的 repo**

   bash
   curl https://download.docker.com/linux/centos/docker-ce.repo -o /etc/yum.repos.d/docker-ce.repo
   

3. **安装依赖**

   bash
   yum install https://download.docker.com/linux/fedora/30/x86_64/stable/Packages/containerd.io-1.2.6-3.3.fc30.x86_64.rpm
   

4. **安装 Docker-ce**

   bash
   yum install docker-ce
   

5. **启动 Docker**

   bash
   systemctl start docker
   

6. **开机启动 Docker**

   bash
   systemctl enable docker
   

7. **安装 Docker-compose**

   bash
   sudo wget https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m) -O /usr/local/bin/docker-compose
   

   如果遇到 `sudo: wget: command not found` 错误，运行：

   bash
   yum -y install wget
   

8. **添加操作权限**

   bash
   sudo chmod +x /usr/local/bin/docker-compose
   

9. **设置快捷方式**

   bash
   sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
   

10. **查看 Docker-compose 版本**

    bash
    docker-compose --version
    

### 三. 服务器部署 ChatGPT

1. **创建 docker-compose.yml 文件**

   - 在服务器上创建目录：`chatgpt_web`

     bash
     mkdir chatgpt_web && cd chatgpt_web
     

   - 创建 `docker-compose.yml` 文件

     bash
     vim docker-compose.yml
     

     如果遇到 `-bash: vim: command not found` 错误，运行：

     bash
     yum -y install vim*
     

   - 填写以下内容到 yml 配置文件中并保存：

     yaml
     version: '3'
     services:
       app:
         image: chenzhaoyu94/chatgpt-web:latest
         ports:
           - 3002:3002
         environment:
           OPENAI_API_KEY: sk-xxx # 修改为申请的秘钥
           TIMEOUT_MS: 60000
     

2. **部署并启动运行**

   bash
   docker-compose up -d
   

3. **登录 ChatGPT Web 页面**

   运行成功后，在浏览器访问 `http://服务器ip:3002`（需要开放 3002 端口）。

4. **其他问题解决**

   - 如果遇到 `fetch failed`，可以刷新页面或重启 Docker。

👉 [野卡 | 一分钟注册，轻松订阅海外线上服务](https://bit.ly/bewildcard)
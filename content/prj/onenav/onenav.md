---
date: '2024-12-13'
title: OneNav Navigate
description: "OneNav deploy on VM debian12"
---
## 环境要求
* 5.6 <= PHP <= 7.4
* 需支持SQLite
* PHP需支持pdo_sqlite组件

```bash
#依赖
sudo apt update && apt upgrade -y
sudo apt install -y software-properties-common apt-transport-https
#添加PHP源
sudo nano /etc/apt/source.list.d/php.list
deb https://mirrors.nju.edu.cn/php/ bookworm main
sudo apt update
#安装PHP5.6/7.4
sudo apt install -y php5.6 php5.6-cli php5.6-sqlite php5.6-pdo_sqlite
sudo apt install -y php7.4 php7.4-cli php7.4-sqlite php7.4-pdo_sqlite
#验证环境要求
php -v
php -m | grep sqlite
php -m | grep pdo_sqlite
```



### installation:
```bash
git clone https://dgithub.xyz/helloxz/onenav.git
```

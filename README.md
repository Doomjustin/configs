# 配置文件

## 常规配置
1. build-essensial
2. boost  -> build & install
3. clang  -> build & install
4. cmake  -> build & install
5. git
6. vim -> .vimrc
7. oh-my-zsh
8. ctags

## Ubuntu 20LTS安装Mysql
1. sudo apt update
2. sudo apt install mysql-server
3. 安装完成后验证是否以运行 sudo systemctl status mysql
4. root账号登录，免密 sudo mysql
5. 创建新用户<br/>
  > CREATE USER 'user'@'domain' IDENTIFIED BY 'password';
6. 给与全Table的访问权限<br/>
  > GRANT ALL ON *.* TO 'user'@'domain';
7. 退出后用新账户登录<br/>
  > exit<br/>
  > mysql -u [user] -p<br/>
  > password: 输入设定的密码

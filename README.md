# 配置文件

## 常规配置
1. build-essensial
2. cmake  -> build & install
3. git
4. vim -> .vimrc
5. oh-my-zsh

## Ubuntu 20 LTS安装Mysql
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

## Ubuntu最新GCC
```shell
sudo apt-get update
sudo apt-get install build-essential software-properties-common -y
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
sudo apt-get update
sudo apt-get install gcc-snapshot -y
sudo apt-get update
sudo apt-get install gcc-11 g++-11 -y
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 60 --slave /usr/bin/g++ g++ /usr/bin/g++-11

# To verify if it worked. Just type in your terminal
gcc -v
```

从源代码编译
```shell
# 相关依赖
sudo apt install libgmp-dev libmpfr-dev libmpc-dev
git clone --recursive git@github.com:gcc-mirror/gcc.git
cd gcc
git switch <version>
./configure

make -j4 install
# 设置优先级方便切换，默认用最高优先级
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 60 --slave /usr/bin/g++ g++ /usr/bin/g++-11
# 切换
sudo update-alternativess --config gcc
sudo update-alternativess --config g++
```

## Ubuntu下载boost
```shell
git clone --recursive git@github.com:boostorg/boost.git
cd boost
git checkout <version>
git submodule update --init
./bootstrap.sh
# ./b2
sudo ./b2 -j4 install

# 此时CMake的find_package()应该能够正常使用了

# headers only
./b2 headers
```
## Ubuntu CMake最新版
支持c++11的编译器<br/>
支持make命令

```shell
git clone git@github.com:Kitware/CMake.git
cd cmake
git checkout <version>
./bootstrap &&
make -j4 &&
sudo make install
```

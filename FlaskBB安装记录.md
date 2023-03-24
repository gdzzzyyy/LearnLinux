
## 安装python3
#### 安装python3所需要的外部库
86  yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel 
87  yum install gcc -y  //安装gcc
90  yum install wget    //安装wget 下载软件
91  wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz  //下载python3.7.4的压缩包
93  mv Python-3.7.4.tgz ../
97  mkdir /usr/local/python3
98  mv Python-3.7.4.tgz /usr/local/
99  cd /usr/local/
101  tar -xvf Python-3.7.4.tgz  //python压缩包解压
102  cd Python-3.7.4

#### 编译python
104  ./configure --prefix=/usr/local/python3/   
105  make  
106  sudo yum -y install make //如果没有make 就通过yum安装make
107  make
108  make install
109  yum -y install libffi-devel
110  make
111  make altinstall
####  创建python3的链接
112  ln -s /usr/local/python3/bin/python3 /usr/bin/python3

## python3安装之后， 就已经有pip3，此时创建pip3的链接
159  ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
181  pip3 install -upgrade setuptools
183  pip3 install --user --upgrade setuptools

## 把python3写入 PATH
192  echo ${PATH}
193  vim ~/.bashrc
    export PATH=$PATH:$HOME/bin
    export PATH=$PATH:$HOME/bin:/usr/local/python3/bin
194  source ~/.bashrc

## redis安装
204  sudo yum install epel-release
205  sudo yum update
206  sudo yum -y install redis
207  sudo systemctl start redis
208  systemctl enable redis.service  //重启redis服务

## mysql 安装
209  yum install mysql
210  yum install mysql-devel
211  wget http://dev.mysql.com/get/mysql80-community-release-el7-5.noarch.rpm
212  rpm -ivh mysql80-community-release-el7-5.noarch.rpm
213  yum install mysql-community-server
214  service mysqld restart
215  mysql -u root -p


## 升级pip 安装requirment.txt的库
272  pip3 install manimlib
273  pip3 -update
282  pip3 install -U setuptools
283  sudo pip3 install -U setuptools
284  pip3 install -U weditor
285  pip3 install -r requirments.txt
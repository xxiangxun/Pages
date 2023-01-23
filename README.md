Linux 上一键安装 Nginx + MySQL + PHP 环境。
一、LNMP 介绍
LNMP 是指一组通常一起使用来运行动态网站或者服务器的自由软件名称首字母缩写，即 Linux + Nginx + MySQL + PHP，相应的，还有 LAMP(Linux + Apache + MySQL + PHP)，以及 LNMPA(Linux + Nginx + MySQL + PHP + Apache)。
因为老王个人感觉 Apache 更耗内存，并且 Nginx 作为网络服务器完全够用，所以老王更喜欢安装 LNMP 环境。
二、LNMP 一键安装
1.开启安装窗口
可选操作。因为安装 LNMP 是比较耗时的操作（安装 + 优化），基本需要 30 分钟左右，具体时间与你 VPS 的配置有关，所以建议大家单独开启一个安装窗口，这样就算中途断开 VPS 的连接，也可以再次连上去查看 LNMP 安装进度。开启安装窗口命令如下：
screen -S lnmp
这里如果提示 screen: command not found，则先安装 screen：
# CentOS
yum update -y && yum -y install screen
# Ubuntu/Debian
apt-get update -y && apt-get install screen -y
如果你在安装 LNMP 过程中中途断开，则可以通过 screen -r lnmp 命令重新打开安装窗口。
2.一键安装 LNMP
LNMP 一键脚本使用命令如下：
wget http://soft.vpser.net/lnmp/lnmp1.6.tar.gz -cO lnmp1.6.tar.gz && tar zxf lnmp1.6.tar.gz && cd lnmp1.6 && ./install.sh lnmp
这里如果你想安装 LAMP 或者 LNMPA，那么只需要将 install.sh 后面的参数 lnmp 换成 lamp 或者 lnmpa。
同样的，如果提示 wget: command not found，则先安装 wget：
# CentOS
yum update -y && yum -y install wget
# Ubuntu/Debian
apt-get update -y && apt-get install wget -y
选择 Nginx + MySQL + PHP 的版本，PHP 建议使用 7 以上的版本，其他可以默认：

<img class="alignnone size-full wp-image-44" src="https://laowangblog.com/wp-content/uploads/2019/08/intall-php-mysql-nginx.jpg" alt="LNMP 一键脚本" width="1282" height="1458" srcset="https://laowangblog.com/wp-content/uploads/2019/08/intall-php-mysql-nginx.jpg 1282w, https://laowangblog.com/wp-content/uploads/2019/08/intall-php-mysql-nginx-264x300.jpg 264w, https://laowangblog.com/wp-content/uploads/2019/08/intall-php-mysql-nginx-768x873.jpg 768w, https://laowangblog.com/wp-content/uploads/2019/08/intall-php-mysql-nginx-900x1024.jpg 900w" sizes="(max-width: 1282px) 100vw, 1282px">
之后按回车即可安装，整个安装过程大概需要 30 分钟。安装完毕后，直接在浏览器输入你 VPS 的公网 IP，就能看到 LNMP 的欢迎界面了。
三、LNMP 配置文件介绍
一键安装 LNMP 环境后， Nginx + MySQL + PHP 的默认安装目录如下：
Nginx 目录: /usr/local/nginx/ MySQL 目录 : /usr/local/mysql/ MySQL 数据库所在目录：/usr/local/mysql/var/ PHP 目录 : /usr/local/php/ 默认网站目录 : /home/wwwroot/default/ Nginx 日志目录：/home/wwwlogs/
LNMP 默认的配置文件目录如下：
Nginx 主配置(默认虚拟主机)文件：/usr/local/nginx/conf/nginx.conf 添加的虚拟主机配置文件：/usr/local/nginx/conf/vhost/域名.conf MySQL 配置文件：/etc/my.cnf PHP 配置文件：/usr/local/php/etc/php.ini php-fpm 配置文件：/usr/local/php/etc/php-fpm.conf
一般维护站点需要用到的命令如下：
重启 nginx/mysql/php：lnmp nginx/mysql/php restart
重启所有：lnmp restart
添加站点：lnmp vhost add
添加数据库：lnmp database add
查看帮助：lnmp

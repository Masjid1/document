
# MySQL的卸载与安装

## MySQL 卸载
0. net stop mysqsl, 使用"mysqld remove"删除之前创建的默认服务
1. 控制面板，程序和功能，卸载mysql server。
2. 删除原安装目录下的mysql文件夹（内含my.ini）。
3. regedit, 删除HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL文件夹。
4. 删除系统生成的程序文件夹：C:\ProgramData\MySQL。
5. 重启电脑。


## [mysql安装](http://www.runoob.com/mysql/mysql-install.html)

MySQL安装的是社区版服务器8.0.11版本：
	[MySQL Community Server 8.0.11](https://dev.mysql.com/downloads/mysql/ "MySQL Community Server")

1. 解压到：C:\web\mysql-8.0.11。  
2. 在解压目录下新建my-default.ini文件。

		[client]
		port=3306

		[mysql]
		default-character-set=utf8
		
		[mysqld]

		default-authentication-plugin=mysql_native_password
		port=3306
		# The TCP/IP Port the MySQL Server will listen on
		port=3306

		# Path to installation directory. All paths are usually resolved relative to this.
		basedir="D:/Program/mysql-8.0.11-winx64"

		# Path to the database root
		datadir=D:/Program/mysql-8.0.11-winx64/data

		# The default character set that will be used when a new schema or table is
		# created and no character set is defined
		character-set-server=utf8

		# The default storage engine that will be used when create new tables when
		default-storage-engine=INNODB

		# Set the SQL mode to strict
		sql-mode="STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

		max_connections=151

3. 以管理员权限打开命令提示符
		
		D:
		cd D:/Program/mysql-8.0.11-winx64/bin
		mysqld install mysql57		// (如果服务已存在可以使用"mysqld remove"删除之前创建的默认服务。)
		mysqld  --initialize --console	// (初始化mysql服务，创建data文件夹，内含一个与计算机同名,扩展名为err的文件。
								// 其中一行为临时密码："A temporary password is generated for root@localhost: 
								// **wwwwwwwwwwww**", 12位。 时间较长。)
		net start mysql
		mysql -u root -p wwwwwwwwwwwww		// (以指定用户身份登录mysql)
		ALTER USER 'root'@'localhost' IDENTIFIED BY 'xxxxxx';	//（修改密码）
		exit	// 退出
		mysql -u root -p xxxxxx	// 重新登录


1. D:\Program\mysql-5.7.22-winx64\bin>**mysqld install mysql57 --defaults-file="D:\Program\mysql-5.7.22-winx64\my.ini"**
	
		Service successfully installed.

2. D:\Program\mysql-5.7.22-winx64\bin>**mysqld  --initialize --console**

		2018-06-16T03:53:27.717857Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
		2018-06-16T03:53:27.717941Z 0 [Warning] 'NO_ZERO_DATE', 'NO_ZERO_IN_DATE' and 'ERROR_FOR_DIVISION_BY_ZERO' sql modes should be used with strict mode. They will be merged with strict mode in a future release.
		2018-06-16T03:53:27.717946Z 0 [Warning] 'NO_AUTO_CREATE_USER' sql mode was not set.
		2018-06-16T03:53:29.011885Z 0 [Warning] InnoDB: New log files created, LSN=45790
		2018-06-16T03:53:29.362618Z 0 [Warning] InnoDB: Creating foreign key constraint system tables.
		2018-06-16T03:53:29.567513Z 0 [Warning] No existing UUID has been found, so we assume that this is the first time that this server has been started. Generating a new UUID: d4a5d5a5-7118-11e8-b94d-309c23154d2f.
		2018-06-16T03:53:29.596795Z 0 [Warning] Gtid table is not ready to be used. Table 'mysql.gtid_executed' cannot be opened.
		2018-06-16T03:53:29.623448Z 1 [Note] A temporary password is generated for root@localhost: B?Ryi(ljr1Tp

3. D:\Program\mysql-5.7.22-winx64\bin>**net start mysql57**

		mysql57 服务正在启动 .
		mysql57 服务已经启动成功。

4. D:\Program\mysql-5.7.22-winx64\bin>**mysql -u root -p**
// (以指定用户身份登录mysql)

		Enter password: **B?Ryi(ljr1Tp**
		Welcome to the MySQL monitor.  Commands end with ; or \g.
		Your MySQL connection id is 3
		Server version: 5.7.22-log

		Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

		Oracle is a registered trademark of Oracle Corporation and/or its
		affiliates. Other names may be trademarks of their respective
		owners.

		Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

		mysql>

5. mysql>**ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';**
//（修改密码为root）

		Query OK, 0 rows affected (0.00 sec)

6. mysql>**exit**
// 退出
		
		Bye

7. D:\Program\mysql-5.7.22-winx64\bin>**mysql -u root -p**

		Enter password: **root**
		Welcome to the MySQL monitor.  Commands end with ; or \g.
		Your MySQL connection id is 3
		Server version: 5.7.22-log

		Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

		Oracle is a registered trademark of Oracle Corporation and/or its
		affiliates. Other names may be trademarks of their respective
		owners.

		Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

		mysql>

8. mysql>**select version();**

		| version()  |
		| 5.7.22-log |

		1 row in set (0.00 sec)

9. mysql>**show variables like 'default_authentication_plugin';**

		| Variable_name                 | Value                 |
		| default_authentication_plugin | mysql_native_password |

		1 row in set, 1 warning (0.03 sec)

10. mysql>**create user 'root'@'%' identified WITH mysql_native_password BY 'root';**
		
		create user 'gogs'@'localhost' identified WITH mysql_native_password BY 'gogs';
		create user 'gogs'@'%' identified WITH mysql_native_password BY 'gogs';
		grant all privileges on *.* to 'root'@'%';
		flush privileges;

		create database gogs;

		grant all privileges on gogs.* to 'gogs'@'localhost';
		grant all privileges on gogs.* to 'gogs'@'%';
		flush privileges;

------------------

	# 在Windows上，你应该将本文件保存到你的服务器安装目录下(例如: C:\Program Files\MySQL\MySQL Server X.Y)。
	# 从而确保服务器使用启动选项"--defaults-file"来入去配置文件。
	# 为了从命令行运行服务器，在命令行解释器中执行：
	# 	mysqld --defaults-file="D:\Program\mysql-5.7.22-winx64\my.ini"
	# 为了手动安装服务器作为Windows服务，在命令行解释器中执行：
	# 	mysqld --install MySQL57 --defaults-file="D:\Program\mysql-5.7.22-winx64\my.ini"
	# 然后在命令行解释器中执行这条命令来打开服务器：
	# 	net start MySQL57

	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';

	select user,host,plugin,create_priv from mysql.user;

	grant all privileges on *.* to 'root'@'%';

	flush privileges;






## MYSQL

현재 오픈소스 DB중에 가장 인기많은 데이터베이스다.

```bash
sudo apt-get update
sudo apt-get install mysql-server

sudo ufw allow 3306

mysql -u root -p
```
-----------------------

### ip 바인딩

데이터베이스에 접근할수있는 ip를 설정한다.

```bash
sudo vi /etc/mysql/my.cnf
혹은 sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```

```
[client]
user=root(유저네임)
password=실제패스워드
port=3306
socket=/var/run/mysql/mysql.sock
[mysqld]
bind-address=ip주소 #0.0.0.0은 모두 허용
```
------------------------

### 패스워드 관련 문제 해결

```sql
GRANT ALL ON *.* TO 'user'@'localhost' IDENTIFIED BY 'passwd' WITH GRANT OPTION;
GRANT ALL ON *.* TO 'user'@'%' IDENTIFIED BY 'passwd' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;
```
```bash
sudo service mysql restart
```
or
```
Stop mysql:
1. service mysql stop

Run mysql with skip grants to be able to login without any password
2. mysqld_safe --skip-grant-tables &

Login as root
3. mysql -u root

4. mysql commands:
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD-HERE") where User='root';
mysql> flush privileges;
mysql> quit

Stop mysql
5. service mysql stop

Start mysql normally:
6. service mysql start

Try to login using your new password:
7. mysql -u root -p
```

-----------
이런에러가 발생하면 아래와같은 명령어를 터미널에서 실행하자.

```bash
ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement.
```
```bash
mysql> SET PASSWORD = PASSWORD('비밀번호');
```

------------

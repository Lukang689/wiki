### 允许远程访问mysql

```
    mysql -uroot -p
    use mysql;
    select host,user from user;
    update user set host='%' where user='root';
    flush privileges;
```

### 修改编码格式

通过命令查看

```
    mysql> show variables like 'character%';
```

同样可以通过命令行修改

```
    mysql> set character_set_server=utf8;
```

或者修改配置/etc/mysql/my.cnf，在mysqld字段中增加

```
    character_set_server=utf8
```

### 将mac序列导入到数据djdb数据库mac表中

```
use djdb;
drop procedure if exists addmac;
delimiter
create procedure addmac()
begin
declare i int;
declare macs int;
declare mace int;
declare stbtype text;
declare pon text;

set stbtype="J6000";
set macs=x'14E00594';
set mace=x'14E0065B';
set pon="POReq201704121";

set i=macs;
start transaction;
while i<=mace do
insert into mac(macAddr0,status,stbtype,po) values(concat("DC2A",hex(i)),0,stbtype,pon);
set i=i+2;
end while;
commit;
end;
delimiter ;
call addmac();
```
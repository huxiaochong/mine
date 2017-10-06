//对于之前的mysql,和oracle有无国共同之处,数据的CRUD操作
（一）创建表
  语法：
  CREATE TABLE 表名称(
   字段名 类型(长度) primary key,
   字段名 类型(长度),
   .......
);
 数据类型：
1. 字符型
（1）CHAR : 固定长度的字符类型，最多存储 2000 个字节
（2）VARCHAR2 :可变长度的字符类型，最多存储 4000 个字节
北京市昌平区建材城西路金燕龙办公楼一层 电话：400-618-9090
（3）LONG : 大文本类型。最大可以存储 2 个 G
2.数值型
NUMBER : 数值类型
例如：NUMBER(5) 最大可以存的数为 99999
 NUMBER(5,2) 最大可以存的数为 999.99
3.日期型
（1）DATE：日期时间型，精确到秒
（2）TIMESTAMP：精确到秒的小数点后 9 位
4.二进制型（大数据类型）
（1）CLOB : 存储字符,最大可以存 4 个 G
（2）BLOB：存储图像、声音、视频等二进制数据,最多可以存 4 个 G
（二）修改表
1. 增加字段语法:
ALTER TABLE 表名称 ADD(列名 1 类型 [DEFAULT 默认值]，列名 1 类型
[DEFAULT 默认值]...)
为业主表增加两个字段，语句：
--追加字段
ALTER TABLE T_OWNERS ADD
(
 REMARK VARCHAR2(20),
 OUTDATE DATE
)
2. 修改字段语法：
ALTER TABLE 表名称 MODIFY(列名 1 类型 [DEFAULT 默认值]，列名 1 类型
[DEFAULT 默认值]...)
修改两个字段的类型，语句：
--修改字段
ALTER TABLE T_OWNERS MODIFY
(
REMARK CHAR(20),
OUTDATE TIMESTAMP
)
3. 修改字段名语法：
ALTER TABLE 表名称 RENAME COLUMN 原列名 TO 新列名
北京市昌平区建材城西路金燕龙办公楼一层 电话：400-618-9090
语句：
ALTER TABLE T_OWNERS RENAME COLUMN OUTDATE TO EXITDATE
4. 删除字段名
--删除一个字段
ALTER TABLE 表名称 DROP COLUMN 列名
--删除多个字段
ALTER TABLE 表名称 DROP (列名 1,列名 2...)
语句：
--删除字段
ALTER TABLE T_OWNERS DROP COLUMN REMARK
（三）删除表
语法：
DROP TABLE 表名称
五、数据增删改
（一）插入数据
语法：
INSERT INTO 表名[(列名 1，列名 2，...)]VALUES(值 1，值 2，...)
北京市昌平区建材城西路金燕龙办公楼一层 电话：400-618-9090
执行 INSERT 后一定要再执行 commit 提交事务
向业主表插入数据：
insert into T_OWNERS VALUES (1,' 张三丰
',1,'2-2','5678',sysdate,1);
语句中的 sysdate 是系统变量用于获取当前日期，点击齿轮的图标后，再点击下
图的绿色图标，此图标为 commit
我们再次录入一条数据，语句如下:
insert into T_OWNERS VALUES (2,'赵大侃
',1,'2-3','9876',sysdate,1);
commit;
（二）修改数据
语法：
UPDATE 表名 SET 列名 1=值 1，列名 2=值 2，....WHERE 修改条件；

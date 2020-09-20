

```


https://jerrynest.io/windows-mysql-installer/
https://clay-atlas.com/blog/2019/11/16/mysql-mysqlworkbench-tutorial-download-install-steps/
下載並安裝 MySQL Installer

https://jerrynest.io/mysql-tutorial/

簡單的 MySQL 使用教學























https://blog.techbridge.cc/2020/02/09/sql-basic-tutorial/

關聯式資料庫




SQL 基本概要和分類
SQL 主要是以 keyword 關鍵字和資料表（table）名稱和欄位（column）名稱當作一段完整的語句。SQL 語法使用分號 ; 當作結尾，英文字母不區分大小寫，單字間使用空白分隔。單行註解寫法 --，多行註解使用 /**/ 包裹。

1. DDL（Data Definition Language）
DDL 又稱為資料定義語言，能建立或刪除資料庫和資料表等用來儲存的單位。

CREATE
DROP
ALTER

2. DML（Data Manipulation Language）
DML 能查詢或修改資料表的紀錄。

INSERT
SELECT
UPDATE
DELETE

3. DCL（Data Control Language）
DCL 為可用來取消操作和設定操作權限的指令。

COMMIT
ROLLBACK
GRANT
REVOKE















https://www.cynet.com.tw/learning/MySql/Page04.htm
MySQL的重要語法















MySQL Workbench 圖形化使用者介面 (GUI)

使用 Workbench
使用 root 或其他使用者帳戶登入

點選左上方 + 新增一個連線。

輸入連線名稱，帳號、密碼 (或連線時輸入)，可以按下「Test Connection」確認資料庫是否連接成功。

查看所有的使用者

use mysql; #使用mysql資料庫
select *from user; -- 選擇user資料表

在編輯區輸入上方 select user 指令，結果將如下圖所示。預設的最高管理者為 root，而 jerry 是安裝時新增的帳號。

執行單行指令快捷鍵：Ctrl + Enter。
執行全部或已框選指令快捷鍵：Ctrl + Shift + Enter。
localhost、127.0.0.1 和 ::1 (IPv6) 皆代表本機地址。
單行註解：- - 註解內容 or #註解內容
多行註解：/註解內容/

新增使用者

如果想要新增額外的帳號，透過這個指令並給予使用者權限

grant privileges on database.table to 'user'@'localhost' identified by 'password'
privileges 設定權限等級。
database.table 設定可以存取的資料庫與資料表名稱。
'user'@'localhost' 設定使用者的帳號與主機。
'password' 設定使用者的密碼。
舉例來說，新增一個帳號 student，密碼為 123

all代表擁有所有管理權限。
.代表所有資料庫裡的所有資料表。
with grant option：可以賦予其他使用者權限。

編輯使用者帳號

想要刪除使用者或是修改密碼，MySQL有內建的安全機制，必須先關閉安全模式才能進行操作

set SQL_SAFE_UPDATES = 0; #關閉Safe Update Mode
delete from user where user ='user'; #刪除使用者
update user set password= password ('password') where user='user'; #修改密碼
flush privileges; #在mysql資料庫內，要用flush更新記憶體上的資料

MySQL資料格式
主要分為三類：Numeric、Date and Time、String Type。

可參考 MySQL 所支援的各種欄位型態

建立/刪除資料庫、資料表
建立/刪除 test1 資料庫

create database test1;
use test1;
show tables;
drop database test1;
建立/刪除 mytable 資料表

create table mytable(school char(5),name char(10),id int);
show tables;
describe mytable;
drop table mytable;

常用語法舉例
資料表查詢 (選擇資料表 mytable 的所有欄位資料)

select * from mytable ;
新增資料

insert into mytable(school, name, id) values ('NCTU','Jerry','123');
insert into mytable values ('NCTU','Jerry','123');
更新資料

update mytable set name = 'HaHa' where id = '123';
刪除資料

delete from mytable where name = 'HaHa';
由 txt 文字檔匯入資料 (用 tap 隔開欄位)

load data local infile "c:\\data.txt" into table mytable
mysql41 - 簡單的 MySQL 使用教學
mysql5 - 簡單的 MySQL 使用教學
資料表查詢+條件+排序 (DESC 代表由大到小排序)

select * from mytable where id = '123' order by name DESC;
改變資料欄位 (加入時間記錄)

alter table mytable add column recordtime TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP;


MySql 基本語法(查詢、插入、更新)
分享: facebook PLURK twitter  
雖然使用MySql已經這麼多年了

但是每每使用這些基本語法卻得重新確認，真是見笑....

趁這機會好好複習一下吧

 

1. 資料表查詢

 SELECT  `欄位` FROM `資料表`;

一般用法： SELECT * FROM `table` ;

翻譯：選擇table這個資料表所有欄位的資料(就是全選啦!!)

備註：星號代表所有欄位，在sql語法、指令中星號代表全部

 

2. 資料表查詢  +  排序

SELECT  `欄位` FROM `資料表` ORDER BY  `特定欄位` DESC ;

一般用法： SELECT  `id`,`name`  FROM `table` ORDER BY  `特定欄位` DESC ;

翻譯： 選取table資料表內的 id 和 name 這兩個欄位，並根據id這欄位做降冪排序(由高而低、由大到小、由z到a)

備註：ASC則是(由低而高、由小到大、由a到z)，與DESC相反

 

3. 資料表查詢 + 查詢條件

SELECT  `欄位` FROM `資料表` WHERE  `特定欄位` = 數字 ;

一般用法： SELECT  *  FROM `table` WHERE  `id` = 363 ;

翻譯： 在table資料表內的尋找 id 欄位的內容是 363 且將 所有欄位的資料都取出來

 

SELECT  `欄位` FROM `資料表` WHERE  `特定欄位` LIKE  字串 ;

一般用法： SELECT  `id`,`name`  FROM `table` WHERE  `name` LIKE  'admin' ;

 翻譯： 在table資料表內的尋找 name 欄位的內容是 admin 且將 id 和 name 這兩個欄位都取出來

 

SELECT  `欄位` FROM `資料表` WHERE  `特定欄位` LIKE  %字串% ;

一般用法： SELECT  `id`,`name`  FROM `table` WHERE  `name` LIKE  %'adm'% ;

翻譯： 在table資料表內的尋找 name 欄位的內容包含 adm ( admin 符合、administrator 也符合) 且將 id 和 name 這兩個欄位都取出來

 

備註：數字形態比對用 = (也可以用 > 、 < 、 >= 、 <=) ; 字串形態比對是使用 LIKE (LIKE 使用的是完全比對);字串如果需要模糊比對需要使用 %

 

4. 新增(插入)一筆資料

INSERT INTO `資料表`(`欄位1`,`欄位2`) VALUES ( '資料1' , '資料2' );

一般用法： INSERT INTO `table`(`id`,`name`) VALUES ( '12' , 'stanley' );

翻譯： 在 table 資料表內新增一筆資料 在 id 欄位內填入 12 ，在 name 欄位內填入 stanley

備註：在新增一筆資料時，必須將所有欄位和值都填上，預設是空值的欄位值可改成''，且須注意資料表本身的欄位結構、儲存型態，例如： id 欄位禁止存入字串、設有primary屬性的欄位不得輸入空值

 

5. 更新(修改)一筆資料

UPDATE `資料表` SET `欄位2` = '資料2'  WHERE `欄位1` = '資料1'  ;

一般用法：UPDATE `table` SET `name` = 'newaurora'  WHERE `id` = '12'  ;

翻譯： 在 table 資料表內找出 id = 12 的資料，並將 name 欄位內的資料修改為 newaurora

備註：更新資料時必須確定條件設定是否正確，如上例，會把資料表內 id 欄位裡是 12 的資料都找出來並修改成newaurora ，因此使用前必須注意條件判斷



















































































http://tw.gitbook.net/html/database/index.html

xampp

MySQL
sqlite
MongoDB 


http://www.ipshop.xyz/13825.html
import MySQLdb


目前常見的 RDBMS 有

MySQL
SQLite
PostgreSQL
Oracle Database
Microsoft SQL

關聯式資料庫
非關聯式資料庫（NoSQL）


常見的關聯式資料庫如MySQL、Oracle與MSSQL。


由於 Heroku 使用 PostgreSQL 資料庫

PostgreSQL連接Python


NoSQL資料庫中的王者【MongoDB】


佈署Python Flask網站留言板應用程式到Heroku + PostgreSQL資料庫系統

介紹MariaDB資料庫的基本操作，MariaDB資料庫與MySQL資料庫操作上並無差別，以下依序介紹MariaDB的安裝以及的基礎操作。

https://cloud.tencent.com/developer/article/1629481


https://www.jianshu.com/p/79cc4a57e9a5

https://djangogirlstaipei.herokuapp.com/tutorials/deploy-to-heroku/?os=windows

http://tw.gitbook.net/html/database/index.html

http://tw.gitbook.net/postgresql/2013080998.html

https://swf.com.tw/?p=1327

https://www.haohaninfo.com/Teach/Python/15.php

https://nkust.gitbook.io/python/sqlite-liao-cao-zuo-jie

http://www.ipshop.xyz/13825.html

https://www.itread01.com/content/1542433630.html



















```

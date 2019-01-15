[TOC]

# PHP

# PHP基础

### 1、变量

#### 变量的命名规则

- 以`$`开头
- 严格区分大小写
- 由字母、数字、下划线组成
- $后面不能以数字开头
- 变量命名要有意义
- 可以使用中文（不推荐使用）
- 驼峰命名法

#### 变量的操作

- 赋值: `=`
- 输出: `echo`
- 判断变量是否存在: `isset()`
- 销毁变量: `unset()`
- 变量和字符串连接：`.`

### 2、单引号和双引号

#### 单引号

- 不解析变量
- 不解析转义字符
- 效率比双引号快
- 转义`\\`和`\'`

#### 双引号

- 解析变量

- 解析转义字符

- 字符串和变量混排使用双引号和大括号

  ```php
  echo "{$name}是我的朋友"；   //xxx是我的朋友
  echo $name.'是我的朋友'；   //xxx是我的朋友
  echo "'$name'是我的朋友";  //'xxx'是我的朋友
  ```

### 3、数据类型

#### 标准类型

##### 整型：整数`integer`

##### 浮点型：小数`float`

##### 布尔类型：`bool、boolean`

##### 字符串: `string`

#### 混合类型

##### 数组: `array`

##### 对象: `object`

#### 特殊类型

##### 空: `null`

##### 资源: `resource`

### 4、数据类型的转换

#### 判断数据类型

```php
$str = '123.abc';
echo gettype($str)
```

#### 数据类型的转换

```php
intval($str);  //转换为整型,截取开头的数字字符串转换为整数
//字符串开头，则转换为0
floatval($str);//转换为浮点型，截取开头的数字字符串转换为浮点数
//字符串开头，则转换为0
strval($num);   //转换为字符串
boolval($num); //转换为布尔型
//null转换成整型为0，null转换成浮点数为浮点型的0;
//null转换成字符串为空字符串,null转换成布尔型为false;
```

#### 判断数据类型常用函数

1. `is_array()`
2. `is_string()`
3. `is_bool()`
4. `is_float()`
5. `is_object()`
6. `is_int()`
7. `is_numeric()`
8. `is_resource()`
9. `is_null()`
10. `is_scalar()`
11. `gettype()`：获取类型
12. `var_dump()`：输出值和类型

### 5、常量

```php
define('ABC','abc');  //常量的定义
echo ABC;
const ABC = 'abc'; //常量的定义
//定义完成不可更改
//一般用大写字母
//作用域是全局的
//常量的值必须为标量
//常量写在字符串中不会被解析
//输出的时候不需要以$开头
defined(ABC);  //判断常量是否被定义
__FILE__;   //当前文件
__LINE__;  //当前代码的行数
PHP_VERSION; //php版本
__DIR__; //当前文件所在目录
__FUNCTION__; //获取函数名
M_PI; //圆周率
__METHOD__; //获取当前成员方法名
__NAMESPACE__;//获取当前命名空间名字
__TRAIT__;//获取当前TRAIT名字(多继承)
__CLASS__;//获取当前类名
```

### 6、运算符

#### 1)、算术运算符

- +：加法
- -：减法
- *：乘法
-  /：除法
- %：取模
- ++：自增
- —：自减

#### 2)、比较运算符

- `>`
- `<`
- `>=`
- `<=`
- `==`
- `===`
- `!=`
- `!==`

#### 3)、逻辑运算符

- `&&`：与
- `||`：或
- `!`：非

#### 4) 、赋值运算符

- `=`
- `+=`
- `-=`
- `*=`
- `/=`
- `%=`
- `.=`

### 7、流程控制

#### 条件语句

##### if条件语句

```php
$num = 1;
if ($num > 1) {
    echo 'dayu';
} elseif ($num < 1) {
    echo 'xiaoyu';
} else {
    echo '=';
}
```

##### switch条件语句

```php
switch($test){
    case 1:
    case 2:
    case 3:
        echo '1,2,3';
        break;
    case 5:
        echo 5;
        break;
    default:
        echo '备胎';
}
$num = 10;
switch(true){
    case $num >5:
        echo 'true';
        break;
    case $num <5:
        echo 'false';
        break;
    default:
        echo '=';
}
```

##### 条件语句为false的情况

- 整型或浮点型的0
- 空字符串，有个空格都为true
- 字符串'0'
- 空字符串'0.0000...' 小数点后面都为0，任何非0位返回true
- 空数组
- null

##### 随机数函数:`mt_rand([min],[max])`

- 没有参数：无限制随机数,整型
- 两个参数：则在最小值和最大值区间内生成随机数，闭区间

#### 循环语句

##### for循环

```php
for ($i = 1; $i < 5; $i++) {
    echo $i . '<br>';
}
```

##### while循环

```php
$i = 1;
while ($i < 5) {
    echo $i . '<br>';
    $i++;
}
```

##### do-while循环

```php
$i = 1;
do {
    echo $i . '<br>';
    $i++;
} while ($i < 5);
```

##### `break`和`continue`

- break：跳出循环，不再执行;
- continue：跳出当前次循环，接着执行下一次循环;

##### 循环嵌套

```php
echo '<table width="800" border="1">';
for ($i = 1; $i < 10; $i++) {
    echo '<tr>';
    for ($j = 1; $j <= $i; $j++) {
        echo "<td>{$j}*{$i}=" . $i * $j."</td>";
    }
    echo '</tr>';
}
echo '</table>';
```

### 8、函数

#### 语法格式

```php
function name (形参) {
    函数体;
    return xxx;   //返回值
}   // 定义函数的语法
$ret = name(实参);    //调用函数
```

> 函数名的命名规则同变量，但是不区分大小写

#### 参数

##### 形参

###### 基本语法

```php
function info($name,$age){
    echo $name. ' ' . $age;
}
```

###### 参数默认值

```php
function info ($name ='Lucy',$age = 25) {
    echo $name.' '.$age;
}
info();  //不传实参则按照默认参数调用函数
```

###### 限制形参的数据类型

> php7.0新增的功能

```php
function sum(int $num1, int $num2) {
    return $num1 + $num2;
}
```

###### 可变参数

> 实际参数是一个数组

```php
function sum(...$arr) {
    var_dump($arr);
}
sum(1,2,3);
```

##### 实参

###### 基本语法

```php
info('Lucy',25);
```

###### 参数拆解

> 把复合数据打散作为函数的参数

```php
function sum($a,$b,$c,$d){
    var_dump($a,$b,$c,$d);
}
$arr = [1,2,3,4];
sum(...$arr);
```

#### 返回值

##### 限制返回值的数据类型

> php7.0新增的功能

```php
function sum(int $num1, int $num2):string
{
    return $num1 + $num2;
}
```

#### 匿名函数

##### 语法格式

```php
$test = function() {
    echo '我是匿名函数';
}
```

##### 调用方式

```php
$test();
```

### 9、作用域

#### 全局变量

- 函数外部的变量
- 函数内部不能调用

#### 内部变量

- 函数内部的变量
- 函数外部不能调用

#### 超全局变量

#### 静态变量

##### `static`关键字

- 只会初始化一次

```php
function total() {
    static $num = 1;   //每次调用$num记录的是上一次的值
    $num *= 2;
}
```

### 10、常用函数

#### 数学函数

##### 随机数

###### `rand()`

###### `mt_rand()`

##### 小数

###### `floor()`:向下取整

###### `ceil()`：向上取整

###### `round()`：四舍五入取整

##### 其它

###### `abs()`：绝对值

###### `pi()`：圆周率

###### `M_PI()`：圆周率

###### `pow()`：指数表达式

###### `max()`：最大值

###### `min()`：最小值

#### 字符串函数

##### 大小写转换

###### `strtolower()`：转换为小写

###### `strtoupper()`：转换为大写

###### `lcfirst()`：首字母小写

###### `ucfirst()`：首字母大写

###### `ucwords()`：每个单词首字母大写

##### 空白处理

###### `trim()`：去掉首尾空白字符

###### `ltrim()`：去掉开头的空白字符

`rtrim()`：去掉结尾的空白字符

###### `chop()`：去掉结尾的空白字符

##### 查找定位

### 11、文件包含

- `include()`
- `include_once()`
- `require()`
- `require_onece()`

> 模块化，引入另外一个文件
>
> `include`引入出错不影响后面代码的执行
>
> `require`引入出错整个程序不能运行

```php
include('2.php');     //引入同一个文件一次以上会报错
require('2.php');    //引入同一个文件一次以上会报错
include_once('2.php');   // 引入一次，不会重复引入
require_once('2.php');   // 引入一次，不会重复引入
```

### 12、数组

#### 数组的定义

##### 定义空数组

```php
$arr = array();
$arr = [];
```

##### 字面量定义

```php
$arr = [1,2,3];
```

##### `array()`定义

```php
$arr = array(1,2,3);
```

##### 指定下标定义

```php
$arr = ['3' => 'a', 'b', 'c'];  //数组下标从3开始
```

##### 定义关联数组

```php
$arr = [
    'java' => '大数据',
    'html' => '页面',
    'php' => '数据库'
];
```

##### 定义多维数组

> 关联数组和索引数组可以混合嵌套

```php
$arr = [
    'php' => ['html','js','css'],
    'java'
];
```

#### 数组的增删改查

##### 查询

###### 查询元素

```php
$arr = [0,1,2,3];
echo $arr[0];   //通过下标查询,下标从0开始
$arr = ['php' =>'good','java' => 'perfect'];
echo $arr['java']; //关联数组的查询
$arr = ['php' =>'good','java' => ['a','b','c']];
echo $arr['java'][1];  //多维数组的查询
```

###### 查询成员个数

```php
echo count($arr);
```

###### 循环索引数组

```php
for ($i=0;$i<count($arr);$i++){
    echo $i;     //获取的是数组的下标
}
```

###### `foreach`循环数组

> 同时获取数组的键和值，适用于索引数组和关联数组

```php
foreach($arr as $key => $value){
    echo $key . '=' . $value;  //遍历数组的键和值
}
foreach($arr as $value){
    echo $value;   //只遍历数组的值
}
```

###### 使用数组通过`list()`给变量赋值

> 只适用于索引数组，如果数组内部有关联数组，则跳过，使用下一个索引数组成员赋值

```php
$arr = [1,2,3,4,5];    // 数组成员数量大于list成员数量不报错
list($a,$b,$c,$d) = $arr;  //满足list内部变量的需求，否则报错
while (list($key, $value) = each($arr)) {
    echo $key . ' ' . $value.'<br>';
}
```

##### 增加

```php
$arr[10] = 4;   // 指定索引添加成员
$arr[] = 5;   // 顺序添加成员，从最大的下标开始
$arr['css'] = 'pretty';  //关联数组添加成员
```

##### 删除

```php
unset($arr[1]);  //删除以后数组中下标不会重新计算
$arr = array_values($arr);  //重新计算下标，返回数组
$arr = array_splice($arr,1,2); //截取数组，返回数组
```

##### 修改

```php
$arr[1] = 'php'; //修改索引数组
$arr['java'] = 'excellent';   //修改关联数组
```

#### 超全局数组

##### `$_GET`

##### `$_POST`

##### `$_REQUEST`

##### `$_SERVER`

##### `$_COOKIE`

##### `$_SESSION`

```php
$username = $_POST['username']; //通过数组方法取值
```

### 13、错误

#### 错误类型

##### Notice

> 后续代码会继续执行

##### Warning

> 后续代码会继续执行

##### Fatal

> 后续代码不会执行

#### 屏蔽错误显示

##### 通过@屏蔽错误

> 不能屏蔽Fatal错误

```php
@var_dump($name);
```

##### 通过配置文件屏蔽错误

```php
display_errors = Off;   //关闭显示错误
display_errors = On;   // 开启显示错误
```

##### 错误日志

```php
error_log = '日志路径';  //错误日志的文件路径
```

### 14、时间

#### 时区

##### 设置时区

###### 通过代码设置

```php
date_default_timezone_set('PRC');   //设置时区
date_default_timezone_set('Asia/Shanghai');   //设置时区
echo date('Y-m-d H:i:s');    // 输出当前日期和事件
```

###### 通过配置文件设置

```php
date.timezone = "PRC"
```

##### 显示时区

```php
echo date_default_timezone_get();  // 显示当前时区的设置
```

#### 时间戳

```php
$time = time();  //获取当前时间戳
echo date('Y-m-d H:i:s', $time) //时间戳转为可读的时间格式
```

### 15、数据库

#### 命令操作数据库

##### 进入和退出操作

###### 进入数据库

> mysql -u用户名 -p密码
>
> mysql -u用户名 -p   根据提示输入密码

###### 退出数据库

> quit  |  exit

###### 取消未执行的命令

> show database \c

##### 数据库相关命令

###### 显示数据库列表

```mysql
show databases;
```

###### 创建数据库

```mysql
create database bbs charset=utf8;
create database bbs character set utf8;
```

###### 删除数据库

```mysql
drop database bbs;
```

###### 切换数据库

```mysql
use bbs;
```

###### 查看当前数据库

```mysql
select database();
```

###### 查看当前用户

```mysql
select user();
```

###### 查看数据库的编码格式

```mysql
show variables like 'character_set_database';
```

###### 修改数据库的编码格式

```mysql
alter database bbs character set utf8;
alter database bbs charset=utf8;
```

##### 数据表相关命令

###### 创建表

```mysql
create table user(
    id int,
    username varchar(32),
    password varchar(32)
) default charset=utf8;
```

###### 显示表

```mysql
show tables;
```

###### 删除表

```mysql
drop table user;
```

###### 显示表结构

```mysql
desc user;
```

###### 修改表名

```mysql
alter table user rename userinfo;
```

###### 修改表字段、编码

```mysql
alter table user change password pass varchar(32) character set utf8;
alter table user modify username varchar(40) character set utf8;
```

###### 修改表编码格式

```mysql
alter table user character set utf8;
alter table user charset=utf8;
```

###### 显示表的创建源码

```mysql
show create table user;
```

###### 删除表字段

```mysql
alter table user drop password;
```

###### 添加表字段

```mysql
alter table user add password varchar(32) first;
alter table user add password varchar(32) after username;
```

#### 数据库数据类型

##### 整型

|   整型    | 所占字节 |        取值范围        |
| :-------: | :------: | :--------------------: |
|  tinyint  |  1字节   |        -128~127        |
| smallint  |  2字节   |      -32768~32767      |
| mediumint |  3字节   |    -8388608~8388607    |
|    int    |  4字节   | -2147483648~2147483647 |
|  bigint   |  8字节   |   +-9.22*10的18次方    |

##### 浮点型

|   浮点类型    | 所占字节 |              备注              |
| :-----------: | :------: | :----------------------------: |
|  float(m, d)  |  4字节   | 单精度浮点数，m总个数，d小数位 |
| double(m, d)  |  8字节   | 双精度浮点数，m总个数，d小数位 |
| decimal(m, d) |          |      存储为字符串的浮点数      |

##### 字符型

| 字符类型 |   所占字节   |    备注    |
| :------: | :----------: | :--------: |
|   char   |  0-255字节   | 定长字符串 |
| varchar  | 0-655355字节 | 变长字符串 |

###### MD5转换

```php
echo md5('abc');   // 转换密码为32位定长字符串存入数据库
```

##### 时间类型

| 时间类型 | 所占字节 |          备注          |
| :------: | :------: | :--------------------: |
|   date   |  4字节   | 日期，格式：2014-09-18 |

##### 自动增长类型

- `auto_increment`,只用于整型，可以设置起始值，默认为1

- 常与后面`primary key`一起使用

- 创建表时在整型字段后面加上：auto_increment=起始值 primary key

- 修改起始值

  ```mysql
  alter table user auto_increment=起始值;
  ```

#### 索引

##### 添加索引

###### 普通索引

```mysql
alter table user add index(age);
```

###### 唯一索引

```mysql
alter table user add unique(password); 
```

###### 全文索引

```mysql
alter table user add fulltext(username);
```

###### 主键索引

```mysql
alter table user add primary key(id);
```

##### 查询索引

```mysql
show index from user;
```

#### 数据库增删改查

##### 添加数据

###### 插入一条数据

```mysql
insert into user values(1,'王宝强','123');
insert user(id,user,pass) values(0,'Lucy','123');
```

###### 插入多条数据

```mysql
insert user(user,pass) values('Lucia','123'),('Lucy','456'),('Artist','789');
```

##### 删除数据

```mysql
delete from user where user='Lucy';
```

##### 修改数据

###### 修改一个字段

```mysql
update user set user='Lucia' where id=1;
```

###### 修改多个字段

```mysql
update user set user="Lucia",pass="223" where id=1;
```

##### 单表查询数据

###### 查询所有数据

```mysql
select * from user;  //效率慢，不推荐使用
select user,pass from user;   //查询指定字段
```

###### 去除重复值

```mysql
select distinct user from user; //user去重
```

###### `where`条件查询

```mysql
select * from user where id=1;
select * from user where id>2;
select * from user where id<2;
```

###### `between`和`and`取区间值

```mysql
select * from user where age between 30 and 40;
```

###### `or`取值

```mysql
select * from user where age=40 or age=50;
```

###### `and`取值

```mysql
select * from user where age>20 and sex=0;
```

###### `!=`取值

```mysql
select * from user where age !=50;
select * from user where age<>50;
```

###### `in`取值

```mysql
select * from user where age in(15,16,17);
```

###### `like`模糊查询

```mysql
select * from user where user like '%香%';
select * from user where user like '%香%' or user like '%北%';
```

###### 排序查询

```mysql
select * from user order by age asc; //默认升序
select * from user order by age desc;  //降序
```

###### `limit`查询

```mysql
select * from user limit 5,3;  //从5开始，查询3条
select * from user limit 3;  // 从0开始，查询3条
```

###### 分组查询

```mysql
select * from user group by room;
```

###### 数量查询

```mysql
select count(*) from user;
```

###### `as`别名

```mysql
select username as name from user;
```

##### 多表查询数据

###### 内联

> where 不能放在on的前面

```mysql
select count(*) from mzitu_title inner join mzitu_tag_2_title on mzitu_title.id=mzitu_tag_2_title.title_id where mzitu_tag_2_title.tag_id=2;
```

###### 左联

```mysql
select shop_user.username from shop_user left join shop_goods on shop_user.gid=ship_goods.id;
```

###### 右联

```mysql
select shop_user.username from shop_user right join shop_goods on shop_user.gid=ship_goods.id;
```

###### 嵌套查询

```mysql
select * from shop_user where gid in(select gid from shop_goods);
```

#### php操作数据库

##### 连接数据库查询数据

```php
//连接数据库
$link = mysqli_connect('localhost','root','1234');
//判断是否连接成功
if (!$link){
    exit('数据库连接失败');
}
//设置字符集
mysqli_set_charset($link,'utf8');
//选择数据库
mysqli_select_db($link,'mzitu');
//准备sql语句
$sql = "select * from mzitu_title limit 10";
//发送sql语句
$res = mysqli_query($link,$sql);
//处理结果集
while($rows = mysqli_fetch_assoc($res)){
    var_dump($rows);  //返回关联数组
}
while($rows = mysqli_fetch_row($res)){
    var_dump($rows);  //返回索引数组
}
while($rows = mysqli_fetch_array($res)){
    var_dump($rows); //返回关联数组和索引数组
}
$rows = mysqli_num_rows($res); //返回查询结果的行数
$rows = mysqli_affected_rows($link); //查询影响的行数
$res = mysqli_insert_id($link); //返回插入数据的id
//关闭数据库
mysqli_close($link);
```

##### 删除数据库数据

```php
$id = $_GET['id'];
$link = mysqli_connect('localhost','root','1234');
if (!$link){
    exit('连接数据库失败')
}
mysqli_set_charset($link,'utf8');
mysqli_select_db('mzitu');
$sql = "delete from mzitu_title where id=$id";
$boolean = mysqli_query($link,$sql);
if ($boolean $$ mysqli_affected_rows($link)) {
    echo '删除成功';
} else {
    echo '删除失败';
}
mysqli_close($link);
```

##### 修改数据库

> 修改数据如果字段是字符串相关类型的，变量需要加引号

```php
<?php  edit.php
$link = mysqli_connect('localhost','root','1234');
if (!$link){
    exit('连接数据库失败')
}
mysqli_set_charset($link,'utf8');
mysqli_select_db($link,'mzitu');
if ($_SERVER['REQUEST_METHOD'] == 'GET'){
    $id = $_GET['id'];
    $sql = "select * from mzitu_title where id=$id";
	$obj = mysqli_query($link,$sql);
	$rows = mysqli_fetch_assoc($obj);
}
mysqli_close($link);
?>
<?php   save.php
$link = mysqli_connect('localhost','root','1234');
if (!$link){
    exit('连接数据库失败')
}
mysqli_set_charset($link,'utf8');
mysqli_select_db($link,'mzitu');
$id = $_POST['id'];
$title = $_POST['title'];
$sql = "update mzitu_title set title='$title' where id=$id";
$res = mysqli_query($link,$sql);
if ($res){
    echo '数据修改成功';
    echo "<a href='index.php'>返回首页</a>"
}
mysqli_close($link);
?>
<html> edit.php
    <form action="save.php" method="post">
        <input type="hidden" value="<?php echo $id ?>" name="id">
        <input type="text" name="title" value="<?php echo $rows['title']?>">
        <input type="submit">
    </form>
</html>

```

##### 分页

```php
<?php
$page = empty($_GET['page']) ? 1 : $_GET['page'];
$sql = "select count(*) as count from mzitu_title";
$result = mysqli_query($link, $sql);
$pageRes = mysqli_fetch_assoc($result);
$count = $pageRes['count'];
//每页的数据条数
$num_per_page = 20;
//最大页
$max_page = ceil($count / $num_per_page);
//偏移量
$offset = ($page - 1) * $num_per_page;
$prev = $page -1;
$next = $page + 1;
if ($prev<1){
    $prev = 1;
}
if ($next>$max_page){
    $next = $max_page;
}
?>
<html>
<body>
<a href="index.php">首页</a>
<a href="index.php?page=<?=$prev?>">上一页</a>
<a href="index.php?page=<?=$next?>">下一页</a>
<a href="index.php?page=<?=$max_page?>">尾页</a>
</body>
</html>
```

### 16、会话控制

#### `cookie`

##### 设置

```php
setcookie('name', 'zhangsan', time() + 60, '/');
//键、值、生效时间、生效路径
```

##### 销毁

```php
setcookie('name', '', time() - 1, '/');
//设置生效时间为过去的时间
```

##### 取值

```php
echo $_COOKIE['name'];
```

##### 登录

> 退出登录就销毁cookie

```php
if (empty($_COOKIE['name'])){
    exit('你没有登录');
} else {
    echo '登录成功';
}
```

#### `session`

##### 设置

```php
session_start();   //开启session
$_SESSION['user'] = 'zhangsan';
session_destroy();   //关闭session
```

##### 取值

```php
session_start();
echo $_SESSION['user'];
```

##### 销毁

```php
session_start();
unset($_SESSION['user']);
```

##### 登录

> 退出登录就销毁session

```php
session_start();
if (empty($_SESSION['user'])){
    exit('你没有登录');
} else {
    echo '登录成功';
}
```

### 17、验证码

```php
function verify($width = 100, $height = 40, $num = 5, $type = 1)
{
    $image = imagecreatetruecolor($width, $height);

    $code = '';
    switch ($type) {
        case 1:
            $str = '0123456789';
            $code = substr(str_shuffle($str), 0, $num);
            break;
        case 2:
            $arr = range('a', 'z');
            shuffle($arr);
            $arr = array_slice($arr, 0, $num);
            $code = join('', $arr);
            break;
        case 3:
            $str = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
            $code = substr(str_shuffle($str), 0, $num);
            break;
    }
    imagefilledrectangle($image, 0, 0, $width, $height,darkColor($image));
    for ($i = 0; $i < $num; $i++) {
        $x = floor($width / $num) * $i;
        $y = mt_rand(10, $height - 20);
        imagechar($image, 4, $x, $y, $code[$i], lightColor($image));
    }
for ($i = 0; $i < 50; $i++) {
        imagesetpixel($image, mt_rand(0, $width), mt_rand(0, $height), darkColor($image));
    }
    header('content-type:image/png');
    imagepng($image);
    imagedestroy($image);
    return $code;
}

function lightColor($image)
{
    return imagecolorallocate($image, mt_rand(130, 255), mt_rand(130, 255), mt_rand(130, 255));
}

function darkColor($image)
{
    return imagecolorallocate($image, mt_rand(0, 120), mt_rand(0, 120), mt_rand(0, 120));
}
```

### 18、水印

### 19、文件操作

```php
readfile('a.txt');    //输出到浏览器
$res = file('a.txt');   //返回索引数组
$str = file_get_contents('a.txt');
file_put_contents('a.txt','新内容')  //如果有内容则覆盖，如果文件不存在，则创建该文件并写入内容
```

```php
$fp = fopen('a.txt','r');   // 以指定模式打开文件获得文件句柄
// r, r+, w, W+, a, a+ 六种模式
fwrite($fp,$str);  //写入文件，模式不同，结果不同
fseek($fp,int);   // 移动文件指针到指定位置
fread($fp,len);   // 读取文件指定长度，模式不同，结果不同
fclose($fp); // 关闭文件句柄
```

```php
var_dump(pathinfo('demo.txt'));
echo basename('demo.txt');  //demo.txt
echo dirname('demo.txt')   //返回文件所在目录
array (size=4)
  'dirname' => string '.' (length=1)     // 文件目录
  'basename' => string 'demo.txt' (length=8)  // 文件全名
  'extension' => string 'txt' (length=3)  // 文件扩展名
  'filename' => string 'demo' (length=4)  // 文件名
```

```php
$arr = ['user' => 'lzl', 'pass' => '123'];
echo http_build_query($arr);
//user=lzl&pass=123

$res = parse_url('https://www.mzitu.com/page/5/?user=lzl');
var_dump($res);
array (size=4)
  'scheme' => string 'https' (length=5)
  'host' => string 'www.mzitu.com' (length=13)
  'path' => string '/page/5/' (length=8)
  'query' => string 'user=lzl' (length=8)
    
parse_str('user=lzl&pass=123');
echo $user,$pass;  //lzl 123
```

### 20、正则表达式

### 21、文件上传

### 22、模板引擎

## PHP高级

### 1、类和对象语法

```php
class Person
{
    /**
     * @$name:成员属性人的姓名
     * @$age: 成员属性人的年龄
     */
    public $name;
    public $age;

    public function __construct($name, $age)
        /**
         * 构造函数
         */
    {
        $this->name = $name;
        $this->age = $age;
    }

    public function eat()
        /**
         * 成员方法
         */
    {
        echo $this->name . "喜欢吃东西<br>";
    }
}

//定义对象的第一种语法
$lzl = new Person('林志玲', 42);
//定义对象的第二种语法
$name = 'Person';
$lyf = new $name('刘亦菲', 28);
//循环遍历对象
foreach ($lyf as $key => $value) {
    echo $key . ':' . $value . '<br>';
}
//调用对象的属性
echo $lzl->name;
//调用对象的方法
$lzl->eat();
```

### 2、继承

#### 基本语法

```php
class Child extends Parent {
    
}
//子类会继承父类的属性和方法
```

#### 访问权限

1. 在类的外部，只可以直接访问public

2. public和protected都可以被子类继承

3. private不能被子类继承,可以在父类里面通过方法调用，然后把方法派生给子类，不能直接在子类内部调用父类的private

   ```php
   class Human(){
       public $money = 3000;
       protected $car = 'BMW';
       private $gf = 'mv';
   }
   ```


#### 重写

##### 覆盖重写

##### 增加功能重写(parent关键字)

```php
//调用父类的普通方法
public function say()
    {
       echo $this->name.'身高'.$this->height.'<br>';
    }

public function say(){
    parent::say();
    echo $this->name.'是老师<br>';
}
//调用父类构造方法
class Actor extends Person
{
    public $weight;
    public function __construct($name, $age, $height,$weight)
    {
        parent::__construct($name, $age, $height);
        $this->weight=$weight;
    }
}
```

##### final关键字

```php
final class Person{
    //此类不能被继承
}
final public function work(){
    //此方法不能被重写
}
```

##### 重写方法中的权限修改

1. 重写的时候权限只能放大不能缩小
2. public -> public
3. protected -> protected public 
4. private -> private protected public

### 3、魔术方法

> 系统在特定的时间自动调用的方法
>
> 不可见成员是指私有的、受保护的或者不存在的成员。

#### `__get(属性名)`

##### 触发时间：对象在外部`访问`不可见成员时调用

```php
public function __get($name)
{
    if ($name=='age'){
        return $this->age;
    }
    if ($name='height'){
        return $this->height;
    }
}
```

#### `__set(属性名,要设置的值)`

##### 触发时间：对象在外部`设置`不可见成员时调用

```php
public function __set($name, $value)
{
    if ($name == 'age') {
        $this->age = $value;
    }
}
```

#### `__unset(属性名)`

##### 触发时间：对象在外部`销毁`不可见成员时调用

```php
public function __unset($name)
{
    if ($name=='age'){
        unset($this->age);
    }else {
        echo '不允许删除';
    }
}
```

#### `__isset(属性名)`

##### 触发时间：对象在外部`isset/empty`不可见成员时调用

```php
public function __isset($name)
{
    return isset($this->$name);
}
```

#### `__construct():构造方法`

##### 触发时间：`创建`对象的时候自动调用

#### `__destruct():析构方法`

##### 触发时间：`销毁`对象的时候自动调用

```php
public function __destruct()
{
	echo $this->name.'对象内存空间被释放';
}
```

#### `__toString():`

##### 触发时间：`echo`对象的时候触发,需要return字符串

```php
public function __toString()
{
    return self::class.'类'.$this->name.'<br>';
}
```

#### `__debugInfo():`

##### 触发时间：`var_dump()`对象的时候触发，需要return一个数组

```php
public function __debugInfo()
{
    return ['age'=>$this->age,'height'=>$this->height];
}
```

#### `__call(函数名，参数数组):`

##### 触发时间：调用不存在的对象方法时候触发

```php
public function __call($name, $arguments)
{

}
```

#### `__callStatic(函数名，参数数组):`

##### 触发时间：调用不存在的静态方法时候触发

#### `serialize()`：序列化

#### `unserialize()`：反序列化

#### 魔术方法的意义

### 4、常量、静态属性和方法

#### 静态属性和方法:`static`关键字

```php
class Math{
    static public $name='林志玲';
    //静态属性的定义
    static public function add($a,$b){
        //静态方法的定义
        return $a + $b;
    }
}
Math::add(1,2); //静态方法的调用
Math::$name; //静态属性的调用
```

#### 类常量:`const`关键字

```php
class Math{
    const PI = 3.14; //类常量的定义
}
Math::PI; //类常量的调用
```

#### 单例模式

```php
class Single{
    public $rand;
    static protected $ins;
    final private function __construct(){
        $this->rand=mt_rand(10000,99999);
    }
    static public function getIns(){
        if(self::$ins==null){
            self::$ins = new self();
        }
        return self::$ins;
    }
}
$a = Single::getIns();
$b = Single::getIns();
```

### 5、自动加载

```php
function myLoad($class){
    require('./lib/'.$class.'.php');
}
spl_autoload_register('myLoad');
//实例化不存在的类的时候，调用指定的函数
$a = new mysql();
```

### 6、抽象类

```php
/**
 * 面向接口编程
 */
abstract class aDB{
    /**
     * [conn 连接数据库]
     * @return [数据库连接] [数据库连接]
     */
    abstract public function conn();
    /**
     * [getAll 查询多条记录]
     * @return [array] [查询数据库的结果二维数组]
     */
    abstract public function getAll();
}
// 实现
class Mysql extends aDB{
    public function conn(){

    }

    public function getAll(){

    }
}
//使用
class Mysql extends aDB{
    $this->conn();
    $this->getAll();
}
```

### 7、接口

- 接口本身就是抽象的，方法前不用加abstract

- 接口里的方法，只能是public

- 类可以同时实现多个接口

  > 抽象类：相当于一类事物的规范。
  >
  > 接口：组成事物的零件的规范。

```php
interface flyer{
    public function fly($oil,$height);
}
interface runner{
    public function run($speed,$dir);
}
interface swimer{
    public function swim($dir);
}

class Super implements flyer,runner{
    public function fly($oil,$height){

    }
    public function run($speed,$dir){

    }
}

$a = new Super();
$a->fly(10,20);
```

### 8、trait

### 9、命名空间

### 10、异常处理

### 11、PDO

## PHP高级实战

### 1、验证码类

### 2、分页类

### 3、文件上传类

### 4、图像处理类

### 5、数据库操作类

### 6、模板引擎类

### 7、设计模式

### 8、自己搭建MVC框架
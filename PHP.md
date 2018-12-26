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